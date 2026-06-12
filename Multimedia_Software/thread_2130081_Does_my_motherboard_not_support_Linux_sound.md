---
title: "Does my motherboard not support Linux sound ?"
date: 2013-03-28
forum: Multimedia Software
---

### Post by ibchristie on 2013-03-28
I have been struggling to get the sound working on my machine for about 18 months now.
I have a Gigabyte motherboard (GA P67A-UD3R-B3) with inbuilt sound (HDA Intel PCH using a Realtek ALC889 chipset) and an i5 CPU. I am running Ubuntu 12.10
I have tried so many different tutorials/how tos/trouble shooting guides that I have lost track. Tonight I carefully worked my way through the trouble shooting guide by Lkjoel and Wildmanne39 which is listed at the start of this thread. Still no success. All I want is bog-standard stereo in and out. I have a pile of vinyl, a very good turntable and a pre-amp which I would like to use to convert my record collection into OGG Vorbis files. Frustratingly I have a very cheap netbook with Ubuntu 12.04 which works fine with Audacity, it just sounds lousy.
I have tried LinuxMint, bootable CDS, bootable USBs all with no success.
Is there something about the Gigabyte motherboard which makes it impossible to get sound from Linux?

In desperation...
Cheers
Ian

---

### Post by Eddie Wilson on 2013-03-28
Good Day, I've used several different Gigabyte motherboards and haven't had any problems with audio. Sometimes I do have to reconfigure Alsa but that's about it. I've tried to look up the number of your motherboard on the Gigabyte web site and got no hits. Could your check your motherboard number again and also what chipset does your motherboard have? Is it intel, via, or nvidia.

Eddie

---

### Post by tgalati4 on 2013-03-28
Does sound work in Windows?  If not dual-boot, then it's possible that the sound chip is defective.  Was this purchased as a new-in-box retail motherboard, or was this a clearance bin special?

---

### Post by ibchristie on 2013-03-28
Eddie;
Thanks for the reply
The Gigabyte specs page for this MB is here:  [http://www.gigabyte.com.au/products/product-page.aspx?pid=3764#sp]("http://www.gigabyte.com.au/products/product-page.aspx?pid=3764#sp")


The chipset is an Intel® P67 Express Chipset
The Audio specs are:-

    Realtek ALC889 codec
    High Definition Audio
    2/4/5.1/7.1-channel
    Support for Dolby® Home Theater
    Support for S/PDIF Out

I probably should have added the fact that I assembled this box myself, but I don't know how that could have affected the configuration of the onboard sound. I added a RADEON HD5450  graphics card (Part no AX5450 512MK3-SHV2) because the MB does not have built in graphics. This graphics card also has HDMI sound but I don't intend to use it. Once I have worked out how to get the onboard sound operational I may fit an MAudio 2496 sound card if I am not happy with the recordings I get from the onboard chipset.

The listing from aplay -l is

**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC889 Digital [ALC889 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Does that help you help me?
Thanks
Ian

---

### Post by ibchristie on 2013-03-28
tgalati4;
Sorry, I don't have Windows on this machine so I can't answer that question.
The motherboard was bought new in the box from a real store although as I said above I assembled the computer myself. It never occurred to me that the chipset could be faulty and it is now too long ago to return it under warranty. This was the first box that I had assembled completely from scratch myself so there is a faint possibility I may have missed something. 
I have Windows 7 on another machine but I have read too much about the hassles of trying to upgrade motherboards without Windows having a fit to be game to try something like moving the hard drive into this box and booting into Windows.
(As an aside, the only reason I have a Windows machine in the house is that the Australian Tax Office has an online tax return system which only works with Internet Explorer and Windows. The machine gets turned on once a year.)

Still hoping ...
Cheers
Ian

---

### Post by robert shearer on 2013-03-29
2 things to try....(assuming that you have** no sound** at all)
1)  boot into bios and check that the onboard sound is enabled.
2) download and burn an Ubuntu 12.04 live cd and boot that then test audio output.

