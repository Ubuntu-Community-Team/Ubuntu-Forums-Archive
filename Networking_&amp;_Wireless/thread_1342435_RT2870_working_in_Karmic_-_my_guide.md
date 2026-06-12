---
title: "RT2870 working in Karmic - my guide"
date: 2009-11-30
forum: Networking &amp; Wireless
---

### Post by mizunoX on 2009-11-30
There are a number of people complaining about problems with their RT2870 based device in Karmic Koala, and a number of fixes have been provided.

I tried a few, and they didn't work for me.  I wasn't able to compile the driver from Ralink, and blacklisting conflicting drivers wasn't enough.

So here's what I did (probably already suggested elsewhere on here):

First I blacklisted two conflicting drivers:

```
sudo gedit /etc/modprobe.d/blacklist.conf
```

Go to the bottom of the file and add 
```
blacklist rt2860sta
blacklist rt2800usb
```

Reboot.

I was now able to connect to my network ONLY if it was set to 2.4Ghz .  And it was flaky at that.  The speed would hover between 1Mbps and 11Mbps.  Not good.

So, I found that this driver can use a config file to set the appropriate settings for your network.

I've attached my config file (I've only erased my SSID and Passkey so you can fill your own in here, as well as the README_STA file from Ralink's driver source.  The README explains each option in the config file if you need to make changes to match your network.

Once you've made the appropriate changes to the config file go ahead and place it where it should go with the following command:

```
sudo mkdir /etc/Wireless/RT2870STA -p
sudo cp RT2870STA.txt /etc/Wireless/RT2870STA.dat
```

(note that the config file needs to have a .dat extension.  I had to rename it to .txt in order to upload to this forum.)

I rebooted after this and all was good.  I was able to connect at 110Mbps (or so) at 2.4Ghz and 216Mbps at 5Ghz.


I hope this helps someone to get more use out of Karmic Koala.
*I'm using kernel 2.6.31-15, 32bit Karmic Koala and my adapter is a Linksys WUSB600n*

---

### Post by mizunoX on 2009-11-30
Sorry, here's the README.

---

### Post by inMotion on 2010-06-14
thanx a lot. This works for me.
Karmic 2.6.31-22
Does it work in Lucid to ?

---

