---
title: "Can't get TV-out working with nvidia card + s-video"
date: 2010-06-23
forum: Multimedia Software
---

### Post by jphekman on 2010-06-23
Hi. I'm trying to get my desktop to output to my TV as a second display.

OS: Ubuntu 9.04
Graphics card: nVidia Corporation C51 [GeForce 6150 LE]

I have run an s-video cable from the computer to the TV. I tested the cable and it does work, and the TV does accept s-video in (from my TiVo) successfully.

As root, I ran nvidia-settings -> X Server Display Configuration. My regular monitor shows up (with a specified resolution), and TV-0, which is marked "(disabled)" where the resolution should be.

Select "TV-0", "configure...", "TwinView." Resolution set to "Auto", Position set to "Right-of". Hit "apply". Get error: "Failed to set MetaMode(1) 'CRT-0: 1280x1024 @1280x1024 +0+0, TV-0: nvidia-auto-select @1024x768 +1280+0' (Mode 2304x1024, id: 50) on X screen 0 \n Would you like to remove this MetaMode?" I have tried choosing both "yes" and "no," and the message goes away, and the TV-0 box is now no longer "disabled," but my TV still doesn't have any picture coming from the computer.

I have also tried setting "configuration" to "separate X screen" instead of "TwinView," and the "position" to "Clones" instead of "Right of". Still no picture to the TV.

In all cases, I have of course saved the settings to /etc/X11/xorg.conf and restarted X.

I do think something is getting through to the TV because when I reboot I see a flicker, but otherwise I have gotten no signal at all to it.

Everything I read online suggests that what I am doing should work. Does anyone have any suggestions for me? Is there some weird gotcha I'm missing? Something to do with apparmor, or something like that?

Thank you!

Jessica

---

### Post by cguy on 2010-10-28
I have the exact same problem on Lucid Lynx + NVIDIA 7100 GS.

Help! :)

---

### Post by jphekman on 2010-10-28
I ended up getting help from the nice people on the mythtv mailing list, who knew that my Nvidia card would only output to a monitor OR a TV -- not both at once! You can test this on your card: shut your computer down; turn on your TV; unplug your monitor; turn on your computer. It should output to your TV. (Note the TV may have to be ON during boot-up to be detected.)

In the end, I bought a new graphics card, and now all is well. It auto-configured and everything.

Good luck!

---

