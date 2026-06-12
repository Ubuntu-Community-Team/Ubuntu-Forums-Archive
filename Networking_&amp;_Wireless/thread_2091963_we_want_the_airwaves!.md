---
title: "we want the airwaves!"
date: 2012-12-06
forum: Networking &amp; Wireless
---

### Post by theramones on 2012-12-06
i have ubuntu running on this machine. the machine is using an asus usb wireless card to connect to the network. to get it working at first was very tough, i had to use ndiswrapper/ndisgtk, with the windows wireless drivers, even after using that, still couldnt get it working...then i installed wicd util....ran it...and weirdly after running it once, but then restarting, i was able to see and connect to the network, even though wicd wasn't running on restart. 

so anyways, we had to get a new router recently, and now, it can connect to the network just fine, can open up firefox, but when trying to go to a website in firefox....immediately at first x would just crash... it was just crashing to a wall of text....and the text would say stuff like (ndiswrapper) and a bunch of other stuff.....i uninstalled and reinstalled firefox, and now can't even go to a website....when starting firefox it says basically &quot;security settings/profile aren't right, firefox might not work properly&quot; and then when clicking on a bookmark, nothing at all happens....when typing in a website, nothing at all happens.  am i screwed? do i have to start from scratch? or is this salvageable?

---

### Post by chili555 on 2012-12-06
I have been sentenced, as reparations for many past sins, to solve your case. I requested, instead, five years in solitary but was denied. Let's get started. Please open a terminal and run and post:```
lsusb
ndiswrapper -l
dmesg | grep ndis
```The pipe symbol | is on the right side of my grimy US keyboard on the same key with \. Thanks.

---

### Post by theramones on 2012-12-06
alan@alan-GN689AA-ABA-m8277c:~$ lsusb Bus 011 Device 002: ID 045e:0745 Microsoft Corp.  Bus 011 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 010 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 008 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver Bus 008 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 007 Device 002: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 006 Device 002: ID 03f0:0f0c Hewlett-Packard Wireless Keyboard and Optical Mouse receiver Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 004 Device 002: ID 045e:009d Microsoft Corp. Wireless Optical Desktop 3.0 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 003 Device 005: ID 046d:082c Logitech, Inc.  Bus 003 Device 004: ID 0781:5530 SanDisk Corp.  Bus 003 Device 002: ID 1058:0730 Western Digital Technologies, Inc.  Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub Bus 002 Device 005: ID 0b05:1786 ASUSTek Computer, Inc.  Bus 002 Device 004: ID 0bda:0111 Realtek Semiconductor Corp. Card Reader Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  alan@alan-GN689AA-ABA-m8277c:~$ ndiswrapper -l net8192su : driver installed 	device (0B05:1786) present (alternate driver: r8712u)  alan@alan-GN689AA-ABA-m8277c:~$ dmesg | grep ndis [   11.606065] ndiswrapper version 1.56 loaded (smp=yes, preempt=no) [   12.640736] ndiswrapper: driver net8192su (Realtek Semiconductor Corp.,11/25/2010,1084.45.1125.2010) loaded [   14.028851] usbcore: registered new interface driver ndiswrapper

---

### Post by chili555 on 2012-12-06
Nice formatting. For the benefit of we who have tri-focals, I reiterate:```
 Device 005: ID 0b05:1786 ASUSTek Computer, Inc. 
