---
title: "Can’t get sound over HDMI cable with Ubuntu 10.4"
date: 2011-03-19
forum: Multimedia Software
---

### Post by cowboyjo on 2011-03-19
I just built a computer for my TV (to use as a media center) .  I am using the Biostar TD55  motherboard’s bulit-in sound and graphics, and an Intel i3 -550 cpu. I am using a widescreen HD TV as the monitor, connected to the computer with an HDMI cable.  Initially, audio was only output from the rear headphone-type jacks.  I added  “options snd-hda-intel model=3stack-6ch-dig” to /etc/modprobe.d/alsa-base.conf, which got the front headphone jack working, too.  However, I cannot figure out how to get sound over the HDMI cable to my TV.  The computer dual boots with Windows, and in Windows I can get sound to the TV over the HDMI cable.  I’d rather use Ubuntu, but this sound problem has me ready to switch back.

I have spent a lot of time on the web trying to troubleshoot this.  I have worked through the basics from [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) , but that just got the front jack working.  Some promising pages talk about a “IEC958” checkbox under Preferences on a Device tab in the Volume Control or Sound Preferences window, but I cannot find anything like that in Ubuntu 10.4; I’m thinking that is from an earlier version.  I messed around in alsamixer (in terminal, typed “alsamixer”, then unmuted everything I could find, including some “S/PDIF” items), but that did not seem to affect anything.  I did try each Profile in the Sound Preferences - Hardware tab; some turned off the headphone jacks, but none got sound to the TV through the HDMI cable.

Please help my figure out how to get sound to my TV through the HDMI cable.  Thanks.   More info. about the sound in my system is below.  I’m not sure what all of it means, but the various sites indicated that parts were important.

[SIZE="3"]“wget -O alsa-info.sh [http://alsa-project.org/alsa-info.sh](http://alsa-project.org/alsa-info.sh) && bash ./alsa-info.sh” output[/SIZE]
[http://www.alsa-project.org/db/?f=806a80bf2360d48a7219b9830e7314552534d9f9](http://www.alsa-project.org/db/?f=806a80bf2360d48a7219b9830e7314552534d9f9)

[SIZE="3"]lspci -v output (Audio device portion)[/SIZE]
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
    Subsystem: Biostar Microtech Int'l Corp Device 8220
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at fb7f4000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

[SIZE="3"]aplay -l output[/SIZE]
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
 Subdevices: 0/1
 Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
 Subdevices: 1/1
 Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
 Subdevices: 1/1
 Subdevice #0: subdevice #0

[SIZE="3"]/proc/asound/pcm contents[/SIZE]
00-00: ALC888 Analog : ALC888 Analog : playback 1 : capture 1
00-01: ALC888 Digital : ALC888 Digital : playback 1 : capture 1
00-02: ALC888 Analog : ALC888 Analog : capture 1
00-03: INTEL HDMI : INTEL HDMI : playback 1

---

