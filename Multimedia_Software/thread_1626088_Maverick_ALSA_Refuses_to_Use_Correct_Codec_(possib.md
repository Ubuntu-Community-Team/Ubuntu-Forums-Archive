---
title: "Maverick: ALSA Refuses to Use Correct Codec (possible bug)"
date: 2010-11-19
forum: Multimedia Software
---

### Post by kelocena on 2010-11-19
Ah, I'm not sure I titled this correctly, but that's as close as I can come to describing it. My sound is staticy/low quality and I know what is wrong, I just can't seem to figure out *why* and how to fix it. It's like ALSA only *partially* recognizes my card...? I don't even--- For the record, I am using an HDA Intel card on a Lenovo IdeaPad Y530. Pooo.

For starters, I had the usual "oh noes! I upgraded and things won't work anymore" scenario. I tried some things, then gave up and just did a fresh install of 10.10. Obviously, that hasn't worked. I tried the same fix that has worked in the past (9.10 and 10.04), which is adding "options snd-hda-intel model=lenovo-sky" to my /etc/modprobe.d/alsa-base.conf. This has had no effect whatsoever in 10.10. My sound card still doesn't show up under Sound Preferences > Devices. So let's get started on figuring this thing out, shall we?

I have the necessary modules installed, and **aplay -l** returns:
> **** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI 0 [INTEL HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0**lspci -v | less** gives me the following for my audio:
> 00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
        Subsystem: Lenovo Device 3a0d
        Flags: bus master, fast devsel, latency 0, IRQ 45
        Memory at d4200000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel
Nothing new there. The results of **wget -O alsa-info.sh [http://alsa-project.org/alsa-info.sh](http://alsa-project.org/alsa-info.sh) && bash ./alsa-info.sh**:
[http://www.alsa-project.org/db/?f=cbd001fd228e5ed7187322efa1dbaef081ec28a4](http://www.alsa-project.org/db/?f=cbd001fd228e5ed7187322efa1dbaef081ec28a4)

Now, the issue is that regardless of "options snd-hda-intel model=lenovo-sky" and/or **sudo modprobe snd-hda-intel**, the sound is still crap. But I have at least noticed something interesting, though I'm not sure where things are going wrong. If you look at the webpage with my sound info and scroll down to "!!HDA-Intel Codec information", you'll see that it lists three codecs. The first is Realtek ALC888, the second is Motorola Si3054, and the final one is Intel Cantiga HDMI. The one I *want* to be using is Realtek, but editing my alsa-base.conf* doesn't fix anything. When I open **alsamixer**, it is still using the wrong codec. It says:
> Card: HDA Intel
Chip: Intel Cantiga HDMIWhy isn't ALSA recognizing my sound card correctly/using the correct module and how do I fix that?

*I also tried adding "options snd-hda-intel index=0" with no luck.

---

### Post by efflandt on 2010-11-20
What do you get for: **dmesg | grep -i hda**

Your WinModem showing up on the same card may have something to do with your issue, since that is an effectively an audio device.  Although, I have not paid attention to solutions for that, since I do not have that problem.

I know little about alsa.  But see if this helps or not, to just use the codec of the first device it finds(?):

options snd-hda-intel probe_mask=1

---

