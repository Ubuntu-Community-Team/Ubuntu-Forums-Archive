---
title: "Wireless not connecting (Broadcom BCM4306)"
date: 2011-04-25
forum: Networking &amp; Wireless
---

### Post by Luinar on 2011-04-25
I've been trying to troubleshoot this myself for the past couple of days, but to no avail so I have come in search of help.

I have a PCI wireless card, it's a Broadcom device using the BCM4306 chipset. I'm running the b43 drivers which were installed using fwcutter.

At my last place the card worked perfectly. There it was connected to an unencrypted network. I've recently moved places and it just refuses to connect to the new network here. The router is set up with a 64-bit WEP key. In Ubuntu, network manager sees the access point and prompts my to enter the password but will not connect, instead continually asking for the login. I have tried using wicd instead of network manager, and that just throws up a "bad password" error.

Signal strength to the access point isn't great, around 50% usually, however the same card connects and works perfectly when I'm booted into Windows Vista. Unfortunately I can't do anything to change the router's configuration and using a cable is not possible.

Any help or suggestions at this point would be greatly appreciated! :)

---

### Post by josephmills on 2011-04-25
hi there could we please see a ```
dmesg | grep b43
```and a ```
lsmod | grep b43 
``` also have you tried to clean your passwords and encryption keys? you can also change your router settings  via wifi but I hope that the 64 bit is not getting in the way of the ipv6 (:confused:). any how thanks

---

### Post by Luinar on 2011-04-25
Hi, thanks for the reply. As requested:

```

gary@serenity:~$ dmesg | grep b43  
 [   14.385753] b43-phy0: Broadcom 4306 WLAN found (core revision 5)  
 [   14.550639] Registered led device: b43-phy0::tx  
 [   14.550657] Registered led device: b43-phy0::rx  
 [   14.550674] Registered led device: b43-phy0::radio  
 [   15.640031] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)  
 
```and
```

gary@serenity:~$ lsmod | grep b43  
 b43             168681     0  
 mac80211   231959     1   b43  
 cfg80211     144694      2  b43,mac80211  
 led_class     2633         1   b43  
 ssb             39320        1 b43  
 
```How would I go about cleaning the password/encryption keys?

Also I should have been a bit more clear; I cannot change the routers config as it is not my own and serves the rest of the building. I can access the settings page if needed to retrieve any neccessary info, but actually altering any settings is a no-no.

---

### Post by Luinar on 2011-04-26
Additionally, attempting to connect from the terminal throws up the following error:

```
No DHCPOFFERS received. 
No working leases in persistent database - sleeping.
```I'm guessing this is probably relevant, but Google has been less than forthcoming with any solutions to this error.

I've also tried inputting the hex code rather than the passphrase for the WEP but still no dice. 

Completely stumped by this.

---

### Post by Luinar on 2011-04-30
Sorry to be a pain and bump this, but thought I'd try one more last ditch call for help.

I've even tried putting a new wireless card in my machine, this time one which has native Linux support to eliminate driver issues. Ubuntu detects the card fine, only trouble is this card doesn't seem to be able to detect the access point (same problem with the new card under Windows) so that hasn't helped.

Anything at all? I'm beginning to fear that I'm going to be stuck with Windows. :(

---

### Post by Luinar on 2011-05-13
For the sake of completeness, marking this as "solved". Unable to fix the original problem, possibly the b43 drivers are a little buggy with WEP connections. In the end found another wireless card which works for me. Good to have Ubuntu back again.

---

### Post by Bernmeister on 2011-12-15
This may help: [http://ubuntuforums.org/showthread.php?p=11539545#post11539545]("http://ubuntuforums.org/showthread.php?p=11539545#post11539545")

---

