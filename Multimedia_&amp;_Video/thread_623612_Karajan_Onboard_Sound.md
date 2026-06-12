---
title: "Karajan Onboard Sound"
date: 2007-11-26
forum: Multimedia &amp; Video
---

### Post by soxs on 2007-11-26
I've got a mainboard with onboard sound (sound: karajan 8CH Audio), but it stays silent no matter if liveCD or not.

```
 $cat /proc/asound/cards:
 0 [CK804          ]: NFORCE - NVidia CK804
NVidia CK804 with ALC850 at irq 22
```
So in fact it is an nVidia CK804 AC'97 Audio Controller (alsa) and an ALC850 (oss) ... thingy..

I don't really know what to do..

Edit: Mainboard is "LANPARTY UT nF4 Ultra-D"

---

### Post by soxs on 2007-11-26
ok I got around that I have to use an intel driver for my onboard device... 
[ [http://www.nvidia.com/object/linux_nforce_1.23.html](http://www.nvidia.com/object/linux_nforce_1.23.html) ]

so where can I get intel8x0.c driver?? for x86_64??

---

### Post by soxs on 2007-11-27
BUMP
this is not supposed to be a one-man-show

Some mor info 4 you..
```
root@x:/home/bernhard# cat /proc/asound/modules
 0 snd_intel8x0

root@x:/home/bernhard# more /proc/asound/cards
 0 [CK804          ]: NFORCE - NVidia CK804
                      NVidia CK804 with ALC850 at irq 22

root@x:/home/bernhard# lspci | egrep audio
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)

root@x:/home/bernhard# more /dev/sndstat
Sound Driver:3.8.1a-980706 (ALSA v1.0.15 emulation code)
Kernel: Linux bernhard 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
NVidia CK804 with ALC850 at irq 22

Audio devices:
0: NVidia CK804 (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
31: system timer

Mixers:
0: Realtek ALC850 rev 0

root@x:/home/bernhard# more /etc/modutils/alsa-base
/etc/modutils/alsa-base: No such file or directory

root@x:/home/bernhard# more /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.15.
Compiled on Nov 27 2007 for kernel 2.6.22-14-generic (SMP).

root@x:/home/bernhard# more /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.15.
Compiled on Nov 27 2007 for kernel 2.6.22-14-generic (SMP).

root@x:/home/bernhard# 

```

---

### Post by Yellow Pasque on 2007-11-27
If you can't get sound with ALSA, give OSSv4 a chance before reinstalling the OS or switching to another one.

---

### Post by soxs on 2007-11-27
May you plx explain why I should stay with outdated oss? I know there are tutorials about this problem, but most really suck and the others don't work, the nvidia driver is just crap... and I am NOT going to switch OS, I love ubuntu! But I need alsa sound! Not less and not more!

And I did not up my system, live cd gave me no soundoutput aswell 64bit ubuntu.

Another output:
```
~$ hwinfo --sound
14: PCI 04.0: 0401 Multimedia audio controller                  
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_10de_59
  Unique ID: 8otl.dHipVU0XmF1
  SysFS ID: /devices/pci0000:00/0000:00:04.0
  SysFS BusID: 0000:00:04.0
  Hardware Class: sound
  Model: "nVidia CK804 AC'97 Audio Controller"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x0059 "CK804 AC'97 Audio Controller"
  SubVendor: pci 0x10de "nVidia Corporation"
  SubDevice: pci 0xcb84 
  Revision: 0xa2
  Driver: "Intel ICH"
  Driver Modules: "snd_intel8x0"
  I/O Ports: 0xf000-0xf0ff (rw)
  I/O Ports: 0xec00-0xecff (rw)
  Memory Range: 0xfe02d000-0xfe02dfff (rw,non-prefetchable)
  IRQ: 22 (72285 events)
  Module Alias: "pci:v000010DEd00000059sv000010DEsd0000CB84bc04sc01i00"
  Driver Info #0:
    Driver Status: snd_intel8x0 is active
    Driver Activation Cmd: "modprobe snd_intel8x0"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```

---

### Post by soxs on 2007-12-11
bump...

---

### Post by Yellow Pasque on 2007-12-11
> May you plz explain why I should stay with outdated oss?
..Because OSSv4 **isn't** outdated (you're probably thinking of OSS 3.x/Free) and it may fix your sound problems. I'm not saying one or the other sound system is better, but it makes sense to try the other one if one isn't working for you.

---

### Post by soxs on 2007-12-14
Well, I want a solution, not an alternative... sry

Fedora 8 detects the soundmodulle aswell correctly, and well.. is aswell unable to give me any output (alsa 1..15, snd_8x0intel)

---

### Post by Yellow Pasque on 2007-12-14
> Well, I want a solution, not an alternative... sry
That's cool. No need for apologies. I realize that you can lead a horse to water, but you can't make it drink :P

---

### Post by soxs on 2007-12-14
Hmm.. somehow you're right, but I really would prefer getting alsa to work properly ^^.. I'll give ossv4 a shot... at least until the snd_8x0intel driver gets fixed or until I buy a new soundcard (final solution, not really keen on)
Note: HL2 doesn't work with oss and wine 9.50... that's one of the real bad things of oss..

---

### Post by Luis Macias on 2007-12-24
Hope this helps:
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

Good luck and happy holidays

---

### Post by soxs on 2007-12-30
thx, but this isn't a real help... sry
I now just know that I was lucky to get an unsupport onboard sound chip

so atm it doesn't matter anyways anymore, was so frustrated, that I bought a Audigy Soublaster LS which has full alsa support

---

