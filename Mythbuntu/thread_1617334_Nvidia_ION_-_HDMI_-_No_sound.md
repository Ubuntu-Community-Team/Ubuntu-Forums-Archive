---
title: "Nvidia ION - HDMI - No sound"
date: 2010-11-09
forum: Mythbuntu
---

### Post by Xrcam on 2010-11-09
[SIZE=3][FONT=Times New Roman]Recently, i bought a new computer (Shuttle XS35GT) for the frontend. This thing is equipped with an Nvidia Ion video card and a HDMI port. I hooked it to the primary TV (Samsung ACL), installed Ubuntu 10.10 with Myth 0.23 and let Nvidia drivers to open source.[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]Using Alsamixer, i found the Nvidia audio card and enabled it. Strangely alsamixer do not show volume control for this card. [/FONT][/SIZE][SIZE=3][FONT=Times New Roman]No sound in Ubuntu, no sound watching TV, no sound using VLC or Firefox Youtube.[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]Any clues ???[/FONT][/SIZE]

---

### Post by Xrcam on 2010-11-09
I will post more informations as soon as possible. Things like:
 
aplay -l
alsamixer printscreen
 
etc....

---

### Post by Brandoo_NZ on 2010-11-09
Sorry - this is just off the top of my head...

Check the Myth Frontend settings - you want to make sure the sound device is set to HDMI

Also, Alsamixer will probably have some of the devices muted. Make sure you unmute all (what are the last 3 controls on the far right?)

You say Alsamixer shows no controls - anything shown in dmesg?

---

### Post by keepitsimpleengr on 2010-11-09
I don't know it the ION is the same as geforce, but this is what I had to do to get sound through hdmi.

