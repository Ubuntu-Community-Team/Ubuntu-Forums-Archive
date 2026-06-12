---
title: "No sound after update on Dell studio 1555"
date: 2010-08-12
forum: Multimedia Software
---

### Post by ravisghosh on 2010-08-12
After recent update of 10.4 on my Dell Studio 1555, the sound stopped working. Searched forum and google, but the only thing I could make out is that it has something to do with pulseaudio. But no clue as to how to solve it.

Here is the aptitude log of the machine.

> Aptitude 0.4.11.11: log report
Tue, Aug 10 2010 02:17:38 +0530

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 9 packages, and remove 0 packages.
36.9kB of disk space will be used
===============================================================================
[UPGRADE] chromium-browser 6.0.486.0~svn20100805r55014-0ubuntu1~ucd1~lucid -> 6.0.487.0~svn20100806r55176-0ubuntu1~ucd1~lucid
[UPGRADE] chromium-browser-inspector 6.0.486.0~svn20100805r55014-0ubuntu1~ucd1~lucid -> 6.0.487.0~svn20100806r55176-0ubuntu1~ucd1~lucid
[UPGRADE] chromium-codecs-ffmpeg 0.5+svn20100611r49485+50002-0ubuntu1~ucd1~lucid -> 0.6+svn20100730r54382+55302-0ubuntu1~ucd1~lucid
[UPGRADE] libpcsclite1 1.5.3-1ubuntu4 -> 1.5.3-1ubuntu4.1
[UPGRADE] python-apt 0.7.94.2ubuntu6.1 -> 0.7.94.2ubuntu6.2
[UPGRADE] tzdata 2010j-0ubuntu0.10.04 -> 2010k-0ubuntu0.10.04
[UPGRADE] tzdata-java 2010j-0ubuntu0.10.04 -> 2010k-0ubuntu0.10.04
[UPGRADE] update-manager 1:0.134.9 -> 1:0.134.10
[UPGRADE] update-manager-core 1:0.134.9 -> 1:0.134.10
===============================================================================

Log complete.
Aptitude 0.4.11.11: log report
Wed, Aug 11 2010 02:34:20 +0530

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 4 packages, and remove 0 packages.
156kB of disk space will be used
===============================================================================
[UPGRADE] acpi-support 0.136 -> 0.136.1
[UPGRADE] chromium-browser 6.0.487.0~svn20100806r55176-0ubuntu1~ucd1~lucid -> 6.0.491.0~svn20100810r55554-0ubuntu1~ucd1~lucid
[UPGRADE] chromium-browser-inspector 6.0.487.0~svn20100806r55176-0ubuntu1~ucd1~lucid -> 6.0.491.0~svn20100810r55554-0ubuntu1~ucd1~lucid
[UPGRADE] libldap-2.4-2 2.4.21-0ubuntu5 -> 2.4.21-0ubuntu5.2
===============================================================================

Log complete.


Any help would be much appreciated.

[COLOR="Blue"]SOLVED - On running "ubuntu-bug audio," I got a message:

```
You seem to have configured PulseAudio to use the "pci-0000_01_00.1" card, while you want output from "HDA-Intel - HDA Intel". Please correct that using pavucontrol or the GNOME volume control. Continue anyway? 
```

Under "Configuration>RV710/730," I changed the "Profile" to "Off."

Then again on running "ubuntu-bug audio," I got a message that something was muted and it asked me to run alsamixer.

On running alsamixer, I found the speaker were muted and then unmuted them. Of note, earlier nothing was muted in alsamixer before changing the RV710/730 Profile off.

This got my audio working :)[/COLOR]

---

### Post by [Shawn] on 2010-08-12
I've had a similar issue to what your experiencing.
Go to terminal and type ```
aplay -l
```and report the output back here.

---

### Post by ravisghosh on 2010-08-13
> **'[Shawn] said:**
> I've had a similar issue to what your experiencing.
Go to terminal and type ```
aplay -l
```and report the output back here.

Here is the output of aplay -l

> shantanu@GreenHead:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


---

