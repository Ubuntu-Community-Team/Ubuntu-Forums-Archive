---
title: "Maverick - GT220 - No HDMI Audio"
date: 2010-10-16
forum: Multimedia Software
---

### Post by Envisages on 2010-10-16
Forgive me if this has been solved elsewhere but I have been unable to find a solution.
I'm running Maverick with a Sparkle GT210 card. HDMI video works great, and though it seems to see the card, I have no audio.

Any help is appreciated

$ cat /proc/version
Linux version 2.6.35-22-generic (buildd@rothera) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #34-Ubuntu SMP Sun Oct 10 09:24:00 UTC 2010

$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.

$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Nvidia GT220 HDMI
Codec: Nvidia GT220 HDMI
Codec: Nvidia GT220 HDMI
Codec: Nvidia GT220 HDMI

$ dmesg | grep Linux
[    0.000000] Linux version 2.6.35-22-generic (buildd@rothera) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #34-Ubuntu SMP Sun Oct 10 09:24:00 UTC 2010 (Ubuntu 2.6.35-22.34-generic 2.6.35.4)
[    0.249034] ACPI: BIOS _OSI(Linux) query ignored
[   15.542102] Linux agpgart interface v0.103

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$ lspci
00:00.0 Host bridge: Intel Corporation 82975X Memory Controller Hub
00:01.0 PCI bridge: Intel Corporation 82975X PCI Express Root Port
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 210] (rev a2)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
04:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5754 Gigabit Ethernet PCI Express (rev 02)

$ cat /proc/asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xeeefc000 irq 16

$ lsmod | grep snd
snd_hda_codec_nvhdmi    12879  4 
snd_hda_intel          22107  0 
snd_hda_codec          87552  2 snd_hda_codec_nvhdmi,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    49006  8 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm

$ grep ^Codec /proc/asound/card?/codec*
/proc/asound/card0/codec#0:Codec: Nvidia GT220 HDMI
/proc/asound/card0/codec#1:Codec: Nvidia GT220 HDMI
/proc/asound/card0/codec#2:Codec: Nvidia GT220 HDMI
/proc/asound/card0/codec#3:Codec: Nvidia GT220 HDMI

$ aplay -L
pulse
    Playback/recording through the PulseAudio sound server
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=1
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=2
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output

Alsamixer shows only S PDIF outputs, all unmuted.

Not sure what more might be needed, (sorry still somewhat new to linux)

---

### Post by lidex on 2010-10-16
Have a look here:
[http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240](http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240)

---

### Post by Envisages on 2010-10-17
> **lidex said:**
> Have a look here:
[http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240](http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240)


Thanks, but I've already tried everything in there.

I did finally manage to get some sound, I set the port_mask option to 0x108 as my receiver is shown in eid#4.0, this gave me 44.1 PCM, and changed my aplay -l to show only one device, but I can't do AC3 or DTS, it only outputs PCM 44.1

---

### Post by lidex on 2010-10-17
> **Envisages said:**
> Thanks, but I've already tried everything in there.

I did finally manage to get some sound, I set the port_mask option to 0x108 as my receiver is shown in eid#4.0, this gave me 44.1 PCM, and changed my aplay -l to show only one device, but I can't do AC3 or DTS, it only outputs PCM 44.1

This seems to be relevant:
[http://ubuntuforums.org/showpost.php?p=7391539&postcount=10](http://ubuntuforums.org/showpost.php?p=7391539&postcount=10)

---

### Post by Envisages on 2010-10-18
> **lidex said:**
> This seems to be relevant:
[http://ubuntuforums.org/showpost.php?p=7391539&postcount=10](http://ubuntuforums.org/showpost.php?p=7391539&postcount=10)

It's a different audio chipset but I gave it a try, set xbmc to 2 channels and enabled DTS & AC3, but I just get a failed to initialize audio device if I attempt to play anything that's AC3 or DTS. Same with 2.1, 3, 3.1, 4, 4.1, 5 & 5.1

It seems to me that the system doesn't recognize that the card can output AC3 or DTS, but I don't know how to get it to.

---

### Post by bprins on 2010-10-26
hey there,

i've got a gt320 (very simular to gt220 architecture).
Not sure if you still have issues, but might be able to push you a bit in the right direction.

First of all, I think you managed a great deal yourself already.

Next step if you didnt already:
edit /etc/modprobe.d/sound.conf (file can be new)
add => options snd-hda-intel enable_msi=0 probe_mask=0xffff,0xfff2

Also make sure your user is listed in the audio group (users & groups -> manage groups -> check audio group -> OK)

Reboot, attach HDMI cable and test
aplay -D plughw:1,3 /usr/share/sounds/alsa/Noise.wav

If this works, give it a try in Xbmc.

This is all based on the Xbmc documentation:
[http://wiki.xbmc.org/?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240](http://wiki.xbmc.org/?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240)

Post back stuff that doesn't work, I'll try my best to help where I can.

---

### Post by Fisralkon on 2011-03-20
Hello,

I just managed to get HDMI audio on a 220 GT, after approx. 1 week of tinkering about, so thought I would share my experiences in case it would help someone (other posts sure helped me, so give back a little).

**My Setup:** AMD64 on ASUS M2N68 MoBo (home-built PC) with integrated NVidia graphics controller VT1708B. Ubuntu 10.04, NVidia drivers 195.36.24. For this PC I purchased a Sweex GT 220 card (on sale in a MediaMarkt shop), in order to hopefully get HDMI output to the TV (Samsung, full HD).

HDMI video worked out of the box for my system. In NVIdia XServer settings (under System -> Administration), I just needed to first set the screen resolution for my monitor and add the TV as a second screen (first pressed "Detect displays", then added TV as a Separate X screen). There's a youtube video that shows this also, but for me this was essentially no problem, took a few reboots to get to the good resolution and then it was OK.

My advice for the graphics part would be to:
1) ensure you're at the latest NVidia driver (at least 195.36.24)
2) first set up your PC monitor for the GT220 card, use e.g. a game like warsow to test graphics acceleration.
3) When monitor is OK, add your HDMI TV as a second, separate X screen and configure acc to TV specs.

