---
title: "Seamless VideoPlayback under Ubuntu Lucid Lynx (10.04) with an ATI/AMD HD4000 series"
date: 2010-06-21
forum: Multimedia Software
---

### Post by hippienerd on 2010-06-21
Yes, it is possible, though it took me quite a while and some  patience, so I decided to write you a little guide.
 My Setup and my purpose:
 I use a pretty good Machine with a two display Setup (23&#8243; LCD + 42&#8243;  Plasma), with the purpose of Videoplayback on the Plasma Screen.(Dual  Screen Setup)
 The Details:
 
[LIST]
[*]AMD Phenom II 4×3,1 Ghz
[*]Gigabyte Mainboard with 790GX and AMD SB750 Realtek audio
[*]4 GB DDR2 800 RAM
[*]500 GB WD HDD Caviar Green
[*]Sapphire RadeonHD 4670 ULtimate with HDMI Output
[*]23&#8243; LCD Screen 1920×1080 via DVI
[*]42&#8243; Panasonic HDReady Plasma via HDMI
[*]Ubuntu LucidLynx 32-bit with the latest AMD Proprietary Driver
[/LIST]
 
[LIST]
[*]Yamaha DolbyDigital Receiver via SPDIF
[/LIST]
 The Problems:
 A very common Problem is Choppy Video, the lack of vsync. You realise  that you have this problem, when every video you watch doesn’t matter  if Youtube or HighDef .mkv is choppy. That is very unsatisfying and  annyoing.This Problem will keep to exist until there is full and stable  GPU-Videoacceleration available for AMD-Owners. At the moment, that is  just not the case.
 Another one is unreasonable stutters during playback, appearing  without any CPU/RAM or HDD activity.
 The Solutions:
 I worked very hard on this, considering myself to be not the absolute  pro, so i tried nearly EVERYTHING. The Vsync-Problem can be clearly  located to be an issue between the AMD Proprietary Driver and Compiz.  After trying really everything just to realise the Videos kept playing  choppy, i chose to uninstall compiz completely. Yes, i tried to activate  VBlank-Sync in the SimpleCompizConfig Manager, it did not change  anything.
 AMD/ATI Driver settings are pretty obvious, open a terminal and  enter:

 sudo aticonfig --sync-video=on

 For the Dual Screen Setup i opened the Catalyst Control Center and  chose in the Display-Manager: Single Display Desktop (Multi-Desktop),  for my Plasma-TV (Panasonic TH-42Px8) i used the recommended Setting  1280×720 @ 50 Hz.
 When the Dual Screen Setup is like this, you will find a complete  Desktop on your LCD/Plasma Display, u will not be able to drag  programs/windows, so you have to start the Mediaplayback Software (in my  case VLC) on the Screen you want to use. Though this might not be your  preferred Dual-Screen Setup, it is in my case the ONLY configuration  that made vsynced Video possible. In the MultiDisplay Setting in the CCC  Videos kept being Choppy and therefore unacceptable.
 I use the absolute latest VLC-build from this Repository:

 [http://ppa.launchpad.net/nvidia-vdpau/cutting-edge-multimedia/ubuntu](http://ppa.launchpad.net/nvidia-vdpau/cutting-edge-multimedia/ubuntu)

 In this 1.2.0 Version of VLC, there is a Video output module called:  GLX Video Output (XCB)
 And it finally worked, real good Video Performance, chops and lines  completely gone.

 I am aware, that when GPU-accelerated Playback for AMD Users will be  stable ( I got it working under xbmc svn release with ridicolously low  cpu-usage playing 720p mkv, but not stable) this will be obsolete,  compiz may come back and all will be fine. Until then, i do not see any  other way. I am using this for a week now, and i am very happy with it.  (Me being happy says a lot)

 The other much more annoying performance problem could be solved by  downloading and compiling the audio alsa driver from the realtek  homepage.Though Sound worked out of the box, there were video  stoppages and artifacts. I would never have discovered it, if it hadn’t  happened playing back sound as well, sometimes 3 minutes of playing an  mp3 would work perfect, until randomly rare stutters would appear. A  very weird problem, which could be solved by the realtek alsa package.
 Thats it, i hope it works for you as well, what i found using google  that the vsync Problem still appears on many situations. Good Luck folks!

---

### Post by Lefuneste on 2010-08-01
YESSSSS !!! AT LAST IT WORKS !!!! :p

I had to mess up a bit with the repository. The way to do it is to add it to Synaptic repositories list with the following formulation (without the quotes)

"deb [http://ppa.launchpad.net/nvidia-vdpau/cutting-edge-multimedia/ubuntu](http://ppa.launchpad.net/nvidia-vdpau/cutting-edge-multimedia/ubuntu) lucid main"

Then leave Synaptic and launch Update Manager instead. Just accept the partial update as you must refresh the whole system (several linked packages) otherwise you'll end up with broken packages and problematic dependecies if you only try to update VLC.

Many thanks for the tip!! I tried for more than 6 months to get rid of this annoying stuttering effect editing more files than I can remember... But with so many ATI adaptors around, it would be time that Ubuntu dev team closes this issue once for all...

---

