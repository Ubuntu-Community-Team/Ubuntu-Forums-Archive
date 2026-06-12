---
title: "Not detecting wlan0"
date: 2009-04-12
forum: Networking &amp; Wireless
---

### Post by mislavb on 2009-04-12
Hi, I am not so new in Ubuntu but this is first time
I work with wireless.

On the internet I found some things...
When I write iwconfig in terminal, this is what I get:

```

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

```

If I write lspci, this is part about my wireless card:

```

03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

```

In Hardware Drivers I see driver for my wireless card but if I enable it everything is the same.

Help please :s

---

### Post by t0mppa on 2009-04-12
Disable the driver in Hardware Drivers and try this: [http://ubuntuforums.org/showthread.php?t=1120259]("http://ubuntuforums.org/showthread.php?t=1120259")

---

### Post by Kevbert on 2009-04-12
Welcome to Ubuntu.
Please take a look at this [COLOR="Red"][post]("http://ubuntuforums.org/showthread.php?p=6929399#post6929399")[/COLOR] (especially #3). You can get the package mentioned via System-Admin-Synaptic Package Manager.

---

### Post by mislavb on 2009-04-12
Thanks, this helped to solve first
part of my problem.

iwconfig:

```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


```

Now, when I go to network manager , I click on 
Wireless connection and enable roaming mode.
It doesn't work...
Nothing happens.
What is next I have to do?

---

### Post by mislavb on 2009-04-12
Does anyone know? :(

---

