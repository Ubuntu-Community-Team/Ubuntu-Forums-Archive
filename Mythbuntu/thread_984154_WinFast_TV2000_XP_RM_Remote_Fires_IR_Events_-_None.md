---
title: "WinFast TV2000 XP RM Remote Fires IR Events - None seen by LIRC"
date: 2008-11-16
forum: Mythbuntu
---

### Post by slœgth on 2008-11-16
Hello,

I have a Leadtek Winfast TV2000 XP RM card with the Y04G0033 remote. I'm running Ubuntu 8.10 with Mythbuntu installed. I've never been able to get the remote to work in version 7.10 or 8.04. However, with 8.10 several buttons miraculously work without lirc. 

The issue:
-Volume, numbers, and some other buttons are recognized by X
-LIRC does not seem to see these events 

The hardware:
-Ubuntu 8.10
-Kernel 2.6.27-7-generic
-GNOME 2.24.1
-Leadtek Winfast TV2000 XP RM card (uses bttv driver)
-PCHDTV tuner card (cx8800, working fine)
-motherboard: ASUS M2A-VM HDMI
-video: GForce 7300 GS

_What has been tried?_
I've searched and read most of the posts regarding WinFast and bttv and tried the relevant solutions (short of patching and recompiling bttv). In particular:
[LIST]
[*][http://ubuntuforums.org/showthread.php?t=610426](http://ubuntuforums.org/showthread.php?t=610426)
[*][http://ubuntuforums.org/showthread.php?t=787218](http://ubuntuforums.org/showthread.php?t=787218)
[*][https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/164627](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/164627)
[*][https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/279472](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/279472)
[/LIST]
All of these issues seemed to be different in that they either had the remotes working in previous ubuntu versions, or there were no events coming from bttv.

I applied the lirc.fdi fix as in [https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/164627](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/164627). This stopped lircd from complaining about exclusive rights.

I can start lirc:
```
theentertainer@theentertainer:~$ sudo lircd -n -d /dev/input/event6 -H devinput
[sudo] password for theentertainer: 
lircd-0.8.3[6598]: lircd(userspace) ready
lircd-0.8.3[6598]: accepted new client on /dev/lircd
```

After running IRW in another terminal, lircd outputs
```
lircd-0.8.3[6598]: accepted new client on /dev/lircd
lircd-0.8.3[6598]: initializing '/dev/input/event6'
```

IRW does not respond to any remote buttons.

irrecord does not respond either. 
```
# sudo irrecord -H dev/input -d /dev/input/event6 ~/test1.conf
[... lots of text ...]
Hold down an arbitrary button.
irrecord: gap not found, can't continue
irrecord: closing '/dev/input/event6'
```

Running evtest does show appropriate events when buttons are pushed.

lshal:
```
udi = '/org/freedesktop/Hal/devices/temp/106'
  info.ignore = true  (bool)
  info.parent = '/org/freedesktop/Hal/devices/pci_109e_36e'  (string)
  info.product = 'Ignored Device'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/ignored-device'  (string)
  input.device = '/dev/input/event6'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/pci_109e_36e'  (string)
  input.product = 'bttv IR (card=34)'  (string)
  linux.device_file = '/dev/input/event6'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.4/0000:03:06.0/input/input6/event6'  (string)
```

dmesg (bttv section, full output is attached):
```
[   12.518109] bttv: Bt8xx card found (0).
[   12.518136] bttv 0000:03:06.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   12.518150] bttv0: Bt878 (rev 17) at 0000:03:06.0, irq: 21, latency: 64, mmio: 0xfdfff000
[   12.518166] bttv0: detected: Leadtek TV 2000 XP [card=34], PCI subsystem ID is 107d:6609
[   12.518168] bttv0: using: Leadtek WinFast 2000/ WinFast 2000 XP [card=34,insmod option]
[   12.518215] bttv0: gpio: en=00000000, out=00000000 in=003ff9d2 [init]
[   12.518276] bttv0: tuner type=43
[   12.518279] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   12.519030] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   12.519760] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   12.551830] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[   12.570643] tuner' 1-0061: chip found @ 0xc2 (bt878 #0 [sw])
[   12.589869] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.6 loaded
[   12.805107] tuner-simple 1-0061: creating new instance
[   12.805111] tuner-simple 1-0061: type set to 43 (Philips NTSC MK3 (FM1236MK3 or FM1236/F))
[   12.906841] bttv0: registered device video0
[   12.906876] bttv0: registered device vbi0
[   12.906908] bttv0: registered device radio0
[   12.906942] bttv0: PLL: 28636363 => 35468950 .. ok
[   12.937633] input: bttv IR (card=34) as /devices/pci0000:00/0000:00:14.4/0000:03:06.0/input/input6
```

Any help getting LIRC to work, or using the ir events outside of LIRC would be wonderful.

Thanks!

---

### Post by idokibovito on 2008-11-27
Hi,

I have the same problem here, trying to get this working and will let you know if I was successful.

Cheers

---

### Post by inexistentia on 2008-11-30
Hi,

I had similar problems - took a while to find a solution (google was my friend).

[Fixing lirc After Updating to Intrepid Ibex]("http://danandchoka.net/?p=181")

Basically, Intrepid sneakily overrides other listeners for remote input from what I can gather.  The above link fixed it for me.

For other lirc + Winfast DTV2000H help, the following was very useful.  I made the lirc modifications specified at the end of the following thread before I made the fix above.

[A story (and request) about the DTV2000H _J_]("http://ubuntuforums.org/showthread.php?t=708217&highlight=lirc+winfast+story")

---

### Post by idokibovito on 2008-12-01
I just found out something, not really the final solution though.
I installed the package "inputlirc", then restarted lircd.
This gives me some output from irw, however not for all buttons.
(you might need to restart inputlirc after restarting lird)

Lirc stopped working for me about 3 Ubuntu releases ago, so I'm not sure how much longer I will have fun desperately trying to get it working. If I do though, will report the results back here.

Regards

---

### Post by inexistentia on 2008-12-01
After applying the fixes linked to in my above post, I still don't have access to my volume up / down buttons and the channel up / down buttons.

I'd like to get them working but I have absolutely no clue even where to start when it comes to detecting button signals on the remote for lirc config.  

Unfortunately lirc's docs are pretty scant as well - there is a program called irrecord and another called mode2 that supposedly help with this, but they require a device ID.  If I use the device ID in my lirc hardware.conf, it doesn't recognise the device.  Round and round in circles :)

---

### Post by idokibovito on 2008-12-02
I think you shouldn't have to use irrecord and irmode, since all the buttons are known and a config file exists for the remote. It even worked back in the days when lirc used the gpio module. 

It's just that some technologies changed, like this new input device support in lirc and the old GPIO module was dropped as far as I know. So we can't use it the old way, and the new one is not yet ready for prime time in Ubuntu as it seems.

At the moment I have no idea what else I could do to get it working. Maybe some updates will solve this for us.

I think it would be a good idea to try Mythbuntu, as I heard it has lirc by default (makes sense for a Media centric distro). If the remote works there as expected, maybe we could find the problem which causes it not to work in Ubuntu as it should.

---

