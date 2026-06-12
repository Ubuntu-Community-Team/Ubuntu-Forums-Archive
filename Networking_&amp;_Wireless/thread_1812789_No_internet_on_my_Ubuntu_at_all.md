---
title: "No internet on my Ubuntu at all"
date: 2011-07-26
forum: Networking &amp; Wireless
---

### Post by Neonone on 2011-07-26
Asus EEE PC 900
Broadcom b4311
followed instructions on [http://ubuntuforums.org/showthread.php?t=1604868&page=44](http://ubuntuforums.org/showthread.php?t=1604868&page=44) and now ethernet doesn't work after this now either. (on other laptop)
NEED HELP PLEASE
Also welcome to delete my last thread that no one but me responded to

---

### Post by wildmanne39 on 2011-07-26
Hi, I have a link for that issue I do not know if you have the same ethernet card or not but I suspect you do here is a link.
[http://askubuntu.com/questions/14970/broadcom-bcm4401-b0-100base-tx-issues](http://askubuntu.com/questions/14970/broadcom-bcm4401-b0-100base-tx-issues)
If you are unsure of your ethernet card you can run this command in a terminal and post the results here.
```
lspci -nn
```

---

### Post by bkratz on 2011-07-26
> **Neonone said:**
> Asus EEE PC 900
Broadcom b4311
followed instructions on [http://ubuntuforums.org/showthread.php?t=1604868&page=44](http://ubuntuforums.org/showthread.php?t=1604868&page=44) and now ethernet doesn't work after this now either. (on other laptop)
NEED HELP PLEASE
Also welcome to delete my last thread that no one but me responded to



If I understand your link--you added the STA driver. In 11.04 the correct driver is the B43 (see this link).
[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)

you probably have a broadcom wired connection too, and using the STA driver tends to blacklist ssb which is used by the wired connection too.

Please go to the terminal and copy/paste the output of the following back here.


```
lspci -nn

lsmod

cat /etc/modprobe.d/blacklist.conf

```

Looks like Wildmann39 got it!

---

### Post by Neonone on 2011-07-26
Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

Ethernet controller: Atheros Commuincations L2 Fast Ethernet (rev 01)

---

### Post by IWantFroyo on 2011-07-26
Go to the Synaptic Package Manager and search 'b43'

There should be about 3 firmware packages (and nothing else). They each say in the descriptions what cards they support. Find the one that supports the BCM4311

I would do this for you, but I'm not running 11.04 at the moment.

Hope that helped.

---

### Post by Neonone on 2011-07-26
When I disable the suggested driver it says the wireless and wired are enabled but only the wired connection shows any signs of internet (even when right next to a wireless router)

---

### Post by nm_geo on 2011-07-26
> **Neonone said:**
> When I disable the suggested driver it says the wireless and wired are enabled but only the wired connection shows any signs of internet (even when right next to a wireless router)

On a hunch here ... Open Synaptic install  firmware-b43-installer verify b43-fwcutter is installed .. it would be better if you would open terminal and copy and paste the commands wildmanne & bkratz asked for.. after installing the firmware .. Reboot without ethernet cable

In terminal copy and paste this 

```
sudo lshw -C network

```

---

### Post by wildmanne39 on 2011-07-26
Hi, open synaptic and type bcm then uninstall everything that has a green dot by it, then install b43-fwcutter and only nothing else not even bcmwl-kerrnel-source.
Then disconnect your wired connection and restart your system, then they should both work hopefully.

If your wireless works but your ehternet does not then do what I it says to do in the link I gave you.
Thank you

---

### Post by Neonone on 2011-07-26
> **IWantFroyo said:**
> Go to the Synaptic Package Manager and search 'b43'

There should be about 3 firmware packages (and nothing else). They each say in the descriptions what cards they support. Find the one that supports the BCM4311

I would do this for you, but I'm not running 11.04 at the moment.

Hope that helped.
RADCAKES that did it. I'll mark the problem as solved!

---

### Post by wildmanne39 on 2011-07-26
Hi, glad you got it fixed.

---

