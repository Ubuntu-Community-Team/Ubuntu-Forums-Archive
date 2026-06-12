---
title: "WLAN Wireless switch no on after maintenance"
date: 2012-05-28
forum: Networking &amp; Wireless
---

### Post by jmperkins on 2012-05-28
I noticed yesterday starting up my Sony Vaio Laptop at the coffee shop running windows XP a RADICAL CHANGE/PROBLEM:

I have a physical hardware switch in the front of my laptop that when in ON position tells my software to enable wireless.

When I power on my laptop after booting EVERY TIME the light on my _switch does not light up (It always has before)_. If I plufg an ethernet cable into my laptop, the switch will light up and everything wireless is FINE until I power up again without ethernet but wireless enabled.

I am not aware of ANY change in my config and can only assume it was some maintenance that I put on from UBUNTU the day before on May 26 (2012).

Release 12.04 32 bit Linux 3.2.0-25-generic GNOME 3.4.1
Wireless/ethernet card : Intel Corporation PRO/Wireless 4965 AG or AGN

CAN anyone tell me what is going on here? PLEASE answer soon as I have to travel tomorrow and need wireless at the airports!

Thanks!
Joe:(

---

### Post by chili555 on 2012-05-28
Please open a terminal and run and post:```
rfkill list all
```Thanks.

---

### Post by jmperkins on 2012-05-29
This is the output after I plugged in the network ethernet to jump start the wireless:

rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

---

### Post by chili555 on 2012-05-29
> **jmperkins said:**
> This is the output after I plugged in the network ethernet to jump start the wireless:

rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: noSo we see nothing wrong because it's working fine. Would you mind if we examine the diagnostics ***before*** you fix it?

---

### Post by jmperkins on 2012-05-30
Yes, sorry, as I will re-issue after fresh boot tonight where WLAN hardware switch light is not ON but should be. 
 
Stay tuned please.

---

### Post by jmperkins on 2012-05-31
powered off, fresh boot, no hardware switch light on for WLAN (should be on.

issue command:
rfkill list all
0: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no


Bottom line: same output as when working. PLEASE FIX-I know that maint a couple of days ago HAS to be the culprit

---

### Post by chili555 on 2012-05-31
Let's see if the wireless driver loaded as expected. Maybe that's the culprit. After a fresh boot where the wireless is not working, run: ```
lsmod | grep iwl
```Is the driver iwl4965 loaded? If not, do:```
sudo modprobe iwl4965
```Did the wireless start? If so, we simply need to tell the driver to load on boot:```
sudo su
echo iwl4965 >> /etc/modules
exit
```If that doesn't fix it, post back and we'll dig deeper.

---

### Post by jmperkins on 2012-06-01
Thanks for sticking with me! I'll do the homework assignment tonight when I get home from work and post it here! Take good care, Joe.
):P

---

