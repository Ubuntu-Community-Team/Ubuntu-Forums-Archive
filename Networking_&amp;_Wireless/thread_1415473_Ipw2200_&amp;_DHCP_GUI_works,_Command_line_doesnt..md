---
title: "Ipw2200 &amp; DHCP GUI works, Command line doesnt."
date: 2010-02-24
forum: Networking &amp; Wireless
---

### Post by Anhedonia on 2010-02-24
Ok , having not used linux for six years and wanting to get back into IT i decided to install the text only server and learn to do every single function from the commandline as i dont think clicking buttons in a GUI is learning anything.

So far ive spent 3 days, 10 hours each day and I'm not kidding.

this is what i do.
```

ipconfg eth0 down (the lan)
ipconfig eth1 up
iwconfig eth1 scan
iwconfig essid techfixpc mode managed ap [the routers mac adress] key :s[the correct key in ascii] (i have tried this with less parameters also)

dhclient eth1 -s 192.168.0.1 (i of course tried without specifying dhcp serrver)
```the dhclient times out and never connects.


I realise i could probably not use DHCP, but then i wont now how to fix this in the future.

I have googled this topic near 100 times now, and read many of the results i have been trying to fix this 3 days now. Still no victory bananna.

Anhedonia

---

### Post by Anhedonia on 2010-02-25
Ive now tried to setup the ip statically as some have quoted fixed this DHCLIENT issue in older systems.

Still no luck whatsoever. This is my fourth day of spending the entire day trying to fix this.

I think i'm going to give up with ubuntu and try to find a distribution with a bit more quality control, for GUI to work and command line not is ridiculous. You would think the command line would come first.

---

### Post by chili555 on 2010-02-25
May I please see your */etc/network/interfaces* file? Also, please verify that Network Manager is ***not*** installed. NM and the command line almost never work together, at all. Are you currently running a windowing manager, Gnome, KDE or similar?

Have you been able to scan and see your network?```
sudo iwlist eth1 scan
```

---

### Post by Anhedonia on 2010-02-28
Hey mate thanks for the reply..

I realized the key s: command musnt of been working with WPA-PSK (or it was never intended too im not sure)

I used the wpa_passphrase command to create an encrypted pass and created the wpa_supplicant.conf file which was missing.

So the solution was to create a wpa_supplicant.conf file with the passphrase/encrypted passphrase from the wpa_passphrase tool.

Thanks. :).

---

