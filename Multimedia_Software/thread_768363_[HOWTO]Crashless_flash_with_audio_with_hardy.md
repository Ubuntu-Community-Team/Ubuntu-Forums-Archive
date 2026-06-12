---
title: "[HOWTO]Crashless flash with audio with hardy"
date: 2008-04-26
forum: Multimedia Software
---

### Post by artir on 2008-04-26
From [Conn's post]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/192888/comments/39") in launchpad:

1.Install this
[URL="http://launchpadlibrarian.net/13470096/nspluginwrapper_0.9.91.5-2ubuntu2_i386.deb"]
http://launchpadlibrarian.net/13470096/nspluginwrapper_0.9.91.5-2ubuntu2_i386.deb[/URL]

1.5 Install libflashsupport
sudo apt-get install libflashsupport

2.Run

sudo apt-get remove --purge flashplugin-nonfree
sudo apt-get install flashplugin-nonfree

Restart firefox et voilá!

---

### Post by kiddo on 2008-06-21
I had stopped believing in humanity. This solution works, even with epiphany's tab-closing problem and flash 9. Here, let me give you a hug :)

---

### Post by wh0rd on 2008-06-21
This is actually a great solution. It should be made a sticky, as a lot of users are having issues with Firefore/Flashaudio/crashing.

---

