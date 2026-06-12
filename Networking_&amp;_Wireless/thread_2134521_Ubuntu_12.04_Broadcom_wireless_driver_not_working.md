---
title: "Ubuntu 12.04 Broadcom wireless driver not working"
date: 2013-04-11
forum: Networking &amp; Wireless
---

### Post by Marshmellow on 2013-04-11
I downloaded Ubuntu 12.04 a while ago on my desktop, and I have never had any other Linux distributions on it before either.
My motherboard is a ASUS P8Z77-V DELUXE, Socket-1155, and upon typing the ```
[COLOR=#000000][FONT=Ubuntu Mono]lspci -nn | grep 0280[/FONT][/COLOR]
``` I am presented with "Broadcom Corporation BCM43228 802.11a/b/g/n [14e4:4359]"

In 'Additional Drivers' the only driver shown is 'Broadcom STA wireless driver', and among the list of hardware it is for use with, BCM43228 IS listed, but activating it only gives me the error message "Sorry, installation of this driver failed." and points me to the jockey log, which is very long and I will not include it unless necessary.

Is it possible to get the Broadcom driver working to give me a wireless connection, or is it simply not compatible? If it is, how?

---

### Post by Hadaka on 2013-04-11
Hi, providing you have not attempted to
load any other drivers, the sta driver should
work with your card.
Please connect to a wired connection then COPY
and paste the following into a terminal...

```
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
 
```
thanks.

---

