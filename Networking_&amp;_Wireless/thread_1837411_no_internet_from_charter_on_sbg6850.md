---
title: "no internet from charter on sbg6850"
date: 2011-09-01
forum: Networking &amp; Wireless
---

### Post by karrank% on 2011-09-01
Just switched from ATT to Charter (faster) with a Motorola SBG6850 modem, No connectivity on (lucid 10.04.2)-- 

Networking enabled, but when I try to select the new network/enter the SSID, key, etc, dialog box won't let me apply the choice. 

Don't even know where to begin looking, can someone point me in the right direction? 

thanks for looking.

---

### Post by praseodym on 2011-09-01
Hi,

please show:

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
sudo iwlist scan
route -n
cat /etc/resolv.conf
```

---

### Post by sidzen on 2011-09-01
Not to detract from you, praseodym . . .

Go here ([http://www.motorola.com/Consumers/US-EN/Consumer-Product-and-Services/Cable-Modems-and-Gateways/SBG6580-SURFboard-eXtreme-Wireless-Cable-Modem-Gateway-US-EN](http://www.motorola.com/Consumers/US-EN/Consumer-Product-and-Services/Cable-Modems-and-Gateways/SBG6580-SURFboard-eXtreme-Wireless-Cable-Modem-Gateway-US-EN)) and download the User Manual

Turn off everything (PC, router, unplug modem)

Wait five minutes and, in order, do the following:
1) plug in modem, wait until all lights are on and green or wait for 2-3 minutes
2) turn on router (if applicable), wait for all lights to be in go-ahead mode
3) turn on PC connected to ethernet port by cable to the modem

Go to page 24 and see how to Restore Wireless Defaults, Option 1

Enter PIN and Login with factory defaults

Set it up  
It may be necessary to call either Charter (for your IP Address range, Gateway address, and Primary & Secondary DNS server IP addresses) and/or Motorola

Change default passwd and all that is necessary for a secure wireless connection nowadays

---

### Post by karrank% on 2011-09-02
Solved--was posting from my Windoze box which the lunkheads from Charter could understand w/o issue. Switched out, Ubuntu box in, and all good--I suspect they didn't even plug the right ethernet cable in the first time. 

Thanks for offering help, folks, love these forums!

---

