---
title: "Server 12.04 doesn't recognize any eth card"
date: 2013-02-22
forum: Networking &amp; Wireless
---

### Post by thvoicwethin on 2013-02-22
Hi all,

I'm having trouble with my Proliant ML570 G2 server. I have a D-Link Eth 1Gbps card installed as well as the integrated eth.

When installing ubuntu via CD, the CD does not recognize any of my ethernet cards. I've tried everything to look for them, and they don't show up at all.
lspci -C network doesn't show
grep doesn't show

only thing that does show is the standard 127.0.0.1 loopback. I'm trying a full format and re-install, but the CD doesn't even recognize they're there. 

The integrated eth port blinks green like it's getting packets, but ubuntu still doesn't see it.

Can anyone help?

---

### Post by sanderj on 2013-02-22
What's the output of

```
lspci | grep -i  net 

```
Here's mine:

```
sander@R540:~$ lspci | grep -i  net 
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
06:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller
sander@R540:~$ 
```

HTH

---

### Post by thvoicwethin on 2013-02-27
> **sanderj said:**
> What's the output of

```
lspci | grep -i  net 

```Here's mine:

```
sander@R540:~$ lspci | grep -i  net 
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
06:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller
sander@R540:~$ 
```HTH

Nothing shows up:
```
andrew@ubuntu:~$ lspci | grep -i net
andrew@ubuntu:~$ 
```

---

### Post by sanderj on 2013-02-27
Weird. Can you try:

```
sudo lshw | grep -i net
```

I expect it to be empty too, but try it just to be sure

The hardware is old, isn't it? Which Ubuntu version are you using?

What happens when you pull out the PCI ethernet card, and then boot again?

---

### Post by thvoicwethin on 2013-02-27
> **sanderj said:**
> Weird. Can you try:

```
sudo lshw | grep -i net
```I expect it to be empty too, but try it just to be sure

The hardware is old, isn't it? Which Ubuntu version are you using?

What happens when you pull out the PCI ethernet card, and then boot again?

Nothing again. The onboard ethernet is lighting up like its sending/receiving, but nothing is showing up in ubuntu. 

12.04 LTS Server 32-bit. D-Link DGE-530T. Currently have 2 installed in PCI slots. Had one before, and it's not responding, tried the other, it's not responding.

Put it in a workstation computer, it works fine. I don't get it. When I first installed Ubuntu 12.04 LTS on my server everything booted and worked fine, I had my access, but I had to re-install due to a failed drive, and now it's giving me all these complications. 

I can't sudo apt-get update or upgrade due to no internet, nor can I install a lightweight GUI just to peer my eyes from a black and white screen :p

---

### Post by sanderj on 2013-02-27
Then you could follow the path of trial-and-error:

live-boot:
Ubuntu 12.04.2
Ubuntu 12.04 64-bit
Ubuntu 12.10
OpenSuSE 12.2

... and see if ethernet pops up.

---

