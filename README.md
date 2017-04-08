# api documentation for  [gulp-changed (v2.0.0)](https://github.com/sindresorhus/gulp-changed#readme)  [![npm package](https://img.shields.io/npm/v/npmdoc-gulp-changed.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-gulp-changed) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-gulp-changed.svg)](https://travis-ci.org/npmdoc/node-npmdoc-gulp-changed)
#### Only pass through changed files

[![NPM](https://nodei.co/npm/gulp-changed.png?downloads=true)](https://www.npmjs.com/package/gulp-changed)

[![apidoc](https://npmdoc.github.io/node-npmdoc-gulp-changed/build/screenCapture.buildNpmdoc.browser.%252Fhome%252Ftravis%252Fbuild%252Fnpmdoc%252Fnode-npmdoc-gulp-changed%252Ftmp%252Fbuild%252Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-gulp-changed/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-gulp-changed/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-gulp-changed/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Sindre Sorhus",
        "email": "sindresorhus@gmail.com",
        "url": "sindresorhus.com"
    },
    "bugs": {
        "url": "https://github.com/sindresorhus/gulp-changed/issues"
    },
    "contributors": [
        {
            "name": "Alex Gorbatchev",
            "url": "github.com/alexgorbatchev"
        },
        {
            "name": "Bo-Yi Wu",
            "url": "github.com/appleboy"
        },
        {
            "name": "Milan Gardian",
            "url": "github.com/milang"
        }
    ],
    "dependencies": {
        "gulp-util": "^3.0.0",
        "through2": "^2.0.0"
    },
    "description": "Only pass through changed files",
    "devDependencies": {
        "del": "^2.2.2",
        "get-stream": "^3.0.0",
        "gulp": "^3.0.0",
        "mocha": "^3.2.0",
        "xo": "*"
    },
    "directories": {},
    "dist": {
        "shasum": "7396d95aeab35c6bcbcb75169fd7f24a271a013b",
        "tarball": "https://registry.npmjs.org/gulp-changed/-/gulp-changed-2.0.0.tgz"
    },
    "engines": {
        "node": ">=4"
    },
    "files": [
        "index.js"
    ],
    "gitHead": "d836d67941172c4182dd632b766dde8e717655a2",
    "homepage": "https://github.com/sindresorhus/gulp-changed#readme",
    "keywords": [
        "gulpplugin",
        "file",
        "files",
        "changed",
        "newer",
        "modified",
        "modification",
        "updated",
        "time",
        "mtime",
        "stat",
        "cache",
        "cached",
        "passthrough"
    ],
    "license": "MIT",
    "maintainers": [
        {
            "name": "sindresorhus",
            "email": "sindresorhus@gmail.com"
        }
    ],
    "name": "gulp-changed",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git+https://github.com/sindresorhus/gulp-changed.git"
    },
    "scripts": {
        "test": "xo && mocha"
    },
    "version": "2.0.0"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module gulp-changed](#apidoc.module.gulp-changed)
1.  [function <span class="apidocSignatureSpan">gulp-changed.</span>compareLastModifiedTime (stream, cb, sourceFile, targetPath)](#apidoc.element.gulp-changed.compareLastModifiedTime)
1.  [function <span class="apidocSignatureSpan">gulp-changed.</span>compareSha1Digest (stream, cb, sourceFile, targetPath)](#apidoc.element.gulp-changed.compareSha1Digest)



# <a name="apidoc.module.gulp-changed"></a>[module gulp-changed](#apidoc.module.gulp-changed)

#### <a name="apidoc.element.gulp-changed.compareLastModifiedTime"></a>[function <span class="apidocSignatureSpan">gulp-changed.</span>compareLastModifiedTime (stream, cb, sourceFile, targetPath)](#apidoc.element.gulp-changed.compareLastModifiedTime)
- description and source-code
```javascript
function compareLastModifiedTime(stream, cb, sourceFile, targetPath) {
	fs.stat(targetPath, (err, targetStat) => {
		if (!fsOperationFailed(stream, sourceFile, err)) {
			if (sourceFile.stat && sourceFile.stat.mtime > targetStat.mtime) {
				stream.push(sourceFile);
			}
		}

		cb();
	});
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.gulp-changed.compareSha1Digest"></a>[function <span class="apidocSignatureSpan">gulp-changed.</span>compareSha1Digest (stream, cb, sourceFile, targetPath)](#apidoc.element.gulp-changed.compareSha1Digest)
- description and source-code
```javascript
function compareSha1Digest(stream, cb, sourceFile, targetPath) {
	fs.readFile(targetPath, (err, targetData) => {
		if (sourceFile.isNull()) {
			cb(null, sourceFile);
			return;
		}

		if (!fsOperationFailed(stream, sourceFile, err)) {
			const sourceDigest = sha1(sourceFile.contents);
			const targetDigest = sha1(targetData);

			if (sourceDigest !== targetDigest) {
				stream.push(sourceFile);
			}
		}

		cb();
	});
}
```
- example usage
```shell
n/a
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
