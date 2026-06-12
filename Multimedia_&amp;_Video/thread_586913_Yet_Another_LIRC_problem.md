---
title: "Yet Another LIRC problem"
date: 2007-10-22
forum: Multimedia &amp; Video
---

### Post by |Eric| on 2007-10-22
here is the thing iget lircd to load but irw kills it also i get an error when i trie to use irrecord 
i folowed the lirc howto for feisty but it dosent seam to work i got the lircd config from 
[http://lirc.sourceforge.net/remotes/msi/](http://lirc.sourceforge.net/remotes/msi/)
my tunner is msi if i remember corretly its a tv@nywhere so it would be ok but its not the reciever dosent seam to work last resort ill reboot in a few seconds 

$ sudo lsmod | grep lirc :
lirc_i2c               11268  0 
lirc_dev               15988  1 lirc_i2c
i2c_core               22784  7 cx88xx,ivtv,lirc_i2c,i2c_ec,bttv,i2c_algo_bit,tveeprom

lspci:

00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
************************ TV tunner Card **************
01:00.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
01:00.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
********************************************************
01:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
01:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
01:05.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 14)
02:00.0 RAID bus controller: Marvell Technology Group Ltd. Unknown device 6145 (rev a1)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8052 PCI-E ASF Gigabit Ethernet Controller (rev 21)
05:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7300 GT] (rev a1)


dmes :

[10331.511330] lirc_dev: IR Remote Control driver registered, at major 61 
[10331.512141] lirc_i2c: no version for "lirc_unregister_plugin" found: kernel tainted.
[10331.556432] ivtv:  ==================== START INIT IVTV ====================
[10331.556436] ivtv:  version 0.10.1 (tagged release) loading
[10331.556437] ivtv:  Linux version: 2.6.20-15-generic SMP mod_unload 586 
[10331.556439] ivtv:  In case of problems please include the debug info between
[10331.556441] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[10331.556443] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[10331.556471] ivtv:  ====================  END INIT IVTV  ====================
[10331.569304] cx2388x v4l2 driver version 0.0.6 loaded

---

