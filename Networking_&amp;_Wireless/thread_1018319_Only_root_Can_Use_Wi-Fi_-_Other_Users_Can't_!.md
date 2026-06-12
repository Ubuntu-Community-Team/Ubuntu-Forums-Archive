---
title: "Only root Can Use Wi-Fi - Other Users Can't !"
date: 2008-12-22
forum: Networking &amp; Wireless
---

### Post by Windows Refugee on 2008-12-22
I'm a brand spanking new Ubuntu (8.10 desktop) user, installed on a Compaq Presario laptop with a Motorola PCMCIA Wi-Fi card (broadcom chipset), and the internal Compaq (Connexant) modem.

I was very frustrated at first, because neither my Wi-Fi card or my modem were working.:cry:  After a bit of research, it seems Ubuntu does not support these devices out-of-the-box.  

After some research, I downloaded the proprietary broadcom driver and the appropriate fwcutter, and installed the driver.  I got a warm and fuzzy feeling all over, when I saw the LEDs on my Wi-Fi card light up !  (I still have to tackle the modem issue, but for now, I'll use the Wi-Fi card.)

I went into SYSTEM > PREFERENCES > NETWORK CONFIGURATION and set it up for my wireless network.  For some reason, manually configuring the IP parameters does not let me connect to my network, but using DHCP will.  I don't understand this, because I'm very comfortable with configuring this stuff.  The other problem I have is that the Wi-Fi connection will only work when I'm logged in as root. I made sure that I gave the other users wireless permission by going into SYSTEM > ADMINISTRATION > USERS & GROUPS, and checking the permissions, but they still can't use Wi-Fi.

One last issue is that according to what I've read, I should be able to run network-admin by navigating to SYSTEM > ADMINISTRATION > NETWORKING, but there is no NETWORKING choice on my ADMINISTRATION menu, and if I open a terminal window and type "network-admin", the system tells me it's not installed.  It advises me to type "apt-get install gnome-network-admin", but that doesn't work either.

Can anybody offer some help for these problems ?  ](*,)

---

