---
title: "Audio-Recorder v1.5 relased for Ubuntu 14.10 (Utopic)"
date: 2014-10-10
forum: Multimedia Software
---

### Post by osmoma on 2014-10-10
[COLOR=#000000]Audio-recorder is now available for Ubuntu 14.10.[/COLOR]
[[IMG]http://bildr.no/thumb/RnZINm0w.jpeg[/IMG]]("http://bildr.no/view/RnZINm0w")
[COLOR=#000000]
Source code: [/COLOR][https://launchpad.net/audio-recorder](https://launchpad.net/audio-recorder)
Packages for Ubuntu 14.10: [https://launchpad.net/~osmoma/+archive/ubuntu/audio-recorder](https://launchpad.net/~osmoma/+archive/ubuntu/audio-recorder)

ChangeLog:
  * Version 1.5 (1.5-4)
* This version requires GStreamer 1.4 (eg. Ubuntu 14.10 is ok, but Ubuntu 14.04 is not).
  * Fixed autostart Bug #1312524 by deleting the file when autostart is set OFF.
  * Fixed compatibility bug in configure.ac. Ref. Bug #1379339, patched by DimStar.
  * Removed dependency to libpulse-dev (removed also files; src/pulseaudio.[ch]). 
  * Using now Gstreamer to get list of audio devices (new files; src/gst-devices.[ch], GStreamer 1.4). 
  * Notice; Fedora Linux, Arch Linux, etc, please see debian/control file for required and changed dependencies.
  * New and unplugged devices are detected automatically.  
  * User can change and add new recording pipelines. Please see [Additional settings] dialog and 
  * implementation in settings-pipe.[ch] module.
  * Improved MP3-recording with id3mux. Ref. Bug #1354973.
  * Better error message at missing Gstreamer-plugin. 
  * Automatic installation of (missing) plugins needs to be completed in next version. 
 
[COLOR=#000000]Muito obrigado e bem-vindo! [/COLOR]
You are very welcome to use it!
[COLOR=#000000]
ps. Please help to translate some new language strings to your lingua.
Ref:  [/COLOR]https://translations.launchpad.net/audio-recorder[COLOR=#000000]
[/COLOR][[img]http://bildr.no/thumb/QnRjVDJm.jpeg[/img]](http://bildr.no/view/QnRjVDJm)[COLOR=#000000]

// Moma[/COLOR]
[COLOR=#000000]Portugal/Palmela[/COLOR]

---

### Post by mc4man on 2014-10-10
Is there any advantage to getting v1.5 into trusty?
(perspective from here is that the user base for 14.10 will be small compared to 14.04

---

### Post by osmoma on 2014-10-10
You can now modify the recording pipelines in the [Additional settings] window. Many users have wanted to change the quality options to get better sound or smaller filesize, etc. Earlier the pipelines were hard-coded in src/media-profiles.c. Now it is up to the user to add new or improve existing pipes. 
Otherwise there are small bugfixes and new device management; it auto-detect new and unPlugged devices,  no need for libpulse-dev, etc.  Unfortunately automatic installation of missing plugins did not get ready for this version. Missing plugin functions failed in my tests. I need to learn more about it.

---

### Post by osmoma on 2014-10-11
Some users have reported that this version of A.r fails to compile on Ubuntu 14.04. It cannot find GstDevice functions. Those functions were added to Gstreamer version 1.4. I will investigate this issue (after I have 14.04 running i VM).

Ref: [https://bugs.launchpad.net/audio-recorder/+bug/1380043](https://bugs.launchpad.net/audio-recorder/+bug/1380043)
Status: This will not be fixed in Ubuntu 14.04. Users of Ubuntu 14.04 should run the older audio-recorder 1.4. 
Audio-recorder 1.5 is for Ubuntu 14.10 only ;-)

[COLOR=#000000][COLOR=#000000]The download numbers are just awesome.  You can also see that the ration of 32/64bit downloads is changing from 1:1 to 1:2 in trusty and to 1:3 in utopic.  So 32bits downloads are [/COLOR][/COLOR]reducing quire rapidly[COLOR=#000000][COLOR=#000000].

$ wget [/COLOR][/COLOR][www.futuredesktop.org/getstats.sh]("http://www.futuredesktop.org/getstats.sh")
[COLOR=#000000][COLOR=#000000]$ chmod +x ./getstats.sh 
[/COLOR][/COLOR]
[COLOR=#000000]$ lsb_release -sc[/COLOR]
utopic

$ ./getstats.sh
Counting 32bit downloads for utopic: audio-recorder 1.5-4~utopic 25
Counting 64bit downloads for utopic: audio-recorder 1.5-4~utopic 89
Total downloads: **114**

$ ./getstats.sh trusty
Counting 32bit downloads for trusty: audio-recorder 1.4-5~trusty 3486
Counting 64bit downloads for trusty: audio-recorder 1.4-5~trusty 6987
Total downloads: **10473**

$ ./getstats.sh quantal
Counting 32bit downloads for quantal: audio-recorder 0.9.8~quantal 7096
Counting 64bit downloads for quantal: audio-recorder 0.9.8~quantal 8286
Total downloads: **15382**

[B][B][B]Thanks for using A.r. Go even more! 
The code is probably not tampered by NSA [IMG]http://ubuntuforums.org/images/smilies/icon_wink.gif[/IMG] 
[https://launchpad.net/audio-recorder](https://launchpad.net/audio-recorder)[/B][/B][/B]

---

