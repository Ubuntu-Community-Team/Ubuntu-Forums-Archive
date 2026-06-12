---
title: "Ubuntu Server 10.4 and hostapd for dual-band wireless AP"
date: 2010-10-01
forum: Networking &amp; Wireless
---

### Post by Xylian on 2010-10-01
Hi people,
I've configured a small ubuntu server 10.4 box on which I'm going to add two mini-pci wireless cards that support 802.11a/b/g/n and that use the ath9k driver to build a dual-band wireless access point (one card that serves legacy 802.11b/g clients and another one for 802.11n clients, and both will be bridged together along with the ethernet interface). I was looking for some documentation about hostapd and I did not find anything about how to configure it in such a scenario.. So, these are my questions for you:

1) how do I set up the hostapd configuration file in order to configure wlan0 as 802.11b/g AP and wlan1 as 802.11n AP, with different channels/modes/WPA-keys etc? Looking at the examples I've found, it seems not possible..

2) do I need to run two instances of hostapd? how should I configure them in order to avoid conflicts?

Any help is wellcome ;-)

Thank you in advance,
   Gianni

---

### Post by Xylian on 2010-10-05
(sorry for double post)

---

### Post by Xylian on 2010-10-05
The problem has been solved very easily, just load the two configuration files in /etc/default/hostapd:

```

RUN_DAEMON="yes"
DAEMON_CONF="/etc/hostapd/hostapd_wlan0_2.4Ghz.conf /etc/hostapd/hostapd_wlan1_5Ghz.conf"
DAEMON_OPTS="-dd"

```

---

### Post by ambipur on 2012-09-21
Hi Xylian,

could you post your hostapd_wlan1_5Ghz.conf file? Thanks in advance!

---

### Post by overdrank on 2012-09-21
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

