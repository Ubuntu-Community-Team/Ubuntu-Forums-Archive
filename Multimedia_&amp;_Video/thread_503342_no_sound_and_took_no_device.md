---
title: "no sound and took no device"
date: 2007-07-17
forum: Multimedia &amp; Video
---

### Post by denar on 2007-07-17
no sound in my pc

ubuntu 7

1
if i click in [IMG]http://ebr0.myftp.org/screenshot2.png[/IMG] "volume control" show this msg "No volume control GStreamer plugins and/or devices found."

and if i right click in  [IMG]http://ebr0.myftp.org/screenshot2.png[/IMG]  and chose prefence nothing happend

2
if i write this command "aplay -l" 
result "aplay: device_list:222: no soundcards found..."

3
my hardware
[IMG]http://ebr0.myftp.org/screenshot3.png[/IMG]

4
multimedia system selctor
i test all of them no sound and no device show
[IMG]http://ebr0.myftp.org/screenshot5.png[/IMG]

5
sound preferences
i check all and nothing happend
[IMG]http://ebr0.myftp.org/screenshot4.png[/IMG]

6
file "/etc/esound/esd.conf" contain
```
[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=

```

7
file "/etc/asound.conf" contain
```
pcm.card0 {
type hw
card 1
}

pcm.!default {
type plug
slave.pcm "dmixer"
}

pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:1,0"
period_time 0
period_size 2048
buffer_size 32768
rate 48000
}
bindings {
0 0
1 1
}
}


```

8
when i test play file "mp3"
[IMG]http://ebr0.myftp.org/screenshot6.png[/IMG]

now how can i repair this proplem and play sound
plese.
and sory i cant speak eng good

thanks.

---

### Post by fredj on 2007-07-18
This is strange, your PC doesn't think you have a sound card installed.
Please open a terminal and type  sudo lshw -class sound
Post the output from that here.
Also in a terminal type  sudo cat /proc/asound/card0/codec\#*
Post the output from that here.
Also type sudo cat /proc/asound/card1/codec\#* and post the output from that.

---

### Post by denar on 2007-07-18
sudo lshw -class sound
```
  *-multimedia:0          
       description: Multimedia video controller
       product: Bt878 Video Capture
       vendor: Brooktree Corporation
       physical id: b
       bus info: pci@02:0b.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=bttv latency=32 maxlatency=40 mingnt=16
       resources: iomemory:dc7fe000-dc7fefff irq:17
  *-multimedia:1
       description: Multimedia controller
       product: Bt878 Audio Capture
       vendor: Brooktree Corporation
       physical id: b.1
       bus info: pci@02:0b.1
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=bt878 latency=32 maxlatency=255 mingnt=4
       resources: iomemory:dc7ff000-dc7fffff irq:17
  *-multimedia:2 UNCLAIMED
       description: Multimedia audio controller
       product: SB Live! EMU10k1
       vendor: Creative Labs
       physical id: c
       bus info: pci@02:0c.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=32 maxlatency=20 mingnt=2
       resources: ioport:df80-df9f irq:9
  *-multimedia UNCLAIMED
       description: Multimedia audio controller
       product: 82801BA/BAM AC'97 Audio
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@00:1f.5
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: latency=0
       resources: ioport:e800-e8ff ioport:ef00-ef3f irq:9

```

sudo cat /proc/asound/card0/codec\#
```
cat: /proc/asound/card0/codec#: No such file or directory
```

sudo cat /proc/asound/card1/codec\#*
```
cat: /proc/asound/card1/codec#*: No such file or directory
```

---

### Post by denar on 2007-07-18
maybe this folder not there "/proc/asound/" :confused:

---

### Post by denar on 2007-07-18
lspci
```
00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 05)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 05)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 05)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 05)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 05)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 05)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation NV11DDR [GeForce2 MX 100 DDR/200 DDR] (rev b2)
02:0b.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 02)
02:0b.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 02)
02:0c.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 05)
02:0c.1 Input device controller: Creative Labs SB Live! Game Port (rev 05)
02:0e.0 Ethernet controller: VIA Technologies, Inc. VT6105 [Rhine-III] (rev 86)

```

---

### Post by denar on 2007-07-18
aplay
```
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'defaults.namehint.extended'
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3982:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm_direct.c:1427:(_snd_pcm_direct_get_slave_ipc_offset) Unknown slave PCM hw:1,0
aplay: main:550: audio open error: No such file or directory

```

---

### Post by fredj on 2007-07-18
You mistyped two of the commands I gave you, they should end in codec\#* not codec#* try again.

---

### Post by fredj on 2007-07-18
Look carefully at the listing produced by the lshw -class sound command
It shows that your video capture card and video capture sound are both detected and have drivers loaded
for them

It also shows that your SBLive card and your 82801BA audio (the motherboard sound chip) are also
detected but they are both marked as UNCLAIMED. This means that no drivers have been loaded
for them and they will not work. 

I suggest that for the present you remove the video capture card and try to get your SBLive card to work.
then reinstall the video card.

---

### Post by denar on 2007-07-18
if cat /proc/asound/card0/codec\#*
result 
```
cat: /proc/asound/card0/codec#*: No such file or directory
```


because the folder asound not thir,i cant find it

---

### Post by denar on 2007-07-19
i removed tv capture and i changed card sound to another pci slot and nothing happend

---

### Post by dragonwings on 2007-07-19
try

sudo asoundconf list                 <<to get list of sound cards

---

### Post by denar on 2007-07-19
i cheacked sudo asoundconf list and nothing happend

---

### Post by denar on 2007-07-22
oK.
how can i repeat this folder /proc/asound/
because  i dont have this folder
may because this folder no sound

---

### Post by denar on 2007-07-23
What

---

### Post by fredj on 2007-07-24
Open a terminal window and type cd /proc/asound
If it says no directory then there is something wrong with your installation.
perhaps you should try reinstalling.

---

### Post by denar on 2007-07-24
there r solution or what

---

### Post by denar on 2007-07-24
thats mean must be reinstall ubuntu???

---

