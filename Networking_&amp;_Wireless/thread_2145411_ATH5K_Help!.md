---
title: "ATH5K Help!"
date: 2013-05-15
forum: Networking &amp; Wireless
---

### Post by thirdeye420 on 2013-05-15
Hi everyone,

I installed the madwifi drivers in an attempt to get my wireless to work with WPA encryption.  Anyways, when I go to additional drivers and try to activate madwifi, I get an error message stating "You removed the configuration file /etc/modprobe.d/blacklist-ath_pci.conf"  I don't remember doing this....   can anyone out there help me resolve this?  I have no wireless networks being displayed at all now...

thanks everyone,..

---

### Post by steeldriver on 2013-05-15
I used to run a couple of ath5k based PCI cards - iirc they work fine with WPA in NetworkManager if you disable hardware encryption (option ath5k nohwcrypt=Y)

However fwiw here is the default blacklist-ath_pci.conf file from 12.04

```
$ cat /etc/modprobe.d/blacklist-ath_pci.conf

# For some Atheros 5K RF MACs, the madwifi driver loads buts fails to
# correctly initialize the hardware, leaving it in a state from
# which ath5k cannot recover. To prevent this condition, stop
# madwifi from loading by default. Use Jockey to select one driver
# or the other. (Ubuntu: #315056, #323830)
blacklist ath_pci

```

---

### Post by thirdeye420 on 2013-05-15
I'm sorry, I'm not very familiar with ubuntu yet...  what should I do with this code?

---

### Post by thirdeye420 on 2013-05-15
anyone???  I'd like to get my wifi working, or else ubuntu is completely useless to me...

---

### Post by steeldriver on 2013-05-15
well I would first check that you really don't have an existing /etc/modprobe.d/blacklist-ath_pci.conf file, and if you don't then open a text editor with root privileges and paste in the contents I posted and save it e.g.

```
gksudo gedit /etc/modprobe.d/blacklist-ath_pci.conf 
```

Or since everything except for the last line is comment text, you could just do

```
 echo "blacklist ath_pci" | sudo tee /etc/modprobe.d/blacklist-ath_pci.conf"
```

which will create a new /etc/modprobe.d/blacklist-ath_pci.conf file with the contents "blacklist ath_pci"

---

### Post by thirdeye420 on 2013-05-15
okay, I did that and rebooted.  I went to additional Driver's and activated madwifi, but I got an error message telling me to check the "jockey.log" in /var/log.  The log is quite long, so I don't want to flood this thread by pasting it.  it says on the bottom of the addtional drivers screen that the driver is "disabled but still in use"..  any idea what this means?

---

