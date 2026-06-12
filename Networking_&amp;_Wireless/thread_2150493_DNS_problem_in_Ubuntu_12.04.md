---
title: "DNS problem in Ubuntu 12.04"
date: 2013-06-01
forum: Networking &amp; Wireless
---

### Post by paulemony on 2013-06-01
Have changed ISP & router, internet worked OK on previous router but now won't connect either wirelessly or ethernet. I can ping google by IP address but not by name. Tried Open DNS but no change. Networking not my forte, appreciate any suggestions, thx

---

### Post by chili555 on 2013-06-01
What does this tell us, from the terminal?```
nm-tool
route -n
traceroute google.com
```

---

### Post by paulemony on 2013-06-01
```
~$ nm-tool

NetworkManager Tool 


State: connected (global) 


- Device: wlan0  [SKY567EF]---------------------------------------------------- 
  Type:              802.11 WiFi 
  Driver:            rt2800usb 
  State:             connected 
  Default:           yes 
  HW Address:        80:1F:02:3A:B4:C3 


  Capabilities: 
    Speed:           57 Mb/s 


  Wireless Properties 
    WEP Encryption:  yes 
    WPA Encryption:  yes 
    WPA2 Encryption: yes 


  Wireless Access Points (* = currentAP) 
    *SKY567EF:       Infra,7C:4C:A5:65:7C:01, Freq 2412 MHz, Rate 54 Mb/s, Strength 65 WPA2 
    BTHomeHub2-N6HR: Infra,00:23:4E:9D:E9:44, Freq 2457 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2 
    SKY4E31E:        Infra,7C:4C:A5:28:12:6D, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA2 
    SKY28250:        Infra,00:1F:33:17:74:57, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WPA 


  IPv4 Settings: 
    Address:         192.168.0.7 
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1 


    DNS:             192.168.0.1 




- Device: eth0----------------------------------------------------------------- 
  Type:              Wired 
  Driver:            skge 
  State:             disconnected 
  Default:           no 
  HW Address:        00:11:D8:22:17:40 


  Capabilities: 
    Carrier Detect:  yes 


  Wired Properties 
Carrier:         on  
```

```
:~$ route -nKernel IP routing table 
Destination     Gateway         Genmask        Flags Metric Ref    Use Iface 
0.0.0.0         192.168.0.1     0.0.0.0        UG    0      0        0 wlan0 
169.254.0.0     0.0.0.0        255.255.0.0     U     1000   0        0 wlan0 
192.168.0.0     0.0.0.0        255.255.255.0   U     2      0        0 wlan0  
```


Catch-22: traceroute not installed

---

### Post by steeldriver on 2013-06-01
You can use tracepath or mtr in place of traceroute - however if you can ping by IP but not by name the first tool I would reach for is 'dig'

```
dig google.com
```

You can also check that the resolvconf service is running and that the symlink got created correctly:

```

service resolvconf status

ls -l /etc/resolv.conf

```

I'd also check whether nm is configured to use dnsmasq:

```
grep dns /etc/NetworkManager/NetworkManager.conf
```

---

### Post by paulemony on 2013-06-01
Downloaded deb via another pc:

```
:~$ traceroute google.comgoogle.com: Name or service not known 
Cannot handle "host" cmdlinearg `google.com' on position 1 (argc 1)  
```

```
~$ dig google.com; <<>> DiG 9.8.1-P1 <<>>google.com 
;; global options: +cmd 
;; connection timed out; no serverscould be reached
 

:~$ ls -l/etc/resolv.conf 
-rw-r--r-- 1 root root 77 Apr  5 15:58/etc/resolv.conf

:~$ grep dns/etc/NetworkManager/NetworkManager.conf
dns=dnsmasq  
```

---

### Post by steeldriver on 2013-06-01
What about the 'service resolvconf status'? Did you remove resolvconf or manually configure /etc/resolv.conf at some point?

The standard desktop installation of 12.04 should use the resolvconf service and /etc/resolv.conf should be a symlink to a dynamically created file in /run i.e.

```
$ service resolvconf status
resolvconf start/running

$ ls -l /etc/resolv.conf 
lrwxrwxrwx 1 root root 29 Jun  1 10:51 /etc/resolv.conf -> ../run/resolvconf/resolv.conf

```

We could just go ahead and reconfigure the resolvconf package but I'd like to understand what you did before suggesting that

---

### Post by paulemony on 2013-06-01
I did try a few trial & error entries gleaned from google but don't recall anything concerned with resolvconf.

```
:~$ service resolvconf statusresolvconf start/running 


:~$ ls -l /etc/resolv.conf 
-rw-r--r-- 1 root root 77 Apr  5 15:58/etc/resolv.conf  
```

---

### Post by steeldriver on 2013-06-01
I think at this point I would just go ahead and reconfigure resolvconf - you could make a backup of the current /etc/resolv.conf file first but (a) it doesn't seem to be working as-is and (b) I think the reconfigure will automatically save a copy as /etc/resolvconf/resolv.conf.d/original anyway

```
sudo dpkg-reconfigure resolvconf
```

It should pop up a terminal based configuration GUI - use the tab and enter keys to choose the answers, I'd suggest answering 'Yes' to the "Prepare /etc/resolv.conf for dynamic updates?" question and 'No' to the one about temporarily appending your existing config to the dynamic one. Then reboot.

---

### Post by paulemony on 2013-06-01
Yep, that's all it needed, answer was very simple (when you know how!)

Many thx.

---

### Post by steeldriver on 2013-06-01
You're welcome - glad we could fix it

---

### Post by IndiGenus on 2013-06-11
> **steeldriver said:**
> I think at this point I would just go ahead and reconfigure resolvconf - you could make a backup of the current /etc/resolv.conf file first but (a) it doesn't seem to be working as-is and (b) I think the reconfigure will automatically save a copy as /etc/resolvconf/resolv.conf.d/original anyway

```
sudo dpkg-reconfigure resolvconf
```

It should pop up a terminal based configuration GUI - use the tab and enter keys to choose the answers, I'd suggest answering 'Yes' to the "Prepare /etc/resolv.conf for dynamic updates?" question and 'No' to the one about temporarily appending your existing config to the dynamic one. Then reboot.

Wow thank you, thank you, thank you!!!!

I'm a Windows tech who's trying to get more familiar with Linux and looking to do some Android ROM stuff so I just installed a fresh copy of 12.04 on a laptop. Was really surprised when I connected to my home network and fired up Firefox and got nada. Quickly realized it was a DNS issue so figured that's got to be an easy fix. I played around with using the Google and Open DNS servers with no luck. Spent several hours researching and looking through forum posts, trying several things, changing config files, etc... with no luck. Was about to give up and try re-installing it then I found this post and bam all fixed. A simple...
 ```
sudo dpkg-reconfigure resolvconf
```
then restart the network manager...
```
sudo restart network-manager
```
...and can now browse. Much thanks again for the help.
David

---

