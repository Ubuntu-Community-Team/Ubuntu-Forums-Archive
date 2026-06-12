---
title: "Video resolution seems to change during video playback"
date: 2011-04-11
forum: Multimedia Software
---

### Post by natomb on 2011-04-11
Hello together,


I am setting up a MythTV environment to switch from Windows based MediaPortal (with a high number of disturbing bugs). Yet, I have three difficulties, which I want to discuss with you. They are:


- No audio via HDMI (see [http://ubuntuforums.org/showthread.php?p=10663374#post10663374](http://ubuntuforums.org/showthread.php?p=10663374#post10663374))
- Video resolution seems to change during video playback
- Channels cannot be found via DVB-S (see [http://ubuntuforums.org/showthread.php?p=10663378#post10663378](http://ubuntuforums.org/showthread.php?p=10663378#post10663378))


As you can see, I have created three posts to keep discussions focused.

Alltogether I have the following setup:

- AMD 5050e CPU
- 8 GByte RAM
- Biostar TA890GXE
- Samsung LE40M86BD, connected via HDMI (and only HDMI)
- Mythbuntu 10.10 with proprietary drivers installed
- Technisat Skystar HD2 DVB-S card (two times)


Now, here is the problem:


Whenever I playback any video material using e.g. VLC, the screen resolution changes. This also applies when playback the video in a window and not fullscreen. The problem is that whenever the screen resolution changes, short time later the TV set blanks screen and show the TV set specific information "unsupported video mode".

How can I enforce to stay in the configured video mode?

Thank you for assistance
  Bjoern

---

### Post by inobe on 2011-04-11
i don't know much about myth, i do know a crap load about hardware.

your specs

    Supported Socket AM3 processors AMD Phenom II / Athlon II processor
    Supported AMD Mutil Core(x6,x4,x2)
    AMD 140W processor support
    AMD 890GX Chipset **with ATI Radeon HD 4290 DX10.1 Graphics**
    4 DIMM supported DDR3-1600(OC)/1333/1066
    On Board 128MB DDR3 Side-Port memory
    Supported SATA 6Gb/s 2X speed than current SATA 3G
    [B]ATI Hybrid Graphics Support
    Integrated HDMI/DVI interface with HDCP Support 1080P HD Video[/B] Experience
    BIOSTAR G.P.U ( Green Power Utility ) for green power saving your desktop
    D.P.U( Digital Power Unit ) Technology for better OC experience

i will be completely honest, ati/ amd proprietary drivers are a hit and miss, they are getting better over time.

the opensource at driver, many have reported it being better.

thinks i would check into...

make sure you have the proprietary driver enabled, if you enable them, and experience undesirable results, look into getting the updated driver and manually installing.

if it's too difficult and you are having severe trouble, try this repository.

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

if you need to know how to add that repo, let us know.


ultimately if everything fails, that free pci-e slot can be a nice home for an nvidia card.

---

### Post by natomb on 2011-04-25
Hello,


after an upgrade to Natty, the graphics problem is solved. Unfortunately, while watching an HDTV video the CPU utilization rised from ~15% in Maverik to >90% in Natty.

Yet, as long as the CPU is not rising to 100% and as long as I do not get video stuttering it is ok.

---

