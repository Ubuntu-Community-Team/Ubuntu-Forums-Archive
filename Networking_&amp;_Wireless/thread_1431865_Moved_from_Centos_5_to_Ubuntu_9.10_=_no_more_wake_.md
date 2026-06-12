---
title: "Moved from Centos 5 to Ubuntu 9.10 = no more wake up on lan"
date: 2010-03-17
forum: Networking &amp; Wireless
---

### Post by oduesp on 2010-03-17
Hello,

I've re-installed my box with a fresh ubuntu 9.10 (64bits) and since  I've lost the ability to wake it up from lan (magic packet method). It  was working flawlessly when centos 5 was installed, so it is not a BIOS  or NIC problem.
It must have something to do with how ubuntu shut down the computer but I dont know what to change (I shut it down from gnome like normal people do, by clicking on the turn off icon).
 Please Help.
  
  root@desktop:~# lspci  | grep -i ethernet
  04:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5754  Gigabit Ethernet PCI Express (rev 02)
  
  root@desktop:~# ethtool eth0
  Settings for eth0:
      Supported ports: [ TP ]
      Supported link modes:   10baseT/Half 10baseT/Full 
                              100baseT/Half 100baseT/Full 
                              1000baseT/Half 1000baseT/Full 
      Supports auto-negotiation: Yes
      Advertised link modes:  10baseT/Half 10baseT/Full 
                              100baseT/Half 100baseT/Full 
                              1000baseT/Half 1000baseT/Full 
      Advertised auto-negotiation: Yes
      Speed: 100Mb/s
      Duplex: Full
      Port: Twisted Pair
      PHYAD: 1
      Transceiver: internal
      Auto-negotiation: on
      Supports Wake-on: g
      Wake-on: g
      Current message level: 0x000000ff (255)
      Link detected: yes
  
  root@desktop:~# cat /sys/class/net/eth0/device/power/wakeup
  enabled

---

### Post by oduesp on 2010-03-18
Bump please help. Ubuntu's gurus must be here... Why if I install another linux's flavor wol stops working. ?

---

### Post by oduesp on 2010-03-19
bump. please tell me at least where to search ?

---

### Post by 2hot6ft2 on 2010-03-19
Maybe this will help
[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8187623](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8187623)

---

### Post by oduesp on 2010-03-24
OK no luck so far. Here are more info on the system and what I've tried.
I will bump this thread until someone help me to fix this ;)

Sys info:
Ubuntu 9.10 x64
Linux desktop 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 04:38:19 UTC 2010 x86_64 GNU/Linux

root@desktop:~# lspci -tv
-[0000:00]-+-00.0  Intel Corporation 82975X Memory Controller Hub
           +-01.0-[0000:01]----00.0  nVidia Corporation NV44 [Quadro NVS 285]
           +-1b.0  Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller
           +-1c.0-[0000:02]--
           +-1c.4-[0000:03]--
           +-1c.5-[0000:04]----00.0  Broadcom Corporation NetXtreme BCM5754 Gigabit Ethernet PCI Express
           +-1d.0  Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1
           +-1d.1  Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2
           +-1d.2  Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3
           +-1d.3  Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4
           +-1d.7  Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller
           +-1e.0-[0000:05]--
           +-1f.0  Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge
           +-1f.1  Intel Corporation 82801G (ICH7 Family) IDE Controller
           +-1f.2  Intel Corporation 82801GR/GH (ICH7 Family) SATA AHCI Controller
           \-1f.3  Intel Corporation 82801G (ICH7 Family) SMBus Controller


root@desktop:~# acpitool -w
   Device    S-state      Status   Sysfs node
  ---------------------------------------
  1. VBTN      S4    *enabled   
  2. PCI0      S5     enabled   no-bus:pci0000:00
  3. PCI4      S5     enabled   pci:0000:00:1e.0
  4. PCI2      S5     enabled   pci:0000:00:1c.0
  5. PCI3      S5     enabled   
  6. PCI1      S5     enabled   pci:0000:00:01.0
  7. PCI5      S5     enabled   pci:0000:00:1c.4
  8. PCI6      S5     enabled   pci:0000:00:1c.5
  9. USB0      S3     disabled  pci:0000:00:1d.0
  10. USB1      S3     disabled  pci:0000:00:1d.1
  11. USB2      S3     disabled  pci:0000:00:1d.2
  12. USB3      S3     disabled  pci:0000:00:1d.3