### Post by lidex on 2010-08-14
Did you check mixer levels? Those updates shouldn't affect audio.
Can you post the output of these terminal commands for me please:
```
uname -a
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```
```
dmesg | grep -C1 -E 'ALSA|HDA|HDMI|sound|hda.codec|hda.intel'
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by ravisghosh on 2010-08-16
> **lidex said:**
> Did you check mixer levels? Those updates shouldn't affect audio.
Can you post the output of these terminal commands for me please:


Thanks for the help lindex. I did check the mixer levels and they are fine. Here are the output of the commands. Also, model of the PC is mentioned in the sig line.

```
shantanu@GreenHead:~$ uname -a
Linux GreenHead 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64 GNU/Linux
```

```
shantanu@GreenHead:~$ dpkg -l | grep "alsa"
ii  alsa-base                                          1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                                         1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                                         4.60-0ubuntu8                                   Bluetooth audio support
ii  gnome-alsamixer                                    0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                                 0.10.28-1                                       GStreamer plugin for ALSA
ii  libesd-alsa0                                       0.2.41-6ubuntu1                                 Enlightened Sound Daemon (ALSA) - transitional package
ii  libsdl1.2debian-alsa                               1.2.14-4ubuntu1.1                               Simple DirectMedia Layer (with X11 and ALSA options)
```

```
shantanu@GreenHead:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: IDT 92HD73C1X5

==> /proc/asound/card1/codec#0 <==
Codec: ATI R6xx HDMI

```

```
shantanu@GreenHead:~$ sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
[sudo] password for shantanu: 
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  shantanu   1951 F.... xfce4-mixer-plu
                     shantanu   1974 F.... pulseaudio
                     shantanu   2120 F.... xfce4-volumed
/dev/snd/controlC1:  shantanu   1951 F.... xfce4-mixer-plu
                     shantanu   2120 F.... xfce4-volumed
```

```
shantanu@GreenHead:~$ dmesg | grep -C1 -E 'ALSA|HDA|HDMI|sound|hda.codec|hda.intel'
[   13.830163]   alloc kstat_irqs on node -1
[   13.830170] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   13.830930] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   13.959604] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input14
[   13.981296] input: HDA Intel Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[   13.981468] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input16
[   13.981609] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input17
[   13.982496] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   13.982534] HDA Intel 0000:01:00.1: setting latency timer to 64
[   14.254442] usb 3-1.3: new full speed USB device using uhci_hcd and address 5
--
[   30.070235] eth0: no IPv6 routers present
[   51.236782] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   57.929401] lo: Disabled Privacy Extensions

```

---

### Post by lidex on 2010-08-16
```
shantanu@GreenHead:~$ sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
[sudo] password for shantanu: 
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  shantanu   1951 F.... xfce4-mixer-plu
                     shantanu   1974 F.... pulseaudio
                     shantanu   2120 F.... xfce4-volumed
/dev/snd/controlC1:  shantanu   1951 F.... xfce4-mixer-plu
                     shantanu   2120 F.... xfce4-volumed
```

Try disabling xfce4-mixer* and xfce4-volume*. If you're trying to use pulse it needs sole control of those devices.

---

### Post by ravisghosh on 2010-08-17
> **lidex said:**
> Try disabling xfce4-mixer* and xfce4-volume*. If you're trying to use pulse it needs sole control of those devices.

Removed both xfce4-mixer and xfce4-volumed but no effect :(

---

### Post by lidex on 2010-08-17
> **ravisghosh said:**
> Removed both xfce4-mixer and xfce4-volumed but no effect :(
Run that dmesg command again and post results.

---

### Post by ravisghosh on 2010-08-17
> **lidex said:**
> Run that dmesg command again and post results.

Here is it lindex:
```

shantanu@GreenHead:~$ dmesg | grep -C1 -E 'ALSA|HDA|HDMI|sound|hda.codec|hda.intel'
[    9.559476]   alloc kstat_irqs on node -1
[    9.559483] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    9.559564] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    9.560047] Console: switching to colour frame buffer device 80x30
--
[    9.605955] phy0: Selected rate control algorithm 'iwl-agn-rs'
[    9.679356] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input14
[    9.753697] input: HDA Intel Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[    9.753774] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input16
[    9.753829] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input17
[    9.754391] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    9.754440] HDA Intel 0000:01:00.1: setting latency timer to 64
[    9.854575] EXT4-fs (sda6): mounted filesystem with ordered data mode
--
[   71.562214] CPUFREQ: Per core ondemand sysfs interface is deprecated - up_threshold
[   76.934940] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   77.424582] lo: Disabled Privacy Extensions
```

---

### Post by lidex on 2010-08-17
> **ravisghosh said:**
> Here is it lindex:
```

