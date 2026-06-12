---
title: "Ubuntu 10.04 and TP TL 722N"
date: 2013-08-25
forum: Networking &amp; Wireless
---

### Post by haris2 on 2013-08-25
[TABLE]
[TR]
[TD="class: votecell"]      

              [/TD]
              [TD="class: postcell"]                Hello,i know there is a similar topic, and other ones explaining  how to do this with TP LINK TL 722N USB Wireless adapter.  I tried a  solution by copying htc 9271 firmware to lib/firmware folder, and  unarchived compat drivers and building a driver but it does not work. I  do not get the errors, but the icon of wireless networks is not popping  out.  But when I went to hardware and devices it shows me that Atheros  wireless device is connected and working correctly.  I would try also  option with and its wrapper, but I don't know which CD I need to have  and what to put on that CD.  Also is it maybe possible that I am able to  make the adapter work with the first solution and maybe not seeing  wireless networks because I don't know how to put wireless icon on a  panel?And whatt kind of CD i need to have ? since it always says "put a cd in the cd rom".

  the lsusb 
  Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 0cf3:9271 Atheros Communications, Inc. AR9271 
   

        

[/TD]
[/TR]
[/TABLE]

---

### Post by chili555 on 2013-08-25
Please give us some additional diagnostics. From a terminal, please run and post:```
lsmod | grep ath
iwconfig
ifconfig
nm-tool
```Thanks.

EDIT: Please see: [http://www.ubuntugeek.com/how-to-fix-network-manager-applet-missing-from-notification-area-in-ubuntu-10-04.html](http://www.ubuntugeek.com/how-to-fix-network-manager-applet-missing-from-notification-area-in-ubuntu-10-04.html)

---

### Post by haris2 on 2013-08-26
Thank you for the answer here are the commands from terminal:
```
haris@ubuntu:~$ lsmod | grep ath
ath9k_htc              43359  0 
mac80211              245169  1 ath9k_htc
ath9k_common            2551  1 ath9k_htc
ath9k_hw              284128  2 ath9k_htc,ath9k_common
ath                    13543  2 ath9k_htc,ath9k_hw
cfg80211              150094  3 ath9k_htc,mac80211,ath
compat                  7267  3 ath9k_htc,mac80211,cfg80211
compat_firmware_class     6200  1 ath9k_htc
led_class               2864  2 ath9k_htc,compat
haris@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

haris@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0c:29:42:5e:7f  
          inet addr:192.168.68.129  Bcast:192.168.68.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe42:5e7f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:142 errors:0 dropped:0 overruns:0 frame:0
          TX packets:153 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26230 (26.2 KB)  TX bytes:22995 (22.9 KB)
          Interrupt:19 Base address:0x2024 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

haris@ubuntu:~$ nm-tool
- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            vmxnet
  State:             disconnected
  Default:           no
  HW Address:        00:0C:29:42:5E:7F

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on


haris@ubuntu:~$ 


```

---

### Post by chili555 on 2013-08-27
> Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            [COLOR="#FF0000"]vmxnet[/COLOR]Is this a virtual machine? Wireless is handled very differently in a virtual environment: [http://askubuntu.com/questions/178804/wireless-network-in-virtualbox](http://askubuntu.com/questions/178804/wireless-network-in-virtualbox)> All "virtual" connections are in reference to cable/wired connected ones. So when you enable a Network card in your virtual guest, it is a virtual wired connection you are creating not a virtual wireless one.Please clarify.

---

### Post by haris2 on 2013-08-27
Hi thanks for the answer,yes you are right when i tested that it was mounted on virtual machine reason why i have the Ubuntu 10.04 on my other computer so i just wanted to do a little test to see is it going to list wireless devices and show my adapter when i do it on my computer ,i was doing that since it always failed on my other computer which has ubuntu 10.04 i didn't knew the diffrence between connections,anyhow and  update on situation i somehow reseted the icon,and manage to get the device working but everytime when i turn off computer it stop working and then i need to go to system/i think it's then administration/hardware and devices and deactivate and activate the driver again if i want that adapter works,any solution with that?

---

### Post by chili555 on 2013-08-27
You might try adding the driver to the list of drivers that load automatically:```
sudo -i
echo ath9k_htc >> /etc/modules
exit
```

---

### Post by haris2 on 2013-08-27
Do i need to run this in terminal,or go to some script and put this code ?thanks

---

### Post by chili555 on 2013-08-27
> **haris2 said:**
> Do i need to run this in terminal,or go to some script and put this code ?thanksIn the terminal.

---

### Post by haris2 on 2013-08-29
It all works thank you ;)

---

### Post by chili555 on 2013-08-29
> **haris2 said:**
> It all works thank you ;)Glad it's working! Please mark the thread Solved: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

