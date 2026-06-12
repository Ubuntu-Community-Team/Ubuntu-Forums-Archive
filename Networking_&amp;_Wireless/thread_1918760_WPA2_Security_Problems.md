---
title: "WPA2 Security Problems"
date: 2012-02-01
forum: Networking &amp; Wireless
---

### Post by romain.astie on 2012-02-01
Hi All,

I'm trying to connect to my WPA2 protected network under lubuntu with a card whose driver is managed by ndiswrapper. I can click on the network and enter my password, but the spinning icon indication the connection status at the bottom of the screen keeps on spinning and 10 minuted later does not connect. Any suggestions as to what I'm doing wrong?

---

### Post by praseodym on 2012-02-01
Hi,

what card do you use? Please show:

```
uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
sudo iwlist scan
dmesg | grep ndis
```
Maybe the (particular?) Windows-driver and/or its firmware dont support WPA2?!

Edit: If its ndiswrapper 1.56 you can replace it by the latest stable release 1.57, but you need to compile again for new kernels:

[http://forum.ubuntuusers.de/topic/wlan-pci-wird-nicht-bei-jedem-start-erkannt/#post-3842662](http://forum.ubuntuusers.de/topic/wlan-pci-wird-nicht-bei-jedem-start-erkannt/#post-3842662)

The red box reads: Dont install (better uninstall it, too) ndisgtk from the repositories, but compile that, too!

---

### Post by romain.astie on 2012-02-01
Clicked Wrong Button

---

### Post by romain.astie on 2012-02-01
WPA2 support isn't (or at least, shouldn't be) a problem, as I've used this card before with a WPA2 network before. ndisgtk has been uninstalled, and I've run the code you wanted me to, in order, according to your list( If you need the commands bolded to sort through it faster, I've attached a pdf version) : ```

romain@romain-pc:~$ uname -a
Linux romain-pc 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux 
romain@romain-pc:~$ lspci -nnk | grep -iA2 net 
02:00.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)
Subsystem: Linksys WPC54G v1 / WPC54GS v1 802.11g Wireless-G Notebook Adapter [1737:4320]
Kernel driver in use: ndiswrapper
romain@romain-pc:~$ lsusb
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
romain@romain-pc:~$ lsmod
Module ndiswrapper bnep rfcomm bluetooth parport_pc ppdev vesafb joydev snd_nm256 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi dcdbas snd_rawmidi snd_seq_midi_event	14475 1 snd_seq_midi snd_seq	51567 2 snd_seq_midi,snd_seq_midi_event snd_timer	28932 2 snd_pcm,snd_seq
snd_seq_device	14172 3 snd_seq_midi,snd_rawmidi,snd_seq psmouse	73673 0 serio_raw	12990 0 snd	55902 9 snd_nm256,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_piix4 video soundcore pcmcia yenta_socket pcmcia_rsrc pcmcia_core shpchp
lp parport floppy
13093 0 18908 0
12600 1 snd 39822 0
27428 0 18367 1 yenta_socket
21511 3 pcmcia,yenta_socket,pcmcia_rsrc 32356 0
17455 0 40930 3 parport_pc,ppdev,lp 60310 0
Size Used by 193669 0
17923 2 38408 0
148839 10 bnep,rfcomm 32114 0
12849 0 13489 1 17393 0
68608 1 106082 1 snd_nm256
12642 1 snd_ac97_codec 80468 2 snd_nm256,snd_ac97_codec
14115 1 snd_pcm 13132 0
14098 0 25241 1 snd_seq_midi
romain@romain-pc:~$ iwconfig
lo	no wireless extensions.
wlan0	IEEE 802.11g ESSID:"Alicias Empire 1" Mode:Managed Frequency:2.437 GHz Access Point: 00:19:9D:33:D5:D9 Bit Rate=1 Mb/s	Tx-Power:8 dBm RTS thr:2347 B	Fragment thr:2346 B Power Management:off Link Quality:35/100 Signal level:-73 dBm Noise level:-96 dBm Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0 Tx excessive retries:0 Invalid misc:0	Missed beacon:0
romain@romain-pc:~$ sudo iwlist scan
[sudo] password for romain: lo	Interface doesn't support scanning.
wlan0	Scan completed : Cell 01 - Address: E0:46:9A:68:38:5A
ESSID:"i-Sails" Protocol:IEEE 802.11b Mode:Managed Frequency:2.437 GHz (Channel 6) Quality:46/100 Signal level:-66 dBm Noise level:-96 dBm Encryption key:on
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s 12 Mb/s; 48 Mb/s
Extra:bcn_int=100 Extra:atim=0 IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : CCMP Pairwise Ciphers (1) : CCMP Authentication Suites (1) : PSK
Cell 02 - Address: 00:21:29:94:AF:2C ESSID:"1048"
Protocol:IEEE 802.11b Mode:Managed Frequency:2.437 GHz (Channel 6) Quality:51/100 Signal level:-63 dBm Noise level:-96 dBm Encryption key:on
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s 12 Mb/s; 48 Mb/s
Extra:bcn_int=100 Extra:atim=0 IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : CCMP Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : PSK Cell 03 - Address: 74:44:01:40:A9:71
ESSID:"1024 Empire BGN" Protocol:IEEE 802.11b Mode:Managed Frequency:2.452 GHz (Channel 9) Quality:48/100 Signal level:-65 dBm Noise level:-96 dBm Encryption key:on
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s 12 Mb/s; 48 Mb/s
Extra:bcn_int=100 Extra:atim=0 IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : CCMP Pairwise Ciphers (1) : CCMP Authentication Suites (1) : PSK
Cell 04 - Address: 00:14:BF:B4:B4:84 ESSID:"skihouse1"
Protocol:IEEE 802.11b Mode:Managed Frequency:2.462 GHz (Channel 11) Quality:40/100 Signal level:-70 dBm Noise level:-96 dBm Encryption key:on
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s 12 Mb/s; 48 Mb/s
Extra:bcn_int=75
Extra:atim=0 Cell 05 - Address: 00:23:69:47:F5:FA
ESSID:"allparkcityrentals" Protocol:IEEE 802.11b
Mode:Managed Frequency:2.412 GHz (Channel 1) Quality:45/100 Signal level:-67 dBm Noise level:-96 dBm Encryption key:on Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
12 Mb/s; 48 Mb/s Extra:bcn_int=100
Extra:atim=0 IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP Pairwise Ciphers (2) : CCMP TKIP Authentication Suites (1) : PSK
IE: WPA Version 1 Group Cipher : TKIP Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK Cell 06 - Address: 00:24:37:8B:7E:20
ESSID:"1049" Protocol:IEEE 802.11b Mode:Managed Frequency:2.412 GHz (Channel 1) Quality:48/100 Signal level:-65 dBm Noise level:-96 dBm Encryption key:on Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
36 Mb/s; 48 Mb/s; 54 Mb/s Extra:bcn_int=100
Extra:atim=0 IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP Pairwise Ciphers (1) : CCMP Authentication Suites (1) : PSK
IE: WPA Version 1 Group Cipher : TKIP Pairwise Ciphers (1) : TKIP Authentication Suites (1) : PSK
Cell 07 - Address: 02:23:69:47:F5:FB ESSID:"Snowcrest301"
Protocol:IEEE 802.11b Mode:Managed Frequency:2.412 GHz (Channel 1) Quality:46/100 Signal level:-66 dBm Noise level:-96 dBm Encryption key:on
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s 12 Mb/s; 48 Mb/s
Extra:bcn_int=100 Extra:atim=0 IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP Pairwise Ciphers (2) : CCMP TKIP Authentication Suites (1) : PSK
IE: WPA Version 1 Group Cipher : TKIP Pairwise Ciphers (2) : CCMP TKIP Authentication Suites (1) : PSK
Cell 08 - Address: 00:1C:DF:EF:4B:61 ESSID:"727"
Protocol:IEEE 802.11b Mode:Managed Frequency:2.412 GHz (Channel 1) Quality:25/100 Signal level:-80 dBm Noise level:-96 dBm Encryption key:on
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s 12 Mb/s; 48 Mb/s
Extra:bcn_int=100
Extra:atim=0 Cell 09 - Address: 00:19:9D:33:D5:D9
ESSID:"Alicias Empire 1" Protocol:IEEE 802.11b Mode:Managed Frequency:2.437 GHz (Channel 6) Quality:35/100 Signal level:-73 dBm Noise level:-96 dBm Encryption key:off
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s 11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s 48 Mb/s; 54 Mb/s
Extra:bcn_int=100 Extra:atim=0
romain@romain-pc:~$ dmesg | grep ndis
[ 3156.019393] ndiswrapper version 1.56 loaded (smp=yes, preempt=no) [ 3156.468686] ndiswrapper: driver lsbcmnds (The Linksys Group, Inc.,07/17/2003, 3.30.15.0) loaded [ 3156.469884] ndiswrapper 0000:02:00.0: enabling device (0000 -> 0002) [ 3156.469970] ndiswrapper 0000:02:00.0: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11 [ 3156.470113] ndiswrapper 0000:02:00.0: setting latency timer to 64 [ 3156.492820] ndiswrapper: using IRQ 11 [ 3156.821708] usbcore: registered new interface driver ndiswrapper [ 3235.360183] ndiswrapper (iw_set_auth:1602): invalid cmd 12 [ 3235.360680] ndiswrapper (set_iw_auth_mode:601): setting auth mode to 7 failed (C0010015) [ 3246.211540] ndiswrapper (set_iw_auth_mode:601): setting auth mode to 7 failed (C0010015) [ 3251.219744] ndiswrapper (iw_set_auth:1602): invalid cmd 12 [ 3251.220619] ndiswrapper (set_iw_auth_mode:601): setting auth mode to 7 failed (C0010015) [ 3262.099689] ndiswrapper (set_iw_auth_mode:601): setting auth mode to 7 failed (C0010015) [ 3267.263823] ndiswrapper (iw_set_auth:1602): invalid cmd 12 [ 3267.264706] ndiswrapper (set_iw_auth_mode:601): setting auth mode to 7 failed (C0010015) [ 3278.111834] ndiswrapper (set_iw_auth_mode:601): setting auth mode to 7 failed (C0010015) [ 3283.122374] ndiswrapper (iw_set_auth:1602): invalid cmd 12 [ 3283.122746] ndiswrapper (set_iw_auth_mode:601): setting auth mode to 7 failed (C0010015) [ 3833.508167] ndiswrapper (iw_set_auth:1602): invalid cmd 12 [ 3896.889198] ndiswrapper (iw_set_auth:1602): invalid cmd 12 [ 3906.905819] ndiswrapper (iw_set_auth:1602): invalid cmd 12
```

It says that I was connected to Alicias Empire 1, but that's not the WPA2 network I need to connect to. the network I need to get to is called I-Sails. Does this help?

---

### Post by praseodym on 2012-02-02
Install the missing Broadcom firmware for this device and uninstall ndiswrapper:

```
wget http://media.ubuntuusers.de/forum/attachments/2480236/Broadcom_Firmware.tar.gz 
sudo tar xvf Broadcom_Firmware.tar.gz -C /lib/firmware/ 
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
sudo update-initramfs -u
```
Reboot.

---

### Post by romain.astie on 2012-02-02
It installed all right (as far as I can tell), but the card isn't checking in with ubuntu. when I click on the wireless icon, it says that there are no network devices available... What should I do now?

EDIT: I figured out why it wasn't working: my card works with 802.11b/g, but not with 802.11i, which is what the network i want to connect to has. OOPS... Reverting to ndiswrapper. will see if I can change the router to 802.11g...

---

### Post by romain.astie on 2012-02-03
I just did a re-scan and the router seems to be on 802.11b. Here is the relevant output:

```
Cell 02 - Address: E0:46:9A:68:38:5A ESSID:"i-Sails"
Protocol:IEEE 802.11b Mode:Managed Frequency:2.437 GHz (Channel 6) Quality:40/100 Signal level:-70 dBm Noise level:-96 dBm Encryption key:on
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s 12 Mb/s; 48 Mb/s
Extra:bcn_int=100 Extra:atim=0 
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : CCMP Pairwise Ciphers (1) : CCMP Authentication Suites (1) : PSK
```

What is curious is that on the line before last it says IEEE 802.11i/WPA2 Version 1. Any ideas if this might be why I can't connect? If so, any solutions?

---

### Post by romain.astie on 2012-02-03
I kind of need express help on this, as I need to get and install large packages... HELP?

---

### Post by praseodym on 2012-02-04
Did you try the Broadcom-STA-driver? Ndiswrapper needs -again- to be uninstalled for this.Did you try the Broadcom-STA-

---

### Post by romain.astie on 2012-02-06
Yes, but as I mentioned before, Ubuntu doesn't recognize the card. When I run lspci, it shows up correctly, but iwconfig doesn't generate the correct output. Further, Ubuntu, under the network menu on the panel, states that no wireless network interfaces are available.

---

### Post by kevdog on 2012-02-06
Check dmesg or /var/log/messages or possibly some other log files located in /var/log.  Error messages will probably be written here.  Post anything that looks suspicious so we can help you out. Please don't post the entire file however.

---

### Post by romain.astie on 2012-02-06
Right smack in the middle of the relevant code it says that the supported encryption modes are _____, listing almost anything I can think of, but no WPA2. And then it hits me: the network I used to connect to WASN'T WPA2. It used the same password as the new network, but was WPA or WEP instead, I can't remember which...  On the other hand, I researched the driver in Linksys help files and it said that the card could do WPA2 with a driver update, but my card is still too old for that...Sorry about the confusion, I really zoned out on this one... SO STUPID OF ME! Problemo Solved (or at least the cause was found and it will be solved in the very near future)

---

