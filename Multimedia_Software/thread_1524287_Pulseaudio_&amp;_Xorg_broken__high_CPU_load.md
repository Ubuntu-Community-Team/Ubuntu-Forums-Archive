---
title: "Pulseaudio &amp; Xorg broken / high CPU load"
date: 2010-07-05
forum: Multimedia Software
---

### Post by Caldrac on 2010-07-05
Hey folks,

I'm trying to fix a system of a friend of mine facing a problem somehow related to pulseaudio and/or xorg.


**Problem:**

I wanted to get Skype working, as it used to freeze, when a call was established, killing the sound immediately. 

Sound (Playing mp3s) does work in general. But some special operation seem to cause a bug, when I open the "Sound Properties" Panel. Sooner or later, if open, it almost freezes the system by pushing some programs to have abnormal high CPU load. Especially Xorg has high values, so the problem is somehow more complex I guess.
[B]

Hardware:[/B]

Asus eeepc 1201T

[LIST]
[*]AMD Athlon Neo MV-40 processor (1.6GHz single core)
[*]AMD M780G chipset
[*]64 bit
[*]ATI Radeon HD 3200 graphics
[*]2GB RAM
[/LIST]
$ lspci | grep Audio
```
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
```$ aplay -l
```
**** Liste der Hardware-Geräte (PLAYBACK) ****
Karte 0: SB [HDA ATI SB], Gerät 0: ALC269 Analog [ALC269 Analog]
 Sub-Geräte: 0/1
  Sub-Gerät #0: subdevice #0
```$ cat /proc/asound/card0/codec#* | grep Codec
```
Codec: Realtek ALC269
```[B]


Software:[/B]

$ uname -a
```
Linux Krassandra 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64 GNU/Linux
```Versions:

[LIST]
[*]skype (2.1.0.81-1ubuntu5)
[*]pulseaudio (1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14)
[*]xorg (1:7.5+5ubuntu1)
[/LIST]


**CPU-Loads:**

Programs, that I saw with high load:

[LIST]
[*]firefox
[*]htop
[*]npviewer.bin
[*]totem
[*]Xorg
[*]pulseaudio
[/LIST]
Once I saw pulseaudio having 100% cpu, normally all (even htop) are having 20-30% adding up to 100%+ then.

Normal CPU-loads, when the system "works":

[LIST]
[*]totem playing mp3 (~30%)
[*]Xorg idle (~10%)
[*]Xorg moving mouse (~18%)
[*]Xorg changing workspace (~55%)
[*]Xorg + gedit constant scrolling 2700 lines (freezes system for some sec)
[/LIST]


[B]Some maybe interesting dmesg:

[/B]```
Jul  5 02:31:29 Krassandra pulseaudio[1039]: alsa-sink.c: ALSA  woke us up to write new data to the device, but there was actually  nothing to write!
Jul  5 02:31:29 Krassandra pulseaudio[1039]: alsa-sink.c: Most likely  this is a bug in the ALSA driver 'snd_hda_intel'. Please report this  issue to the ALSA developers.

```I think, this could be a reasonable reason, but I haven't found something  useful yet.

```
pulseaudio[1261]: ratelimit.c: 4526 events suppressed
```This  occured regulary during a high-load-time within thousands. when sound  works it is normally only one digit.

```
Jul  5 02:31:29 Krassandra pulseaudio[1039]: alsa-util.c:  Disabling timer-based scheduling because high-resolution timers are not  available from the kernel.
Jul  5 03:21:45 Krassandra kernel: [   79.520038] Clocksource tsc  unstable (delta = -109730578 ns)
```I also tried to change "hpet"(default) to "acpi_pm"(the 2nd one  available here), which at least didn't fix the occurence of a freeze.

```
kernel[...]:===>rtl8192se_link_change():ieee->iw_mode is 2
```This message occures quite frequently. I am using a special wlan-driver (rtl8192se-linux-2.6.0015.0127.2010_20100516-1_amd64_2.6.32-22), a deb package someone put together for this wireless card (Realtek Semiconductor Co., Ltd. Device 8171 (rev 10)), to fixe some stability issues. I can't provide you a link atm, if that would help, as the German Ubuntu community site is down. Anyway it seems to be independent of the more serious issue. Once it was even the only message, which appeared during one high-load-time and not more frequently as before, so i guess this is not the problem.


