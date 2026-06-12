---
title: "Audio playing from ALSA skips"
date: 2008-08-23
forum: Multimedia Software
---

### Post by Sinkingships7 on 2008-08-23
Whenever I play music or sound from my browser (YouTube, purevolume), everything works great. No problems there. But whenever I try to play music from a program like Rhythmbox, I get these odd 'skips' a second or two, maybe once every 30 seconds or so of the song. This problem persists with every song with every music playing application, including XMMS2+Esperanza. 

Having read other threads that lead me to believe that the problem was in PulseAudio, I attempted various fixes, but to no prevail. I did a clean command-line install of Ubuntu, which DOES NOT come with PulseAudio; only ALSA. The problem continues anyway. Which means that it is NOT PulseAudio's fault, but rather ALSA's. 

Does anybody else have this problem? Does anybody know how to fix this problem?

---

### Post by Sinkingships7 on 2008-08-23
If it helps, I just tried the new Songbird, and the problem is dramatically decreased. It happens rarely, if ever.

---

### Post by Alka-Seltzer PLUS on 2009-06-03
same problem on jaunty ... :(

---

### Post by Lantesh on 2009-06-20
I have the exact same problem in Mint 7 (based in Jaunty).  Any experts out there have any ideas?

---

### Post by Lantesh on 2009-06-30
I found a solution that works, but it's not for the squeamish.  Therefore I'm going to keep this guide brief, and if you understand what I'm talking about then you will have no issues.  If you don't then well...don't try this.  If you do this wrong your system will be hosed.

Ok so what you need to do is edit your sources.list file and add the Karmic Koala repos.  Sudo apt-get update and then install the 2.6.30-10 kernel via Synaptic.  Don't forget the headers too.  While you are in there upgrade ALSA, the Gstreamer codecs, and Pulse Audio.  Be very careful what packages you mark for upgrade.  Pay particular attention to what packages will be removed, and don't upgrade a package if you think it's going to mess something up.  There were one or two things I had marked, but then unmarked.  Just be careful and use common sense.

If you've got an Nvidia graphics card: Reboot, and start up in to low graphics mode.  Next go back into synaptic and upgrade from the 180 to the 185 drivers.  You need the 185 drivers for this kernel.  You have to do this.  Now go into the Hardware drivers tool in the administrative menu, and enable the drivers.  It's only going to show 173 and 180.  Just pick 180 and it will enable the 185 drivers.

Reboot and choose the new kernel.  Everything should load fine.  As long as you didn't mess with your xorg.conf file video should work correctly now that the 185 drivers are enabled.

Finally remove the Karmic repos from your sources.list file and sudo apt-get update again.

If you've got an ATI graphics card I can't help you.  I've never used one with Linux.

I can tell you with 99.9% certainty that this fixed all my audio issues.  I leave the .1% to chance, because hey you never know.

Good luck.  8)

---