shantanu@GreenHead:~$ dmesg | grep -C1 -E 'ALSA|HDA|HDMI|sound|hda.codec|hda.intel'
[    9.559476]   alloc kstat_irqs on node -1
[    9.559483] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    9.559564] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    9.560047] Console: switching to colour frame buffer device 80x30
--
[    9.605955] phy0: Selected rate control algorithm 'iwl-agn-rs'
[    9.679356] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input14
[    9.753697] input: HDA Intel Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[    9.753774] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input16
[    9.753829] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input17
[    9.754391] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    9.754440] HDA Intel 0000:01:00.1: setting latency timer to 64
[    9.854575] EXT4-fs (sda6): mounted filesystem with ordered data mode
--
[   71.562214] CPUFREQ: Per core ondemand sysfs interface is deprecated - up_threshold
[   76.934940] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   77.424582] lo: Disabled Privacy Extensions
```
Hmm, I'm sorry , I meant the fuser command. :oops:

---

### Post by ravisghosh on 2010-08-18
> **lidex said:**
> Hmm, I'm sorry , I meant the fuser command. :oops:

Here is the fuser command output:
```
[sudo] password for shantanu: 
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  shantanu   2237 F.... pulseaudio
/dev/snd/controlC1:  shantanu   2237 F.... pulseaudio
/dev/snd/pcmC1D3p:   shantanu   2237 F...m pulseaudio

```

Thanks lidex for your continued help in fixing the issue.

---

### Post by lidex on 2010-08-19
> **ravisghosh said:**
> Here is the fuser command output:
```
[sudo] password for shantanu: 
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  shantanu   2237 F.... pulseaudio
/dev/snd/controlC1:  shantanu   2237 F.... pulseaudio
/dev/snd/pcmC1D3p:   shantanu   2237 F...m pulseaudio

```

Thanks lidex for your continued help in fixing the issue.

That looks as it should. Did you tweak anything audio related before the update that may have been undone? All the basics check out - levels good, not muted, etc?
Let's see what happens when you run this command:
```
ubuntu-bug audio
```

---

### Post by ravisghosh on 2010-08-19
I ran "ubuntu-bug audio" and it said:

```
You seem to have configured PulseAudio to use the "pci-0000_01_00.1" card, while you want output from "HDA-Intel - HDA Intel".
 Please correct that using pavucontrol or the GNOME volume control. Continue anyway?
```

Then I installed pavucontrol, but there was no option of selecting HDA-Intel or anything else. 

I continued with the debug and I could hear the test tone. However, when the test tone was alternating between channels, I did not hear anything.

Here is the link of launchpad bug report: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/620524](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/620524)

---

### Post by lidex on 2010-08-19
What about 'Sound Preferences'? On the 'Hardware' tab under 'Choose a device to configure'.

---

### Post by ravisghosh on 2010-08-19
> **lidex said:**
> What about 'Sound Preferences'? On the 'Hardware' tab under 'Choose a device to configure'.

I'm on xubuntu and dont have Sound Preferences or Hardware thingi.

On xfce4-mixer, I can select:
1. HDA Intel (Alsa Mixer).
2. HDA ATI HDMI (Alsa Mixer).
3. IDT 92HD73C1X5 (OSS Mixer)
4. Playback RV710/730 Digital Stereo (HDMI) (PulseAudio Mixer).
5. Playback Internal Audio Analog Stereo (PulseAudio Mixer).
6. Capture: Monitor of RV710/730 Digital Stereo (HDMI) (PulseAudio Mixer).
7. Capture: Monitor of Internal Audio Analog Stereo (PulseAudio Mixer).
8. Capture: Internal Audio Analog Stereo (PulseAudio Mixer).

---

### Post by lidex on 2010-08-19
OK, wasn't sure about that. Does pulse come in the default xubuntu install? I'm wondering if you actually need it.

---

### Post by ravisghosh on 2010-08-19
> **lidex said:**
> OK, wasn't sure about that. Does pulse come in the default xubuntu install? I'm wondering if you actually need it.

I guess it does not come with default xubuntu. As far as I remember, I installed it to get audio working on my Dell 1555 laptop.

Can I do away with this and install something else to get audio working?

---

### Post by lidex on 2010-08-19
> **ravisghosh said:**
> I guess it does not come with default xubuntu. As far as I remember, I installed it to get audio working on my Dell 1555 laptop.

Can I do away with this and install something else to get audio working?

You may be better off trying to get it working then. So you had to do some tinkering previously. Try this. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=dell-eq 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

---

### Post by ravisghosh on 2010-08-19
@lindex - Followed the instructions, but to no avail. :(

---

### Post by lidex on 2010-08-19
> **ravisghosh said:**
> @lindex - Followed the instructions, but to no avail. :(
Now try your mixer and select hda-intel. It would be helpful for you to post screenshots of xfce-mixer and alsamixer

---

### Post by ravisghosh on 2010-08-19
HDA Intel was selected earlier.

---

### Post by lidex on 2010-08-19
> **ravisghosh said:**
> HDA Intel was selected earlier.

Try alsamixer and mute your digital/spdif elements

---

### Post by ravisghosh on 2010-08-19
Tried that, no sound yet.

---