[http://ubuntuforums.org/showpost.php?p=9988441&postcount=18]("http://ubuntuforums.org/showpost.php?p=9988441&postcount=18")

---

### Post by youknowjoe on 2010-11-10
aplay -l 

should return something like this:

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

vi /etc/asound.conf or ~/.asoundrc and add the following based upon the results from aplay -l:

pcm.!default {
    type hw
    card 0
    device 3
}
ctl.!default {
    type hw           
    card 0
}

Can't remember if I rebooted or not.
Then use alsamixer to umute devices.
I'm doing this from memory so I may have missed something, uncle google helped me out when I was working this issue for a Zotac ION board.

---

### Post by Xrcam on 2010-11-11
Thanks for the help !
Here comes more informations:
 
[FONT=Arial]albator@shuttle:~$ cat /proc/asound/cards[/FONT]
[FONT=Arial] 0 [Intel          ]: HDA-Intel - HDA Intel[/FONT]
[FONT=Arial]                      HDA Intel at 0xfcffc000 irq 43[/FONT]
[FONT=Arial] 1 [NVidia         ]: HDA-Intel - HDA NVidia[/FONT]
[FONT=Arial]                      HDA NVidia at 0xfe97c000 irq 17[/FONT]
[FONT=Arial]albator@shuttle:~$[/FONT]
[FONT=Arial] [/FONT]
[FONT=Arial]albator@shuttle:~$ aplay -l[/FONT]
[FONT=Arial]**** List of PLAYBACK Hardware Devices ****[/FONT]
[FONT=Arial]card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog][/FONT]
[FONT=Arial]  Subdevices: 1/1[/FONT]
[FONT=Arial]  [/FONT][FONT=Arial]Subdevice #0: subdevice #0[/FONT]
[FONT=Arial]card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI][/FONT]
[FONT=Arial]  Subdevices: 1/1[/FONT]
[FONT=Arial]  Subdevice #0: subdevice #0[/FONT]
[FONT=Arial]card 1: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI][/FONT]
[FONT=Arial]  Subdevices: 1/1[/FONT]
[FONT=Arial]  Subdevice #0: subdevice #0[/FONT]
[FONT=Arial]card 1: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI][/FONT]
[FONT=Arial]  Subdevices: 1/1[/FONT]
[FONT=Arial]  Subdevice #0: subdevice #0[/FONT]
[FONT=Arial]card 1: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI][/FONT]
[FONT=Arial]  Subdevices: 1/1[/FONT]
[FONT=Arial]  [/FONT][FONT=Arial]Subdevice #0: subdevice #0[/FONT]
[FONT=Arial]albator@shuttle:~$[/FONT]
[FONT=Arial] [/FONT]
[FONT=Arial]albator@shuttle:~$ aplay -L[/FONT]
[FONT=Arial]default[/FONT]
[FONT=Arial]pulse[/FONT]
[FONT=Arial]    Playback/recording through the PulseAudio sound server[/FONT]
[FONT=Arial]front:CARD=Intel,DEV=0[/FONT]
[FONT=Arial]    HDA Intel, STAC92xx Analog[/FONT]
[FONT=Arial]    Front speakers[/FONT]
[FONT=Arial]surround40:CARD=Intel,DEV=0[/FONT]
[FONT=Arial]    HDA Intel, STAC92xx Analog[/FONT]
[FONT=Arial]    4.0 Surround output to Front and Rear speakers[/FONT]
[FONT=Arial]surround41:CARD=Intel,DEV=0[/FONT]
[FONT=Arial]    HDA Intel, STAC92xx Analog[/FONT]
[FONT=Arial]    4.1 Surround output to Front, Rear and Subwoofer speakers[/FONT]
[FONT=Arial]surround50:CARD=Intel,DEV=0[/FONT]
[FONT=Arial]    HDA Intel, STAC92xx Analog[/FONT]
[FONT=Arial]    5.0 Surround output to Front, Center and Rear speakers[/FONT]
[FONT=Arial]surround51:CARD=Intel,DEV=0[/FONT]
[FONT=Arial]    HDA Intel, STAC92xx Analog[/FONT]
[FONT=Arial]    5.1 Surround output to Front, Center, Rear and Subwoofer speakers[/FONT]
[FONT=Arial]surround71:CARD=Intel,DEV=0[/FONT]
[FONT=Arial]    HDA Intel, STAC92xx Analog[/FONT]
[FONT=Arial]    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers[/FONT]
[FONT=Arial]dmix:CARD=Intel,DEV=0[/FONT]
[FONT=Arial]    HDA Intel, STAC92xx Analog[/FONT]
[FONT=Arial]    Direct sample mixing device[/FONT]
[FONT=Arial]dsnoop:CARD=Intel,DEV=0[/FONT]
[FONT=Arial]    HDA Intel, STAC92xx Analog[/FONT]
[FONT=Arial]    Direct sample snooping device[/FONT]
[FONT=Arial]hw:CARD=Intel,DEV=0[/FONT]
[FONT=Arial]    HDA Intel, STAC92xx Analog[/FONT]
[FONT=Arial]    Direct hardware device without any conversions[/FONT]
[FONT=Arial]plughw:CARD=Intel,DEV=0[/FONT]
[FONT=Arial]    HDA Intel, STAC92xx Analog[/FONT]
[FONT=Arial]    Hardware device with all software conversions[/FONT]
[FONT=Arial]hdmi:CARD=NVidia,DEV=0[/FONT]
[FONT=Arial]    HDA NVidia, NVIDIA HDMI[/FONT]
[FONT=Arial]    HDMI Audio Output[/FONT]
[FONT=Arial]hdmi:CARD=NVidia,DEV=1[/FONT]
[FONT=Arial]    HDA NVidia, NVIDIA HDMI[/FONT]
[FONT=Arial]    HDMI Audio Output[/FONT]
[FONT=Arial]hdmi:CARD=NVidia,DEV=2[/FONT]
[FONT=Arial]    HDA NVidia, NVIDIA HDMI[/FONT]
[FONT=Arial]    HDMI Audio Output[/FONT]
[FONT=Arial]hdmi:CARD=NVidia,DEV=3[/FONT]
[FONT=Arial]    HDA NVidia, NVIDIA HDMI[/FONT]
[FONT=Arial]    HDMI Audio Output[/FONT]
[FONT=Arial]dmix:CARD=NVidia,DEV=3[/FONT]
[FONT=Arial]    HDA NVidia, NVIDIA HDMI[/FONT]
[FONT=Arial]    Direct sample mixing device[/FONT]
[FONT=Arial]dmix:CARD=NVidia,DEV=7[/FONT]
[FONT=Arial]    HDA NVidia, NVIDIA HDMI[/FONT]
[FONT=Arial]    Direct sample mixing device[/FONT]
[FONT=Arial]dmix:CARD=NVidia,DEV=8[/FONT]
[FONT=Arial]    HDA NVidia, NVIDIA HDMI[/FONT]
[FONT=Arial]    Direct sample mixing device[/FONT]
[FONT=Arial]dmix:CARD=NVidia,DEV=9[/FONT]
[FONT=Arial]    HDA NVidia, NVIDIA HDMI[/FONT]
[FONT=Arial]    Direct sample mixing device[/FONT]
[FONT=Arial]dsnoop:CARD=NVidia,DEV=3[/FONT]
[FONT=Arial]    HDA NVidia, NVIDIA HDMI[/FONT]
[FONT=Arial]    Direct sample snooping device[/FONT]
[FONT=Arial]dsnoop:CARD=NVidia,DEV=7[/FONT]
[FONT=Arial]    HDA NVidia, NVIDIA HDMI[/FONT]
[FONT=Arial]    Direct sample snooping device[/FONT]
[FONT=Arial]dsnoop:CARD=NVidia,DEV=8[/FONT]
[FONT=Arial]    HDA NVidia, NVIDIA HDMI[/FONT]
[FONT=Arial]    Direct sample snooping device[/FONT]
[FONT=Arial]dsnoop:CARD=NVidia,DEV=9[/FONT]
[FONT=Arial]    HDA NVidia, NVIDIA HDMI[/FONT]
[FONT=Arial]    Direct sample snooping device[/FONT]
[FONT=Arial]hw:CARD=NVidia,DEV=3[/FONT]
[FONT=Arial]    HDA NVidia, NVIDIA HDMI[/FONT]
[FONT=Arial]    Direct hardware device without any conversions[/FONT]
[FONT=Arial]hw:CARD=NVidia,DEV=7[/FONT]
[FONT=Arial]    HDA NVidia, NVIDIA HDMI[/FONT]
[FONT=Arial]    Direct hardware device without any conversions[/FONT]
[FONT=Arial]hw:CARD=NVidia,DEV=8[/FONT]
[FONT=Arial]    HDA NVidia, NVIDIA HDMI[/FONT]
[FONT=Arial]    Direct hardware device without any conversions[/FONT]
[FONT=Arial]hw:CARD=NVidia,DEV=9[/FONT]
[FONT=Arial]    HDA NVidia, NVIDIA HDMI[/FONT]
[FONT=Arial]    Direct hardware device without any conversions[/FONT]
[FONT=Arial]plughw:CARD=NVidia,DEV=3[/FONT]
[FONT=Arial]    HDA NVidia, NVIDIA HDMI[/FONT]
[FONT=Arial]    Hardware device with all software conversions[/FONT]
[FONT=Arial]plughw:CARD=NVidia,DEV=7[/FONT]
[FONT=Arial]    HDA NVidia, NVIDIA HDMI[/FONT]
[FONT=Arial]    Hardware device with all software conversions[/FONT]
[FONT=Arial]plughw:CARD=NVidia,DEV=8[/FONT]
[FONT=Arial]    HDA NVidia, NVIDIA HDMI[/FONT]
[FONT=Arial]    Hardware device with all software conversions[/FONT]
[FONT=Arial]plughw:CARD=NVidia,DEV=9[/FONT]
[FONT=Arial]    HDA NVidia, NVIDIA HDMI[/FONT]
[FONT=Arial]    Hardware device with all software conversions[/FONT]
[FONT=Arial][EMAIL="albator@shuttle:~$"]albator@shuttle:~$[/EMAIL][/FONT]
 
 
[FONT=Arial] Alsamixer printscreens:[/FONT]
[FONT=Arial][/FONT] 
[FONT=Arial][/FONT]

