---
title: "Sound issues with Dell Zino HD"
date: 2010-12-21
forum: Multimedia Software
---

### Post by chosenbeans on 2010-12-21
Hello, I installed Ubuntu Desktop Edition 10.10 32bit on a friend's Dell Inspiron Zino HD. Without making any changes I noticed the sound did not work. I made sure his speakers were plugged in the correct input on the machine. I made sure sound was not muted and turned up in volume control. Still the sound did now work. I tried various sound solutions from many forums with no avail. I tried asking the Ubuntu IRC channel but got no response. If someone would please just try and give me help that would be awesome. Here are some details about my machine.

**aplay -l**
```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

``` 

**cat /proc/asound/card0/codec#* | grep Codec**
```
Codec: Conexant CX20561 (Hermosa)
```

**lspci**
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Dell Device 9602
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)

```

**alsa-base.conf**
```
http://pastebin.com/YVMhTdBe
```

**pulseaudio -vvv**
```
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
D: core-rtclock.c: Timer slack is set to 50 us.
D: core-util.c: RealtimeKit worked.
I: core-util.c: Successfully gained nice level -11.
I: main.c: This is PulseAudio 0.9.21-63-gd3efa-dirty
D: main.c: Compilation host: i686-pc-linux-gnu
D: main.c: Compilation CFLAGS: -g -O2 -g -Wall -O3 -Wall -W -Wextra -pipe -Wno-long-long -Winline -Wvla -Wno-overlength-strings -Wunsafe-loop-optimizations -Wundef -Wformat=2 -Wlogical-op -Wsign-compare -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wpointer-arith -Winit-self -Wdeclaration-after-statement -Wfloat-equal -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-declarations -Wmissing-noreturn -Wshadow -Wendif-labels -Wcast-align -Wstrict-aliasing=2 -Wwrite-strings -Wno-unused-parameter -ffast-math -Wp,-D_FORTIFY_SOURCE=2 -fno-common -fdiagnostics-show-option
D: main.c: Running on host: Linux i686 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 01:41:57 UTC 2010
D: main.c: Found 2 CPUs.
I: main.c: Page size is 4096 bytes
D: main.c: Compiled with Valgrind support: no
D: main.c: Running in valgrind mode: no
D: main.c: Running in VM: no
D: main.c: Optimized build: yes
D: main.c: All asserts enabled.
I: main.c: Machine ID is 6310f8eec1ed0f77aef80c7d00000009.
I: main.c: Session ID is 6310f8eec1ed0f77aef80c7d00000009-1292975060.730566-728406775.
I: main.c: Using runtime directory /home/justin/.pulse/6310f8eec1ed0f77aef80c7d00000009-runtime.
I: main.c: Using state directory /home/justin/.pulse.
I: main.c: Using modules directory /usr/lib/pulse-0.9.21/modules.
I: main.c: Running in system mode: no

```

**cat /proc/asound/modules**
```
0 snd_hda_intel
 1 snd_hda_intel
```

I have tried editing alsa-base.conf with some options but nothing has worked yet. There seems to be a close bug about this codec on launchpad but of course that doesn't help.[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/557006](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/557006)

Any one who is willing to help get this working world be awesome. Thanks for reading and thanks for the help.

---

### Post by lyndon153 on 2011-01-14
You probably already know that the rear audio doesn't work on the zino with ubuntu. (at least with 10.4). I'm running 10.4 64-bit and that is the case. Does the front audio not work in 10.10 ? I'm interested because I was planning on upgrading .

---

### Post by chosenbeans on 2011-02-03
I'm not sure, I'll have to give it a try when I get another chance to work with this machine. This never occurred to me as a possible solution. I was too busy looking for a way to fix the rear ports. I'll get back to you when I am able test this possible solution. Thanks.

---

