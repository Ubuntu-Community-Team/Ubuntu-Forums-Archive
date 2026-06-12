---
title: "Auto-connect to wireless net not working (and workaround)"
date: 2008-12-28
forum: Networking &amp; Wireless
---

### Post by breininge on 2008-12-28
Ubuntu 8.10 installed as standalone O/S on Dell Inspiron 3800 laptop and working very well with exception of auto-connect to wireless network. Details as follows:
Mixed wireless network: 802.11b and .11g ;
Network card: Linksys WPC11 v3 (uses 802.11b) ;
Driver: orinoco ;
Security: WEP ;

Auto-connect to the Wifi worked initially (after Ubuntu first installed) but failed to work soon afterwards for reasons unknown. I then stumbled upon the following workaround (using GUI tools) to connect to the Wifi. It is bizarre but seems to indicate a problem with WEP key recognition.

Right click Network Connections icon in the top toolbar;
  Edit Connections ;
     Wireless ;
        highlight Auto eth1 ('eth1' is the interface name) ;
           EDIT ;
             Wireless Security ;
                Show Key ;
                   OK ;

The connection is established as soon as 'OK' is clicked (following 'Show Key'). There is a stable Wifi connection from then on (until the next boot...).

I'd be grateful for help from the Ubuntu community to resolve this mystery. Thank you!

---

### Post by Rockin' Moe on 2009-04-10
Hi, same problem here, but with an Encore router and WPA/WPA2. Workaround is just as effective (thanks for that), but still looking for a permanent fix.

---

### Post by Kulgan on 2009-04-10
To follow through on your WEP theory, have you tried using WPA or diabling WEP?

Edit:
Sorry RM!
Also noticed breininge is using wireless b. Is that the same in both cases? And could the network adapter have any bearing on it? What are your specs, Rockin' Moe? :P

---

### Post by breininge on 2009-05-02
> **Rockin' Moe said:**
> Hi, same problem here, but with an Encore router and WPA/WPA2. Workaround is just as effective (thanks for that), but still looking for a permanent fix.
Thanks Rockin'Moe! Good news: Ubuntu 9.04 fixes the problem. Auto-connect works perfectly now following a boot or when coming out of suspend.

---

### Post by breininge on 2009-05-02
> **Kulgan said:**
> To follow through on your WEP theory, have you tried using WPA or diabling WEP?

Edit:
Sorry RM!
Also noticed breininge is using wireless b. Is that the same in both cases? And could the network adapter have any bearing on it? What are your specs, Rockin' Moe? :P
Thanks, Kulgan! No sense staying with 8.10: Ubuntu 9.04 has fixed my wireless auto-connect problem. Am thrilled with this release! 

BTW, disconnecting WEP or using WPA did not fix the problem in 8.10.

---

