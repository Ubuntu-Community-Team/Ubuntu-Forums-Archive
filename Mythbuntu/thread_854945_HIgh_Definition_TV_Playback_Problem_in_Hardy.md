---
title: "HIgh Definition TV Playback Problem in Hardy"
date: 2008-07-10
forum: Mythbuntu
---

### Post by deepee_oz on 2008-07-10
Hi All

I'm running the 64bit version and have been working on a dual tuner setup for Mythbuntu. I'm located in Brisbane, Australia.

I have been having issues when trying to display High Definition channels. The picture comes to a virtual standstill then jumps a load of frames plays a couple of frames then repeats the whole mess. The audio goes into juddery slow motion while this is going on.
SD channels are all good.

I have tried most of the TV Playback adjustments in the front end setup but nothing seems to make much difference.

The box is set up as dual boot with Vista and the tuners (2 x Winfast Dongle Gold with modules compiled from Linux TV)signal quality etc are all good.

One thought is that the HD programs carry 5.1 channel audio while the SD programs are a AC-3 stereo (I'm using digital audio out). Maybe the issue relates to demuxing the surround audio tracks?

Any thoughts, pointers, tools or fixes would be greatly appreciated as I have spent days on this!

Thanks
deepee_oz

---

### Post by ian dobson on 2008-07-10
Hi,

Could we have abit more information:-

1) CPU/memory installed
2) Graphic card +drivers used
3) Is you system a combined frontend/backend
4) What do you see in the frontend.log file when it's skipping?
5) What output ar you using for the display?

Regards
Ian Dobson

---

### Post by deepee_oz on 2008-07-10
Hi Ian

Thanks very much for your reply.
With the info in the log I can now see I have a graphics driver issue.
I'm using a MSI-K9A2GM mobo with AMD quad core and 2GB. It has integrated Radeon HD3200 onboard graphics.
Had all sorts of issues trying to get the right resolutions to display on my LCD TV screen using HDMI output and went to the restricted ATI drivers from the Ubuntu repos.

You've pointed me in the right direction and I'll make a follow-up post when I work out what's going on.

Thanks
deepee_oz

---

### Post by Lindsay.Mathieson on 2008-07-10
Hi deepee, I'm also in Brisbane, AU - just thought I'd let you know I have no problems with the FTA HD channels. My system spec is Mythbuntu 8.04, AMD Dual 5200+ and a Onboard NVidia 7050.

Which HD channels are giving you problems?

---

### Post by deepee_oz on 2008-07-10
Hi Lindsay

All of them are currently unwatchable but looks to be more graphics adaptor related.
Doing some more testing and (hopefully!) will sort it out...

Regards
deepee

---

### Post by JugeHuge on 2008-07-10
Try adding
Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"
Option "TexturedVideo" "on"
under Section "Device" on xorg.conf

and then run aticonfig --input=/etc/X11/xorg.conf

---

### Post by jbman on 2008-07-10
Sounds like the ATI driver is going problems. What is TOP showing when you try and playback HD? 

What playback profile setting are you using.

---

### Post by netslacker on 2008-07-10
There are a number of us with the ATI HD 3200 IGP that are having troubles within myth/linux/ubuntu.  

Here is the thread I started:
[http://ubuntuforums.org/showthread.php?t=827232&highlight=ati+smooth+video](http://ubuntuforums.org/showthread.php?t=827232&highlight=ati+smooth+video)

You can try the current 8.6 driver from ati.amd.com... maybe that will give you some success (it's definitely resolve the jitters, but in many cases gives horizontal tearing). But most of us have gone and purchased a cheap nvidia card (7100) to solve the issues w/ ATI until their drivers are up to snuff.

---

### Post by tqft on 2008-07-11
Deepee - any luck?

I am also in Brisbane - Hardy x86_32, Fusion HDTV Pro tuner card, onboard intel graphics chip.  Works fine (except channel7 - see separate post) watching HDTV (Rage) right now with vlc as a test, was watching rage with Myth before.

---

