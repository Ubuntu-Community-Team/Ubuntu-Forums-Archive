---
title: "Lagging more in Ubuntu 9.04 than it should be."
date: 2009-06-05
forum: Multimedia Software
---

### Post by MetroidJunkie2008 on 2009-06-05
Specs: 2GB RAM, AMD Sempron 1.8GHz Single-core, and 8800GT GeForce 512MB VRAM.

I'm getting bad performance (Poor framerates) while doing things in Ubuntu that worked just fine on Windows XP, such as viewing videos in HD and some Linux games, such as OpenArena, which are supposed to work just fine on much lesser specs. 
   What makes that strange is that Sauerbraten, a much more graphically intense game, is running fine on maxed out settings, even on an online match. I have the Nvidia accelerated graphics driver version 180 and it seems to recognize that I have a GeForce 8800GT just fine.
   Any suggestions to improve the performance?

---

### Post by MetroidJunkie2008 on 2009-06-05
Guess nobody can help me?

---

### Post by MetroidJunkie2008 on 2009-06-11
Nevermind.

---

### Post by Pinball Wizard on 2009-06-11
What did you do to get the framerates up? I don't experience the problems you speak of but I know I am looking to optimize a machine that is dedicated to doing one task: Media center.

---

### Post by MetroidJunkie2008 on 2009-06-11
I mean I give up.

---

### Post by xlearner on 2009-06-12
Did you see this thread - [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

Could this be a problem with your graphics card? Do you have an Intel card?

---

### Post by keypox on 2009-06-12
welcome to ubuntu.  I have yet to see a system perform better on ubuntu than on windows.

---

### Post by Pinball Wizard on 2009-06-12
Here is a list of what videro cards are supported as of 9.04's release: [http://www.x.org/wiki/Projects/Drivers?action=show&redirect=VideoDrivers](http://www.x.org/wiki/Projects/Drivers?action=show&redirect=VideoDrivers)

---

### Post by Pinball Wizard on 2009-06-12
Sorry to double post.... It is his video card. He has an Nvidia video card and XOrg (the basis of ubuntu graphics) does not currently support ANY of their cards.

---

### Post by MetroidJunkie2008 on 2009-06-14
> **Pinball Wizard said:**
> Sorry to double post.... It is his video card. He has an Nvidia video card and XOrg (the basis of ubuntu graphics) does not currently support ANY of their cards.

Are you saying, in Ubuntu's standards, I have what amounts to a $110 paperweight? -_- Most people have Nvidia, especially if their PCs were originally intended to be gaming machines.

---

### Post by Pinball Wizard on 2009-06-14
> **MetroidJunkie2008 said:**
> Are you saying, in Ubuntu's standards, I have what amounts to a $110 paperweight? -_- Most people have Nvidia, especially if their PCs were originally intended to be gaming machines.

I completely missed it as Nvidia video cards are listed as NV. So go to System->Administration->Hardware Drivers. This is where proprietary, closed-source drivers are listed that can be installed (most of the time). Tell me how that goes and I will continue from there (i.e. it doesn't list it or you are still having problems). Either way keep us up-to-date.

---

### Post by MetroidJunkie2008 on 2009-06-14
> **Pinball Wizard said:**
> I completely missed it as Nvidia video cards are listed as NV. So go to System->Administration->Hardware Drivers. This is where proprietary, closed-source drivers are listed that can be installed (most of the time). Tell me how that goes and I will continue from there (i.e. it doesn't list it or you are still having problems). Either way keep us up-to-date.

It's already activated. Sauerbraten even works with a fast framerate, despite all the graphics effects.

[IMG]http://i44.tinypic.com/906p03.png[/IMG]

It's strange. This game works fine, yet it lags when doing things like streaming video, especially with HD videos. In my experience, Ubuntu's lagging more than Windows on these things.

---

### Post by Arup on 2009-06-14
For HD video, you need to compile a vdpau and multi threaded enabled mplayer, pound for pound it blows away the players on Win as players in Win environment don't make use of all the cores. VDPAU will put all the decoding load on your nvidia GPU so you will get seamless HD playback even on slow PCs with cheap 8 series nvidia cards.

---

### Post by MetroidJunkie2008 on 2009-06-15
> **Arup said:**
> For HD video, you need to compile a vdpau and multi threaded enabled mplayer, pound for pound it blows away the players on Win as players in Win environment don't make use of all the cores. VDPAU will put all the decoding load on your nvidia GPU so you will get seamless HD playback even on slow PCs with cheap 8 series nvidia cards.

If by core, you mean processor, I have a single-core processor anyway. I plan to get a dual-core but, yeah. So, how do I compile a vdpau and multi-threaded enabled mplayer?

---

### Post by Pinball Wizard on 2009-06-15
He means that it will use your GeForce card to process the HD video and such. That processor is optimized to handle video instead of your CPU. Mplayer normally uses your CPU but with the version you compile it goes to your GPU. Here are some good (and up to date) directions : [http://blog.avirtualhome.com/2009/05/29/how-to-compile-mplayer-with-vdpau-support-on-ubuntu/](http://blog.avirtualhome.com/2009/05/29/how-to-compile-mplayer-with-vdpau-support-on-ubuntu/)

---

