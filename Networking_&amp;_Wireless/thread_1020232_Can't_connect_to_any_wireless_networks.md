---
title: "Can't connect to any wireless networks"
date: 2008-12-23
forum: Networking &amp; Wireless
---

### Post by Solomon Douglas on 2008-12-23
Hello -

I'm absolutely new to Ubuntu.  I successfully installed 8.10 on a Toshiba Satellite A25-S307, and so far it mostly seems to be working.

The exception thus far is wireless networking.  My wireless card is an Atheros AR5211.  When I click on the networking icon in the corner of the screen, it lists some wireless networks (but fewer networks than other laptops can see, and fewer than this one could see when it was running Windows).

When I try to connect to an open network, it fails, with the message "Network is disconnected".

Problem number one: how can I connect to the wireless networks that are available?

Problem number two: how can I restore my wireless card to the sensitivity that it had under Windows?

Thanks!

---

### Post by S_e_P_p on 2008-12-24
Hello,

Maybe you could try this:

[http://ubuntuforums.org/showthread.php?t=795984](http://ubuntuforums.org/showthread.php?t=795984)

it is not exactly the same wifi card but I suppose you can use this guide.

Greets,
SePp

---

### Post by superprash2003 on 2008-12-24
post output of **iwlist scanning** from the terminal

---

### Post by Solomon Douglas on 2008-12-24
```
sara@max:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:13:10:B1:A3:A6
                    ESSID:"Espresso Vivace - Brix wireless"
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Quality=42/70  Signal level=-53 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100

pan0      Interface doesn't support scanning.

```

Espresso Vivace is the network that I'm trying to connect to.

---

### Post by Hobgoblin on 2008-12-24
Try this.

Install **linux-backports-modules-intrepid-generic**

Then in System>Administration>Hardware drivers

Disable the Support for Atheros 802.11 wireless LAN cards, and enable the Support for 5xxx series of Atheros 802.11 wireless LAN cards.

Reboot.

---

### Post by Solomon Douglas on 2008-12-24
Wow, fabulous.  That worked!  Thank you!  And my girlfriend Sara (it's her computer) thanks you too.

---

