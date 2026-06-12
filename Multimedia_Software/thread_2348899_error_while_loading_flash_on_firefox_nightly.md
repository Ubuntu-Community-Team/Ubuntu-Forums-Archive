---
title: "error while loading flash on firefox nightly"
date: 2017-01-09
forum: Multimedia Software
---

### Post by ajgreeny on 2017-01-09
I suggest you remove all flashplugin packages you have installed at present that include **flash**, **pepperflash** or **gnash** in their names, ie,

browser-plugin-freshplayer-pepperflash
pepperflashplugin-nonfree
flashplugin-installer
gnash
gnash-common

then enable the canonical-partner repos and install just the **adobe-flashplugin** package which will also pull in **adobe-flashplugin-gtk**; that should now be the only packages needed in any browser.
Chrome uses its inbuilt pepperflash system so no need to worry about that, if you use Chrome.

---

