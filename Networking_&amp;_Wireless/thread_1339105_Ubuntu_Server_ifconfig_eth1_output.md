---
title: "Ubuntu Server ifconfig eth1 output"
date: 2009-11-27
forum: Networking &amp; Wireless
---

### Post by chrislynch8 on 2009-11-27
Hi,

I issue **ifconfig eth1** in the RX line I have the following

**RX packets:1601164 error:0 dropped:0 overruns:0 frame:230971**

I have read that the frame count indicate that the packets received have an invalid CRC or the device may be about to malfunction. 

Could it also indicate that another device on the network is causing the issue?

What type of commands can I type to see where the packets are coming from etc...

Rgds
Chris

---

### Post by iponeverything on 2009-11-27
```
sudo apt-get install tcpdump
```

then do:

```
sudo tcpdump -n -i eth1
```

If you ssh'ed in you can exclude your own traffic with:

```
sudo tcpdump -n -i eth1 not port 22
```

And say you also want to exclude ip address 123.123.1.1

```
sudo tcpdump -n -i eth1 not port 22 and not host 123.123.1.1
```

I think you get the idea..

---

### Post by chrislynch8 on 2009-11-27
Thanks,

I'll do it on site Monday - will this affect network traffic from the users and will it tell my if packets are curropt??????

Thanks again for the help

Rgds
Chris

---

### Post by iponeverything on 2009-11-27
> **chrislynch8 said:**
> Thanks,

I'll do it on site Monday - will this affect network traffic from the users and will it tell my if packets are curropt??????

Thanks again for the help

Rgds
Chris

tcpdump is passive, but for trying to find the where the frame issues are coming from, I would go from switch to switch and look for interface errors - try to track it down that way.

---

### Post by Yoann Juet on 2009-11-28
> **chrislynch8 said:**
> I have read that the frame count indicate that the packets received have an invalid CRC or the device may be about to malfunction. 

Another tip. If the FCS, CRC (...) increments, check for a duplex mismatch. For instance, your computer operates at full-duplex while the switch interface operates at half-duplex.

On your computer, use mii-tool or ethtool to check for speed and duplex negotiation.

---

