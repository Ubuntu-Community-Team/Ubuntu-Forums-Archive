---
title: "Help with Kaffeine  in version 10.10"
date: 2010-10-23
forum: Multimedia Software
---

### Post by leeper69 on 2010-10-23
Hi I have been using  kaffeine to watch and record video with Ubuntu 10.4-1 and everything works fine but when I downloaded version 10.10 I can no longer get Kaffeine to work it will find the channels in my area but when I try to play them I get this error message ( cannot find demux plug in for MRL
fifo:/home/us/.kde/share/apps/kaffeine/dvbpipe.m2t) I don't understand this message! I am using Gnome not KDE for my desktop and this directory is not in the Ubuntu 10.4-1 operating system either and Kaffeine works perfectly with  that version. Has anyone else had this problem?

---

### Post by sofasurfer on 2010-10-23
Well, since nobody has answered you, let me throw my question out there too.

I just installed Lucid (10.04).

Installed multimedia-Howto. Did not install the "audio & video streaming" section because I was not sure how to proceed since it appears that the proceedure removes kaffeine, which I want to keep. So I don't know if I should just go ahead and follow it or what? And do I use option 1 or option 2?

I opened Kaffeine and ran the channel search and it went smoothly. But when I tried to watch a channel I got this message, "Cannot find demux plugin for MRL "fifo:/home/daryl/.kde/share/apps/kaffeine/dvbpipe.m2t".

So gurus. We need your help. Please? I need my tv :-)

---

### Post by sofasurfer on 2010-10-24
I just stumbled onto my solution. Its at [http://ubuntuforums.org/showthread.php?t=1482558](http://ubuntuforums.org/showthread.php?t=1482558)
The answer is to run "sudo apt-get install libxine1-all-plugins".
Fixed mine immediately.

---

### Post by leeper69 on 2010-10-24
THANK YOU SOFASURFER!!!!!!!!!!!
that did the trick Kaffeine is back to working.

---

### Post by sofasurfer on 2010-10-24
Once in a while I get something right :-)

---

### Post by venik212 on 2010-12-22
I have done all these things, and I am still getting the Cannot find demux plugin... etc.

---

