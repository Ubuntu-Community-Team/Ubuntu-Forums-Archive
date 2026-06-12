---
title: "No more sound after upgrade to Lucid."
date: 2010-04-30
forum: Multimedia Software
---

### Post by sasciame on 2010-04-30
After upgrading to Lucid, my Compaq Presario Deskpro EN has no sound.  

[FONT=monospace]
[LIST=1]
[*]steven@EWCCFD:~$ aplay -l
[*]**** List of PLAYBACK Hardware Devices  ****
[*]card 0: I82801BAICH2 [Intel  82801BA-ICH2], device 0: Intel ICH [Intel 82801BA-ICH2]
[*]  Subdevices: 0/1
[*]  Subdevice #0: subdevice #0
[*]steven@EWCCFD:~$ lspci -v | grep   82801BA-ICH2
[*]steven@EWCCFD:~$ lspci -v | grep  Intel
[*]00:00.0 Host bridge: Intel Corporation  82815 815 Chipset Host Bridge and Memory Controller Hub (rev 04)
[*]00:01.0 PCI bridge: Intel Corporation  82815 815 Chipset AGP Bridge (rev 04)
[*]00:1e.0 PCI bridge: Intel Corporation  82801 PCI Bridge (rev 02)
[*]00:1f.0 ISA bridge: Intel Corporation  82801BA ISA Bridge (LPC) (rev 02)
[*]00:1f.1 IDE interface: Intel  Corporation 82801BA IDE U100 Controller (rev 02) (prog-if 80 [Master])
[*]        Subsystem: Intel Corporation  Device 2411
[*]00:1f.4 USB Controller: Intel  Corporation 82801BA/BAM USB Controller #1 (rev 02)
[*]        Subsystem: Intel Corporation  Device 2411
[*]00:1f.5 Multimedia audio controller:  Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 02)
[*]        Kernel driver in use: Intel ICH
[*]02:08.0 Ethernet controller: Intel  Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 01)
[*]steven@EWCCFD:~$
[/LIST]



It appears that my sound card has been found.  It doesn't appear to be muted, and yes the master volume is up.

Has anyone else experienced anything like this?  Any help would be much appreciated
[/FONT]

---

### Post by Moustacha on 2010-04-30
I've got this too
```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
	Subsystem: Micro-Star International Co., Ltd. Device 7250
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at f9ef0000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```
still trying to google for a solution if there is one

Edit:I think I've found the fix. It's bad config settings.
In the sound mixer panel go to "Playback:Internal Audio Analog Stereo(PulseAudio Mixer)" or something like it, add the master control to the panel and then un-mute it. Now it works!

---

### Post by tocker on 2010-05-01
Hi,

I have the same problem.

Try opening a terminal and type the command:
```
pulseaudio
```

If you now have sound, you know that *it's not a hardware or missing libraries issue*.

It seems that Pulse Audio doesn't start automatically after the upgrade. I'm not sure why - I just found out a couple of minutes ago...

---

### Post by sosias on 2010-05-01
arthur@HerzausGold:~$ pulseaudio
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() fehlgeschlagen.

I got this and still no sound:(

---

### Post by djxcon on 2010-05-01
Same here...no sound on an audiophile 2496 but I do have sound on an external sound card. 

```

**** List of PLAYBACK Hardware Devices ****
card 0: M2496 [M Audio Audiophile 24/96], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: UA4FX [UA-4FX], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by henrik_daver on 2010-05-01
> **sosias said:**
> arthur@HerzausGold:~$ pulseaudio
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() fehlgeschlagen.

I got this and still no sound:(

Same here. Also, if I try to start the "Default Sound Card" menu item (under "Settings") nothing happens.

```

**** Lista över PLAYBACK hårdvaruenheter ****
kort 0: Intel [HDA Intel], enhet 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Underordnade enheter: 0/1
  Underordnad enhet nr. 0: subdevice #0
kort 0: Intel [HDA Intel], enhet 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0
kort 0: Intel [HDA Intel], enhet 3: INTEL HDMI [INTEL HDMI]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0
kort 0: Intel [HDA Intel], enhet 6: Si3054 Modem [Si3054 Modem]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0

```

---

### Post by lilpiggie on 2010-05-01
Try opening a terminal and type the command: ```
alsamixer
```

Check if it says "MM" under any of the playback devices such as Master, Speaker, etc. ("MM" means the left+right stereo channels are muted) 
You can toggle muting on or off by pressing the "m" key, use the arrow keys to navigate and change it to "OO".

---

### Post by subluminal on 2010-05-01
Running `alsamixer` revealed that my speaker volume had been set to zero, but drivers and hardware were still doing there thing. Setting it to 100% returned everything to normal.

---

### Post by begonia on 2010-05-01
I am really really tired of my sound breaking every time I upgrade or get a new kernel or whatever.  It's a really sad state of affairs in Ubuntu land...

---

### Post by rickc1970 on 2010-05-01
My sound is working however the speaker icon that was on the top toolbar is no longer there. I can adjust the volume with the keyboard and all but I would like to be able to just click the icon to adjust it. Anyone know how to fix this? This only changer after the upgrade to 10.04.

---

### Post by ivotron on 2010-05-02
[This]("http://ubuntuforums.org/showpost.php?p=9214046&postcount=12") solved the issue for me

---

### Post by lidex on 2010-05-02
It's been moved. You need to add the indicator applet to the panel for it to show.

---

### Post by noiq on 2010-05-03
> **Moustacha said:**
> Edit:I think I've found the fix. It's bad config settings.
In the sound mixer panel go to "Playback:Internal Audio Analog Stereo(PulseAudio Mixer)" or something like it, add the master control to the panel and then un-mute it. Now it works!

The same worked for me, too. Thanks Moustacha.

---

### Post by slumbergod on 2010-05-30
Just removed pulse audio from Xubuntu Lucid. What a surprise, sound is much, much better. I was so disappointed when I saw that pulse had been added back for Lucid. Why, oh why, does anyone bother with pulse-abomination-audio?????

---

### Post by spivee69 on 2010-07-07
ivotron, thanks for the link.  Worked great.  This was driving me nuts.

---

### Post by tigerdog on 2010-07-12
link did not work here.  System has onboard nVidia/Realtek sound (not used) and M-audio 24/96.  M-audio does not work under lucid; still works under Win2K so not hardware related.

---

### Post by mfarshada on 2011-11-09
I also had no sound after upgrading to lucid. I typed alsamixer, then a set of volumes appeared in the terminal window and I noticed that the speaker volume was zero! (stupid, yeah) I increased it to max, and life is good now.

BTW, pulseaudio reported:
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.

---

### Post by tigerdog on 2011-11-09
> **tigerdog said:**
> link did not work here.  System has onboard nVidia/Realtek sound (not used) and M-audio 24/96.  M-audio does not work under lucid; still works under Win2K so not hardware related.
FWIW, M-audio works fine under 11.10.

---