[B]Other Details
[/B]
[LIST]
[*]I tried acpi=off, what turned out to be even worse responsive
[*]Swap-Drive is used by the system but has always 0 usage. Seems also very unusual to me.
[*]To fix an issue about automatic switching of "line-out" and "headphones" due to plugging in headphones I finally found an option in /etc/modprobe.d/alsa-base.conf (model=lenovo probe_mask=1), if that could add it's sum to the more-than-whole
[/LIST]
Any help would be highly appreciated, I don't know, where to go on. If you need a deeper look into the syslog, don't hesitate to ask :) Thanks in advance.

---

### Post by Caldrac on 2010-07-05
bump

---

### Post by Yellow Pasque on 2010-07-06
BIOS update might help and also check to se if you can enable HPET in the BIOS.

---

### Post by Caldrac on 2010-07-06
Thanks, Temüjin. The BIOS is really not up to date, but the owner is not willing to risk to brick her system. I haven't found any change history for the BIOS, so I can't tell, if something's in there, or not. Unfortunately there's no option concerning the clocksource within the BIOS.

---

### Post by Caldrac on 2010-07-06
[B]debug of gnome-volume-control
[/B]
I tried to find out, which operation is causing such a high-cpu-phase by  opening gnome-volume-control (this is, what i meant with "Sound  Properties Panel"), which always causes such a phase together with totem  playing an mp3. When I first open GVC, it needs about 10-20 sec until  the phase occurs after the red line:

$ gnome-volume-control --debug
```
** (gnome-volume-control:1649): DEBUG: Enabling debugging
** (gnome-volume-control:1649): DEBUG: Updating client: index=0  name='ConsoleKit Session /org/freedesktop/ConsoleKit/Session1'
** (gnome-volume-control:1649): DEBUG: Updating client: index=1  name='GNOME Volume Control Media Keys'
** (gnome-volume-control:1649): DEBUG: Updating client: index=3  name='ayatana.indicator.sound'
** (gnome-volume-control:1649): DEBUG: Updating client: index=8  name='XSMP Session on gnome-session as  104fccb0ec9299cc7b12784236164253100000011280030'
** (gnome-volume-control:1649): DEBUG: Updating client: index=10  name='Totem Video-Player'
** (gnome-volume-control:1649): DEBUG: Updating client: index=11  name='GNOME Volume Control Dialog'
** (gnome-volume-control:1649): DEBUG: Updating sink: index=0  name='alsa_output.pci-0000_00_14.2.analog-stereo' description='Internes  Audio Analog Stereo' map='front-left,front-right'
** (gnome-volume-control:1649): DEBUG: Updating source: index=0  name='alsa_output.pci-0000_00_14.2.analog-stereo.monitor'  description='Monitor of Internes Audio Analog Stereo'
** (gnome-volume-control:1649): DEBUG: Updating source: index=1  name='alsa_input.pci-0000_00_14.2.analog-stereo' description='Internes  Audio Analog Stereo'
** (gnome-volume-control:1649): DEBUG: Udpating card  alsa_card.pci-0000_00_14.2 (index: 0 driver: module-alsa-card.c):
** (gnome-volume-control:1649): DEBUG:     Profile  'output:analog-stereo': 0 sources 1 sinks
** (gnome-volume-control:1649): DEBUG:     Profile  'output:analog-stereo+input:analog-stereo': 1 sources 1 sinks (Current)
** (gnome-volume-control:1649): DEBUG:     Profile  'output:analog-surround-40': 0 sources 1 sinks
** (gnome-volume-control:1649): DEBUG:     Profile  'output:analog-surround-40+input:analog-stereo': 1 sources 1 sinks
** (gnome-volume-control:1649): DEBUG:     Profile  'input:analog-stereo': 1 sources 0 sinks
** (gnome-volume-control:1649): DEBUG:     Profile 'off': 0 sources 0  sinks
** (gnome-volume-control:1649): DEBUG:     Property: 'alsa.card' = '0'
** (gnome-volume-control:1649): DEBUG:     Property: 'alsa.card_name' =  'HDA ATI SB'
** (gnome-volume-control:1649): DEBUG:     Property:  'alsa.long_card_name' = 'HDA ATI SB at 0xfbbf8000 irq 16'
** (gnome-volume-control:1649): DEBUG:     Property: 'alsa.driver_name' =  'snd_hda_intel'
** (gnome-volume-control:1649): DEBUG:     Property: 'device.bus_path' =  'pci-0000:00:14.2'
** (gnome-volume-control:1649): DEBUG:     Property: 'sysfs.path' =  '/devices/pci0000:00/0000:00:14.2/sound/card0'
** (gnome-volume-control:1649): DEBUG:     Property: 'device.bus' =  'pci'
** (gnome-volume-control:1649): DEBUG:     Property: 'device.vendor.id' =  '1002'
** (gnome-volume-control:1649): DEBUG:     Property:  'device.vendor.name' = 'ATI Technologies Inc'
** (gnome-volume-control:1649): DEBUG:     Property: 'device.product.id'  = '4383'
** (gnome-volume-control:1649): DEBUG:     Property:  'device.product.name' = 'SBx00 Azalia (Intel HDA)'
** (gnome-volume-control:1649): DEBUG:     Property:  'device.form_factor' = 'internal'
** (gnome-volume-control:1649): DEBUG:     Property: 'device.string' =  '0'
** (gnome-volume-control:1649): DEBUG:     Property:  'device.description' = 'Internes Audio'
** (gnome-volume-control:1649): DEBUG:     Property:  'module-udev-detect.discovered' = '1'
** (gnome-volume-control:1649): DEBUG:     Property: 'device.icon_name' =  'audio-card-pci'
** (gnome-volume-control:1649): DEBUG: deleted the custom theme dir
** (gnome-volume-control:1649): DEBUG: Card selection changed
** (gnome-volume-control:1649): DEBUG: Updating input settings
** (gnome-volume-control:1649): DEBUG: Create monitor for 1
** (gnome-volume-control:1649): DEBUG: Updating output settings
** (gnome-volume-control:1649): DEBUG: Volume changed (for Balance bar)
** (gnome-volume-control:1649): DEBUG: Card selection changed
** (gnome-volume-control:1649): DEBUG: Adding effects stream
** (gnome-volume-control:1649): DEBUG: Updating source: index=1  name='alsa_input.pci-0000_00_14.2.analog-stereo' description='Internes  Audio Analog Stereo'
** (gnome-volume-control:1649): DEBUG: Updating source output: index=0  name='Spitzenerkennung' client=11 source=1
** (gnome-volume-control:1649): DEBUG: deleted the custom theme dir
** (gnome-volume-control:1649): DEBUG: deleted the custom theme dir
** (gnome-volume-control:1649): DEBUG: Updating client: index=12  name='Native client (UNIX socket client)'
[COLOR=Red]** (gnome-volume-control:1649): DEBUG: Updating  client: index=12 name='gnome-settings-daemon'[/COLOR]
```After the first time, I only need to open GVM causing the phase  immediately before this red line:

