---
title: "Wireless"
date: 2011-07-26
forum: Networking &amp; Wireless
---

### Post by Harley36 on 2011-07-26
I am new to wireless using Ubuntu,but have never gotten it to work in any version up to an including 11.04 I can see the networks and it says I am connected but I can not get on the internet. I have an older laptop (Dell Inspiron 9300) with an Intel Pro/Wireless 2915 ABG. Every thing I read says the Linux driver is in the kernel. The driver being used is ipw 2200. Can someone help me? I also don't know how to change the driver. My computer dual boots with Win. XP and has no problem with wireless when using Windows
John Payne

---

### Post by lkjoel on 2011-07-26
> **Harley36 said:**
> I am new to wireless using Ubuntu,but have never gotten it to work in any version up to an including 11.04 I can see the networks and it says I am connected but I can not get on the internet. I have an older laptop (Dell Inspiron 9300) with an Intel Pro/Wireless 2915 ABG. Every thing I read says the Linux driver is in the kernel. The driver being used is ipw 2200. Can someone help me? I also don't know how to change the driver. My computer dual boots with Win. XP and has no problem with wireless when using Windows
John Payne
Could you give me the output of these Terminal commands?
```
uname -a
```
```
lsb_release -a
```
```
nm-tool
```
```
ifconfig
```
```
lspci | grep Ethernet
```

---

### Post by Harley36 on 2011-07-26
john@johnsbiglaptop:~$ uname -a

Linux johnsbiglaptop 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:09:46 UTC 2011 i686 GNU/Linux

john@johnsbiglaptop:~$ lsb_release -a

No LSB modules are available.

Distributor ID:	Ubuntu

Description:	Ubuntu 10.04.3 LTS

Release:	10.04

Codename:	lucid

john@johnsbiglaptop:~$ nm-tool



NetworkManager Tool



State: connected



- Device: eth0  [Auto eth0] ----------------------------------------------------

  Type:              Wired

  Driver:            b44

  State:             connected

  Default:           yes

  HW Address:        00:12:3F:CF:75:E2



  Capabilities:

    Carrier Detect:  yes

    Speed:           100 Mb/s



  Wired Properties

    Carrier:         on



  IPv4 Settings:

    Address:         192.168.1.101

    Prefix:          24 (255.255.255.0)

    Gateway:         192.168.1.1



    DNS:             192.168.1.1

    DNS:             68.87.85.102

    DNS:             68.87.69.150





- Device: eth1 -----------------------------------------------------------------

  Type:              802.11 WiFi

  Driver:            ipw2200

  State:             unavailable

  Default:           no

  HW Address:        00:12:F0:5D:09:5A



  Capabilities:



  Wireless Properties

    WEP Encryption:  yes

    WPA Encryption:  yes

    WPA2 Encryption: yes



  Wireless Access Points 





john@johnsbiglaptop:~$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:12:3f:cf:75:e2  

          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0

          inet6 addr: fe80::212:3fff:fecf:75e2/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:44581 errors:0 dropped:0 overruns:0 frame:0

          TX packets:28790 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:26556859 (26.5 MB)  TX bytes:4640078 (4.6 MB)

          I
Sorry to take so long to get back--- I had to leave for a while.
I hope the above will answer your questions. I ran each command then copied. Thanks for your help

---

### Post by lkjoel on 2011-07-26
Do you know the company and model of the Wireless Card?

---

### Post by Harley36 on 2011-07-26
Yes, it is Intel Pro/Wireless 2915ABG. Not sure but I think it is followed by net.

---

### Post by lkjoel on 2011-07-26
According to here: [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel), it seems that it should be working out of the box...

Try downloading the attachment into your home folder, open up a Terminal window and type in it:
```
cd ~
chmod +x wireless.sh
./wireless.sh eth1 *YOURNETWORKNAME*
```

---

### Post by Harley36 on 2011-07-26
Still no go! Very frustrating! Thanks for all of your help! Looks like Windows when I want to go wireless. ECK, I am trying to get away from Windows and totally to Ubuntu.

---

### Post by lkjoel on 2011-07-26
Try entering an Ubuntu LiveCD into your disk tray, reboot, and then check if it recognizes your wireless card.

---

### Post by Harley36 on 2011-07-26
I have not tried that yet, but what I have found is all of the wireless networks I have added and tried get the IP from Comcast. only one will get it from my router and it will not allow any security. Enough for tonight. I will work with it in the AM.

---

