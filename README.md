Buffer Extensions Master Repo
=============================

For help with using this repo and it's nested repos see the [Buffer hackpad](https://buffer.hackpad.com/Extensions-Shared-Repos-101-7AswcCRsHEI).

## Install

After cloning the repo, you'll need all of the subrepos. To pull in nested subrepos:

    $ git submodule update --recursive --merge --init

To install all necessary packages for grunt:

    $ npm install -g grunt-cli
    $ npm install

Download the Firefox addon SDK and checkout the most recent stable
[release](https://github.com/mozilla/addon-sdk/releases):

    $ curl https://ftp.mozilla.org/pub/mozilla.org/labs/jetpack/addon-sdk-1.17.tar.gz | tar xz
    $ mv addon-sdk-1.17 sdks/firefox

If this file is not available use the SDK github repo

    $ git clone https://github.com/mozilla/addon-sdk.git sdks/firefox
    $ cd sdks/firefox
    $ git checkout tags/1.17

## Build

* **Chrome** - Run `grunt chrome` to build
* **Firefox** - Run `grunt firefox` to build both the Buffer-hosted and the
addon.mozilla.org version
* **Safari** - Get a Safari developer cert from a team member and use the Safari
Extension Builder to create a `.safariextz` file
* **Opera** - Check out the "opera" branch in the `buffer-chrome` repo, merge
master into that branch. Grab the `chrome.pem` key from the Buffer Dropbox
(Buffer Engineering/Extensions/Opera), and use that to build the `.nex` file in
the panel at "opera://extensions".

## Deploy

[Deploy information](https://buffer.hackpad.com/Extensions-Shared-Repos-101-7AswcCRsHEI#:h=Deploying).

## Grunt helper tasks

Update the nested "buffer-<browser>" repos.

    $ grunt update-repos

Update the nested "buffer-extension-shared" repos in each browser repo.

    $ grunt update-shared

Update the version in main `package.json` and have it update each browser's
version.

    $ grunt update-versions

## Test

This currently only tests the Chrome sub-repo's shared code.

    $ grunt mocha

## Build

    $ grunt chrome
    $ grunt firefox
