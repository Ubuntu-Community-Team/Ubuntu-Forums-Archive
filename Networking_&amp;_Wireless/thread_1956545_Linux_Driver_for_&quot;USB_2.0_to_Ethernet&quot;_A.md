---
title: "Linux Driver for &quot;USB 2.0 to Ethernet&quot; Adaptor?"
date: 2012-04-11
forum: Networking &amp; Wireless
---

### Post by novicee on 2012-04-11
**I have bought a ST Lab "USB 2.0 to Ethernet" adaptor (P/N: USB 2.0-LAN100-1). The disk that came with it appears to have a driver only for Windows. I need a driver for Linux (specifically Ubuntu 11.10).**
[B]
I looked on the ST Lab web site but was unable to find a Linux driver for this product. I also tried several times to contact ST Lab support via the website but have received no reply.

It would be appreciated if anyone could tell me if there is a Linux driver for this product?           [/B] 
  
  [B][FONT=&quot]
[/FONT][/B]
    
  [B][FONT=&quot]
[/FONT][/B]

---

### Post by roelforg on 2012-04-11
> **novicee said:**
> **I have bought a ST Lab "USB 2.0 to Ethernet" adaptor (P/N: USB 2.0-LAN100-1). The disk that came with it appears to have a driver only for Windows. I need a driver for Linux (specifically Ubuntu 11.10).**
 
**I looked on the ST Lab web site but was unable to find a Linux driver for this product. I also tried several times to contact ST Lab support via the website but have received no reply.**
 
**It would be appreciated if anyone could tell me if there is a Linux driver for this product? **
 

 
 


 
You may wanna use the "unbold" button on the editor.
 
Anyways...
Plug it in,
Run:
```

sudo lsusb
sudo lspci
sudo lshw -C network
sudo ifconfig -a
sudo cat /etc/network/interfaces

```
 
Some can take a long time,
the 3rd one may appear to be stuck at "PCI (SYSFS)", but it just takes a long time to scan so just let it run until your prompt reappears.

---

### Post by novicee on 2012-04-11
[FONT=Arial][SIZE=3]Roelforg[/SIZE][/FONT],

[FONT=Arial][SIZE=3]Thanks for your reply. I will try the code in your post.

Comment on bolding - noted.

- Novice [/SIZE][/FONT]

---