---

### Post by Xrcam on 2010-11-11
Gnome graphical interface mixer printscreen:

---

### Post by byronmyth on 2010-11-11
This worked for me:
 
[FONT=Calibri][SIZE=3]Use synaptics to load &#8220;[COLOR=red]linux-backports-modules-als-2.6.32-25-generic[/COLOR]&#8221;. Once installed and system re-booted, load &#8220;alsamixer&#8221; in a terminal window, press F6 to change to Nvidia sound, then unmute the channels. F6 will not display channels unless the backport is loaded.[/SIZE][/FONT]
 
[FONT=Calibri][FONT=Calibri]In audio settings under audio output device enter: [COLOR=red]ALSA: plughw:1,7[/COLOR] this will direct sound via HDMI  (no gap between ALSA: and plughw:1,7)[/FONT][/FONT]

---

### Post by Xrcam on 2010-11-23
(Solved)
 
Problem source: **Too low volume** (even at maximum volume)
 
Solution:
 
Put this line at the end of /etc/modprobe.d/alsa-base
options snd-hda-intel model=3stack
 
Configure frontend sound properties to use HDMI.
Voilà !!

---

### Post by rwurttem on 2010-11-24
> **byronmyth said:**
> This worked for me:
[FONT=Calibri][FONT=Calibri]In audio settings under audio output device enter: [COLOR=red]ALSA: plughw:1,7[/COLOR] this will direct sound via HDMI  (no gap between ALSA: and plughw:1,7)[/FONT][/FONT]

