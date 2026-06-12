---
title: "I dont have a WPA_Supplicant.conf file"
date: 2006-07-04
forum: Networking &amp; Wireless
---

### Post by harryhoudini66 on 2006-07-04
I have reinstalled WPA_SUPPLICANT and WPA_GUI a bunch of times and I dont have the file. I do a search and cannot locate it either.

---

### Post by harryhoudini66 on 2006-07-04
harryhoudini66@LINUX-UBUNTU:~$ locate wpa_supplicant
/etc/wpa_supplicant
/etc/wpa_supplicant/ifupdown.sh
/sbin/wpa_supplicant
/usr/share/doc/wpasupplicant/examples/wpa_supplicant.conf.gz
/usr/share/man/man5/wpa_supplicant.conf.5.gz
/usr/share/man/man8/wpa_supplicant.8.gz
harryhoudini66@LINUX-UBUNTU:~$

---

### Post by blackdalek on 2006-09-08
I can't find this file eihter. It just doesn't exist. Nor can I find how to create it or where to get this file. Every wifi setup howto I have tried has just come to a similar dead end.

---

### Post by mjm1231 on 2006-09-09
Mine doesn't exist either (Xubuntu) but you can unzip the one in /usr/share/doc/wpasupplicant/examples. After looking at it, I'm thinking it would be easier to write a fresh one... the example one is damn long which makes it hard to be sure which settings are needed for my specific setup. I was hoping all I had to do was add my PSK passphrase. 

If I find a better guide to building your own conf file, I'll post it here.

---

### Post by cookfromfrozen on 2006-09-10
It's easier and better just to write your own conf file.

This goes at the top:

```

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

```

Then use the command

```

wpa_passphrase <your SSID>

```

Then enter the passkey when prompted.  Copy and paste the output into the conf file below those two lines I posted above and that should be it for most configurations.

---

