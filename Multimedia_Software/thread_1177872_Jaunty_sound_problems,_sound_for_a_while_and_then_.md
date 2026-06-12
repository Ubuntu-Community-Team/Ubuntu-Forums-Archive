---
title: "Jaunty sound problems, sound for a while and then non"
date: 2009-06-03
forum: Multimedia Software
---

### Post by cahlfors on 2009-06-03
Hi,

I have recent come across this problem with my sound in Jaunty.
When I try to play sounds music movies or what ever, there will be sound for a while, maybe a couple mins max, then it will start crackling and there is no other sound. If I'm playing a movie it will do the same, but the movie will start to fast forward as well. I have tried changing sound preferences as a work around for now, and found that it happens with both pulse audio and alsa. OSS is working, but there is a small skip from time to time. I have gotten use to that, but flash player cant use OSS, so no youtube, and its frustrating.

I'm not sure how this happened, but I think it may have started after a recent update maybe 2-3 weeks ago.

Oh, and sound works just perfectly in vista and win7 so, the card itself should have no problems.

So if some one can help I would be very grateful. :D
Just give me the commands for what info you need and I'll post it back.


Carl-Eric

---

### Post by phanidee on 2009-06-06
same problem here, any help would be greatly appreciated.

-
Phani

---

### Post by cahlfors on 2009-06-30
Does anyone have any clue at all?

Please help.



Carl-Eric

---

### Post by Lantesh on 2009-06-30
I had this issue too in Mint 7 (based on Jaunty). Here is my reply/fix from another thread:

I found a solution that works, but it's not for the squeamish. Therefore I'm going to keep this guide brief, and if you understand what I'm talking about then you will have no issues. If you don't then well...don't try this. If you do this wrong your system will be hosed.

Ok so what you need to do is edit your sources.list file and add the Karmic Koala repos. Sudo apt-get update and then install the 2.6.30-10 kernel via Synaptic. Don't forget the headers too. While you are in there upgrade ALSA, the Gstreamer codecs, and Pulse Audio. Be very careful what packages you mark for upgrade. Pay particular attention to what packages will be removed, and don't upgrade a package if you think it's going to mess something up. There were one or two things I had marked, but then unmarked. Just be careful and use common sense.

If you've got an Nvidia graphics card: Reboot, and start up in to low graphics mode. Next go back into synaptic and upgrade from the 180 to the 185 drivers. You need the 185 drivers for this kernel. You have to do this. Now go into the Hardware drivers tool in the administrative menu, and enable the drivers. It's only going to show 173 and 180. Just pick 180 and it will enable the 185 drivers.

Reboot and choose the new kernel. Everything should load fine. As long as you didn't mess with your xorg.conf file video should work correctly now that the 185 drivers are enabled.

Finally remove the Karmic repos from your sources.list file and sudo apt-get update again.

If you've got an ATI graphics card I can't help you. I've never used one with Linux.

I can tell you with 99.9% certainty that this fixed all my audio issues. I leave the .1% to chance, because hey you never know.

Good luck. 8)

---

