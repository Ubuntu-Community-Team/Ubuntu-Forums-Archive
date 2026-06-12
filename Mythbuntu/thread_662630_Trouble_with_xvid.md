---
title: "Trouble with xvid"
date: 2008-01-09
forum: Mythbuntu
---

### Post by clay_leblanc on 2008-01-09
Hey guys, been playing around with MythTV, and decided to use mythbuntu since I have previous experience with Ubuntu itself, as well as Xubuntu...


but I have come to a problem.

I boot Mythbuntu, and then I get to the MythTV front end, I then go to Media Library, then Videos, and go to watch some videos I stored. They're in xvid avi files... It'll  say a lot of unknown stuff, no running time, or anything, and trying to play it just puts a "loading "file.name"" text on the screen, and then it goes away.

Although, when I get out of the MythTV frontend and get to the desktop gui, and play the files using mplayer or whatever, they work fine.

I've also tried apt-getting w32codecs,  totem, ubuntu-restricted-codecs, and something-xine. Nothing seems to help even after reboots.

I've also noticed an option on the MythTV Control Center to enable the w32codecs, i applied that, tried playing the video. It didn't play, even after reboot.

Any help would be appreciated,

Thanks!

---

### Post by AlecJ on 2008-01-10
What player is Mythbuntu set to use?

setup~Media setting~Video settings~Player settings

I guess Mplayer?

I have used both Mplayer and xine, I find xine is smoother

My Default player setting is:-

xine -r 4:3 -f -l --no-splash %s

And while your in this menu, check the setting of the file type for avi.

---

