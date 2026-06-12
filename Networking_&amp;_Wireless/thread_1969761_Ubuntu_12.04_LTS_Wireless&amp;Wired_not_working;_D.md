---
title: "Ubuntu 12.04 LTS Wireless&amp;Wired not working; Driver fails to install."
date: 2012-04-30
forum: Networking &amp; Wireless
---

### Post by Maverick Mungbean on 2012-04-30
Hi all, 

I just installed Ubuntu 12.04 on my laptop through update manager. It´s done now, but my Wireless connection doesn´t work, (it shows up though, you can edit it.) I tried looking for a solution on my laptop by plugging in the ethernet cable, but that doesn´t seem to work either. I´ve got a hunch about that but I really need help with the Wireless! Driver is deactivated, but activating it does NOT work..

Please respond, thanks.

---

### Post by Maverick Mungbean on 2012-04-30
anyone?... Sorry for being impatient, but I really need help a.s.a.p. :(

Using a Lenovo g550 by the way.

---

### Post by chili555 on 2012-04-30
May we see some details? Please open a terminal and run and post:```
rfkill list all
lspci -nn | grep 0280
```Thanks.

---

### Post by Maverick Mungbean on 2012-04-30
> **chili555 said:**
> May we see some details? Please open a terminal and run and post:```
rfkill list all
lspci -nn | grep 0280
```Thanks.

Uh, the Wireless is somehow working now, still no luck with the driver though. Entered the commands after it started working though.

The output of the commands are as follows:

```
rfkill list all

```
output
```
0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```


```
 lspci -nn | grep 0280

```
output

```
04:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

```

thanks for your help.

---

### Post by chili555 on 2012-04-30
With the ethernet cable attached, please do:```
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```Now is it working?

---

### Post by Maverick Mungbean on 2012-04-30
> **chili555 said:**
> With the ethernet cable attached, please do:```
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```Now is it working?

It is. You are a saint, thanks so much! :)

---

### Post by chili555 on 2012-04-30
My ex-wife's lawyer would disagree! Would you please use thread tools at the top to Mark Solved so that the searchers can find the solution?

-----------

**Note to searchers**: This is for pci.id 14e4:4315 only. If that's not your pci.id, please keep searching.

---

### Post by Maverick Mungbean on 2012-04-30
Done and done.

---

