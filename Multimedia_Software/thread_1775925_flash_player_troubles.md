---
title: "flash player troubles"
date: 2011-06-05
forum: Multimedia Software
---

### Post by jimbean on 2011-06-05
this is what i get when i try to install flash from synaptic

adobe-flashplugin:
 Depends: libgdk-pixbuf2.0-0 (>=2.21.6) but it is not installable
 Recommends: adobe-flash-properties-gtk but it is not going to be   
 installed or
 adobe-flash-properties-kde but it is not going to be installed

-----------------------------------------------------------------------

adobe-flash-properties-kde:
 Depends: adobe-flashplugin but it is not going to be installed
 Depends: libkdecore5 (>=4:4.3.4) but it is not installable
 Depends: libkdeui5 (>=4:4.3.4) but it is not installable
 Depends: libkutils4  but it is not installable




adobe-flash-properties-gtk:
 Depends: adobe-flashplugin but it is not going to be installed
 Depends: libgdk-pixbuf2.0-0 (>=2.21.6) but it is not installable

---

### Post by wolfen69 on 2011-06-05
Are you trying to get flash for firefox? You could also go [here]("http://get.adobe.com/flashplayer/") and download the .tar.gz file, extract it, and put libflashplayer.so into /home/user_name/.mozilla/plugins

Restart firefox.

---

### Post by jimbean on 2011-06-05
thankyou i created the plugin folder and installed libflashplayer.so ,into it
worked for me solved thanks

---

### Post by lovinglinux on 2011-06-05
You won't be able to get updates this way.

Get [Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/). It automates that process and also check for the latest beta releases from Adobe and warn you when you need to update. Additionally, it apply performance tweaks and remove conflicting plugins.

---

