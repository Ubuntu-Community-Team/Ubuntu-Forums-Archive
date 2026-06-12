---
title: "Flash works fine in Konqueror, but No Sound in Firefox"
date: 2009-08-22
forum: Multimedia Software
---

### Post by _axiom_ on 2009-08-22
I don't think the problem is with Flash, since HTML5 Video is also silent.

```
about:plugins
``` tells me I am running Flash 10.0 d21 in both browsers.

I have tried things such as uninstalling (with --purge) and reinstalling Firefox with apt, and removing and reinstalling  flashplugin-installer flashplugin-nonfree  

One place suggested doing something with [PulseAudio]("http://ubuntuforums.org/showthread.php?p=7208079"), but another place informed me that Kubuntu [does not use PulseAudio]("http://ubuntuforums.org/showthread.php?t=789578").

Another post suggested that I edit [/etc/firefox/firefoxrc]("http://www.macewan.org/2006/06/01/howto-firefox-flash-video-sound-on-ubuntu-linux-dapper/"), but I had no file there.  Added one with the suggested line, but to no effect. 

I am running the apt-gettable 3.5.2 version of Firefox.



==These People seem to be having the same propblem==
[https://bugs.launchpad.net/ubuntu/+bug/367173](https://bugs.launchpad.net/ubuntu/+bug/367173)

---

