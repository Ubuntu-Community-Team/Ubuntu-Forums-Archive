---
title: "Fixing network interfaces"
date: 2011-05-27
forum: Networking &amp; Wireless
---

### Post by The*Master on 2011-05-27
I accidentally killed the dhclient processes. I am unable to access the Internet wirelessly or with Ethernet. It's a little irritating because now I have to post this using my phone. I'm looking for a way to reformat the network files to how they looked when I first installed ubuntu. I don't know quite what these are, or really anything about it.

The /etc/network/interfaces file has the following information:

auto lo
iface lo inet loopback

I'm pretty sure there's supposed to be more.

iwconfig typed into the terminal gives me this:

hans@hans-laptop:~$ iwconfig
lo                  no wireless extensions.

eth1              no wireless extensions.

wlan1            IEEE 802.11abg ESSID:"FBR-WEST TZ bg"
                      Mode:Managed Frequency:2.426 GHz Access Point: Not-Associated
                      Tx-Power=14 dBm
                      Retry long limit:7 RTS thr:off Fragment thr:off
                      Power Management:off

According to lshw, the logical name for my Ethernet interface is eth1. I think it used to be eth0. It's an 88E8055 PCI-E Gigabit Ethernet Controller.

The wireless interface has logical name wlan1. I think this used to be wlan0. It's a PRO/Wireless 3945ABG [Golan] Network Connection. The driver is iwl3945 - [phy0]

Any help would be appreciated. Thanks.

---

### Post by The*Master on 2011-05-27
The smileys are an accident. It seems the forum interpreted : followed by o as a smiley.

---

### Post by Iowan on 2011-05-27
You can check */etc/udev/rules.d/70-persistent-net.rules * to see how interfaces are defined.

Slightly off-topic, but FYI, there's an "Additional Option" to "Disable smilies in text".

---

### Post by bab1 on 2011-05-27
> **Iowan said:**
> You can check */etc/udev/rules.d/70-persistent-net.rules * to see how interfaces are defined.

Slightly off-topic, but FYI, there's an "Additional Option" to "Disable smilies in text".

Iowan,

I seriously did not know that.  How do you do it?

---

