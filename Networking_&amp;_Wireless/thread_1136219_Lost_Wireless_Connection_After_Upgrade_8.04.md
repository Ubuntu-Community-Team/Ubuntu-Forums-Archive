---
title: "Lost Wireless Connection After Upgrade 8.04"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by mbyaske@hotmail.com on 2009-04-24
I have a Dell netbook which connected well the first two weeks of use.  I recieved an Ubuntu software update 8.04 and now I can not connect.  I have network manager now, where I did previously and it can not find a network.  Under network manager under wirless devices it says device is unmanaged.

---

### Post by pytheas22 on 2009-04-24
Please post the output of these commands:
```

lshw -C Network
lspci -nn
uname -rm
lsusb
sudo iwlist scan
```

---

### Post by mbyaske@hotmail.com on 2009-04-25
ark@mark:~$ lshw -C Network 
bash: lshw: command not found 
mark@mark:~$ lspci -nn 
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GME Express Memory Controller Hub [8086:27ac] (rev 03) 
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03) 
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03) 
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02) 
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02) 
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 02) 
00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 02) 
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 02) 
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 02) 
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 02) 
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 02) 
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 02) 
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2) 
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02) 
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02) 
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 02) 
02:00.0 System peripheral [0880]: JMicron Technologies, Inc. Unknown device [197b:2382] 
02:00.2 SD Host controller [0805]: JMicron Technologies, Inc. Unknown device [197b:2381] 
02:00.3 System peripheral [0880]: JMicron Technologies, Inc. Unknown device [197b:2383] 
03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01) 
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller [10ec:8136] (rev 02) 
mark@mark:~$ uname -rm 
2.6.24-22-lpia i686 
mark@mark:~$ lsub 
bash: lsub: command not found 
mark@mark:~$ sudo iwlist scan 
[sudo] password for mark: 
lo Interface doesn't support scanning. 


eth0 Interface doesn't support scanning. 


sms Interface doesn't support scanning. 


eth1 Scan completed : 
Cell 01 - Address: 00:1B:2F:0C:4D:44 
ESSID:"Yaske" 
Mode:Managed 
Frequency:2.437 GHz (Channel 6) 
Quality:5/5 Signal level:-38 dBm Noise level:-92 dBm 
Encryption key:on 
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s 
12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s 
48 Mb/s; 54 Mb/s 
Cell 02 - Address: 00:19:E3:FB:ED:EF 
ESSID:"floweringgarden" 
Mode:Managed 
Frequency:2.412 GHz (Channel 1) 
Quality:1/5 Signal level:-88 dBm Noise level:-90 dBm 
IE: IEEE 802.11i/WPA2 Version 1 
Group Cipher : TKIP 
Pairwise Ciphers (2) : CCMP TKIP 
Authentication Suites (1) : PSK 
IE: WPA Version 1 
Group Cipher : TKIP 
Pairwise Ciphers (1) : TKIP 
Authentication Suites (1) : PSK 
Encryption key:on 
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s 
11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s 
48 Mb/s; 54 Mb/s 
Cell 03 - Address: 00:14:BF:3A:AE:3E 
ESSID:"linksys" 
Mode:Managed 
Frequency:2.462 GHz (Channel 11) 
Quality:1/5 Signal level:-80 dBm Noise level:-66 dBm 
Encryption key:off 
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 
24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s 
12 Mb/s; 48 Mb/s 


mark@mark:~$

---

### Post by pytheas22 on 2009-04-25
It looks like your card itself works fine from the command line, so the problem is just with NetworkManager.  It's probably [this bug]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/280417").  To check, please post the output of this command:
```

cat /etc/NetworkManager/nm-system-settings.conf
```

If what I suspect is true, this should be easy to fix.

You should also make sure that your system is up to date, because according to that bug report, this issue was fixed a while ago (I assume you're up to date if you just upgraded, but maybe not).

---

### Post by mbyaske@hotmail.com on 2009-04-25
cat: /etc/NetworkManager/nm-system-settings.conf: No such file or directory

---

### Post by pytheas22 on 2009-04-25
Sorry, apparently Ubuntu 8.04 does this slightly differently than 8.10.  What is the output of:
```

cat /etc/network/interfaces
```

---

### Post by mbyaske@hotmail.com on 2009-04-25
mark@mark:~$ cat /etc/network/interfaces 
auto lo 
iface lo inet loopback 
















iface eth1 inet dhcp 
wireless-key F37F2503E6 
wireless-essid Yaske 


auto eth1 
mark@mark:~$

---

### Post by pytheas22 on 2009-04-25
Ah, I think that's the problem.  Please open up your interfaces file by typing:
```

sudo gedit /etc/network/interfaces
```

Delete everything except the top two lines, so that the file looks like this:
```

auto lo
iface lo inet loopback 
```

Then save and close the file, and reboot.  Does this solve the problem?

---

### Post by mbyaske@hotmail.com on 2009-04-25
YESSSSSSSSSS!!!!
 
I owe you a cold one.

---

### Post by pytheas22 on 2009-04-25
Glad it's fixed :) Sorry it took a little while to get to the bottom of it.

---

