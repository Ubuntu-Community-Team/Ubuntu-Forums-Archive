---
title: "Xsane doesn't work with net scanner"
date: 2006-06-03
forum: Networking &amp; Wireless
---

### Post by mass_ga on 2006-06-03
Hi, I have a multifunction HP printer/scanner that works with USB port but not with wireless net. This is the result of scanimage command:

massimo@ubuntu:~$ SANE_DEBUG_NET=128 scanimage -L
[sanei_debug] Setting debug level of net to 128.
[net] sane_init: authorize = 0x80491d0, version_code = 0xbfcff378
[net] sane_init: SANE net backend version 1.0.13 (AF-indep+IPv6) from sane-backends 1.0.17
[net] sane_init: Client has little endian byte order
[net] sane_init: searching for config file
[net] sane_init: trying to add 192.168.1.2
[net] add_device: adding backend 192.168.1.2
[net] add_device: backend 192.168.1.2 added
[net] sane_init: done reading config
[net] sane_init: evaluating environment variable SANE_NET_HOSTS
[net] sane_init: done
[net] sane_get_devices: local_only = 0
[net] connect_dev: trying to connect to 192.168.1.2
[net] connect_dev: [0] connection succeeded (IPv4)
[net] connect_dev: sanei_w_init
[net] connect_dev: net_init (user=massimo, local version=1.0.3)
[net] connect_dev: freeing init reply (status=Success, remote version=1.0.3)
[net] connect_dev: done
[net] sane_get_devices: got 192.168.1.2:hpaio:/usb/Photosmart_2700_series?serial=MY4B6F10H00401
[net] sane_get_devices: finished (1 devices)
device `net:192.168.1.2:hpaio:/usb/Photosmart_2700_series?serial=MY4B6F10H00401' is a hp Photosmart_2700_series multi-function peripheral
device `hpaio:/usb/Photosmart_2700_series?serial=MY4B6F10H00401' is a hp Photosmart_2700_series multi-function peripheral
[net] sane_exit: exiting
[net] sane_exit: closing dev 0x807f5a0, ctl=3
[net] sane_exit: finished.

And this of scanimage -T:

scanimage: open of device net:192.168.1.2:hpaio:/usb/Photosmart_2700_series?serial=MY4B6F10H00401 failed: Error during device I/O

It seems that there is an I/O error. Config files seemes to be ok and I can't understand waht is going on ! Any suggestions?

---

### Post by odysseus_nz on 2006-06-18
So here's the story, (K)ubuntu Dapper ships with HPLIP 0.9.7, but wireless scanning was only added in HPLIP 0.9.8, but hey, that's understandable, after all 0.9.8 was only released in January so we can't expect it to have been included yet, obviously not stable enough yet...  What's that you say, we shipped with a beta version of Cups 1.2???  Surely not!

Other goodness like fax support was added in 0.9.9 which was released in February, 0.9.10 was released in March and 0.9.11 was released in May.  The 1.0 version was released in June.  We can only hope someone backports it, as it has all the latest printer drivers and full feature support that you think would be important to a desktop distribution.

John (disgruntled, in case you hadn't noticed, and considering a return to a distro where my Photosmart 3310 will actually work again.).

---

