---
title: "dvb-bt8xx causes computer to crash! Twinhan DVB-T 3021 (Visionplus) problem."
date: 2007-03-13
forum: Multimedia &amp; Video
---

### Post by pfred on 2007-03-13
I have a problem with my Twinhan DVB-T 3021 (a.k.a. Visionplus). By consulting various threads:

[Twinhan TV not working Help me man, I am going mad!]("http://ubuntuforums.org/showthread.php?t=294020")

[VisionPlus (twinhan) PCI vid card]("http://ubuntuforums.org/showthread.php?t=56351")

etc.

I worked out that the modules below don't load and I have no /dev/dvb/adapter0/, not even /dev/dvb/. When I add the following:

> **Lem said:**
> Adding the following to /etc/modules worked for me.

dvb-bt8xx
dst
dvb_core

then restart.

...my computer freezes at bootup. I also tried to modprobe the modules:
```
modprobe dst
modprobe dvb_core
modprobe dvb-bt8xx
```


The first two lines work fine but when I press enter after "modprobe dvb-bt8xx" my computer totally freezes and both the mouse and keyboard stops responding, hence I have to reboot.

When I try to create a cannel list using dvb-utils I get:

```
~$ scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/au-Melbourne
scanning /usr/share/doc/dvb-utils/examples/scan/dvb-t/au-Melbourne
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2247: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 2 No such file or directory

```

Of course, since the directory is not there...

dmesg | grep bt says:
```

~$ dmesg | grep bt
[17179589.236000] bttv: driver version 0.9.16 loaded
[17179589.236000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[17179589.412000] bttv: Bt8xx card found (0).
[17179589.412000] bttv0: Bt878 (rev 17) at 0000:02:08.0, irq: 217, latency: 32, mmio: 0xe7000000
[17179589.412000] bttv0: detected: Twinhan VisionPlus DVB [card=113], PCI subsystem ID is 1822:0001
[17179589.412000] bttv0: using: Twinhan DST + clones [card=113,autodetected]
[17179589.412000] bttv0: gpio: en=00000000, out=00000000 in=00f100fe [init]
[17179589.412000] bttv0: using tuner=4
[17179589.428000] bttv0: add subdevice "dvb0"
[17179589.428000] bt878: AUDIO driver version 0.0.0 loaded
[17179589.428000] bt878: Bt878 AUDIO function found (0).
[17179589.428000] bt878_probe: card id=[0x11822],[ Twinhan VisionPlus DVB ] has DVB functions.
[17179589.428000] bt878(0): Bt878 (rev 17) at 02:08.1, irq: 217, latency: 32, memory: 0xe7001000
```

...which all seems to be in order.

lsmod | grep bt says:
```
~$ lsmod | grep bt
bt878                  12472  0 
bttv                  176116  1 bt878
video_buf              27652  1 bttv
ir_common              28548  1 bttv
compat_ioctl32          2432  1 bttv
i2c_algo_bit           10376  1 bttv
v4l2_common            17280  2 tuner,bttv
btcx_risc               6280  1 bttv
tveeprom               16144  1 bttv
videodev               10752  1 bttv
i2c_core               23424  7 i2c_ec,nvidia,tuner,bttv,i2c_algo_bit,tveeprom,i2c_nforce2

```

...which is also fine (except for the missing modules that I am trying to add). 
I am very confused on why the module "dvb-bt8xx" causes the computer to crash. I haven't been able to find anyone with the same problem on the forum. If anyone has a solution or can point me in the right direction... please help.

---

### Post by pfred on 2007-03-27
bump!!

---

