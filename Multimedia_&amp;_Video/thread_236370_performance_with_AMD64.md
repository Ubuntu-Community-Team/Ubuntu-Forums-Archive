---
title: "performance with AMD64"
date: 2006-08-14
forum: Multimedia &amp; Video
---

### Post by mixandgo on 2006-08-14
Hello,

  I am using Ubuntu Dapper on an amd64 athlon +3400 (laptop) with 2.6.15-26-amd64-generic SMP PREEMPT kernel. My audio interface is a RMC Multiface II / Cardbus. I've manually compile alsa 1.0.12rc2.

  I think the audio performance is way wrong :

with jackd -R -dalsa -r48000 -p128 -n2 -D -Chw:1,0 nothing else, I get 1.2% - 1.9% CPU usage if I don't do anything. When I load zynaddsubfx it goes to 13%, again without touching the midi keybooard. By pressing C major chord with the default sound zynaddsubfx starts, I get a CPU usage of 20%.

with jackd -R -dalsa -r48000 -p256 -n2 -D -Chw:1,0 nothing else, I get 0.65% - 0.96% CPU usage if I don't do anything. When I load zynaddsubfx it goes to 7.2% - 8%, again without touching the midi keybooard. By holding C major chord with the default sound zynaddsubfx starts, I get a CPU usage of 11%.

  Could anyone please test something similar to my setup and post here ? I don't think this is normal.

Thanks !

---