Hey byronmyth, 

I just wanted to thank you for this post. Thanks to you... I now have working audio on my Shuttle XS35GT.  I did have to add "ALSA: plughw:1,7" to my mixer config on the next configuration page though.

Kind regards,
-=Raj=-

** Side note... I replaced the built-in wireless module with an Intel Centrino 6200... much better range and stability.

---

### Post by byronmyth on 2010-11-26
Glad to have helped. However, I found after bringing my setup up to date recently that I lost sound again. This time I needed to load [FONT=Calibri][SIZE=3][COLOR=#ff0000]linux-backports-modules-als-2.6.32-26-generic[/COLOR][/SIZE][/FONT] to get the alsamixer to load the HDMI options.

---

### Post by Wibbe82 on 2011-02-28
> **Xrcam said:**
> (Solved)
 
Problem source: **Too low volume** (even at maximum volume)
 
Solution:
 
Put this line at the end of /etc/modprobe.d/alsa-base
options snd-hda-intel model=3stack
 
Configure frontend sound properties to use HDMI.
Voilà !!

I'm having the same problem and this line didn't help me. It might have to do with that I'm a complete beginner and I even had to google how to get permission to edit the file. I didn't have the file alsa-base only alsa-base.conf, is this the same file?

Could someone please help me with step by step instructions to solve this problem?

Edit, might ad some info:

wibbe@HTPC:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf9ef8000 irq 53
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfbbfc000 irq 19
wibbe@HTPC:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC887 Analog [ALC887 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC887 Digital [ALC887 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
wibbe@HTPC:~$ aplay -L
default
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=Intel,DEV=0
    HDA Intel, ALC887 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC887 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC887 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC887 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC887 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC887 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC887 Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=Intel,DEV=0
    HDA Intel, ALC887 Analog
    Direct sample mixing device
dmix:CARD=Intel,DEV=1
    HDA Intel, ALC887 Digital
    Direct sample mixing device
dsnoop:CARD=Intel,DEV=0
    HDA Intel, ALC887 Analog
    Direct sample snooping device
dsnoop:CARD=Intel,DEV=1
    HDA Intel, ALC887 Digital
    Direct sample snooping device
hw:CARD=Intel,DEV=0
    HDA Intel, ALC887 Analog
    Direct hardware device without any conversions
hw:CARD=Intel,DEV=1
    HDA Intel, ALC887 Digital
    Direct hardware device without any conversions
plughw:CARD=Intel,DEV=0
    HDA Intel, ALC887 Analog
    Hardware device with all software conversions
plughw:CARD=Intel,DEV=1
    HDA Intel, ALC887 Digital
    Hardware device with all software conversions
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
dmix:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    Direct sample mixing device
dmix:CARD=NVidia,DEV=7
    HDA NVidia, NVIDIA HDMI
    Direct sample mixing device
dmix:CARD=NVidia,DEV=8
    HDA NVidia, NVIDIA HDMI
    Direct sample mixing device
dmix:CARD=NVidia,DEV=9
    HDA NVidia, NVIDIA HDMI
    Direct sample mixing device
dsnoop:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=7
    HDA NVidia, NVIDIA HDMI
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=8
    HDA NVidia, NVIDIA HDMI
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=9
    HDA NVidia, NVIDIA HDMI
    Direct sample snooping device
hw:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=7
    HDA NVidia, NVIDIA HDMI
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=8
    HDA NVidia, NVIDIA HDMI
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=9
    HDA NVidia, NVIDIA HDMI
    Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=7
    HDA NVidia, NVIDIA HDMI
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=8
    HDA NVidia, NVIDIA HDMI
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=9
    HDA NVidia, NVIDIA HDMI
    Hardware device with all software conversions

---

### Post by bcg30506 on 2011-02-28
> **byronmyth said:**
> Glad to have helped. However, I found after bringing my setup up to date recently that I lost sound again. This time I needed to load [FONT=Calibri][SIZE=3][COLOR=#ff0000]linux-backports-modules-als-2.6.32-26-generic[/COLOR][/SIZE][/FONT] to get the alsamixer to load the HDMI options.

To make this work past upgrades and updates, install the version generic package instead of the one specific to your kernel version.  For example, I'm running 10.04 (lucid) so I installed:

linux-backports-modules-alsa-lucid-generic

and it auto selects the right version to install based upon the running kernel.

---

### Post by bcg30506 on 2011-03-01
Installing the alsa module backports did add the nvidia audio to my alsamixer choices when I press F6.  But now I still don't get sound over HDMI.  I've made several attempts with suggestions from searching the web but unfortunately I made things worse.  Now my analog audio is broken too.  My volume control shows no controls at all.  Before my attempts, it did correctly show the analog controls, just no digital ones.

Also now, whenever I try and run Sound Preferences, I get a window saying "Waiting for sound system to respond".  This is a new symptom.

I'm hoping someone can please help me.  I'm running mythbuntu 10.04 on a ZaReason laptop.

Here's the info:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC259 Analog [ALC259 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
```
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
	Subsystem: Device 1b0a:00b9
	Flags: bus master, fast devsel, latency 0, IRQ 35
	Memory at fb200000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

01:00.0 VGA compatible controller: nVidia Corporation Device 0a29 (rev a2)
	Subsystem: Device 1b0a:00b9
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f7000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at d0000000 (64-bit, prefetchable) [size=32M]
	I/O ports at e000 [size=128]
	[virtual] Expansion ROM at f8000000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia-current, nvidiafb, nouveau

01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
	Subsystem: Device 1b0a:00b9
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f8080000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```
I don't know what else to show.

---

### Post by bcg30506 on 2011-03-02
Okay, the missing analog controls were solved by me commenting out all lines like:

load-module module-alsa-sink device=hw:0,1

in /etc/pulse/default.pa

then doing sudo killall pulseaudio.

Also, now my HDMI works once I set mythtv to use the hw:1,7 device.  I have no idea what I did for it to start working.  The default.pa file is back to its original form as it was when I tried it without success.

Now, does anyone know how to make it hot-pluggable?  In other words, I want my display & sound to go over HDMI when the cable is plugged in, and back to the built-in laptop screen & speakers when the cable is disconnected from the TV.

---

### Post by bcg30506 on 2011-03-02
HDMI hotplug works now thanks to this site!
[Laptop display hotplug]("http://gtk-apps.org/content/show.php/Laptop+external+display+hotplugging?content=138742&PHPSESSID=bb6bde5f07e6f4d3685706814f3ed880")
It's a simple install and works like a charm.

---

### Post by cblanquer on 2011-03-02
Same config XS35GT but Kubuntu 10.10.
I am trying to get an acceptable sound on hdmi output.
My goal is to direct through phonom:
[LIST]
[*]music & video sound to the analog output
[*]any other to the hdmi output
[/LIST]

Remarks:
If I enable channel 1 (starting from 0 till 3) I get the expected sound but covered by cracks and sparks!
In my other box with Kubuntu 10.10 also, enabling hdmi means no sound is available to the analog output.

Any ideas? THX

---

