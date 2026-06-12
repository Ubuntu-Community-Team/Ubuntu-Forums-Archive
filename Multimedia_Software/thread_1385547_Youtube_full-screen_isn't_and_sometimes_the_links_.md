---
title: "Youtube full-screen isn't and sometimes the links don't do anything when clicked"
date: 2010-01-19
forum: Multimedia Software
---

### Post by Miggles on 2010-01-19
I've recently done a fresh install of 9.10 x64 on my Dell M1330 (C2D 2.4GHz, 4GB, 8400GS) and I'm trying to fix the problems I have with Flash.

The problems are mainly two-fold:
1. Sometimes Youtube videos are simply do not function when I click on a button in them. This appears to happen more or less at random. When I encounter one of these videos they have all of the relevant hover actions and the like but they refuse to do anything when I click. Refreshing the browser has no effect - that video simply will not play.

2. When Youtube videos do play, clicking on full screen results in the small Youtube video in the middle of the screen while the playback bar goes the complete width.

I have uninstalled and reinstalled multiple times. Each problem exists in Firefox and Chrome. I even dabbled with Gnash but performance is not so good (even if the ability to save every streamed file was rather pleasant).

I'm using the NVidia 190 driver with Twinview (the second screen is attached through the HDMI port) if that's relevant.

I haven't been able to find anybody else mentioning these issues so I'm guessing it's something particular to my setup and that there is solution. Any suggestions will be greatly appreciated.

---

### Post by asuastrophysics on 2010-01-20
> **Miggles said:**
> I've recently done a fresh install of 9.10 x64 on my Dell M1330 (C2D 2.4GHz, 4GB, 8400GS) and I'm trying to fix the problems I have with Flash.

The problems are mainly two-fold:
1. Sometimes Youtube videos are simply do not function when I click on a button in them. This appears to happen more or less at random. When I encounter one of these videos they have all of the relevant hover actions and the like but they refuse to do anything when I click. Refreshing the browser has no effect - that video simply will not play.

2. When Youtube videos do play, clicking on full screen results in the small Youtube video in the middle of the screen while the playback bar goes the complete width.

I have uninstalled and reinstalled multiple times. Each problem exists in Firefox and Chrome. I even dabbled with Gnash but performance is not so good (even if the ability to save every streamed file was rather pleasant).

I'm using the NVidia 190 driver with Twinview (the second screen is attached through the HDMI port) if that's relevant.

I haven't been able to find anybody else mentioning these issues so I'm guessing it's something particular to my setup and that there is solution. Any suggestions will be greatly appreciated.

You're problem is in the flash player, not the browser. This has been an unsolved bug for the past 5 months. I've sort of just gotten used to the workaround:
If no response after clicking: Middle click and left click at the same time. 

Again I really don't know why it's taken so long for a fix.

---

### Post by akitotenk on 2010-01-20
You have 2 solution
1- easy
Disable desktop effet and all work
2- a little more complicated
there is a beta native flash player for 64bit you need to install it 
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)
and type in terminal

sudo mv libflashplayer.so /usr/lib/mozilla/plugins/
you need to remove flash 32 first

there is a repo too to add for use flash 64x but try to find it if you have a problem

---

### Post by Miggles on 2010-01-20
> **asuastrophysics said:**
> You're problem is in the flash player, not the browser. This has been an unsolved bug for the past 5 months. I've sort of just gotten used to the workaround:
If no response after clicking: Middle click and left click at the same time. 

Again I really don't know why it's taken so long for a fix.

Sorry, when I said I uninstalled and re-installed multiple times I was referring to Flash, not the browsers.

I have just found this by changing my google terms (it's got more to do with the x64 than anything else, it seems) [http://ubuntuforums.org/showthread.php?t=1325824](http://ubuntuforums.org/showthread.php?t=1325824)

So I'll be giving this and the other suggestions in this thread a try tonight.

Cheers.

---

### Post by Miggles on 2010-01-20
A bit more hunting has found this: [http://ubuntuforums.org/showthread.php?t=1358591](http://ubuntuforums.org/showthread.php?t=1358591)

Which I fired up and it seems to have fixed the clicky problem. Now I just have the full screen issue. I'll keep looking for a solution to that.

---

