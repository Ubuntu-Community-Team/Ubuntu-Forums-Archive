---
title: "Conexant cx24120/cx24118 dvbs"
date: 2018-01-06
forum: Multimedia Software
---

### Post by whynot on 2018-01-06
Hi everyone
I have a Conexant CX24120/CX24118 dvbt-s tv card under Ubuntu 17.10 64X system.I think its allready installed.
But there is no device called /dev/video0 and most of the softwares are working with this device how could we activate this device?

```

$ uname -a
Linux whynot-Bus 4.13.0-21-generic #24-Ubuntu SMP Mon Dec 18 17:29:16 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

```

```
$ ls /dev/dvb/adapter0/
ca0  demux0  dvr0  frontend0

```
```
$ lspci -vvv | grep -i "SkyStar"
07:02.0 Network controller: Techsan Electronics Co Ltd B2C2 FlexCopII DVB chip / Technisat SkyStar2 DVB card (rev 02)
	Subsystem: Techsan Electronics Co Ltd B2C2 FlexCopII DVB chip / Technisat SkyStar2 DVB card

```

```
$ dmesg | grep DVB
[   29.940245] dvbdev: DVB: registering new adapter (FlexCop Digital TV device)
[   32.209969] cx24120: Conexant cx24120/cx24118 - DVBS/S2 Satellite demod/tuner
[   33.382806] b2c2_flexcop_pci 0000:07:02.0: DVB: registering adapter 0 frontend 0 (Conexant CX24120/CX24118)...
[   33.382852] b2c2-flexcop: initialization of 'Sky2PC/SkyStar S2 DVB-S/S2 rev 3.3' at the 'PCI' bus controlled by a 'FlexCopIIb' complete

```

```

$ dmesg | grep -i b2c2
[   29.887679] b2c2-flexcop: B2C2 FlexcopII/II(b)/III digital TV receiver chip loaded successfully
[   29.941797] b2c2-flexcop: MAC address = 00:08:c9:f1:ac:0f
[   33.382801] b2c2-flexcop: ISL6421 successfully attached.
[   33.382803] b2c2-flexcop: found 'Conexant CX24120/CX24118' .
[   33.382806] b2c2_flexcop_pci 0000:07:02.0: DVB: registering adapter 0 frontend 0 (Conexant CX24120/CX24118)...
[   33.382852] b2c2-flexcop: initialization of 'Sky2PC/SkyStar S2 DVB-S/S2 rev 3.3' at the 'PCI' bus controlled by a 'FlexCopIIb' complete

```

Thanks

---

### Post by whynot on 2018-01-07
```
sudo wget https://github.com/OpenELEC/dvb-firmware/blob/master/firmware/dvb-fe-cx24120-1.20.58.2.fw?raw=true -O /lib/firmware/dvb-fe-cx24120-1.20.58.2.fw
sudo reboot
```
no hope

---

### Post by deadflowr on 2018-01-07
What are you trying to use it with?
(Mythtv, or vlc or me-tv or tvheadend+kodi/openelec/something, or other)

Looks like everything is ready to go.

---

### Post by whynot on 2018-01-08
Here are some errors while restart process
```

$ dmesg
[   27.054000] CX24123: wrong demod revision: e9
[   29.267296] nxt200x: Unknown/Unsupported NXT chip: 00 00 00 00 00

$ cat /var/log/boot.log
[FAILED] Failed to start AppArmor initialization.
See 'systemctl status apparmor.service' for details.
         Starting Raise network interfaces...
[FAILED] Failed to start Automatic USB/Bluet&#8230;-0000:00:1a.0-usb1-1x2d1-1x2d1.3).
See 'systemctl status udev-configure-pr&#8230;sb1-1x2d1-1x2d1.3.service' for details.

```
It's not that important which software Kaffeine tvtime vlc mplayer.I want that device finally works.
By the way I have 64 bit Ubuntu system
```

$ uname -i
x86_64

```
Could it be that problem?

---

