---
title: "University of Pittsburgh WIRELESS-PITTNET issue"
date: 2009-03-26
forum: Networking &amp; Wireless
---

### Post by phymacs on 2009-03-26
solved

---

### Post by Sephenon on 2010-01-18
How did it get solved?  What should I do?

---

### Post by Jayayess1190 on 2010-01-19
> **Sephenon said:**
> How did it get solved?  What should I do?

This is what the Pitt page says:

> CSSD cannot provide instructions to configure Linux devices, cell phones, smart phones, or other wi-fi devices to connect to Wireless PittNet. We do provide the information you will need to configure your device to connect:
[LIST]
[*]**Network SSID**
WIRELESS-PITTNET 
[*]**Security Type**
WPA-Enterprise 
[*]**Encryption Type**
TKIP 
[*]**Authentication Method**
PEAP 
EAP-MSCHAPv2[/LIST]

---

### Post by Sephenon on 2010-01-19
Those sons of Bs.  The higher up floors of the towers don't get any wi fi at all unless you're in a lounge and I'm not up for sitting in the damn lounge EVERYtime I need to work.  And I'm trying to migrate from windows so this is shenanigans.  I'll try it during my break today at somewhere in posvar and then I'll see what happens.

---

### Post by Sephenon on 2010-01-19
Alright, I tried to connect in David Lawrence and it's giving me nothing.  Under the wireless security tab it says to enter a username and password after I entered all the details you guys put up, so I figure it just wants my pitt username and password and such.  Even after all of this, I'm getting no results, let alone I don't know if my laptop's even picking up the signal.  But when I reboot in windows, it's fine.  Any help?

---

### Post by bkratz on 2010-01-19
> **Sephenon said:**
> Alright, I tried to connect in David Lawrence and it's giving me nothing.  Under the wireless security tab it says to enter a username and password after I entered all the details you guys put up, so I figure it just wants my pitt username and password and such.  Even after all of this, I'm getting no results, let alone I don't know if my laptop's even picking up the signal.  But when I reboot in windows, it's fine.  Any help?




Why not just do a 

sudo iwlist scan

in terminal and see what signals you actually do see.

---

### Post by Sephenon on 2010-01-19
My interface doesn't support it it says.

---

### Post by bkratz on 2010-01-19
> **Sephenon said:**
> My interface doesn't support it it says.

It doesn't sound like you have the wireless drivers setup, otherwise you would have received a couple of not supported for the wired and bluetooth, but the scan would have taken place with the wireless.

Can you copy/paste the outputs of the following commands back here?


sudo lshw -C network   (that is lshw in lowercase and c in uppercase)

lspci  (that is LSPCI in lowercase)

This should tell someone what the wireless card is and it's condition.

---

