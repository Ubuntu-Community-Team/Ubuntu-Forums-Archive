---
title: "USB-N13 Ubuntu 10.10"
date: 2010-11-24
forum: Networking &amp; Wireless
---

### Post by jej2003 on 2010-11-24
I have spent a few hours trying to get my new USB-N13 wireless Adapter working with Ubuntu and I am really still struggling.  If I do an iwconfig I get the following:

```

lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:"linksys"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.442 GHz  Access Point: 00:25:9C:D9:A1:9F   
          Bit Rate=130 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=71/100  Signal level:-68 dBm  Noise level:-82 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```Which tells me Ubuntu has found the USB Adapter.  For whatever reason I can't configure this using the Network Manager.  If I manually configure the adapter by doing

```

iwconfig ra0 essid linksys
dhclient

```I can connect, but if I restart those settings are lost.  So first question, why does this not show up in network manager for me to configure, and second question why can't I access anything beyond my router?  Second question, if I can't get network manager to work how can I set this up to work with my WPA enabled router (currently encryption is off to test things)?

---

### Post by uncaspi on 2010-11-25
If there are additional lines except lo interface lines, they are not handled by the network-manager.

To access the outside world you must probably add a route.

sudo route add default gw x.x.x.x ra0

To encrypt use the key option in iwconfig. See man iwconfig

---

### Post by jej2003 on 2010-11-25
Not sure I follow what you mean by:

> If there are additional lines except lo interface lines, they are not handled by the network-manager.

a bit of googling led me to this [page]("http://everyjoe.com/technology/howto-use-iwconfig/") as an example of how to use WPA Supplicant...I'll have to try this.

Ultimately though I'd like this all handled by network manager, how can I do this?

---

### Post by shenmeister on 2010-12-02
Which driver are you using for this adapter?

I downloaded the latest driver from ASUS and compiled it. In the readme file, it says to make sure 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y' are set in the ./os/linux/config.mk file to allow NetworkManager to work.

I'm running 10.04 Lucid and the adapter didn't work out-of-the-box, which is why I installed the driver. I don't know if this is the case in 10.10.

---