$ gnome-volume-control --debug
```
** (gnome-volume-control:2458): DEBUG: Enabling debugging
** (gnome-volume-control:2458): DEBUG: Updating client: index=0  name='ConsoleKit Session /org/freedesktop/ConsoleKit/Session1'
** (gnome-volume-control:2458): DEBUG: Updating client: index=1  name='GNOME Volume Control Media Keys'
** (gnome-volume-control:2458): DEBUG: Updating client: index=3  name='ayatana.indicator.sound'
** (gnome-volume-control:2458): DEBUG: Updating client: index=8  name='XSMP Session on gnome-session as  104ec4b1d878af0985127842283922678600000010740030'
** (gnome-volume-control:2458): DEBUG: Updating client: index=14  name='Totem Video-Player'
** (gnome-volume-control:2458): DEBUG: Updating client: index=19  name='GNOME Volume Control Dialog'
** (gnome-volume-control:2458): DEBUG: Updating sink: index=0  name='alsa_output.pci-0000_00_14.2.analog-stereo' description='Internes  Audio Analog Stereo' map='front-left,front-right'
** (gnome-volume-control:2458): DEBUG: Updating source: index=0  name='alsa_output.pci-0000_00_14.2.analog-stereo.monitor'  description='Monitor of Internes Audio Analog Stereo'
** (gnome-volume-control:2458): DEBUG: Updating source: index=1  name='alsa_input.pci-0000_00_14.2.analog-stereo' description='Internes  Audio Analog Stereo'
** (gnome-volume-control:2458): DEBUG: Udpating card  alsa_card.pci-0000_00_14.2 (index: 0 driver: module-alsa-card.c):
** (gnome-volume-control:2458): DEBUG:     Profile  'output:analog-stereo': 0 sources 1 sinks
** (gnome-volume-control:2458): DEBUG:     Profile  'output:analog-stereo+input:analog-stereo': 1 sources 1 sinks (Current)
** (gnome-volume-control:2458): DEBUG:     Profile  'output:analog-surround-40': 0 sources 1 sinks
** (gnome-volume-control:2458): DEBUG:     Profile  'output:analog-surround-40+input:analog-stereo': 1 sources 1 sinks
** (gnome-volume-control:2458): DEBUG:     Profile  'input:analog-stereo': 1 sources 0 sinks
** (gnome-volume-control:2458): DEBUG:     Profile 'off': 0 sources 0  sinks
** (gnome-volume-control:2458): DEBUG:     Property: 'alsa.card' = '0'
** (gnome-volume-control:2458): DEBUG:     Property: 'alsa.card_name' =  'HDA ATI SB'
** (gnome-volume-control:2458): DEBUG:     Property:  'alsa.long_card_name' = 'HDA ATI SB at 0xfbbf8000 irq 16'
** (gnome-volume-control:2458): DEBUG:     Property: 'alsa.driver_name' =  'snd_hda_intel'
** (gnome-volume-control:2458): DEBUG:     Property: 'device.bus_path' =  'pci-0000:00:14.2'
** (gnome-volume-control:2458): DEBUG:     Property: 'sysfs.path' =  '/devices/pci0000:00/0000:00:14.2/sound/card0'
** (gnome-volume-control:2458): DEBUG:     Property: 'device.bus' =  'pci'
** (gnome-volume-control:2458): DEBUG:     Property: 'device.vendor.id' =  '1002'
** (gnome-volume-control:2458): DEBUG:     Property:  'device.vendor.name' = 'ATI Technologies Inc'
** (gnome-volume-control:2458): DEBUG:     Property: 'device.product.id'  = '4383'
** (gnome-volume-control:2458): DEBUG:     Property:  'device.product.name' = 'SBx00 Azalia (Intel HDA)'
** (gnome-volume-control:2458): DEBUG:     Property:  'device.form_factor' = 'internal'
** (gnome-volume-control:2458): DEBUG:     Property: 'device.string' =  '0'
** (gnome-volume-control:2458): DEBUG:     Property:  'device.description' = 'Internes Audio'
** (gnome-volume-control:2458): DEBUG:     Property:  'module-udev-detect.discovered' = '1'
** (gnome-volume-control:2458): DEBUG:     Property: 'device.icon_name' =  'audio-card-pci'
** (gnome-volume-control:2458): DEBUG: deleted the custom theme dir
** (gnome-volume-control:2458): DEBUG: Card selection changed
** (gnome-volume-control:2458): DEBUG: Updating input settings
** (gnome-volume-control:2458): DEBUG: Create monitor for 1
** (gnome-volume-control:2458): DEBUG: Updating output settings
** (gnome-volume-control:2458): DEBUG: Volume changed (for Balance bar)
** (gnome-volume-control:2458): DEBUG: Card selection changed
[COLOR=Red]** (gnome-volume-control:2458): DEBUG: Adding effects  stream[/COLOR]
** (gnome-volume-control:2458): DEBUG: Updating source: index=1  name='alsa_input.pci-0000_00_14.2.analog-stereo' description='Internes  Audio Analog Stereo'
** (gnome-volume-control:2458): DEBUG: Updating source output: index=2  name='Spitzenerkennung' client=19 source=1
** (gnome-volume-control:2458): DEBUG: deleted the custom theme dir
** (gnome-volume-control:2458): DEBUG: deleted the custom theme  dir
```

---

### Post by Caldrac on 2010-07-06
Well, it seems, that another model within "/etc/modprobe.d/alsa-base.conf" did the job. 

The first time I tried some models, I had a look into an old "/usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz" (damn), which had only one entry "model=basic", therefore I tried some other models, than listed by Alsa.

**The right model for Asus EeePC 1201T (Codec: ALC296) seems to be "model=eeepc-p901"** (although it only fixes to supress internal speakers when something is plugged in on "line-out", whereas the internal micro still does not work - the same as with all other models, i already tried out).

I never encountered such **serious** problems using a wrong model though, especially the symptoms were all almost the same with all other models. 
Checking the syslog, now there's no message about wrong waking of pulseaudio by alsa anymore, pulseaudio event suppression is always lower than 7, and even the Clocksource hpet seems to work now.

Even Xorg is now running nicely, no CPU high-loads anymore, e.g. moving the mouse has only a reasonable effect now.

If anyone can provide me some background knowledge, how these thing are interconnected and why the audiomodel has such an impact, I would be interested in it.

---

