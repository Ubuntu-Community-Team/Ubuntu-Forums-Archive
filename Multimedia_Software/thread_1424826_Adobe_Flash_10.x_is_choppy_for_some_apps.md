---
title: "Adobe Flash 10.x is choppy for some apps"
date: 2010-03-08
forum: Multimedia Software
---

### Post by haribol707 on 2010-03-08
Hello,

I have faced this problem both on 9.04 and 9.10 with the following combinations:

FF 3.5, 3.6 & latest available Adobe Flash player 10.x 
Google Chrome beta & latest available Adobe Flash player 10.x 

I have no problems with playing Flash based videos, both compact size and full-screen. However, when I play the occassional Flash based game (continuous action on the screen, if that matters), it gets really ugly. The entire flash screen becomes choppy/flickers and it is not at all a good experience using it. I have no such problems with Windows.

I have Nvidia GeForce 8700M card and installed with 185.18.36 driver (installed through hardware drivers prompt).

I also faced the same problem on another Desktop with 9.10 and environment (Nvidia Quadro FX 500).

I read from the forum (old post) that disabling compiz can help. Tried that option as well with limited success. 

Let me know if this a known limitation or if there is something that can be done to fix the issue.

---

### Post by Tikkyca on 2010-03-08
Same here,if you were playing pet society on facebook with windows it will run smooth,but on linux no,i hate that adobe really needs to support linux more.

---

### Post by haribol707 on 2010-03-08
Yes, I play a flash cricket game (sport) and it is just not possible with Linux. While I thought Steve Jobs went overboard with his Flash ranting, I now see why he made the smart choice. Hopefully, there is a solution soon!

---

### Post by no2498 on 2010-03-08
see if this helps any at all you may need to restart the computer

open a terminal type ( gstreamer-properties ) click enter
click video set the plugin to   x window system (no xv)

this comes from the cheese help faq's

write down what its set to so you can set it back if you need to
i hope it helps you all

---

### Post by haribol707 on 2010-03-08
Thank you for the suggestion. I will try it out and let you know!

---

### Post by haribol707 on 2010-03-09
hello no2428, I configured changes as you suggested and there is a marked improvement in the flicker issue! Though, there still is a bit of flicker now, it is not such a bad experience as it was before! Thank you for your suggestion.

Let me know if this helped anyone else.

---

### Post by deertan on 2010-06-28
Tried your suggestion and it completely eliminated my flickering video in full screen!

Thanks very much!

---

### Post by areayetee on 2010-10-13
works perfectly now - thanks soo much

---

### Post by eival on 2010-11-01
> **no2498 said:**
> see if this helps any at all you may need to restart the computer

open a terminal type ( gstreamer-properties ) click enter
click video set the plugin to   x window system (no xv)

this comes from the cheese help faq's

write down what its set to so you can set it back if you need to
i hope it helps you all

wow this helped me out for my online sports packages MLB.tv and NBA league pass both use flash and they that would flicker like crazy if i tried doing anything in another browser window, now its 99% flicker free
:popcorn:

---

### Post by dave2001 on 2011-11-04
THANK YOU!!

  no2498's solution worked for me!

I am using Ubuntu 10.04 LTS with the latest firefox 7 and adobe flash player version 11.x

I had horribly choppy full-screen flash video in browser. I tried many other solutions listed on the forums. I also tried using different versions of firefox and the flash plugin. The solution offered here is the only thing that worked!

---

### Post by beew on 2011-11-04
no xv is not a solution as you get bad quality videos. First try a newer version of flash (11.xx) and see it improves, if your Nvidia card is vdpau enabled the latest beta flash 11 from adobe uses hardware decoding (though not the stable version). The easiest way to get it would be to install the flash-aid plugin for Firefox and run the script in wizard mode, it installs flash, clears up broken and inconsistent versions and does some optimizations like enabling GPU acceleration if available(if you have a vdpau enabled Nvidia card)

If you need flash just for Youtube and a few other sites you may want to try the flashvideoreplacer addon for Firefox (for this you need to also install the gecko-mediaplayer from the repo) As the name suggests with this you wouldn't need flash at all for the supported sites (youtube, vimeo and a few other sites) 

Minitube is also good for watching youtube without flash (need the version from webupd8 ppa though, the versions in everything before and up to Natty are broken, and probably is broken in 11.10 too, but even if it is not at the moment you should still install from ppas because it has to be kept up to date and Ubuntu doesn't do feature updates. Youtube changes its formats from time to time and old versions will stop working)

---

### Post by dave2001 on 2011-11-04
> **beew said:**
> no xv is not a solution as you get bad quality videos.

Well, as stated in my last post.. I have tried MANY other things to get full screen flash working correctly, and this is the only one that did it.

I have tried: Every version of flash and other players available with the "FLASH-AID" addon for Firefox. I've also tried installing them manually in-case the addon wasn't working properly.
I tried plugins such as "flash-replacer" but they only work on a limited number of sites.
I have tried the GPU validation over-ride, also enabling or disabling hardware acceleration. I've tried disabling KMS and using an xorg.conf to try different video card setttings.

I've also done a fresh install of both 11.04 and 11.10 to see if they had better support for full-screen flash. The video played great, but the audio was completely garbled, and I was unable to find any fix for it.

The gstreamer-settings solution offered in this thread may not be perfect, but the resulting video quality is comparable to what I get when running windows7 (dual boot machine) so I'm happy with it. I can actually watch full-screen flash in Ubuntu now!

---

