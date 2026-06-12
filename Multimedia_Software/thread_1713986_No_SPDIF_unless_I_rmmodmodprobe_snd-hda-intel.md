---
title: "No SPDIF unless I rmmod/modprobe snd-hda-intel"
date: 2011-03-24
forum: Multimedia Software
---

### Post by philpem on 2011-03-24
Hi guys,

I'm trying to get SPDIF output working on my desktop machine. Basically, I've got an ASUS Rampage Formula motherboard which came with the SupremeFX II sound card, and SPDIF on the motherboard (both optical and co-ax).

Problem is, ASUS cheaped out on the power filtering. Any LAN or HDD activity produces matching squeals on the sound output. I like my music. This ruins it.

So to solve the problem, I attached an SPDIF decoder/headphone amp to the optical (Toslink) output. When this works, it works great -- stereo 44100Hz PCM audio, and the music sounds *great*.

But it never works when the machine has just booted. To get it working, I have to open up a terminal and run this command:

```
killall amarok; killall vlc; kill `ps uax |grep flash | grep -v grep | awk '{print $2}'` ; killall pulseaudio; sudo rmmod snd-hda-intel; sudo modprobe snd-hda-intel
```

Effectively, I have to kill Amarok, VLC and the Flash plugin, then kill PulseAudio, rmmod the sound driver, and reload it. Every other time I modprobe the sound driver, the SPDIF output works. So basically:

- System boots, SPDIF dead -- "NO INPUT SIGNAL!" on the decoder display
- After 1st run of the above command, SPDIF OK -- "OPTICAL  PCM44k" on the decoder display
- Run the above command again -- sound stops working.
- Repeat from #2.

What the heck is going on here?!

How can I get my SPDIF output working from when the machine boots, withou having to jump through all these hoops?

Running Maverick Meerkat, sound profile is "Digital Stereo (IEC958) Output + Digital Stereo (IEC958) Input". I'm running the ubuntu-audio-dev PPA drivers, but get the same problem with the stock drivers in the kernel package.

uname -a:
Linux cheetah 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:39:03 UTC 2011 x86_64 GNU/Linux

cpuinfo:
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
stepping	: 11
cpu MHz		: 3005.691
cache size	: 4096 KB
physical id	: 0
siblings	: 4
core id		: 0
cpu cores	: 4
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm dts tpr_shadow vnmi flexpriority
bogomips	: 6011.38
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:


lspci (sound devices):
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)


Thanks,
Phil.

---

### Post by PCNetSpec on 2011-03-24
Have you installed alsamixer, then tried unmuting spdif in alsamixer ?

can you send the output from:

```
cat /proc/asound/card0/codec#* | grep Codec
```
and
```
sudo lshw -C multimedia
```

---

### Post by philpem on 2011-03-24
> **PCNetSpec said:**
> Have you installed alsamixer, then tried unmuting the spdif in alsamixer ?

Alsamixer says the SPDIF is unmuted:

S/PDIF:                 100<>100
S/PDIF Default PCM:     [OO]
S/PDIF Playback Source: PCM

Muting Default PCM has no effect on the output. Changing Playback Source from PCM to anything else (ADC1, ADC2, ADC3) kills SPDIF -- the receiver reports signal lock, but there's no audio.

> can you send the output from: ```
cat /proc/asound/card0/codec#* | grep Codec
```
```
Codec: Analog Devices AD1988B
```

> and ```
sudo lshw -C multimedia
```
```
philpem@cheetah:~$ sudo lshw -C multimedia
  *-multimedia            
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:47 memory:f9ff8000-f9ffbfff

```

---

### Post by PCNetSpec on 2011-03-24
Have you tried adding one of these options to your:

/etc/modprobe.d/alsa-base.conf


AD1988/AD1988B/AD1989A/AD1989B
==============================
  **6stack**	6-jack
  **6stack-dig**	ditto with SPDIF
  **3stack**	3-jack
  **3stack-dig**	ditto with SPDIF
  **laptop**	3-jack with hp-jack automute
  **laptop-dig**	ditto with SPDIF
  **auto**		auto-config reading BIOS (default)

by opening a terminal and entering:
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```

then adding a line at the end that reads:

> options snd-hda-intel model=**6stack-dig**
***_or_***
> options snd-hda-intel model=**3stack-dig**
etc.

saving the file, and rebooting ?

---

### Post by philpem on 2011-03-24
> **PCNetSpec said:**
> Have you tried adding one of these options to your:

/etc/modprobe.d/alsa-base.conf


AD1988/AD1988B/AD1989A/AD1989B
==============================
  **6stack**	6-jack
  **6stack-dig**	ditto with SPDIF
  **3stack**	3-jack
  **3stack-dig**	ditto with SPDIF
  **laptop**	3-jack with hp-jack automute
  **laptop-dig**	ditto with SPDIF
  **auto**		auto-config reading BIOS (default)

by opening a terminal and entering:
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```

then adding a line at the end that reads:


***_or_***

etc.

saving the file, and rebooting ?

Yep, I tried all the SPDIF-enabled ones before posting here... No change.

Thanks,
Phil.

---

### Post by PCNetSpec on 2011-03-24
As this appears to be a pulseaudio issue, have you installed pavucontrol and tried setting SPDIF as the output in there?

---

### Post by philpem on 2011-03-24
> **PCNetSpec said:**
> As this appears to be a pulseaudio issue, have you installed pavucontrol and tried setting SPDIF as the output in there?

Yep -- under Output Devices I've got:

Internal Audio Digital Stereo (IEC958)

The 'lock channels together' and 'set as fallback' buttons appear to be selected.

On the Configuration tab, the audio profile is the same as that set in the Sound Preferences app -- IEC958 + IEC958.

---

### Post by PCNetSpec on 2011-03-24
Short of installing paman, which also installs padevchooser, and seeing if there is anything useful in there... I don't know what else to suggest... I'll keep looking though, you never know...

I suppose you could try disabling pulseaudio:

[http://www.jeffsplace.net/node/12](http://www.jeffsplace.net/node/12)

[EDIT]
Hmm... What is selected as the output plugin and device in gstreamer-properties

maybe selecting ALSA as the plugin ??

---

### Post by philpem on 2011-03-28
> **PCNetSpec said:**
> Short of installing paman, which also installs padevchooser, and seeing if there is anything useful in there... I don't know what else to suggest... I'll keep looking though, you never know...

I suppose you could try disabling pulseaudio:

[http://www.jeffsplace.net/node/12](http://www.jeffsplace.net/node/12)


Hmm. Now the sound more-or-less works when the machine boots, but after a couple of minutes it cuts out. To get the sound back, I have to stop all apps which are using ALSA, rmmod snd-hda-intel, then modprobe it again.

I'm thinking there's a bug in the snd-hda-intel driver, or the chipset (#2 wouldn't surprise me, the ICH9R has more bugs than an ant farm!)

---

### Post by illectronic on 2011-03-31
> **PCNetSpec said:**
> Short of installing paman, which also installs padevchooser, and seeing if there is anything useful in there... I don't know what else to suggest... I'll keep looking though, you never know...

I suppose you could try disabling pulseaudio:

[http://www.jeffsplace.net/node/12](http://www.jeffsplace.net/node/12)

[EDIT]
Hmm... What is selected as the output plugin and device in gstreamer-properties

maybe selecting ALSA as the plugin ??


[http://www.jeffsplace.net/node/12](http://www.jeffsplace.net/node/12)

Thank you so much this worked!!!!

---

