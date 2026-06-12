---
title: "Optimize Video and Sound (CA0106 &amp; Cape Verde XT)"
date: 2014-09-30
forum: Multimedia Software
---

### Post by Desslok on 2014-09-30
Hello,
      I've built a new PC that I'm having a bit of trouble getting tweaked right for Ubuntu 14.04 and was hoping I could reach out to the community to get some help.   Essentially just want to list out my hardware and make sure I'm going down the right path for tweaking and whatnot.   Here's the hardware and some idiosyncrasies I'm seeing:

04:06.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster    (AKA SB0570, SB Audigy SE)
[INDENT]Initially only got sound out of the right-hand speaker.   I've since discovered the trick of opening up alsamixer and turning the volume up on the right-hand side.   However now I don't any audio from the subwoofer. (Speaker set similar to logitech z506).[/INDENT]

01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde XT [Radeon HD 7770/8760 / R7 250X]
[INDENT]This seems to be working reasonably well now after I installed the fglrx-updates driver from the repo.  However I "believe" that it supports H.264 and when I run top, I still see a pretty good bit of CPU usage when I play movies in smplayer.   I installed the xvba-va-driver which I "thought" helped to enable that.  But maybe I missed a step (possibly need to put something in a config file to enable it?)[/INDENT]


Also, when I've played a few videos, I get the following error:
MPlayer interrupted by signal 6 in module: decode_audio
ID_SIGNAL=6
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.

Just before I started doing a lot of web research, I figured I'd ask to see if anyone had some "known fixes" for this hardware config.  Posting below other things I've seen folks in the forums ask for:

me@host:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 10: HDMI 4 [HDMI 4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 11: HDMI 5 [HDMI 5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (external gfx0 port B) (rev 02)
00:00.2 IOMMU: Advanced Micro Devices, Inc. [AMD/ATI] RD990 I/O Memory Management Unit (IOMMU)
00:02.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port B)
00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port D)
00:07.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port G)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 42)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:16.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 5
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde XT [Radeon HD 7770/8760 / R7 250X]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde/Pitcairn HDMI Audio [Radeon HD 7700/7800 Series]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 09)
03:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
04:06.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster

More than happy to provide more if needed.

Thanks,
Clif

---

### Post by Bucky Ball on 2014-09-30
You might like to install Pulseaudio Volume Control (is in the repos) if not already installed. That will help with finer-grained tweaking of audio settings. If you have Pulseaudio installed already, that is. 

In your Software Sources (use Xfce so not sure, but 'Software Updater>Settings (bottom left corner)>Other Software>Canonical Partners repo is enabled? In 'Ubuntu Software' tab, 'Proprietary Drivers for devices' and 'Software Restricted by Copyright' enabled?).

---

### Post by Desslok on 2014-09-30
Bucky,

     Thanks for the input, looks like I'd already tried that and it really didn't make a difference.  Still no audio from the Subwoofer.   I "suspect" that something in the driver may just have a channel matched up wrong or something, but haven't had the time to Google it thoroughly enough yet.  As much as I hate it, time is starting to become a premium item and I may be forced to purchase a copy of Microsoft Windows (1st time since like Windows 95) just so I can get the "it just works" for the most part experience.  But, hoping I'll get lucky and someone out there may come across my post and have seen and fought the battle ;-).

Thanks,
Clif

---

### Post by Bucky Ball on 2014-10-01
I'm hear you, Desslok. Is odd and a rare prob from what I can find. How exactly do you have these speakers plugged into the comp? Run it by me again, in case you haven't ...;)

PS: If you have been at it since Gutsy and only had seven support posts, that is a great vote for Ubuntu!! Was this all workng fine in other releases (i.e. 12.04?)

---

### Post by Desslok on 2014-10-02
Bucky,

     Thanks for the reply.   The speakers are just plugged into the green black and orange line out jacks on the back of the card.  From what I'm reading on wikipedia that should be:

 	Lime green      Analog line level audio output for the main stereo signal (front speakers or headphones).
        Black               Analog line level audio output for the surround speakers (rear speakers).
        Orange            Analog line level audio output for the center speaker / Subwoofer  (I found a diagram somewhere that indicated it was a 

     The speakers were working fine with the onboard audio on my old PC (Which I'm pretty sure started at like 7.04, later got upgraded to 8.04, 10.04, and 12.04).   But, this is a brand spanking new PC so is the time I've tried linux on it.  I did however boot it up on a 12.04 live CD and it seemed to have the same issue.  I had Windows 2012 R2 on it for about 6 months working on practicing some installs for work, but unfortunately never bothered to hook up the speakers.  So, I'm kinda thinking this is either a hardware problem with the Audigy SE, or a driver problem that's been around for a while (saw several folks who had had the sound only on the right channel issue).  I've got a 2nd HDD in here that is still blank, I _may_ throw Windows on it real quick and just confirm that it works there to see if I can rule out a hardware problem if I get the extra hour or two over the next few days.
     As to the prior posts.  I've at least played with Linux since the 1994 time period, but I've only really converted over to using it as my _Primary_ os at home since I'm guessing around 2004.   Originally had run Debian, util I got some piece of hardware that was just "easier" to get working on Ubuntu.    I can generally follow instructions, but as I get older I'm getting a little less tolerant of "too many steps" ;-).     But, if you need me to provide any more info, I'd be happy to provide.. just be patient with me.

Thanks,
Clif

---

