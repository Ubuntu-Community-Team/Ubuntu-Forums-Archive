---
title: "video &amp; mplayer/totem/vlc playback problem"
date: 2010-10-09
forum: Multimedia Software
---

### Post by maddbaron on 2010-10-09
When I try watching HD or avi files with totem the sound and video skips then equalizes on its own, when I try in vlc same thing but I play with the sound until video and sound sync but there is slowness in video.

mplayer won't start. I installed the gmplayer front end and I just get that but no video or sound, video won't play.

I've reinstalled all the media files with no solution, this has all started about 3 weeks ago and has gotten progressively worst. 

Is there a solution to this problem?

---

### Post by cchhrriiss121212 on 2010-10-09
More info please:
What is your video card, and what drivers are you using? This seems like an update issue, so you may need to roll back your current driver.
Is the problem just with HD video? You say HD and avi files, but avi can carry HD video as well.

---

### Post by maddbaron on 2010-10-09
> **cchhrriiss121212 said:**
> More info please:
What is your video card, and what drivers are you using? This seems like an update issue, so you may need to roll back your current driver.
Is the problem just with HD video? You say HD and avi files, but avi can carry HD video as well.

video card is ATI Radeon™ HD 4200 integrated graphics
I'm using the drivers that came with 10.04, i think ati restricted. Haven't changed them to my knowledge. Is there a way I can review my past system updates to see if i did a driver update?

i have most problems with HD video files, but AVI's worked fine... old avi's i had for years worked fine then few weeks back started acting up. I haven't messed with my video files, i barely used mplayer but when i first installed it, it worked but I preferred vlc and totem now mplayer simply won't work.   I am really at a loss b/c the video and sound is out of sync for either a few seconds or several minutes then works fine rest of the way or occasionally acts up again then works fine... could it be an issue with the a recent kernel update?

---

### Post by cchhrriiss121212 on 2010-10-09
The drivers that come with Ubuntu will be open source, you may get better results with the proprietary ones (check System>Hardware drivers).
I wonder if you could check your cpu usage when watching the videos?

May be a kernel issue, easy to test out if you have the old one in your GRUB menu, just hold down shift when booting.

---

### Post by maddbaron on 2010-10-09
> **cchhrriiss121212 said:**
> The drivers that come with Ubuntu will be open source, you may get better results with the proprietary ones (check System>Hardware drivers).
I wonder if you could check your cpu usage when watching the videos?

May be a kernel issue, easy to test out if you have the old one in your GRUB menu, just hold down shift when booting.

yeah I have the previous Kernel... i like to keep one as backup in case the new one messes up...I'll try it on next reboot

---

