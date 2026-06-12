---
title: "Flash plugin not installed"
date: 2006-10-24
forum: Multimedia &amp; Video
---

### Post by Jonathan Métillon on 2006-10-24
Hi,

I just installed flashplugin-nonfree on Ubuntu 6.06 using apt-get:

```
$ sudo apt-get install flashplugin-nonfree
The following NEW packages will be installed
  flashplugin-nonfree
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Setting up flashplugin-nonfree (7.0.63.3ubuntu3) ...
```So it's ok for this part. But when I go on any website that use Flash using my gecko-powered browser, like disney.go.com, it says I've no Flash.

Indeed, in the about:plugin page I can't find anything Flash related. And I have no ~/.mozilla/plugins directory.

What's going on?

---

### Post by x64Jimbo on 2006-10-24
Have you tried installing the plugin by clicking on the green puzzle piece that comes up in place of the flash movie?

---

### Post by Hobbes on 2006-10-24
download the brand new Flash 9 plugin here: [http://labs.adobe.com/downloads/flashplayer9.html](http://labs.adobe.com/downloads/flashplayer9.html) 

Then read the readme and follow its instructions, basically drop the .so file in /usr/lib/firefox/plugins/   (requires a sudo cp or sudo mv).

Then you will not only have flash but it will work with audio properly (Flash 7 does not on flash movies like youtube), but you can go to flash 8 and flash 9 sites!

Enjoy.

---

### Post by Jonathan Métillon on 2006-10-24
Thank you Hobbes, that fixed the issue!

Flash 9, at last! Wow! :D

---

