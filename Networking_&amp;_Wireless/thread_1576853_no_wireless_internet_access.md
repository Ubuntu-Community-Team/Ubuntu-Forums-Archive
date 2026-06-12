---
title: "no wireless internet access"
date: 2010-09-17
forum: Networking &amp; Wireless
---

### Post by thenetminder33 on 2010-09-17
Hi i am extremely new to linux and am having lots of problems with my dual boot between ubuntu and win7. I cant connect to the internet with my wireless( or my lan for that matter, but i mainly want to use my wireless).
I am going to follow the ticket provided by one of the sticky threads [http://ubuntuforums.org/showthread.php?p=6183681]("http://ubuntuforums.org/showthread.php?p=6183681")

**1.Machine Brand and Model**
Actually i am using a computer i built myself using following components
AMD Phenom II x4 965 CPU
ASRock 890FX Mobo
Radeon HD 5770 Graphics

**2.Wireless Brand**
Ralink Technology, Corp.
AZIO AWU354

**3.Interface**
```

wlan0   IEEE 802.11bgn  ESSID: off/any
        Mode: Managed   Access Point: Not-Associated  Tx-Power=10 dBm
        Retry  long limit:7  RTS thr:off  Fragment thr:off
        Encryption Key:off
        Power Management:on
```

**4.Modules**
No wlan0 module was listed in printout

**5.Kernel Boot Messages**
```

[ 2611.467965] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

**6.Network Config**
```

*-network
   description: Wireless Interface
   physical id:1
   logical name:wlan0
   serial: c8:3a:35:c4:68:64
   capabilities: ethernet physical wireless
   configuration: broadcast=yes multicast=yes wireless= IEEE 802.11bgn
```

**7.Scan for networks**
```
wlan0   No scan results
```

**8.Ubuntu Version**
```
Ubuntu 10.04.1 LTS
```

**9.Kernel/Architechture**
```
2.632-24-generic x86_64
```

**10.Restart Network**
```
* Reconfiguring Network interfaces...          [ OK ] 
```

Also, going along with the other problems ive been having
System>Preferences>Network Connections  will not open

Thanks so much for any help

---

### Post by grahammechanical on 2010-09-18
I can not give the clever answers but what privileges do you have under Users and Groups. System>Administration. May be, somehow, you do not have the privilege of connecting to a network. Are you set up as Administrator or is it classed as Custom. Check your Advanced Settings.

Regards

---

### Post by thenetminder33 on 2010-09-18
Im pretty sure im an administrator as i have the only account on the computer,

However when i try to open users and groups i get this error message in a dialogue box

```
The configuration could not be loaded
An unknown error occured
```

---

### Post by thenetminder33 on 2010-09-18
running ubuntu from live CD in try mode:

I can get wired connection

No networks appear under wireless

Terminal scan returns no results

---

### Post by thenetminder33 on 2010-09-18
I reinstalled ubuntu from a new live cd and most of my problems were solved--except the wireless

I can now access network connections and other tools

I can also use wired LAN connections


However my wireless still does not see any networks

---

