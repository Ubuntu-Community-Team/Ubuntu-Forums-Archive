---
title: "IPv6, IRC Connection problems, and more?"
date: 2011-04-20
forum: Networking &amp; Wireless
---

### Post by flametai1 on 2011-04-20
Hi to everyone, I've been having some MAJOR problems. 

First off I originally had Linux Mint 10 installed, reformatted the hard drive, installed Ubuntu 10.10

Right off the back I've been having trouble with my internet. I was able to just install programs from Software Center, and updates. If I opened up FireFox and tried going to a website it wouldn't work. I tried pinging sites, Sent 5 packets, 0% worked. I found out that disabling IPv6 in FireFox allows me to access websites. Is this effecting all my other programs? If so how can I disable it for EVERYTHING? 

Also IRC will not connect to any IRC server via XChat

I'm not fully understanding why this is interfering with my internet when it worked fine on Linux Mint 10 which is based off of Ubuntu?

Has anyone else had these problems?

Anyone that can help me? It would be greatly appreciated!

---

### Post by wojox on 2011-04-20
Diable at boot. Do this in your terminal:

```
gksudo gedit /etc/default/grub
```

Look for **GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash”**

Change to **GRUB_CMDLINE_LINUX_DEFAULT=”ipv6.disable=1 quiet splash”**

Save it close it and run:

```
sudo update-grub
```

Reboot. :P

---

### Post by flametai1 on 2011-04-20
It's working never mind! =D Thank you a lot wojox!

---

