---
title: "AR5001X+, which driver? madwifi, ath5k need help"
date: 2009-01-29
forum: Networking &amp; Wireless
---

### Post by stevenvu on 2009-01-29
I found an old laptop lying about the house and decided to install ubuntu on it. Fairly old machine with a celeron 1.4ghz cpu. I'm currently having problems with the wireless. 

I'm really confused. I've been searching the net for a good couple of hours trying to find out how to get this blasted chip working. The problem is there are 3 drivers. madwifi, ath5k and ath9k. Which one am I supposed to use. 

Here's what i've done so far:

Installed Ubuntu 8.10

Updated 8.10

discovered wireless wasn't working, ath0 doesn't appear when iwconfig is run

Read the release notes and installed ath5k using the backports package

```
Atheros ath5k wireless driver not enabled by default

The version of the ath5k driver for Atheros wireless devices included in Linux 2.6.27 interferes with the use of the madwifi driver for some wireless devices and as a result has been disabled by default. Many Atheros chipsets will work correctly with the madwifi driver, but some newer chipsets may not, and the madwifi driver may not work with WPA authentication. If you have an Atheros device that does not work with madwifi, you will want to install the linux-backports-modules-intrepid-generic package, which includes an updated version of the ath5k driver. While not installed by default, this linux-backports-modules-intrepid-generic package is included on the Ubuntu 8.10 CD and DVD images for ease of installation. 
```

Blacklisted ath_pci

wireless still not working, ath0 doesn't appear in iwconfig.

```

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

```

lshw shows device unclaimed.

```

        *-network:0 UNCLAIMED
             description: Ethernet controller
             product: Atheros AR5001X+ Wireless Network Adapter
             vendor: Atheros Communications Inc.
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: latency=168 maxlatency=28 mingnt=10
```

What should I do next? Any help would most definitely be appreciated.

---

### Post by waj1122 on 2009-01-29
Don't know whether you've checked here or not, 
[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

This is how I got my wifi (ath5k) up and running.

Bill

---

### Post by Ryuhayabusa on 2009-04-28
thanks guys,

i have trouble with atheros madwifi ar5212 and will try this.

---

### Post by Woodwa on 2010-01-06
> **waj1122 said:**
> Don't know whether you've checked here or not, 
[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

This is how I got my wifi (ath5k) up and running.

Bill

thanks the 1st part Got my ar5001x running in 9.10 karmic

---

