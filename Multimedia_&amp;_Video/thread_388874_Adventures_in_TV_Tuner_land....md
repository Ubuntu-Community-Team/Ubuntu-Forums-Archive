---
title: "Adventures in TV Tuner land..."
date: 2007-03-20
forum: Multimedia &amp; Video
---

### Post by tm0054 on 2007-03-20
I bought a new TV Tuner today (a usb 2.0 hauppage hvr 950) and it semi-works in Ubuntu but needs a lot of help. First let me say that the video and audio work perfectly in Vista so none of this has to do with the tv tuner itself...

First I followed these directions to get the drivers installed: [http://lunapark6.com/?p=2682](http://lunapark6.com/?p=2682)

I've downloaded a handful of TV Tuner programs...

ALL the programs display video but all of them show a green distorted bar across the top of the screen (no green bar is apparent in Vista).

I've tried XawTV, TVtime and MythTV. I have no sound at all in Xaw and TVTime... I have sound in MythTV but it sounds horrible like it's at an extremely low bitrate or something. Again all programs show a green bar across the top of the picture.

Is there a configuration somewhere that can help me? Is there somewhere I can bump up the sound quality/turn the sound on? Are there better drivers somewhere? What is ivtv?

---

### Post by rebeljt on 2007-04-08
> **tm0054 said:**
> I bought a new TV Tuner today (a usb 2.0 hauppage hvr 950) and it semi-works in Ubuntu but needs a lot of help. First let me say that the video and audio work perfectly in Vista so none of this has to do with the tv tuner itself...

First I followed these directions to get the drivers installed: [http://lunapark6.com/?p=2682](http://lunapark6.com/?p=2682)

I've downloaded a handful of TV Tuner programs...

ALL the programs display video but all of them show a green distorted bar across the top of the screen (no green bar is apparent in Vista).

I've tried XawTV, TVtime and MythTV. I have no sound at all in Xaw and TVTime... I have sound in MythTV but it sounds horrible like it's at an extremely low bitrate or something. Again all programs show a green bar across the top of the picture.

Is there a configuration somewhere that can help me? Is there somewhere I can bump up the sound quality/turn the sound on? Are there better drivers somewhere? What is ivtv?

I was thinking about buying one of these today. Are you still having these problems? I'd be interested to know before I replaced my crappy Leadtek Winfast 2000 with it. 

JT

---

### Post by freegeekcore on 2007-04-09
##The Issue##
Ive just upgraded dapper to edgy on my system and now i am not getting any sound from tvtime it was working before i have an internal audio cable going from my tvtuner card to my on board sounds Aux. port.VIA Technologies Inc.VT8233/A/8235/8237 AC97 Audio Controller I  selected preferences in sound settings and made sure the right device was being selected and that Aux. was enabled and full blast.  Plz if you have any idea as to how to correct this email me [email]insanekrazy1986@gmail.com[/email] plz

##lspci##
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:09.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 02)
00:09.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 02)
00:0a.0 Network controller: Texas Instruments ACX 100 22Mbps Wireless Interface
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 If [Radeon 9000] (rev 01)
01:00.1 Display controller: ATI Technologies Inc Radeon RV250 [Radeon 9000] (Secondary) (rev 01)

---

