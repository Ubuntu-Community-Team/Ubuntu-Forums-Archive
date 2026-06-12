---
title: "SMplayer suddenly not working"
date: 2008-07-25
forum: Multimedia Software
---

### Post by Dual_Chikara on 2008-07-25
A few days ago, I DLed SMplayer after having it recommended to me because of how well it handles subtitle. Yesterday, I was playing with the controls to get a feel for the program, and I clicked the ten minute forward skip button. Immediately after that the program stopped playing ANY videos. Since then I have tried playing videos in a number of containers and codecs in SMplayer, but nothing works! Even a fresh reinstall has done nothing for me. attached is what happens when I try to load a video.

---

### Post by rvm4000 on 2008-07-25
What does the mplayer log say (Options->View logs) after you try to play a file?

---

### Post by Dual_Chikara on 2008-07-25
here is the Mplayer log:> /usr/bin/mplayer -noquiet -nofs -sub-fuzziness 1 -identify -msglevel demux=6 -slave -vo xv -ao pulse -zoom -nokeepaspect -framedrop -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 58720270 -colorkey 0x020202 -monitoraspect 1.6 -subfont-autoscale 1 -subfont-text-scale 5 -subcp ISO-8859-1 -subpos 100 -contrast 0 -brightness 0 -hue 0 -saturation 0 -volume 40 -nocache -osdlevel 0 -vf-add screenshot -channels 2 -af volnorm=2 /media/sdb1/Downloads/[GoGGu]Bounen no Xamdou 01 Xam`d at the Dawn of War.mkv

MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3800+ (Family: 15, Model: 79, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Unknown option on the command line: -volume
Error parsing option on the command line: -volume


---

### Post by Dual_Chikara on 2008-07-25
and the SmPlayer log is attached, due to there being too many "images" somewhere in the text.

---

### Post by rvm4000 on 2008-07-25
> **Dual_Chikara said:**
> 
Unknown option on the command line: -volume
Error parsing option on the command line: -volume


Go to Preferences->General->Audio and set the option "Change volume just before playing" to No. 
(That option requires a patched mplayer to work).

---

### Post by Dual_Chikara on 2008-07-25
> **rvm4000 said:**
> Go to Preferences->General->Audio and set the option "Change volume just before playing" to No. 
(That option requires a patched mplayer to work).
Thanks, that did it! are there any other options I should leave alone so this doesn't happen again?

---

### Post by rvm4000 on 2008-07-25
Yes, the option "High speed playback without altering the pitch" (in General->Audio) won't work with mplayer 1.0rc2 as it requires a new audio filter (scaletempo) which was added to mplayer a few weeks after the release of 1.0rc2.

---

### Post by Dual_Chikara on 2008-07-25
I'll watch out for that. Thanks again, and great program!

---

