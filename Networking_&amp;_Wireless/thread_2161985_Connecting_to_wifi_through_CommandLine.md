---
title: "Connecting to wifi through CommandLine"
date: 2013-07-12
forum: Networking &amp; Wireless
---

### Post by Jaspermid on 2013-07-12
Hi guys,

I am having some trouble loading up ubuntu and my live USB also doesn't work. Want to download boot-repair package so I can fix this. Unfortunately did not connect my laptop to internet yet. Was wondering whether someone knows how to connect to my wifi through the command line. Apologies if this is a bit of a noob question. Thanks,

Jasper

---

### Post by Jaspermid on 2013-07-12
[COLOR=#666666][FONT=Consolas]$ sudo iwconfig eth1 essid "asdasd" gives: Error for wireles Request "SET ESSID" (8B1A) SET failed on device ethi : no such device [/FONT][/COLOR]

---

### Post by Jaspermid on 2013-07-12
[http://askubuntu.com/questions/138472/how-do-i-connect-to-a-wpa-wifi-network-using-the-command-line](http://askubuntu.com/questions/138472/how-do-i-connect-to-a-wpa-wifi-network-using-the-command-line) does not work. Cannot get the wpasupplicant. GKSU gedit gives warning cannot open display

---

### Post by steeldriver on 2013-07-12
If your connection is WPA/WPA2 then imho the easiest way is to edit your /etc/network/interfaces file and add a 'stanza' for the interface there e.g. (assuming that your wifi interface is called wlan0 - it may not be, 'ifconfig -a' should tell you)

```

iface wlan0 inet dhcp
    wpa-ssid *yourssid*
    wpa-psk *yourpassphrase*
dns-nameservers 192.168.1.1

```

You may not need an explicit dns-nameservers line if you get DNS servers via DHCP. If you have a static IP address scheme then you will need to add the IP and netmask and change 'dhcp' to 'static'. Then save the file and restart networking:

```

sudo service networking restart

```

or if that doesn't work

```

sudo /etc/init.d/networking restart

```

(or just reboot). If you are on a WEP connection it's similar but the keynames are wireless-essid and wireless-key iirc.

For WEP it's actually possible to bring up in a pure commandline using iwconfig to set the essid and key but I don't think that's the case with WPA - in any case, editing the file is straightforward. Don't forget to edit it back out (or comment it out with # signs) once you are back to the desktop, if you want network-manager to take over the interface again.

---

### Post by Jaspermid on 2013-07-12
Booting is already fixed :) tnx

---

### Post by Jaspermid on 2013-07-12
thnx for the response steeldrived. Managed to fix my boot problems another way.

---

