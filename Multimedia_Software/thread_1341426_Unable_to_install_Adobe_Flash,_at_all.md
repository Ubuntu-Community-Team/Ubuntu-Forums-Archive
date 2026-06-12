---
title: "Unable to install Adobe Flash, at all"
date: 2009-11-29
forum: Multimedia Software
---

### Post by lukjad on 2009-11-29
Whenever I try to install Adobe Flash, something goes wrong. I've tried to reinstall it multiple ways, remove configuration files for Firefox 3.5 and Adobe, and the error still continues. Anyone have any ideas?

I'm using Firefox 3.5 on Ubuntu 9.04. The error message is below.

```
lukjad007@stationy:~$ sudo apt-get install flashplugin-nonfree 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  flashplugin-installer nspluginwrapper
Suggested packages:
  konqueror-nsplugins ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-installer flashplugin-nonfree nspluginwrapper
0 upgraded, 3 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B/213kB of archives.
After this operation, 782kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package nspluginwrapper.
(Reading database ... 381870 files and directories currently installed.)
Unpacking nspluginwrapper (from .../nspluginwrapper_1.2.2-0ubuntu5_amd64.deb) ...
Selecting previously deselected package flashplugin-installer.
Unpacking flashplugin-installer (from .../flashplugin-installer_10.0.22.87ubuntu2_amd64.deb) ...
Selecting previously deselected package flashplugin-nonfree.
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_10.0.22.87ubuntu2_amd64.deb) ...
Processing triggers for man-db ...
Setting up nspluginwrapper (1.2.2-0ubuntu5) ...
plugin dirs: :/var/lib/flashplugin-installer/
Auto-update plugins from /usr/lib/mozilla/plugins
Looking for plugins in /usr/lib/mozilla/plugins
Auto-update plugins from /usr/lib64/mozilla/plugins
Looking for plugins in /usr/lib64/mozilla/plugins
Auto-update plugins from /usr/lib/firefox/plugins
Looking for plugins in /usr/lib/firefox/plugins
Auto-update plugins from /usr/lib64/firefox/plugins
Looking for plugins in /usr/lib64/firefox/plugins
Auto-update plugins from /var/lib/flashplugin-installer/
Looking for plugins in /var/lib/flashplugin-installer/
Auto-update plugins from /root/.mozilla/plugins
Looking for plugins in /root/.mozilla/plugins

Setting up flashplugin-installer (10.0.22.87ubuntu2) ...
Downloading...
--2009-11-29 18:04:33--  http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.0.22.87.orig.tar.gz
Resolving archive.canonical.com... 91.189.90.142
Connecting to archive.canonical.com|91.189.90.142|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2009-11-29 18:04:34 ERROR 404: Not Found.

download failed
The Flash plugin is NOT installed.

Setting up flashplugin-nonfree (10.0.22.87ubuntu2) ...
lukjad007@stationy:~$
```

---

### Post by lukjad on 2009-11-29
I happened to notice the excellent guide [here]("http://ubuntuforums.org/showthread.php?t=766683"), and decided to give it a try. It fixed all of my issues and now I have flash back. I wish there was a thanks button for the forum still, because he earned it. :)

---

