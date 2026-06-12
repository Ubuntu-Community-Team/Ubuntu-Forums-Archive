---
title: "Wireless trouble"
date: 2006-05-01
forum: Networking &amp; Wireless
---

### Post by meat on 2006-05-01
I am trying to get wireless working.  I believe I have the driver working and the card active, because I can see a wirelss signal and it says the card (eth1) is active, but my wireless network (WAP?) is not showing up in the SSID section.  The network icon says that my network is disconnected.  I typed my SSID and my WEP key and hit enter and it takes forever and then says active.


computer: IBM T21 laptop
network card: PCMCIA Oninoco Gold 11b/g
Ubuntu: Dapper Drake

---

### Post by Jason_25 on 2006-05-01
What's the output of ```
sudo iwconfig
``` at the terminal?

---

### Post by meat on 2006-05-01
eth1   IEEE 802.11b  ESSID:"name I typed in for SSID"  Nickname:"some nickname"

mode:Managed  Frequency:2.437 GHz  Access Point 00:80:c8:12:E3:E8
Bit rate:11 Mb/s  Sensitivity:1/3
Link Quality=45/92  Sig level=-40 dBm Noise level=-85 dBm

The rest are all 0's

---

### Post by Jason_25 on 2006-05-01
Ok then type
```

sudo iwconfig eth1 key inserthexkeyhere

```
To add your key.  You should be connected now.  To make your changes permanent, edit the /etc/network/interfaces file.

---

### Post by meat on 2006-05-01
insertthekeyhere is that text or hexadecimal?

---

### Post by meat on 2006-05-01
Ok, I typed that line of code in terminal hexadecimal, but I already had the encryption key displayed.  That did not fix it.

What does the nickname signify?  (My wife set up the wireless network and she says I have the right key and SSID)

---

### Post by Jason_25 on 2006-05-01
'that did not fix it'.  What does that mean?  Can you not ping the router?  Do you have a valid ip address?

---

### Post by meat on 2006-05-01
How do I ping the router?  I am using DHCP.  I just installed Ubuntu yesterday, so wireless has never worked.

---

### Post by meat on 2006-05-01
OK, after a reboot, it works.  Thank you!

---