``````
$ ndiswrapper -l net8192su : driver installed device (0B05:1786) present (alternate driver: r8712u) 
```And, finally:```
$ dmesg | grep ndis 
[ 11.606065] ndiswrapper version 1.56 loaded (smp=yes, preempt=no) 
[ 12.640736] ndiswrapper: driver net8192su (Realtek Semiconductor Corp.,11/25/2010,1084.45.1125.2010) loaded 
[ 14.028851] usbcore: registered new interface driver ndiswrapper 
```We wonder if any competing drivers are loaded. Now let's see:```
lsmod | grep -e ndis -e r8712 -e 8192
```So far, nothing at all alarming.

---

### Post by theramones on 2012-12-06
```
ndiswrapper                   192828  0 
```

---

### Post by chili555 on 2012-12-06
We see no driver problems, so let's turn to Network Manager and Wicd. Let's see who's running and who's not.```
ps aux | grep -i -e wicd -e network
```And some general diagnostics:```
nm-tool
```

---

### Post by theramones on 2012-12-06
```
alan@alan-GN689AA-ABA-m8277c:~$ ps aux | grep -i -e wicd -e network
root       789  0.0  0.2  25520  4564 ?        Ssl  18:40   0:00 NetworkManager
root      1770  0.0  0.0   2580  1248 ?        S    18:59   0:00 /sbin/dhclient -d -4 -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-wlan0.pid -lf /var/lib/dhcp/dhclient-3bafa92f-8ab8-4608-a3fd-6b69a8d08741-wlan0.lease -cf /var/run/nm-dhclient-wlan0.conf wlan0
alan      2056  0.0  0.0   4188   892 pts/0    S+   19:13   0:00 grep --color=auto -i -e wicd -e network

alan@alan-GN689AA-ABA-m8277c:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        00:1D:60:C1:78:0D

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [Auto japanese] -----------------------------------------------
  Type:              802.11 WiFi
  Driver:            ndiswrapper
  State:             connected
  Default:           yes
  HW Address:        30:85:A9:6E:1C:E6

  Capabilities:
    Speed:           150 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *japanese:       Infra, C8:D7:19:18:12:5C, Freq 2412 MHz, Rate 54 Mb/s, Strength 79 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.104
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1




```

---

### Post by chili555 on 2012-12-07
We see Network manager is running, and not Wicd. You evidently have an IP address and are connected with no apparent difficulties. Now let's see if you correctly get to the internet without Firefox.```
ping -c3 192.168.1.1
ping -c3 8.8.8.8
ping -c3 www.google.com
```Then, we'll look at your Firefox installation:```
firefox www.google.com
```Starting Firefox in the terminal may give us clues as to what is going wrong.

---

### Post by theramones on 2012-12-07
pings went through all fine...quick response time no packets lost.  then did the firefox command  it popped up the same dialog box that's been coming up then x crashed and did the text dump  examples of some of the text ```
[77580.440366] Call Trace: [77580.440394] [] ? NdisFreePacket+0x7d/0xb0 [ndiswrapper] 
```  etc etc, bunch of hex  ```
BUG: unable to handle kernel paging request at fffffffc IP: [] kthread_data+0xf/0x20  
```  etc etc, bunch of stuff about kernel and worker

---

### Post by chili555 on 2012-12-07
> pings went through all fine...quick response time no packets lost.That suggests it's not an ndiswrapper or networking issue. Let's check the message logs for clues:```
cat /var/log/syslog | grep -e firefox -e kworker
```Let's try to reinstall Firefox:```
sudo apt-get install --reinstall firefox*
```Now try again. Does it crash X?

---

### Post by theramones on 2012-12-11
the first command did nothing.  the second command ended up crashing x....after going through and asking for confirmation (y/n) twice....it went through a bunch of stuff and then x just crashed, no text dump this time just blank screen ......i don't think its a firefox problem though, because i tried to use the internet a different way earlier, by going into the ubuntu software center...and when it came time for it to connect to the internet to download software, it did the same crash that had been happening in firefox, where it crashed to a text dump with messages about ndiswrapper  but using firefox now doesnt crash x....it simply does not work, it doesnt even time out when trying to go to a website...when you click on a bookmark, it is as if you never clicked the bookmark at all....nothing at all happens

---

### Post by chili555 on 2012-12-11
Let's see if there are any clues here:```
cat /var/log/Xorg.0.log | grep -e WW -e EE
```In the Xorg logs, WW is a warning and EE is an error. Also check here, although the file may or may not exist:```
cat /var/log/Xorg.0.log.old | grep -e WW -e EE
```

---

