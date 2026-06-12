---
title: "Performance vs. Windows?"
date: 2007-12-07
forum: Mythbuntu
---

### Post by radio1 on 2007-12-07
I've been playing around with several HTPC configurations for the past few years. I've flip-flopped setups several times using:

MythTV (KnoppMyth)
BeyondTV
GB-PVR
Mediaportal
XBMC (front-end for MythTV)

Right now, I have a 30" Samsung HDTV (CRT w/HDMI-in and 2 Composite-in).

My HTPC right now is:
AMD Semp 3000+ w/2GB DDR800
PVR150 MCE card
Asus AMD 690G  w/ATI X1250 HDMI-out and HD audio
200GB PATA drive

The computer is somewhat laggy as hell, and acts a lot slower than my old KnoppMyth box with a Duron 800 w/ 768MB and a FX5600.

I'd like to give Mythbuntu a try... But I have a few questions:

1) Would it be more responsive than a Windows-based HTPC? (I think it would)
2) Is there Mythbuntu support for ATI Linux (HDMI out) drivers? (I've searched somewhat when I was building this box earlier in the year. But I could not find any real success stories using MythTV and ATI video chipsets...)

Whenever I have played around with Linux, it has been Ubuntu- so I am familiar with it.

Thanks for the help.

---

### Post by newlinux on 2007-12-07
1. Most likely. That hardware should run pretty well for your needs in Linux.

2. I'm not sure... And I know I haven't heard of anyone getting HD-Audio to work in Linux in general... Although my experience and knowledge is far from exhaustive, especially with ATI and Linux.

---

### Post by radio1 on 2007-12-07
Thanks.

Actually right now, I have an M-Audio Revolution 7.1 in it. So, I know that's at least ALSA-compatible.

I am just more concerned with the ATI portion of it... I did try KnoppMyth several months back when I built the machine and it could not recognize any of the hardware...

---

### Post by superm1 on 2007-12-07
You will likely need the proprietary drivers activated to get tv out to be working correctly (After install).

I'd say, pop an extra hard drive in the box, do a quick install (its less than 20 minutes to install), and activate the proprietary video driver during install.  See what happens!

According to [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.34.8.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.34.8.html)
Support for your chipset was added during the 8.34 series.  Gutsy ships with the 8.37 series.

---

### Post by tohc1 on 2007-12-07
I have recently built a new htpc using a 690G chipset motherboard (Biostar TA690) and had a similar problem with the video lagging - I also used knoppmyth before with my previous box (socket a sempron) so I knew that the hardware should handle it fine.

It turns out that the linux drivers (ati fglrx) for the 690G video aren't quite good enough yet and in particular there is no xv overlay support for the x1250 graphics, or any other video overlays.

To check run mythfrontend from a terminal, start a video and alt-tab back to it you should see a warning about the computer not being able to playback at full speed and skipping frames.

In the end to get it working I put a cheap nvidia card in the pc and I am using that until the drivers are better.

---

### Post by superm1 on 2007-12-07
> **tohc1 said:**
> I have recently built a new htpc using a 690G chipset motherboard (Biostar TA690) and had a similar problem with the video lagging - I also used knoppmyth before with my previous box (socket a sempron) so I knew that the hardware should handle it fine.

It turns out that the linux drivers (ati fglrx) for the 690G video aren't quite good enough yet and in particular there is no xv overlay support for the x1250 graphics, or any other video overlays.

To check run mythfrontend from a terminal, start a video and alt-tab back to it you should see a warning about the computer not being able to playback at full speed and skipping frames.

In the end to get it working I put a cheap nvidia card in the pc and I am using that until the drivers are better.
You have to activate the video overlay yourself.  It's not on by default.

See aticonfig

---

### Post by tohc1 on 2007-12-08
Unfortunately, that with the xv overlay activated. 

The Xorg log says something like xv overlays not supported on avivo based hardware, and the problem is acknowledged on the unofficial fglrx driver website website:

[http://wiki.cchtml.com/index.php/Troubleshooting](http://wiki.cchtml.com/index.php/Troubleshooting)

---

### Post by radio1 on 2007-12-08
Is this true even for the new ATI Linux Catalyst 7.11 drivers?

When I reading Superm1's link, at the very bottom it said that those driver did not support video acceleration for Linux. (My slowness is in Windows...)

The whole point of me using the 690G board was the that it was totally integrated- you can't ask much more from a board than:

1) On-board firewire, on-board HDMI-out, on-board SPDIF optical-out
2) On-board USB 2.0, blu-ray/hd-dvd/hdcp-certification
3) Component-out and svideo-out

I guess I should have researched more, but ATI had gotten some accolades for their improved Linux support.

So, is it even worth converting my HTPC to a Linux solution before I can buy a cheapo NVidia card?

**(I mean am I just running standard-def recordings possibly transcoded to Xvid or Divx...?!)**

---

### Post by superm1 on 2007-12-08
> **radio1 said:**
> Is this true even for the new ATI Linux Catalyst 7.11 drivers?

When I reading Superm1's link, at the very bottom it said that those driver did not support video acceleration for Linux. (My slowness is in Windows...)

The whole point of me using the 690G board was the that it was totally integrated- you can't ask much more from a board than:

1) On-board firewire, on-board HDMI-out, on-board SPDIF optical-out
2) On-board USB 2.0, blu-ray/hd-dvd/hdcp-certification
3) Component-out and svideo-out

I guess I should have researched more, but ATI had gotten some accolades for their improved Linux support.

So, is it even worth converting my HTPC to a Linux solution before I can buy a cheapo NVidia card?

**(I mean am I just running standard-def recordings possibly transcoded to Xvid or Divx...?!)**
You know it wouldn't hurt to try the newest drivers...

---

### Post by radio1 on 2007-12-08
Oh. Yah, I know...

But I haven't even installed it yet. The box is presently WinXP w/GBPVR. But I wanted to get a feel if (in anyone's experience) an ATI chipset was an insurmountable issue.

As much as I like MythTV distros (and I do), I don't want to exchange a couple of minor annoyances with my setup for a serious issue.

:)

---