HDMI sound next, for this I set out to follow the XBMC link posted earlier. After seeing that I had alsa 1.0.21 installed, I followed the steps to get alsa 1.0.23. This went OK, but before the system picked it up I also had to install and upgrade linux-headers-alsa-driver-2.6.32-29-generic (using package manager and upgrade manager). 'cat /proc/asound/version' then displayed 1.0.23.

After reboot, 4 HDMI devices showed up in aplay -l, as so many have reported, and I had no sound on any, as so many have also reported.

First, I tried different options in /etc/modprobe.d/alsabase.conf to find that excluding probe_mask, or having probe_mask=0xffff, would show me the 4 devices. Having probe_mask=0xfff2 or 0xffff,0xfff2 would cause no sound device to be shown, I interpreted this as a conflict between MoBo and PCI card.

With the 4 devices visible, I unmuted all in alsamixer, then tested them one by one using gstreamer-properties (an excellent tool for this!) and aplay-D plughw:1,[3,7,8,9]. Based on this I decided that 1,7 was the device I wanted to use. After trying and failing to find info about probe_mask, I tried different options and ended up with the following line in alsa-base.conf:

# GT220 HDMI
options snd-hda-intel enable_msi=0 probe_mask=0xffff,0xfff3 

With this option, I got a system that would reliably come up with MoBo audio working and the following devices reported by aplay-l:

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: NVidia [HDA NVidia], device 1: VT1708B Digital [VT1708B Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia_1 [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia_1 [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I then introduced the line for /etc/pulse/default.pa from the Wiki page, as follows:

load-module module-alsa-sink device=plughw:1,7

Where "plughw" shold be either "hw" or "plughw" depending on your results with "gstreamer-properties" and "aplay -D" and "1,7" should of course also be adapted acc. to this.

I finally created /etc/asound.conf, with only the following line:

pcm:iec958 hdmi:NVidia_1

where NVidia_1 is the name of my card reported by aplay -l

After reboot, I now have 3 audio devices in the sound applet:

- "Internal analog audio" (MoBo sound controller - goes to PC monitor speakers), works reliably 
- "High definition audio controller (HDMI)" - selectable but no sound in TV. Could it be because TV is connected with the DVI/HDMI port of the TV? Or HW conflict with MoBo? Anyway, not going further down this path right now. :confused:
- "High definition audio controller" - works reliably, good quality stereo sound in TV through HDMI (test sounds, system sounds, youtube, rythmbox, mp3 playback etc.). :p

I am still curious about probe_mask and how it actually works, so if someone can give info here I guess it's interesting for everyone.

To sum up, I essentially followed the xbmc page, but had to try various probe_mask options before arriving at one that seems OK for my setup. I also made the mistake of setting "hw" and not "plughw" in default.pa and this resulted in crackling, noisy sound on TV. So take care to add the correct option here (same as gives good sound using aplay -D).

Summary of my steps:

1) Make sure to have alsa 1.0.23 installed (follow the xbmc steps)

2) Try different options in modprobe.d/alsa-base.conf until the devices you need come up (check with aplay -l). At least in my case, certain options would conflict with MoBo sound. The option 0xfff3 I ended up with is not documented anywhere else as a useful option, so I would be curious to get an explanation about this from someone more guru-style....

3) For every mod_probe option, use gstreamer-properties, aplay -D, and testing system sounds in the sound applet. Don't forget to also test MoBo sound so you don't break it by mistake. Also remember that devices may get muted when you change configs and reboot / reload alsa - use alsamixer to check this and unmute if needed.

4) Once you've decided on the device, add it to /etc/pulse/default.pa (take care to use the correct "hw" or "plughw" option)

5) Finally, if needed, append / create /etc/asound.conf according to end of xbmc page. In my case, I omitted the hdmi line, because I couldn't get sound from it and I suspected it conflicted somehow with MoBo sound controller. I'm happy with the other option working.

Hope all this can be of help to someone. And if a guru out there can point out why certain things ended up the way they did, I'm also curious to know.

Cheers,

---

### Post by kuaiat on 2011-12-18
Hey, this is very basic, but just in case it may help others I sum up my problem and the solution:

I couldn get any sound using HDMI (graphic card: Nvidia Geforce GT 220) on Ubuntu11.10.

I clicked on System Settings/Additional Drivers.

Then select "NVIDIA accelerated graphics driver" and click activate.

After it's been downloaded and installed, reboot.

Then System Settings/Sound
- Hardware: Select HDMI. Profile: Digital Stereo (HDMI) nr 2 Output  -->>Important to select the profile.
- Output: HDMI.

---

