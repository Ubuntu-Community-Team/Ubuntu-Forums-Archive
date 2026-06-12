---
title: "Trouble setting up wifi."
date: 2012-02-12
forum: Networking &amp; Wireless
---

### Post by bRcLY on 2012-02-12
Using ubuntu live CD 8.04 I am trying to get the wireless to work.

1)  If I go to "Wireless Networking--Troubleshooting--Check for device recognition", it directs me to go to: "System--Preference--Hardware Information".   I can't find "Hardware Information" listed under "Preference".

2) When I go to the Network Icon (double screen) I assume I should click on "802.1 protected wire network" to set up my wifi.  It asks me to fill out a form.  One of the spaces asks for "Identity".  What is this referring?  When I fill it out without answering this I get a message saying I need a "Network Name" (passphrase) or "encription key".  I this different from the password for my router?  I fill in "password" and "Network Key"

The internet works fine with ubuntu when I plug the computer directly into the router.  The wifi works fine when I run windows instead of ubuntu.

---

### Post by praseodym on 2012-02-12
Hi,

Ubuntu 8.04 is outdated, so I recommend usind a newer version, at least 10.04 (10.10 is running out of support in april this year, too). Please show the outputs of

```
lspci -nn
lsusb
```
from 8.04. From newer versions
```
lspci -nnk | grep -iA2 net
lsusb
lsmod
rfkill list
iwconfig
```

---

### Post by bRcLY on 2012-02-12
The reason I am using 8.08 is that the 10.04 live CD with EMC2 would not load.  The Ubuntu EMC2 forum suggested this happens a lot and to try 8.04 because there doesn't seem to be the same problem.  I was successful using 8.04 with EMC2 live CD.  I would love to use a newer version--any suggestions?  I put the CD in and there starts to be writing on the screen then it stops and nothing happens but the CD drive continues to make noise like it is working.



I went to teminal and typed in lsusb and lspci -nn and got the following: 
(Thank you for your efforts.)

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ lsusb
Bus 004 Device 003: ID 058f:6364 Alcor Micro Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:c05a Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 04f2:0841 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 0000:0000  
ubuntu@ubuntu:~$ 

ubuntu@ubuntu:~$ lspci -nn
00:00.0 RAM memory [0500]: nVidia Corporation Unknown device [10de:0754] (rev a2)
00:01.0 ISA bridge [0601]: nVidia Corporation Unknown device [10de:075c] (rev a2)
00:01.1 SMBus [0c05]: nVidia Corporation Unknown device [10de:0752] (rev a1)
00:01.2 RAM memory [0500]: nVidia Corporation Unknown device [10de:0751] (rev a1)
00:01.3 Co-processor [0b40]: nVidia Corporation Unknown device [10de:0753] (rev a2)
00:01.4 RAM memory [0500]: nVidia Corporation Unknown device [10de:0568] (rev a1)
00:02.0 USB Controller [0c03]: nVidia Corporation Unknown device [10de:077b] (rev a1)
00:02.1 USB Controller [0c03]: nVidia Corporation Unknown device [10de:077c] (rev a1)
00:04.0 USB Controller [0c03]: nVidia Corporation Unknown device [10de:077d] (rev a1)
00:04.1 USB Controller [0c03]: nVidia Corporation Unknown device [10de:077e] (rev a1)
00:07.0 Audio device [0403]: nVidia Corporation Unknown device [10de:0774] (rev a1)
00:08.0 PCI bridge [0604]: nVidia Corporation Unknown device [10de:075a] (rev a1)
00:09.0 RAID bus controller [0104]: nVidia Corporation Unknown device [10de:0ad8] (rev a2)
00:0a.0 Ethernet controller [0200]: nVidia Corporation Unknown device [10de:0760] (rev a2)
00:10.0 PCI bridge [0604]: nVidia Corporation Unknown device [10de:0778] (rev a1)
00:12.0 PCI bridge [0604]: nVidia Corporation Unknown device [10de:075b] (rev a1)
00:13.0 PCI bridge [0604]: nVidia Corporation Unknown device [10de:077a] (rev a1)
00:14.0 PCI bridge [0604]: nVidia Corporation Unknown device [10de:077a] (rev a1)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration [1022:1200]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map [1022:1201]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller [1022:1202]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control [1022:1203]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control [1022:1204]
01:05.0 FireWire (IEEE 1394) [0c00]: Agere Systems FW323 [11c1:5811] (rev 70)
02:00.0 VGA compatible controller [0300]: ATI Technologies Inc Unknown device [1002:954f]
02:00.1 Audio device [0403]: ATI Technologies Inc Unknown device [1002:aa38]
04:00.0 Network controller [0280]: Atheros Communications Inc. Unknown device [168c:002a] (rev 01)
ubuntu@ubuntu:~$

---

### Post by bRcLY on 2012-02-12
When I use the ubuntu EMC2 live CD going to the internet am I covered security wise?  I have security software on the computer but with Windows OS.  Does it automaticlly cover Ubuntu OS also or do I have to download more security software?

---

### Post by praseodym on 2012-02-12
For 8.04 you need to compile the driver via linux-wireless. Due to an old linux version you need an older driver version:

[http://www.linuxwireless.org/](http://www.linuxwireless.org/)

Package compat-wireless-old.tar.gz:

```
sudo apt-get install linux-headers-$(uname -r) build-essential
wget [http://www.orbit-lab.org/kernel/compat-wireless-2.6/2009/01/compat-wireless-old-2009-01-18.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-2.6/2009/01/compat-wireless-old-2009-01-18.tar.bz2)
tar jxvf compat-wireless-old-2009-01-18.tar.bz2
```
Some more config is neccessary:

```
sudo cp ~/compat-wireless-2*/scripts/ath* ~/compat-wireless-2*/scripts/b43* /usr/sbin 
sudo mkdir /usr/lib/compat-wireless 
sudo cp ~/compat-wireless-2*/scripts/load.sh ~/compat-wireless-2*/scripts/unload.sh ~/compat-wireless-2*/scripts/modlib.sh /usr/lib/compat-wireless 
```
Compilation via:
```
cd compat-wireless-20*
make
sudo make install
```
Load the driver:
```
sudo modprobe ath9k
sudo /etc/init.d/networking restart
```

---

### Post by bRcLY on 2012-02-12
Thank you for your response.   Unfortunately, for the most part I don't understand what you are talking about.

I went to the web site listed and looked for my "Atheros 802.11 a/b/g/n dualband Wireless Network Module".  I did not see this listed.

You talked about a "Package compat-wireless-old.tar.gz:".  I don't know what to do with this information. Do I type the listed lines at the terminal?

Should I be spending this time on 8.04 or is there a way to get the 10.04 live CD to work?

Bruce

---

### Post by bRcLY on 2012-02-13
SOLVED
I figured out how to run the ubuntu 10.04 live CD.   Then I was able to get on the INTERNET using wifi.
Thank you for all the help.
Bruce

---

