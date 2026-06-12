---
title: "Fiefox sound but no video mp4"
date: 2012-07-23
forum: Multimedia Software
---

### Post by cscj01 on 2012-07-23
I am currently running Ubuntu 12.04 x64 and Firefox 14.0.1.  I went to a site that was an mp4 file.  All I got was the progress bar and controls with sound but no video.  I used Flash-Aid to install the x64 Adobe Beta version, 11.2.202.236.  When things still did not work (same symptoms), I used Flash-Aid>Help>Generate Report to see if I could determine what might be happening.  In the report, I get the following error messages:```
Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Flash symlinks


/usr/lib/mozilla/plugins/libflashplayer.so: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, stripped
/usr/lib/mozilla/plugins/flashplugin-alternative.so: broken symbolic link to `/etc/alternatives/mozilla-flashplugin'
/etc/alternatives/mozilla-flashplugin: broken symbolic link to `/usr/lib/gnash/libgnashplugin.so'
/usr/lib/flashplugin-installer/libflashplayer.so: ERROR: cannot open `/usr/lib/flashplugin-installer/libflashplayer.so' (No such file or directory)
/usr/lib/flashplugin-nonfree/libflashplayer.so: ERROR: cannot open `/usr/lib/flashplugin-nonfree/libflashplayer.so' (No such file or directory)
/usr/lib/adobe-flashplugin/libflashplayer.so: ERROR: cannot open `/usr/lib/adobe-flashplugin/libflashplayer.so' (No such file or directory)
/usr/lib/lightspark/lightspark.so: ERROR: cannot open `/usr/lib/lightspark/lightspark.so' (No such file or directory)
/usr/lib/swfdec-mozilla/libswfdecmozilla.so: ERROR: cannot open `/usr/lib/swfdec-mozilla/libswfdecmozilla.so' (No such file or directory)
/usr/lib/gnash/libgnashplugin.so: ERROR: cannot open `/usr/lib/gnash/libgnashplugin.so' (No such file or directory)
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)
/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so' (No such file or directory)
```I have been upgrading on-line since Ubuntu 9.10, so it seems I have some "Flash" modules that are not there causing broken links as well as other Flash players/plug-ins.

What is the best approach to clean up this situation so that I do not have the broken links and other plug-ins I do not need?  Also, are there other things I should look for in the report that may indicate what the problem is?

---

