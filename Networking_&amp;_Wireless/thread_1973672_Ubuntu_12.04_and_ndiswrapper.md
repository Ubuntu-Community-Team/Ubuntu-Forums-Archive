---
title: "Ubuntu 12.04 and ndiswrapper"
date: 2012-05-05
forum: Networking &amp; Wireless
---

### Post by PSauthor on 2012-05-05
I have just upgraded my old Toshiba laptop to Ubuntu from 10.04 to 12.04. Before the upgrade ndiswrapper worked perfectly so I could install the Windows XP driver for my Belkin wireless card. Now I have upgraded to 12.04 I cannot re-install my Windows XP driver for my wireless card. The following error message appears:-

"Module could not be loaded. Error was:
FATAL: Module ndiswrapper not found.
Is the ndiswrapper module installed?"

The ndiswrapper is installed and it shows the my Windows XP driver is installed and hardware is present, but the wireless card is not working. Also, in Applications, I have the shortcut to start ndiswrapper. Using this shortcut, ndiswrapper starts OK.

I have also tried using Terminal to install and use ndiswrapper, but I get the same error message.

Regards

PSauthor

---

### Post by praseodym on 2012-05-05
Hi,

what card/stick is that? Please show:

```
uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
dmesg | grep ndis
```

---

### Post by PSauthor on 2012-05-05
Hello

It is a Belkin Wireless G Plus Notebook Card model number F5D7011 version 1212df. This PC card worked fine with Ubunutu 10.04 and ndiswrapper.

Ubuntu 12.04 seems to be having a problem with ndiswrapper. Yet my Windows XP driver is installed and ndiswrapper does open to allow me to install the driver. When I click on "Install" button I get the error message. After rebooting the laptop, the card no longer functions.

Regards

PSauthor

---

### Post by PSauthor on 2012-05-05
This the code from my laptop, I think. Not too sure if I have done it correctly.


peewee@Test-Toshiba:~$ uname -a
Linux Test-Toshiba 3.2.0-030200-generic #201201042035 SMP Thu Jan 5 01:44:33 UTC 2012 i686 i686 i386 GNU/Linux
peewee@Test-Toshiba:~$ lspci -nnk | grep n-iA2 net
grep: net: No such file or directory
peewee@Test-Toshiba:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 1d57:001a  
peewee@Test-Toshiba:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

peewee@Test-Toshiba:~$ rfkill list
peewee@Test-Toshiba:~$ dmseg | grep ndis
No command 'dmseg' found, did you mean:
 Command 'mmseg' from package 'sunpinyin-utils' (main)
 Command 'dmesg' from package 'util-linux' (main)
dmseg: command not found
peewee@Test-Toshiba:~$

---

### Post by praseodym on 2012-05-05
Please check the syntax of the commands:
> 
lspci -nnk | grep -iA2 net
dmesg | grep ndis

---

### Post by PSauthor on 2012-05-06
Sorry about that. Sometimes my fingers have a mind of their own.

Text from Terminal is below.

Regards

PSauthor


peewee@Test-Toshiba:~$ uname -a
Linux Test-Toshiba 3.2.0-030200-generic #201201042035 SMP Thu Jan 5 01:44:33 UTC 2012 i686 i686 i386 GNU/Linux
peewee@Test-Toshiba:~$ lspci -nnk | grep -iA2 net
02:09.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
	Subsystem: Toshiba America Info Systems Device [1179:0002]
	Kernel driver in use: 8139too
--
05:00.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
	Subsystem: Belkin F5D7011 v2000 High-Speed Mode Wireless G Notebook Card [1799:7011]
	Kernel modules: ssb
peewee@Test-Toshiba:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
peewee@Test-Toshiba:~$ lsmod
Module                  Size  Used by
snd_intel8x0           33330  2 
snd_ac97_codec        105571  1 snd_intel8x0
bnep                   17749  2 
bluetooth             153156  7 bnep
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                76379  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25103  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51256  2 snd_seq_midi,snd_seq_midi_event
snd_timer              24609  2 snd_pcm,snd_seq
snd_seq_device         14130  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 39578  0 
joydev                 17313  0 
nouveau               719184  2 
ttm                    64800  1 nouveau
yenta_socket           27140  0 
snd                    55724  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         36749  1 nouveau
pcmcia_rsrc            18292  1 yenta_socket
pcmcia_core            21506  3 pcmcia,yenta_socket,pcmcia_rsrc
soundcore              12600  1 snd
drm                   197071  4 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13152  1 nouveau
mxm_wmi                12859  1 nouveau
wmi                    18645  1 mxm_wmi
ppdev                  12900  0 
snd_page_alloc         14036  2 snd_intel8x0,snd_pcm
shpchp                 32285  0 
toshiba_acpi           17847  0 
psmouse                73554  0 
video                  18792  1 nouveau
parport_pc             32006  1 
sparse_keymap          13658  1 toshiba_acpi
serio_raw              13027  0 
lp                     13349  0 
parport                36664  3 ppdev,parport_pc,lp
firewire_ohci          39598  0 
8139too                23241  0 
firewire_core          56694  1 firewire_ohci
8139cp                 22353  0 
crc_itu_t              12627  1 firewire_core
peewee@Test-Toshiba:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

peewee@Test-Toshiba:~$ rfkill list
peewee@Test-Toshiba:~$ dmesg | grep ndis
peewee@Test-Toshiba:~$

---

### Post by praseodym on 2012-05-06
For this device ndiswrapper is not needed, uninstall it via:

```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper* ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
```
and install the needed firmware for this device:
```

wget http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz 
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
sudo modprobe b43
```

---

### Post by sundararamany on 2012-05-07
Hello, I followed the steps and my Belkin has started working now. Mine is a COMPAQ PRESARIO 1500 model.

Thanks you. Regards, Sundar

---

### Post by PSauthor on 2012-05-07
Hello

Thank you very much.

My Belkin card is now working and my old Toshiba laptop (2004) now has a new lease of life.

Regards

PSauthor

---

### Post by jerryf196 on 2012-10-08
I installed ubuntu 12.10beta and I have a compaq paserio r4000 and it does not work.

Any clue anyone?

---

### Post by elgandoz on 2013-06-12
> **jerryf196 said:**
> I installed ubuntu 12.10beta and I have a compaq paserio r4000 and it does not work.

Any clue anyone?

I followed just the lasts steps on my father's Compaq Presario R4000 (64bit) with the Broadcom BCM4306 802.11b/g on Ubuntu 13.04, and everything worked, instantly!

So, as Praseidom wrote...
```
wget http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz 
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
sudo modprobe b43
```

Good luck ):P

---

### Post by budjako on 2013-06-21
I have the same problem here now with different specs but with almost the same card. I tried to do the instructions that you've stated but it said that the file that is to be downloaded is not available anymore. Do you have any other solution for this? I'm sorry about this. I know that this post is kind of old already but I would really appreciate it if you could help me. thanks :)

---

### Post by budjako on 2013-06-21
oh. my bad. I just misspelled a word. it works after I rebooted my laptop. thanks to the this post. Cheers! : )

---