Checking that the onboard has not been disabled in favour of the hdmi and that there isn't a configuration problem from your modifications to date.

---

### Post by ibchristie on 2013-03-29
Robert;
Thanks for your interest.
I have checked the BIOS and it has onboard peripherals enabled.
I tried a magazine cover Ubuntu 12.04 disc, a 12.04 Lubuntu disc and and a Linux Mint 14 disc, all with no luck. I have also tried a Ubuntu Studio ISO which I downloaded and burnt but it hung during boot so ....

Not giving up just yet...
Cheers
Ian

---

### Post by tgalati4 on 2013-03-29
Intel and Realtek sound chips are well-supported in linux.  So the fact that you are pulling your hair out over this problem points to a possible hardware problem--a bad sound chip, or a poor motherboard connection to the sound chip.  I would use the M-Audio card and move on, because none of the distros that you have tested work.  If it doesn't work in Windows--I know what a pain installing Windows can be--that would be a confirmation of a hardware problem.

Take a high-quality, macro picture of that part of the motherboard and post it.  It's possible that it is a manufacturing error.

---

### Post by Yellow Pasque on 2013-03-29
> I have tried so many different tutorials/how tos/trouble shooting guides that I have lost track.
So even if you fix the original issue, sound may still not work. :\

Here'e generally what I tell users with no sound on an HDA device:
1) Make sure BIOS is latest if possible/applicable
2) Install latest ALSA driver: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)
3) Reboot
4) If it's still not working, file a bug report with the following command. On Ubuntu 12.10 and later, the Alsa info ( [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo) ) is gathered automatically, but you may want to attach a verbose pulse log just in case the issue is with pulseaudio: [https://wiki.ubuntu.com/PulseAudio/Log](https://wiki.ubuntu.com/PulseAudio/Log)
```
apport-bug audio
```

---

### Post by ibchristie on 2013-04-07
Thanks to everyone who offered help. I have mostly given up on sound with this particular machine.
I tried ignoring the lack of HDA sound and going straight to my M-Audio card but the computer hangs during boot once the card is inserted. I suspect there is a hardware problem.
I tried using the Australian Tax Office e-tax website (see an earlier reply above) through WINE and it appears to work! That means I no longer have to keep my Windows box for tax returns. In turn that means I can try my M-Audio card in that (lower spec) box. If successful I will set it up as a dual boot Windows/Linux machine and then if the sound card works with the Linux installation I will delete the Windows partition leaving me finally free!
When I eventually gat around to the next motherboard upgrade I will have another go.
Until then...
Thanks for all the advice
Cheers
Ian

---

### Post by CatKiller on 2013-04-07
Definitely sounds like a hardware problem, with the hangs and all. I've had motherboards that were flaky on arrival but since it's your first build it might be something as simple as incorrect placement of the stand-offs between the motherboard and case, or slivers of metal from screws, or something of that nature.

I've got the same sound device in my computer as well as an Audiophile 192 and it worked fine out of the box. The only annoyance was that it kept defaulting to the HDMI that wasn't connected to anything but that was easily fixed by disabling that output in Pulse.

I concur with a previous poster that there may now be multiple problems with 18 months of fiddling, but faulty hardware aside there's no essential reason why that sound device shouldn't work.

---

### Post by ibchristie on 2013-06-26
Update June 2013
Today I bought another motherboard. Just an ASUS P8z77-V LX. Nothing flash. Swapped it over with the Gigabyte MB, lo and behold (or do I mean hist, hark ...) I have sound! I changed nothing else. So, I am inclined to go with the suggetsion that there was a hardware fault.
Mind you I now have a problem with the display of my Ubuntu desktop. The launcher bar does not load so I can only get at the programs which ahve icons on the desk top. There are a few other window manager problems as well. Linux Mint works perfectly so I may just switch permanently to that.

To those who helped with this thanks and maybe I can return the favour someday.
Cheers
Ian

---