root@desktop:~# ethtool -i eth0
driver: tg3
version: 3.99
firmware-version: 5754-v3.13
bus-info: 0000:04:00.0

root@desktop:~# ethtool eth0
Settings for eth0:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: Twisted Pair
    PHYAD: 1
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: g
    Wake-on: g
    Current message level: 0x000000ff (255)
    Link detected: yes

root@desktop:~# grep NETDOWN /etc/init.d/halt 
NETDOWN=no
    if [ "$NETDOWN" = "no" ]; then

root@desktop:~# cat /sys/devices/pci0000\:00/0000\:00\:1c.5/power/wakeup 
enabled


When the system is down the light on the NIC is solid. And, even more frustrating, when I launch a magic packet on the network to wake it up, it start blinking...like "oh this magic packet is for me but... ubuntu told me to stay sleepy".....

I've set up a test system with the 9.10 i386 and e1000's based NIC. And WoL IS functioning. So now I suspect a bug in the tg3's driver that canonical choose to put in their kernel.

---

### Post by tgalati4 on 2010-03-24
Search acpitool.  You need to keep a portion of the pci bus awake so that the network card can wake the rest of the system.

---

### Post by oduesp on 2010-03-24
> **tgalati4 said:**
> Search acpitool.  You need to keep a portion of the pci bus awake so that the network card can wake the rest of the system.

please read thread before posting, there IS a acpitool's result posted.
Dont want to be rude, but please stop with your generic answer and try to be more specific.

---

### Post by tgalati4 on 2010-03-25
Sorry, l'm using a nokia n800 and I missed part of your post.  Does Centos have a live cd boot feature?  If so, boot into Centos and see what driver gets loaded.

Also, on my poweredge server with a similar broadcom card, I have all of my S5 pci slots disabled except the actual slot that controls the ethernet card.  I don't know if that would make a difference.  Plus, my wake-on-lan script sends 3 wake pings with 2 second delays between each.  Don't know why, but a single ping doesn't work--unlike Red October.

---

### Post by oduesp on 2010-03-26
> **tgalati4 said:**
> Sorry, l'm using a nokia n800 and I missed part of your post.  Does Centos have a live cd boot feature?  If so, boot into Centos and see what driver gets loaded.

Also, on my poweredge server with a similar broadcom card, I have all of my S5 pci slots disabled except the actual slot that controls the ethernet card.  I don't know if that would make a difference.  Plus, my wake-on-lan script sends 3 wake pings with 2 second delays between each.  Don't know why, but a single ping doesn't work--unlike Red October.

Thanks for your reply, appreciated. I'm building a new vanilla kernel (2.6.33.1) and will post result here. I will also try a centos live cd to see which module is loaded, good idea.

I cant understand why ubuntu is behind other linux distribution on this.

---

### Post by tgalati4 on 2010-03-26
Red Hat, which Centos is based on, has been around a long time, and many server/enterprise issues (like wake-on-lan) have been solved.  Ubuntu, being based on Debian, has a different heritage, more organic, more community implemented than the corporate-leaning Red Hat.  So Ubuntu is actually ahead of Red Hat in many areas that community members (individual users) care about--creative hardware support, music/video production, laptop and netbook features, foreign language support, and social networking integration.

Most people ultimately choose a linux distro that works best with their hardware.

---

### Post by oduesp on 2010-04-13
Prob Solved with info over there:
[http://www.htgi.ca/DellPoweEdge1750-Debian-WOL](http://www.htgi.ca/DellPoweEdge1750-Debian-WOL)

---