### Post by floogy on 2006-08-14
I may have the same issue on dapper amd64 3500+ 1GB RAM onboard sound :( with a rt patched vanilla 2.6.17.8-rt8 .

~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

It seems, that I have a lot of xruns, crashes etc.
```

delay of 1508.000 usecs exceeds estimated spare time of 1272.000; restart ...
delay of 1538.000 usecs exceeds estimated spare time of 1272.000; restart ...
delay of 1643.000 usecs exceeds estimated spare time of 1272.000; restart ...
zombified - calling shutdown handler
00:10:14.729 Shutdown notification.
00:10:14.729 Client deactivated.
00:10:14.730 JACK was stopped successfully.
cannot send request type 7 to server
cannot read result for request type 7 from server (Broken pipe)
```

3%-4& dsp load with no audio application running. and 13%-17% with only 1 connection between Last.FM player (running with jacklaunch) and alsa_pcm.

```
00:18:31.225 XRUN callback (2 skipped).
00:19:35.737 XRUN callback (8).
delay of 1736.000 usecs exceeds estimated spare time of 1209.000; restart ...
**** alsa_pcm: xrun of at least 0.014 msecs
00:19:36.582 XRUN callback (1 skipped).
00:20:20.344 XRUN callback (10).
**** alsa_pcm: xrun of at least 0.020 msecs
00:20:21.443 XRUN callback (11).
delay of 1339.000 usecs exceeds estimated spare time of 1094.000; restart ...
**** alsa_pcm: xrun of at least 0.061 msecs
00:20:23.483 XRUN callback (1 skipped).
00:20:24.830 XRUN callback (13).
delay of 10152.000 usecs exceeds estimated spare time of 1143.000; restart ...
delay of 3407.000 usecs exceeds estimated spare time of 1143.000; restart ...
00:20:25.522 XRUN callback (1 skipped).
00:20:26.290 XRUN callback (15).
**** alsa_pcm: xrun of at least 0.020 msecs
delay of 3596.000 usecs exceeds estimated spare time of 1205.000; restart ...
```

If the delay exceeds estimated spare time I can hear heaviest distortions, and interrupts, clicks etc.

I got an average system load of 3.9% with lastfm and qjackctl.
CPU Load is all the time 100% and on 2,2 Ghz .

Could it be that a few problems apear due to cpu frequency change, powermanagement and irq sharing?

```
$ egrep -i "(80|MPU)"  /proc/interrupts
  1:       3399   IO-APIC-edge     i8042
 10:          0   IO-APIC-edge     MPU401 UART
 12:     138887   IO-APIC-edge     i8042
[COLOR="Red"]225:    1826643   IO-APIC-fasteoi  libata, NVidia CK804[/COLOR]

$ cat /proc/asound/cards
 0 [CK804          ]: NFORCE - NVidia CK804
                      NVidia CK804 with ALC850 at 0xd2003000, irq 225
 1 [UART           ]: MPU-401 UART - MPU-401 UART
                      MPU-401 UART at 0x330, irq 10

```

```
$ ps axu|grep jack
gerhard   8653  2.1  3.5  79308 35516 ?        S<Ll Aug14   1:02 /usr/bin/qjackctl
gerhard  12549  1.6  3.6  48812 36600 ?        SLsl 00:17   0:26 /usr/bin/jackd -R -t5000 -dalsa -dhw:0 -r48000 -p64 -n2 -D -Cplug:dmix -S -i2 -o2
gerhard  12583  0.0  0.1   5756  1264 pts/1    S+   00:18   0:00 /bin/sh /usr/bin/jacklaunch ./lastfm.sh
gerhard  16222  0.0  0.0   2704   552 pts/0    S+   00:45   0:00 grep jack

```

Or is that due to a crappy soundcard (indeed onboard sound: asus A8N-SLI Deluxe nforce chipset).

---

### Post by floogy on 2006-08-16
I figured out, that I missed the CONFIG_HZ=1000, it still is set to 250 :(
Huh! I thought, I already changed that, at least I felt shure about that. I had to doublecheck it *before* compile the kernel, though.

I'll try that this evening.

@mixandgo

Could it be, that you got the same problem with the 2.6.15-26-amd64-generic SMP PREEMPT kernel?

Please, try ```
egrep -i CONFIG_HZ /boot/config-`uname -r`
```

It should be something like CONFIG_HZ=1000

---

### Post by floogy on 2006-08-16
**CONFIG_HZ=1000** is now set **without any effect** on the xruns and delays, though :(

I'm fiddling now with **apic=off noapic nolapic** to get an proper single irq for my onboard sound.

I don't know how to get my audio device working without sharing the irq with libata and usb.

```
$ cat /proc/interrupts
           CPU0
  0:     222092    XT-PIC-level    timer
  1:         95    XT-PIC-level    i8042
  2:          0    XT-PIC-level    cascade
  3:          0    XT-PIC-level    skge
  4:       9761    XT-PIC-level    nvidia
  5:          0    XT-PIC-level    MPU401 UART
  7:          1    XT-PIC-level    parport0
  8:          0    XT-PIC-level    rtc
  9:          0    XT-PIC-level    acpi
 10:      23134    XT-PIC-level    libata, ehci_hcd:usb2, eth0
 11:      41336    XT-PIC-level    libata, ohci_hcd:usb1, NVidia CK804
 12:       1317    XT-PIC-level    i8042
 14:        797    XT-PIC-level    ide0
 15:       2239    XT-PIC-level    ide1
NMI:        125
LOC:     221974
ERR:          0
MIS:          0
```

Can someone please help on irq sharing/handling?!

---

### Post by zettberlin on 2006-08-16
> **mixandgo said:**
> 

with jackd -R -dalsa -r48000 -p256 -n2 -D -Chw:1,0 nothing else, I get 0.65% - 0.96% CPU usage if I don't do anything. When I load zynaddsubfx it goes to 7.2% - 8%, again without touching the midi keybooard. By holding C major chord with the default sound zynaddsubfx starts, I get a CPU usage of 11%.

  Could anyone please test something similar to my setup and post here ? I don't think this is normal.


Well, it looks not completely normal to me too. I get up to 6.5% at most with this test and I "only" run a PIV 2.8GHZ and use seq24 in xfce to trigger the chord.

Maybe something with the driver for your hw1-device - USBinterface, i suspect?

---

### Post by dolson on 2006-08-17
Wow, if your CPU usage as reported by JACK is that low, you're lucky. Mine is frequently very high. As in, 50%-95%, when doing anything with audio through it. Although I don't know where that number comes from, since my actual CPU usage doesn't get reported that high in `top.`

---

### Post by zettberlin on 2006-08-17
So here i got some more detailed tests:

running with:
/usr/bin/jackd -R -p256 -t1000 -u -dalsa -dhw:0 -r44100 -p256 -n2 -zr
qjackctl reports as follows:

having Zynadd play the default sound with a 3-voicechord:

5.8 - 6 % CPU usage 

Zynadd plays 8 voices:

8.5 - 8.9 % CPU usage 

Zynadd plays the same 8 voices with the preset called "usr/share/zynaddsubfx/banks/Choir and Voice/0005-Choir Pad1.xiz":

12 - 13 %

the same patch but playing 12 voices:

15 - 18 % and 1 xrun when loading the patch

12 voices and the patch "/usr/share/zynaddsubfx/banks/Synth/0037-Resonance Synth.xiz"

another xrun and  0.85 - 0.91 % CPU
(could it be, that there is something terribly wrong about the usage-report in qjackctl ?)

top shows about 12 % CPU anyhow at the same time...

BTW, it works like a charm, no klicks, no scratch etc.

---

### Post by dolson on 2006-08-17
Just a note, not sure if you're aware or not (it is in the wiki though), but you will never eliminate Xruns when you are loading stuff up or launching apps. Especially with ZynAddSubFX right now, because it's very not-realtime-friendly.

---

### Post by zettberlin on 2006-08-18
The first xrun showed up while zynadd was running already as i loaded one of the patches.
At the other hand i loaded 6-7 different patches to experiment a little and i did only had 
2 xruns in the whole session.

---

### Post by dolson on 2006-08-18
Yes, loading patches will do that in some apps, specifically Zyn, because as I said, it is not designed to be realtime-friendly. Clicking almost anywhere in the interface gives me Xruns because it does run with realtime priority, but it's not coded properly, so that's why it does that. Hopefully it is fixed at some point.

---

