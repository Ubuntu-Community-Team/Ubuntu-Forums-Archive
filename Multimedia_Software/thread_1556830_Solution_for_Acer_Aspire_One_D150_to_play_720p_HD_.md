---
title: "Solution for Acer Aspire One D150 to play 720p HD video"
date: 2010-08-20
forum: Multimedia Software
---

### Post by roy913 on 2010-08-20
Owners of aspire one D150 may experience choppy unwatchable video and here are some of the possible solutions. The CPU usage can stand still at 100% most of the time when playing 720p video even if you watch it from your harddrive, not to mention in youtube.

1. VLC
[LIST]
[*]add "Cutting Edge Multimedia" in your software source and install vlc player:
[*]here is the link: [https://launchpad.net/~nvidia-vdpau/+archive/cutting-edge-multimedia]("https://launchpad.net/~nvidia-vdpau/+archive/cutting-edge-multimedia")

[*]After that remember to check the "Accelerated Video Output" box in preferences.
[/LIST]

I cannot express enough gratitude to the Nvidia Vdpau Team for packaging all these software so we novice need not to go through all those command-line and compiling.

2. SMplayer
I found that providing the current hardware specs, its better to adopt the above solution to use VLC-vaapi for better video quality but if you are a mplayer maniac then here you go:
[LIST]
[*]Install SMplayer, Mplayer
[*]in SMplayer, go to preferences
[*]choose xvmc as your video decoder
[*]then in advanced, options for mplayer, type in "-vo xvmc," (remember to include the comma)
[*]in performance, choose ""skip always" loop filter
[/LIST]

3. youtube
providing you are using firefox
install an add-on called "FlashVideoReplacer"
then instead of using flash player, firefox uses mplayer to play youtube video, which solves the issue that no hw acceleration for flash player in linux

afterward:
I have tried using mplayer with vaapi provided by Cutting Edge Multimedia but it seems that the "-va vaapi" option is not working. More specifically, once "-va" option is applied there is only sound and no video. I assume its a hardware issue which -va is not for intel 945gse. So I choose "-vo vaapi" as the mplayer option in SMplayer, which result in very choppy image. if anyone knows how to use vaapi with 945gse, please let me know.

---

### Post by lovinglinux on 2010-08-20
> **roy913 said:**
> 3. youtube
providing you are using firefox
install an add-on called "FlashVideoReplacer"
then instead of using flash player, firefox uses mplayer to play youtube video, which solves the issue that no hw acceleration for flash player in linux

Thanks for using and sharing [FlashVideoReplacer]("https://addons.mozilla.org/en-US/firefox/addon/161869/"). If you have any suggestions to improve it, please let me know. 

BTW, Linux has hardware acceleration for flash. The problem is that it doesn't use xv, doesn't work with Compiz and not all flash content is ready for it. More info at [http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html)

---

### Post by roy913 on 2010-08-22
there are just so many restrictions in getting hardware acceleration for flash, even for xp i still cannot get it. so i ll probably stick with your add-on for the time being.

---

