---
title: "Connecting to wireless network trouble"
date: 2009-06-20
forum: Networking &amp; Wireless
---

### Post by mikestanton45 on 2009-06-20
(i'm completely new to ubuntu)
 
I'm just lost in general, i don;t know how to connect to my router on my laptop in ubuntu. I can connect and such when i use windows xp, but when i boot in linux it just doesnt seem to work. when i go the the little network buttion thingy ( i dont know what its called, new to linux) wired network and wireless netowrk are both greyed out, i tryed connecting to hidden networks, put my sid in, set it up blah blah blah, nothing worked, when i go to system>administration>Hardware drivers, there are no drivers installed and i have no idea how to find out what my wireless card is.
 
Any help anyone could give me would be awsome, linux looks like a great os but with wireless internet, i'd rather stick with xp =/

---

### Post by roger_1960 on 2009-06-20
Hi

Might not be this simple, but have you right clicked on the "little network button thingy" and checked the Enable wireless box?

---

### Post by mikestanton45 on 2009-06-20
> **roger_1960 said:**
> Hi
 
Might not be this simple, but have you right clicked on the "little network button thingy" and checked the Enable wireless box?
 yes.  it didn't work

---

### Post by Idefix82 on 2009-06-20
Ok, go to Applications->Accessories->Terminal,
now type into the terminal window (hitting enter between the two lines)
```
lshw -C network
ifconfig

```
copy the output and paste it here. I'm sure we will be able to sort you out.

---

### Post by mikestanton45 on 2009-06-20
ok give me a min

---

### Post by mikestanton45 on 2009-06-20
> **Idefix82 said:**
> Ok, go to Applications->Accessories->Terminal,
now type into the terminal window (hitting enter between the two lines)
```
lshw -C network
ifconfig

```
copy the output and paste it here. I'm sure we will be able to sort you out.
 
 
  *-network               
       description: Ethernet interface
       product: NetLink BCM5789 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: [EMAIL="pci@0000:02:00.0"]pci@0000:02:00.0[/EMAIL]
       logical name: eth0
       version: 21
       serial: 00:03:25:31:40:e8
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 firmware=5789-v3.49a latency=0 module=tg3 multicast=yes
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: [EMAIL="pci@0000:03:09.0"]pci@0000:03:09.0[/EMAIL]
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:4a:64:c9
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 96:d9:6c:67:b1:b9
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
[EMAIL="mike@itachi:~$"]mike@itachi:~$[/EMAIL] ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:25:31:40:e8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)
  is what i got

---

### Post by Ayuthia on 2009-06-20
You have a Broadcom 4318 card.  You will need to install b43-fwcutter to get the module to work.  You can do this through Synaptic or you can go into the Terminal:
```
sudo apt-get update
sudo apt-get install b43-fwcutter
```

---

### Post by mikestanton45 on 2009-06-20
> **Ayuthia said:**
> You have a Broadcom 4318 card. You will need to install b43-fwcutter to get the module to work. You can do this through Synaptic or you can go into the Terminal:
```
sudo apt-get update
sudo apt-get install b43-fwcutter
```
 
didnt work this is what i got back
 
 
 [EMAIL="mike@itachi:~$"]mike@itachi:~$[/EMAIL] sudo apt-get update
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
  Could not resolve 'security.ubuntu.com'
Reading package lists... Done
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg)  Could not resolve 'security.ubuntu.com'
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'
W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
[EMAIL="mike@itachi:~$"]mike@itachi:~$[/EMAIL] sudo apt-get install b43-fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package b43-fwcutter

---

### Post by Idefix82 on 2009-06-20
Yeah, that's because your wired internet connection doesn't seem to work either, which is strange because the card NetLink BCM5789 should be supported out of the box. I don't have experience with this card, maybe somebody else can explain, what's going wrong with that.

---

### Post by Ayuthia on 2009-06-20
Can you try the following from the Terminal:
```
sudo modprobe -r b43 ssb tg3
sudo modprobe tg3
sudo ifconfig eth1 up
sudo dhclient eth1
```Hopefully that will get your wired card running.  If it does, please try to see if you can install b43-fwcutter again.

---

### Post by Idefix82 on 2009-06-20
Ayuthia, I'm curious. The driver tg3 is already in control of the card (see his output from lshw -C network). So what are the first two lines for?

---

### Post by Ayuthia on 2009-06-20
> **Idefix82 said:**
> Ayuthia, I'm curious. The driver tg3 is already in control of the card (see his output from lshw -C network). So what are the first two lines for?
Sorry.  I just wanted to disable the wireless card drivers (b43 and ssb) first in case it is interfering with the wired card.  I have seen instances when the wireless card firmware is installed, the wired works fine.  I am hoping that if we just disable the wireless, the wired will kick in.

If that doesn't work, you can try this guide and it will help you get the firmware installed for your wireless card:
[http://ubuntuforums.org/showpost.php?p=6077792&postcount=72](http://ubuntuforums.org/showpost.php?p=6077792&postcount=72)

---

