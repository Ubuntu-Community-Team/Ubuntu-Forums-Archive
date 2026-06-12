---
title: "WiFi connection to router inactive - Acer Inspire 1520"
date: 2013-05-26
forum: Networking &amp; Wireless
---

### Post by EddieColl on 2013-05-26
Hello, I am new to the Forum and would be very grateful and appreciative of advice/help with regard to Wireless/WIFI connectivity to my router.


I have a laptop Acer Aspire 1520 and having installed Ubuntu 12.04 for a friend to use, now find that the wireless connection hasn't been activated. To be honest I'm not surprised as a year ago, I bought a Leonovo from a seller of Ubuntu-ready laptops and on delivery, found the this problem and so phoned them up and they gave me about 4 lines of commands over the phone to be inserted into the Terminal as Sudo (ie as administrator). This fixed the problem however I am conscious that the makes of laptop are different and so reckon that the commands will be different.


My network does not appear in the list of available networks, nor do any others (ie BTOpenzone would normally but doesn't).


The cable ethernet does work as I have connected the laptop to the router by cable to do all the system updates, so this is purely a WiFi connection issue.


Can anyone tell me what the 3 or 4 lines of commands for the Terminal are please?


Thanks.


Ed

---

### Post by praseodym on 2013-05-26
Please check the outputs of:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
sudo iwlist scan
```

---

### Post by EddieColl on 2013-05-26
Hi,thanks for this. I typed in the scripts into Terminal and these are the outputs:

----------
vano@vano-Aspire-1520:~$ lspci -nnk | grep -iA2 net
00:0a.0 Ethernet controller [0200]: InProComm Inc. IPN 2220 802.11g [17fe:2220]
    Subsystem: AMBIT Microsystem Corp. T60N871 802.11g Mini PCI Wireless Adapter [1468:0305]
00:0b.0 CardBus bridge [0607]: Texas Instruments PCI7420 CardBus Controller [104c:ac8e]
--
00:0c.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet [10ec:8169] (rev 10)
    Subsystem: Acer Incorporated [ALI] Device [1025:006e]
    Kernel driver in use: r8169

vano@vano-Aspire-1520:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


vano@vano-Aspire-1520:~$ lsmod
Module                  Size  Used by
vesafb                 13516  1 
joydev                 17393  0 
snd_via82xx            24718  2 
snd_via82xx_modem      18377  5 
gameport               15060  1 snd_via82xx
snd_ac97_codec        110213  2 snd_via82xx,snd_via82xx_modem
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80916  5 snd_via82xx,snd_via82xx_modem,snd_ac97_codec
snd_mpu401_uart        13865  1 snd_via82xx
snd_seq_midi           13132  0 
snd_rawmidi            25424  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
nvidia               4708655  22 
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
i2c_viapro             12969  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 39826  0 
psmouse                86520  0 
snd                    62218  21 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13027  0 
snd_page_alloc         14108  3 snd_via82xx,snd_via82xx_modem,snd_pcm
k8temp                 12905  0 
rfcomm                 38139  0 
bnep                   17830  2 
soundcore              14635  1 snd
via_ircc               26781  0 
bluetooth             158479  10 rfcomm,bnep
yenta_socket           27465  0 
pcmcia_rsrc            18367  1 yenta_socket
irda                  185517  1 via_ircc
binfmt_misc            17292  1 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
shpchp                 32265  0 
ppdev                  12849  0 
crc_ccitt              12627  1 irda
video                  19115  0 
parport_pc             32114  1 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
pata_via               13428  2 
firewire_ohci          40172  0 
r8169                  56368  0 
firewire_core          56940  1 firewire_ohci
crc_itu_t              12627  1 firewire_core


vano@vano-Aspire-1520:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

vano@vano-Aspire-1520:~$ rfkill list
vano@vano-Aspire-1520:~$ sudo iwlist scan
[sudo] password for vano: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
-----------

Not sure how to interpret the outputs. Grateful for advice on what it means and what to do next.

Thanks.

---

### Post by praseodym on 2013-05-26
For this wireless device you need ndiswrapper.

Download these files:

[https://launchpad.net/ubuntu/+archive/primary/+files/ndiswrapper-common_1.58%7Erc1-0ubuntu1_all.deb](https://launchpad.net/ubuntu/+archive/primary/+files/ndiswrapper-common_1.58%7Erc1-0ubuntu1_all.deb)

[https://launchpad.net/ubuntu/+archive/primary/+files/ndiswrapper-dkms_1.58%7Erc1-0ubuntu1_all.deb](https://launchpad.net/ubuntu/+archive/primary/+files/ndiswrapper-dkms_1.58%7Erc1-0ubuntu1_all.deb)

and for 32bit:
[https://launchpad.net/ubuntu/+archive/primary/+files/ndiswrapper-utils-1.9_1.58%7Erc1-0ubuntu1_i386.deb](https://launchpad.net/ubuntu/+archive/primary/+files/ndiswrapper-utils-1.9_1.58%7Erc1-0ubuntu1_i386.deb)
or 64bit:
[https://launchpad.net/ubuntu/+archive/primary/+files/ndiswrapper-utils-1.9_1.58%7Erc1-0ubuntu1_amd64.deb](https://launchpad.net/ubuntu/+archive/primary/+files/ndiswrapper-utils-1.9_1.58%7Erc1-0ubuntu1_amd64.deb)

Save the files in "Downloads" and install them via:
```

sudo dpkg -i ~/Downloads/*.deb
```
The windows drivers are attched. Please refer to [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by EddieColl on 2013-05-26
Thanks, I have installed the drivers and also downloaded the windows driver (which was attached) and extracted it. Unfortunately, the actions haven't activated the WiFi connection. Is it worth running through the Terminal commands routine (above in the first reply) again to retest and confirm the activation status?

Also just for info, whilst this is a 64-bit machine running off an Athlon AMD 64 processor, the install of Ubuntu is 32-bit, and so I installed the driver for the i-386 (32 bit).

Thanks again for the help.

---

### Post by praseodym on 2013-05-26
Install the driver with
```

sudo ndiswrapper -i /path/to/driver.inf
sudo modprobe -v ndiswrapper
```
You can try both 32bit INF files. Check afterwards:
```

ndiswrapper -l
lsmod
dmesg | grep ndis
```

---

