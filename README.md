# api documentation for  [vision (v4.1.1)](https://github.com/hapijs/vision#readme)  [![npm package](https://img.shields.io/npm/v/npmdoc-vision.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-vision) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-vision.svg)](https://travis-ci.org/npmdoc/node-npmdoc-vision)
#### Templates rendering plugin support for hapi.js

[![NPM](https://nodei.co/npm/vision.png?downloads=true)](https://www.npmjs.com/package/vision)

[![apidoc](https://npmdoc.github.io/node-npmdoc-vision/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-vision_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-vision/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-vision/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-vision/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "bugs": {
        "url": "https://github.com/hapijs/vision/issues"
    },
    "dependencies": {
        "boom": "4.x.x",
        "hoek": "4.x.x",
        "items": "2.x.x",
        "joi": "10.x.x"
    },
    "description": "Templates rendering plugin support for hapi.js",
    "devDependencies": {
        "babel-core": "6.x.x",
        "babel-plugin-transform-react-jsx": "6.x.x",
        "code": "4.x.x",
        "ejs": "2.x.x",
        "handlebars": "4.x.x",
        "hapi": "15.x.x",
        "hapi-react-views": "6.x.x",
        "lab": "11.x.x",
        "marko": "3.x.x",
        "mustache": "2.x.x",
        "nunjucks": "2.x.0",
        "pug": ">=2.0.0-beta6",
        "react": "0.14.x",
        "react-dom": "0.14.x"
    },
    "directories": {},
    "dist": {
        "shasum": "e1b612b2d2e2f20310a039290fd49d51248f82da",
        "tarball": "https://registry.npmjs.org/vision/-/vision-4.1.1.tgz"
    },
    "engines": {
        "node": ">=4.0.0"
    },
    "gitHead": "10760955c69b54450adcaaa219ac2f945c38ee3d",
    "homepage": "https://github.com/hapijs/vision#readme",
    "keywords": [
        "view",
        "render",
        "template",
        "hapi"
    ],
    "license": "BSD-3-Clause",
    "main": "lib/index.js",
    "maintainers": [
        {
            "name": "hueniverse",
            "email": "eran@hammer.io"
        },
        {
            "name": "jagoda",
            "email": "jeffrey.jagoda@gmail.com"
        }
    ],
    "name": "vision",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git://github.com/hapijs/vision.git"
    },
    "scripts": {
        "test": "lab -a code -t 100 -L",
        "test-cov-html": "lab -a code -r html -o coverage.html"
    },
    "version": "4.1.1"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module vision](#apidoc.module.vision)
1.  [function <span class="apidocSignatureSpan">vision.</span>manager (options)](#apidoc.element.vision.manager)
1.  [function <span class="apidocSignatureSpan">vision.</span>register (server, pluginOptions, next)](#apidoc.element.vision.register)
1.  object <span class="apidocSignatureSpan">vision.</span>manager.prototype

#### [module vision.manager](#apidoc.module.vision.manager)
1.  [function <span class="apidocSignatureSpan">vision.</span>manager (options)](#apidoc.element.vision.manager.manager)

#### [module vision.manager.prototype](#apidoc.module.vision.manager.prototype)
1.  [function <span class="apidocSignatureSpan">vision.manager.prototype.</span>_compile (template, engine, settings, callback)](#apidoc.element.vision.manager.prototype._compile)
1.  [function <span class="apidocSignatureSpan">vision.manager.prototype.</span>_loadHelpers (engine)](#apidoc.element.vision.manager.prototype._loadHelpers)
1.  [function <span class="apidocSignatureSpan">vision.manager.prototype.</span>_loadPartials (engine)](#apidoc.element.vision.manager.prototype._loadPartials)
1.  [function <span class="apidocSignatureSpan">vision.manager.prototype.</span>_path (template, settings, isLayout, next)](#apidoc.element.vision.manager.prototype._path)
1.  [function <span class="apidocSignatureSpan">vision.manager.prototype.</span>_prepare (template, options, callback)](#apidoc.element.vision.manager.prototype._prepare)
1.  [function <span class="apidocSignatureSpan">vision.manager.prototype.</span>_prepareEngine (engine, next)](#apidoc.element.vision.manager.prototype._prepareEngine)
1.  [function <span class="apidocSignatureSpan">vision.manager.prototype.</span>_prepareTemplates (template, engine, options, callback)](#apidoc.element.vision.manager.prototype._prepareTemplates)
1.  [function <span class="apidocSignatureSpan">vision.manager.prototype.</span>_render (compiled, context, request, callback)](#apidoc.element.vision.manager.prototype._render)
1.  [function <span class="apidocSignatureSpan">vision.manager.prototype.</span>_response (template, context, options, request)](#apidoc.element.vision.manager.prototype._response)
1.  [function <span class="apidocSignatureSpan">vision.manager.prototype.</span>registerHelper (name, helper)](#apidoc.element.vision.manager.prototype.registerHelper)
1.  [function <span class="apidocSignatureSpan">vision.manager.prototype.</span>render (filename, context, options, callback)](#apidoc.element.vision.manager.prototype.render)



# <a name="apidoc.module.vision"></a>[module vision](#apidoc.module.vision)

#### <a name="apidoc.element.vision.manager"></a>[function <span class="apidocSignatureSpan">vision.</span>manager (options)](#apidoc.element.vision.manager)
- description and source-code
```javascript
manager = function (options) {

    Joi.assert(options, internals.schema.manager);

    // Save non-defaults values

    const engines = options.engines;
    const defaultExtension = options.defaultExtension;

    // Clone options

    const defaults = Hoek.applyToDefaultsWithShallow(internals.defaults, options, ['engines', 'context']);
    delete defaults.engines;
    delete defaults.defaultExtension;

    // Prepare manager state

    const extensions = Object.keys(engines);
    Hoek.assert(extensions.length, 'Views manager requires at least one registered extension handler');

    this._context = defaults.context;
    this._engines = {};
    this._defaultExtension = defaultExtension || (extensions.length === 1 ? extensions[0] : '');

    // Load engines

    extensions.forEach((extension) => {

        const config = engines[extension];
        const engine = {};

        if (config.compile &&
            typeof config.compile === 'function') {

            engine.module = config;
            engine.config = defaults;
        }
        else {
            Joi.assert(config, internals.schema.view);

            engine.module = config.module;
            engine.config = Hoek.applyToDefaultsWithShallow(defaults, config, ['module']);
        }

        engine.suffix = '.' + extension;
        engine.compileFunc = engine.module.compile;

        if (engine.config.compileMode === 'sync') {
            engine.compileFunc = function (str, opt, next) {

                let compiled = null;
                try {
                    compiled = engine.module.compile(str, opt);
                }
                catch (err) {
                    return next(err);
                }

                const renderer = function (context, runtimeOptions, renderNext) {

                    let rendered = null;
                    try {
                        rendered = compiled(context, runtimeOptions);
                    }
                    catch (err) {
                        return renderNext(err);
                    }

                    return renderNext(null, rendered);
                };

                return next(null, renderer);
            };
        }

        if (engine.config.isCached) {
            engine.cache = {};
        }

        // When a prepare function is provided, state needs to be initialized before trying to compile and render
        engine.ready = !(engine.module.prepare && typeof engine.module.prepare === 'function');

        // Load partials and helpers

        this._loadPartials(engine);
        this._loadHelpers(engine);

        // Set engine

        this._engines[extension] = engine;
    });
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.vision.register"></a>[function <span class="apidocSignatureSpan">vision.</span>register (server, pluginOptions, next)](#apidoc.element.vision.register)
- description and source-code
```javascript
register = function (server, pluginOptions, next) {

    server.decorate('server', 'views', function (options) {

        Hoek.assert(options, 'Missing views options');
        this.realm.plugins.vision = this.realm.plugins.vision || {};
        Hoek.assert(!this.realm.plugins.vision.manager, 'Cannot set views manager more than once');

        if (!options.relativeTo &&
            this.realm.settings.files.relativeTo) {

            options = Hoek.shallow(options);
            options.relativeTo = this.realm.settings.files.relativeTo;
        }

        const manager = new Manager(options);
        this.realm.plugins.vision.manager = manager;
        return manager;
    });

    server.decorate('server', 'render', internals.render);
    server.decorate('request', 'render', internals.render);

    server.handler('view', internals.handler);

    server.decorate('reply', 'view', function (template, context, options) {

        const realm = (this.realm.plugins.vision || this.request.server.realm.plugins.vision || {});
        Hoek.assert(realm.manager, 'Cannot render view without a views manager configured');
        return this.response(realm.manager._response(template, context, options, this.request));
    });

    return next();
}
```
- example usage
```shell
...

**You will need to install 'vision' using something like 'npm install --save vision' before you can register it.**

'''js
const server = new Hapi.Server();
server.connection({ port: 8080 });

server.register(require('vision'), (err) => {

    if (err) {
        console.log("Failed to load vision.");
    }
});
'''
**NOTE:** Vision is included with and loaded by default in Hapi < 9.0.
...
```



# <a name="apidoc.module.vision.manager"></a>[module vision.manager](#apidoc.module.vision.manager)

#### <a name="apidoc.element.vision.manager.manager"></a>[function <span class="apidocSignatureSpan">vision.</span>manager (options)](#apidoc.element.vision.manager.manager)
- description and source-code
```javascript
manager = function (options) {

    Joi.assert(options, internals.schema.manager);

    // Save non-defaults values

    const engines = options.engines;
    const defaultExtension = options.defaultExtension;

    // Clone options

    const defaults = Hoek.applyToDefaultsWithShallow(internals.defaults, options, ['engines', 'context']);
    delete defaults.engines;
    delete defaults.defaultExtension;

    // Prepare manager state

    const extensions = Object.keys(engines);
    Hoek.assert(extensions.length, 'Views manager requires at least one registered extension handler');

    this._context = defaults.context;
    this._engines = {};
    this._defaultExtension = defaultExtension || (extensions.length === 1 ? extensions[0] : '');

    // Load engines

    extensions.forEach((extension) => {

        const config = engines[extension];
        const engine = {};

        if (config.compile &&
            typeof config.compile === 'function') {

            engine.module = config;
            engine.config = defaults;
        }
        else {
            Joi.assert(config, internals.schema.view);

            engine.module = config.module;
            engine.config = Hoek.applyToDefaultsWithShallow(defaults, config, ['module']);
        }

        engine.suffix = '.' + extension;
        engine.compileFunc = engine.module.compile;

        if (engine.config.compileMode === 'sync') {
            engine.compileFunc = function (str, opt, next) {

                let compiled = null;
                try {
                    compiled = engine.module.compile(str, opt);
                }
                catch (err) {
                    return next(err);
                }

                const renderer = function (context, runtimeOptions, renderNext) {

                    let rendered = null;
                    try {
                        rendered = compiled(context, runtimeOptions);
                    }
                    catch (err) {
                        return renderNext(err);
                    }

                    return renderNext(null, rendered);
                };

                return next(null, renderer);
            };
        }

        if (engine.config.isCached) {
            engine.cache = {};
        }

        // When a prepare function is provided, state needs to be initialized before trying to compile and render
        engine.ready = !(engine.module.prepare && typeof engine.module.prepare === 'function');

        // Load partials and helpers

        this._loadPartials(engine);
        this._loadHelpers(engine);

        // Set engine

        this._engines[extension] = engine;
    });
}
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.vision.manager.prototype"></a>[module vision.manager.prototype](#apidoc.module.vision.manager.prototype)

#### <a name="apidoc.element.vision.manager.prototype._compile"></a>[function <span class="apidocSignatureSpan">vision.manager.prototype.</span>_compile (template, engine, settings, callback)](#apidoc.element.vision.manager.prototype._compile)
- description and source-code
```javascript
_compile = function (template, engine, settings, callback) {

    if (engine.cache &&
        engine.cache[template]) {

        return callback(null, engine.cache[template]);
    }

    settings.compileOptions.filename = template;            // Pass the template to Jade via this copy of compileOptions

    // Read file

    Fs.readFile(template, { encoding: settings.encoding }, (err, data) => {

        if (err) {
            return callback(Boom.badImplementation('Failed to read view file: ' + template));
        }

        engine.compileFunc(data, settings.compileOptions, (err, compiled) => {

            if (err) {
                return callback(Boom.wrap(err));
            }

            if (engine.cache) {
                engine.cache[template] = compiled;
            }

            return callback(null, compiled);
        });
    });
}
```
- example usage
```shell
...

    this._path(template, compiled.settings, false, (err, templatePath) => {

        if (err) {
return callback(err);
        }

        this._compile(templatePath, engine, compiled.settings, (err, compiledTemplate) => {

if (err) {
    return callback(err);
}

compiled.template = compiledTemplate;
...
```

#### <a name="apidoc.element.vision.manager.prototype._loadHelpers"></a>[function <span class="apidocSignatureSpan">vision.manager.prototype.</span>_loadHelpers (engine)](#apidoc.element.vision.manager.prototype._loadHelpers)
- description and source-code
```javascript
_loadHelpers = function (engine) {

    if (!engine.config.helpersPath ||
        !engine.module.registerHelper ||
        typeof engine.module.registerHelper !== 'function') {

        return;
    }

    const helpersPaths = [].concat(engine.config.helpersPath);

    helpersPaths.forEach((helpersPath) => {

        let path = internals.path(engine.config.relativeTo, helpersPath);
        if (!Path.isAbsolute(path)) {
            path = Path.join(process.cwd(), path);
        }

        Fs.readdirSync(path).forEach((file) => {

            file = Path.join(path, file);
            const stat = Fs.statSync(file);
            if (!stat.isDirectory() &&
                Path.basename(file)[0] !== '.') {

                try {
                    const helper = require(file);
                    if (typeof helper === 'function') {
                        const offset = path.slice(-1) === Path.sep ? 0 : 1;
                        const name = file.slice(path.length + offset, -Path.extname(file).length);
                        engine.module.registerHelper(name, helper);
                    }
                }
                catch (err) {
                    console.warn('WARNING: vision failed to load helper \'%s\': %s', file, err.message);
                }
            }
        });
    });
}
```
- example usage
```shell
...

        // When a prepare function is provided, state needs to be initialized before trying to compile and render
        engine.ready = !(engine.module.prepare && typeof engine.module.prepare === 'function');

        // Load partials and helpers

        this._loadPartials(engine);
        this._loadHelpers(engine);

        // Set engine

        this._engines[extension] = engine;
    });
};
...
```

#### <a name="apidoc.element.vision.manager.prototype._loadPartials"></a>[function <span class="apidocSignatureSpan">vision.manager.prototype.</span>_loadPartials (engine)](#apidoc.element.vision.manager.prototype._loadPartials)
- description and source-code
```javascript
_loadPartials = function (engine) {

    if (!engine.config.partialsPath ||
        !engine.module.registerPartial ||
        typeof engine.module.registerPartial !== 'function') {

        return;
    }

    const load = function () {

        const partialsPaths = [].concat(engine.config.partialsPath);

        partialsPaths.forEach((partialsPath) => {

            const path = internals.path(engine.config.relativeTo, partialsPath);
            const files = traverse(path);
            files.forEach((file) => {

                const offset = path.slice(-1) === Path.sep ? 0 : 1;
                const name = file.slice(path.length + offset, -engine.suffix.length).replace(/\\/g, '/');
                const src = Fs.readFileSync(file).toString(engine.config.encoding);
                engine.module.registerPartial(name, src);
            });
        });
    };

    const traverse = function (path) {

        let files = [];

        Fs.readdirSync(path).forEach((file) => {

            file = Path.join(path, file);
            const stat = Fs.statSync(file);
            if (stat.isDirectory()) {
                files = files.concat(traverse(file));
                return;
            }

            if (Path.basename(file)[0] !== '.' &&
                Path.extname(file) === engine.suffix) {

                files.push(file);
            }
        });

        return files;
    };

    load();
}
```
- example usage
```shell
...
        }

        // When a prepare function is provided, state needs to be initialized before trying to compile and render
        engine.ready = !(engine.module.prepare && typeof engine.module.prepare === 'function');

        // Load partials and helpers

        this._loadPartials(engine);
        this._loadHelpers(engine);

        // Set engine

        this._engines[extension] = engine;
    });
};
...
```

#### <a name="apidoc.element.vision.manager.prototype._path"></a>[function <span class="apidocSignatureSpan">vision.manager.prototype.</span>_path (template, settings, isLayout, next)](#apidoc.element.vision.manager.prototype._path)
- description and source-code
```javascript
_path = function (template, settings, isLayout, next) {

    // Validate path

    const isAbsolutePath = Path.isAbsolute(template);
    const isInsecurePath = template.match(/\.\.\//g);

    if (!settings.allowAbsolutePaths &&
        isAbsolutePath) {

        return next(Boom.badImplementation('Absolute paths are not allowed in views'));
    }

    if (!settings.allowInsecureAccess &&
        isInsecurePath) {

        return next(Boom.badImplementation('View paths cannot lookup templates outside root path (path includes one or more \'../\')'));
    }

    // Resolve path and extension

    let paths;
    if (isAbsolutePath) {
        paths = [template];
    }
    else {
        paths = [].concat((isLayout && settings.layoutPath) || settings.path);

        for (let i = 0; i < paths.length; ++i) {
            paths[i] = internals.path(settings.relativeTo, paths[i], template);
        }
    }

    Items.serial(paths, (path, nextFile) => {

        Fs.stat(path, (err, stats) => {

            if (!err &&
                stats.isFile()) {

                return next(null, path);
            }

            return nextFile();
        });
    },
    () => {

        return next(Boom.badImplementation('View file not found: '' + template + ''. Locations searched: [' + paths.join(',') + ']'));
    });
}
```
- example usage
```shell
...

internals.Manager.prototype._prepareTemplates = function (template, engine, options, callback) {

    const compiled = {
settings: Hoek.applyToDefaults(engine.config, options)
    };

    this._path(template, compiled.settings, false, (err, templatePath) => {

if (err) {
    return callback(err);
}

this._compile(templatePath, engine, compiled.settings, (err, compiledTemplate) => {
...
```

#### <a name="apidoc.element.vision.manager.prototype._prepare"></a>[function <span class="apidocSignatureSpan">vision.manager.prototype.</span>_prepare (template, options, callback)](#apidoc.element.vision.manager.prototype._prepare)
- description and source-code
```javascript
_prepare = function (template, options, callback) {

    options = options || {};

    const fileExtension = Path.extname(template).slice(1);
    const extension = fileExtension || this._defaultExtension;
    if (!extension) {
        return callback(Boom.badImplementation('Unknown extension and no defaultExtension configured for view template: ' + template
));
    }

    const engine = this._engines[extension];
    if (!engine) {
        return callback(Boom.badImplementation('No view engine found for file: ' + template));
    }

    template = template + (fileExtension ? '' : engine.suffix);

    // Engine is ready to render

    if (engine.ready) {
        return this._prepareTemplates(template, engine, options, callback);
    }

    // Engine needs initialization

    return this._prepareEngine(engine, (err) => {

        if (err) {
            return callback(err);
        }

        return this._prepareTemplates(template, engine, options, callback);
    });
}
```
- example usage
```shell
...

internals.Manager.prototype.render = function (filename, context, options, callback) {

    if (!callback) {
return internals._wrapMethod(this, this.render, [filename, context, options]);
    }

    this._prepare(filename, options, (err, compiled) => {

if (err) {
    return callback(err);
}

this._render(compiled, context, null, (err, rendered) => {
...
```

#### <a name="apidoc.element.vision.manager.prototype._prepareEngine"></a>[function <span class="apidocSignatureSpan">vision.manager.prototype.</span>_prepareEngine (engine, next)](#apidoc.element.vision.manager.prototype._prepareEngine)
- description and source-code
```javascript
_prepareEngine = function (engine, next) {

    // _prepareEngine can only be invoked when the prepare function is defined

    try {
        return engine.module.prepare(engine.config, (err) => {

            if (err) {
                return next(err);
            }

            engine.ready = true;
            return next();
        });
    }
    catch (err) {
        return next(err);
    }
}
```
- example usage
```shell
...

if (engine.ready) {
    return this._prepareTemplates(template, engine, options, callback);
}

// Engine needs initialization

return this._prepareEngine(engine, (err) => {

    if (err) {
        return callback(err);
    }

    return this._prepareTemplates(template, engine, options, callback);
});
...
```

#### <a name="apidoc.element.vision.manager.prototype._prepareTemplates"></a>[function <span class="apidocSignatureSpan">vision.manager.prototype.</span>_prepareTemplates (template, engine, options, callback)](#apidoc.element.vision.manager.prototype._prepareTemplates)
- description and source-code
```javascript
_prepareTemplates = function (template, engine, options, callback) {

    const compiled = {
        settings: Hoek.applyToDefaults(engine.config, options)
    };

    this._path(template, compiled.settings, false, (err, templatePath) => {

        if (err) {
            return callback(err);
        }

        this._compile(templatePath, engine, compiled.settings, (err, compiledTemplate) => {

            if (err) {
                return callback(err);
            }

            compiled.template = compiledTemplate;

            // No layout

            if (!compiled.settings.layout) {
                return callback(null, compiled);
            }

            // With layout

            this._path((compiled.settings.layout === true ? 'layout' : compiled.settings.layout) + engine.suffix, compiled.settings
, true, (err, layoutPath) => {

                if (err) {
                    return callback(err);
                }

                this._compile(layoutPath, engine, compiled.settings, (err, layout) => {

                    if (err) {
                        return callback(err);
                    }

                    compiled.layout = layout;
                    return callback(null, compiled);
                });
            });
        });
    });
}
```
- example usage
```shell
...
    }

    template = template + (fileExtension ? '' : engine.suffix);

    // Engine is ready to render

    if (engine.ready) {
return this._prepareTemplates(template, engine, options, callback);
    }

    // Engine needs initialization

    return this._prepareEngine(engine, (err) => {

if (err) {
...
```

#### <a name="apidoc.element.vision.manager.prototype._render"></a>[function <span class="apidocSignatureSpan">vision.manager.prototype.</span>_render (compiled, context, request, callback)](#apidoc.element.vision.manager.prototype._render)
- description and source-code
```javascript
_render = function (compiled, context, request, callback) {

    if (this._context) {
        let base = typeof this._context === 'function' ? this._context(request) : this._context;
        if (context) {
            base = Hoek.shallow(base);
            const keys = Object.keys(context);
            for (let i = 0; i < keys.length; ++i) {
                const key = keys[i];
                base[key] = context[key];
            }
        }

        context = base;
    }

    context = context || {};

    if (compiled.layout &&
        context.hasOwnProperty(compiled.settings.layoutKeyword)) {

        return callback(Boom.badImplementation('settings.layoutKeyword conflict', { context, keyword: compiled.settings.layoutKeyword
 }));
    }

    compiled.template(context, compiled.settings.runtimeOptions, (err, renderedContent) => {

        if (err) {
            return callback(Boom.badImplementation(err.message, err));
        }

        // No layout

        if (!compiled.layout) {
            return callback(null, renderedContent);
        }

        // With layout

        context[compiled.settings.layoutKeyword] = renderedContent;
        compiled.layout(context, compiled.settings.runtimeOptions, (err, renderedWithLayout) => {

            delete context[compiled.settings.layoutKeyword];

            if (err) {
                return callback(Boom.badImplementation(err.message, err));
            }

            return callback(null, renderedWithLayout);
        });
    });
}
```
- example usage
```shell
...

    this._prepare(filename, options, (err, compiled) => {

if (err) {
    return callback(err);
}

this._render(compiled, context, null, (err, rendered) => {

    if (err) {
        return callback(err);
    }

    return callback(null, rendered, compiled.settings);
});
...
```

#### <a name="apidoc.element.vision.manager.prototype._response"></a>[function <span class="apidocSignatureSpan">vision.manager.prototype.</span>_response (template, context, options, request)](#apidoc.element.vision.manager.prototype._response)
- description and source-code
```javascript
_response = function (template, context, options, request) {

    Joi.assert(options, internals.schema.viewOverride);

    const source = { manager: this, template, context, options };
    return request.generateResponse(source, { variety: 'view', marshal: internals.marshal, prepare: internals.prepare });
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.vision.manager.prototype.registerHelper"></a>[function <span class="apidocSignatureSpan">vision.manager.prototype.</span>registerHelper (name, helper)](#apidoc.element.vision.manager.prototype.registerHelper)
- description and source-code
```javascript
registerHelper = function (name, helper) {

    Object.keys(this._engines).forEach((extension) => {

        const engine = this._engines[extension];

        if (typeof engine.module.registerHelper === 'function') {
            engine.module.registerHelper(name, helper);
        }
    });
}
```
- example usage
```shell
...
        Path.basename(file)[0] !== '.') {

        try {
            const helper = require(file);
            if (typeof helper === 'function') {
                const offset = path.slice(-1) === Path.sep ? 0 : 1;
                const name = file.slice(path.length + offset, -Path.extname(file).length);
                engine.module.registerHelper(name, helper);
            }
        }
        catch (err) {
            console.warn('WARNING: vision failed to load helper \'%s\': %s', file, err.message);
        }
    }
});
...
```

#### <a name="apidoc.element.vision.manager.prototype.render"></a>[function <span class="apidocSignatureSpan">vision.manager.prototype.</span>render (filename, context, options, callback)](#apidoc.element.vision.manager.prototype.render)
- description and source-code
```javascript
render = function (filename, context, options, callback) {

    if (!callback) {
        return internals._wrapMethod(this, this.render, [filename, context, options]);
    }

    this._prepare(filename, options, (err, compiled) => {

        if (err) {
            return callback(err);
        }

        this._render(compiled, context, null, (err, rendered) => {

            if (err) {
                return callback(err);
            }

            return callback(null, rendered, compiled.settings);
        });
    });
}
```
- example usage
```shell
...
        html: {
            compile: function (template) {

                Mustache.parse(template);

                return function (context) {

                    return Mustache.render(template, context);
                };
            }
        }
    },
    relativeTo: __dirname,
    path: 'templates'
});
...
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
