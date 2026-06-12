---
title: "Proxim Silver 802.11b/g PCMCIA card..."
date: 2006-02-13
forum: Networking &amp; Wireless
---

### Post by chopsbuntu on 2006-02-13
As stated in the title, I have the Proxim Silver card for my HP Pavilion ze4600 laptop. My router is a Linksys WRT54G. 

Anyway, everything works fine, but I never did install any special drivers or software for the Proxim card. Whatever Ubuntu loaded on my computer as it was installing is the only thing that the wifi card is working off of.

The thing that bugs me is that anytime I take my laptop out of my room where the router is, the signal drops drastically, and even gets disconnected from time to time. I'm only in the very next room, not even 30 feet away and there's only one inner wall (drywall and 2x4s) between me and the router. 

When I had Windows XP Pro installed on this laptop, I had Poxim's software installed and I had a heck of a lot more range than this. I could go halfway through the house without loosing a signal. Now I can barely get anything into the very next room!

Is there anything that can boost the effeciency of the card, or more suitable drivers for my particular card?

If I recall, I do remember seeing something about Proxim in Synaptic, but that was on my tower PC, not on the laptop. :-k 

Any suggestions would be greatly appreciated.

BTW, everything on the router is the same, and the IP is static. All the DNS, IPS, etc, etc are correct which leads me to think it has to do with finding the proper drivers.

---

### Post by chopsbuntu on 2006-02-14
Nothing at all? :-k

---

### Post by Lambert on 2006-02-14
Let's see if we can find what driver it's using and go from there.

post output of this command

```
sudo lshw -C network
```

Also post output of these commands

```

iwconfig
iwpriv [interfacename]

```

replace [interfacename] with name of device...wlan0, eth1, etc...

---

### Post by chopsbuntu on 2006-02-14
Hello Lambert! I think this is what you were asking for. And I want to thank you for trying to help me out with this! ;) 

**_sudo lshw -C network_**
> *-network
       description: 802.11g Wireless Upgrade Kit.
       product: CIS REV 1.2
       vendor: Proxim, Corp.
       physical id: 0
       version: Copyright 2003
       slot: Socket 0
       resources: irq:11

> *-network
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 1
       bus info: pci@02:00.0
       logical name: ath0
       version: 01
       serial: 00:20:a6:50:64:67
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wir eless
       configuration: broadcast=yes driver=ath_pci driverversi on=0.9.6.0 (EXPERIMENTAL) ip=192.168.1.122 multicast=yes wirel ess=IEEE 802.11g
       resources: iomemory:2c800000-2c80ffff irq:11


---

### Post by chopsbuntu on 2006-02-14
**_iwconfig_**
> ath0      IEEE 802.11g  ESSID:"House Of Pootinks"
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:0C:41:D4:50:57
          Bit Rate:48 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=35/94  Signal level=-60 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:74  Invalid misc:74   Missed beacon:121

sit0      no wireless extensions.


**_iwpriv ath0_**
> ath0      Available private ioctls :
          setoptie         (8BE8) : set 256 byte  & get   0
          getoptie         (8BE9) : set   0       & get 256 byte
          setkey           (8BE2) : set  60 byte  & get   0
          delkey           (8BE4) : set   7 byte  & get   0
          setmlme          (8BE6) : set  42 byte  & get   0
          addmac           (8BEA) : set   1 addr  & get   0
          delmac           (8BEC) : set   1 addr  & get   0
          chanlist         (8BEE) : set  32 byte  & get   0
          setparam         (8BE0) : set   2 int   & get   0
          getparam         (8BE1) : set   1 int   & get   1 int
          turbo            (0001) : set   1 int   & get   0
          get_turbo        (0001) : set   0       & get   1 int
          mode             (0002) : set   1 int   & get   0
          get_mode         (0002) : set   0       & get   1 int
          authmode         (0003) : set   1 int   & get   0
          get_authmode     (0003) : set   0       & get   1 int
          protmode         (0004) : set   1 int   & get   0
          get_protmode     (0004) : set   0       & get   1 int
          mcastcipher      (0005) : set   1 int   & get   0
          get_mcastcipher  (0005) : set   0       & get   1 int
          mcastkeylen      (0006) : set   1 int   & get   0
          get_mcastkeylen  (0006) : set   0       & get   1 int
          ucastciphers     (0007) : set   1 int   & get   0
          get_uciphers     (0007) : set   0       & get   1 int
          ucastcipher      (0008) : set   1 int   & get   0
          get_ucastcipher  (0008) : set   0       & get   1 int
          ucastkeylen      (0009) : set   1 int   & get   0
          get_ucastkeylen  (0009) : set   0       & get   1 int
          keymgtalgs       (0015) : set   1 int   & get   0
          get_keymgtalgs   (0015) : set   0       & get   1 int
          rsncaps          (0016) : set   1 int   & get   0
          get_rsncaps      (0016) : set   0       & get   1 int
          roaming          (000C) : set   1 int   & get   0
          get_roaming      (000C) : set   0       & get   1 int
          privacy          (000D) : set   1 int   & get   0
          get_privacy      (000D) : set   0       & get   1 int
          countermeasures  (000E) : set   1 int   & get   0
          get_countermeas  (000E) : set   0       & get   1 int
          dropunencrypted  (000F) : set   1 int   & get   0
          get_dropunencry  (000F) : set   0       & get   1 int
          wpa              (000A) : set   1 int   & get   0
          get_wpa          (000A) : set   0       & get   1 int
          driver_caps      (0010) : set   1 int   & get   0
          get_driver_caps  (0010) : set   0       & get   1 int
          maccmd           (0011) : set   1 int   & get   0
          wme              (0012) : set   1 int   & get   0
          get_wme          (0012) : set   0       & get   1 int
          hide_ssid        (0013) : set   1 int   & get   0
          get_hide_ssid    (0013) : set   0       & get   1 int
          ap_bridge        (0014) : set   1 int   & get   0
          get_ap_bridge    (0014) : set   0       & get   1 int
          inact            (0017) : set   1 int   & get   0
          get_inact        (0017) : set   0       & get   1 int
          inact_auth       (0018) : set   1 int   & get   0
          get_inact_auth   (0018) : set   0       & get   1 int
          inact_init       (0019) : set   1 int   & get   0
          get_inact_init   (0019) : set   0       & get   1 int
          ibss             (001A) : set   1 int   & get   0
          get_ibss         (001A) : set   0       & get   1 int
          pureg            (001B) : set   1 int   & get   0
          get_pureg        (001B) : set   0       & get   1 int
          reset            (0063) : set   1 int   & get   0


---

### Post by Lambert on 2006-02-14
Nothing I can see. I was curious if it was a power setting but not sure. You havre the same TX-power of 18dbm as I do and I have good range. 

The only thing I can suggest is trying the madwifi-ng driver which is the newer version of what you're using currently. You can find instructions by going to the tips and tricks section and search for madwifi.

Not sure this is the answer but something you could consider trying but note the warnings about the other drivers that will be uninstalled. Not sure which one's you're using

Maybe somebody else has some ideas, just bump the thread every day and hopefully they will see it. Or search the web using various keywords. atheros or madwifi would good ones to include

---

### Post by chopsbuntu on 2006-02-14
Hmm... Maybe this will give me the opportunity to buy the new Linksys WRT54GX4 with SRX400 technology. :mrgreen:

---

### Post by peanut butter on 2006-02-14
dont buy linksys. ours alwase was broken buy netgear.

u might want to try ndiswrapper it works with my wireless card (some acer ipn2000 thing)
some people say its a bad idea but i cant see why.

---

### Post by chopsbuntu on 2006-02-15
[QUOTE=peanut butter]dont buy linksys. ours alwase was broken buy netgear.

u might want to try ndiswrapper it works with my wireless card (some acer ipn2000 thing)
some people say its a bad idea but i cant see why.[/QUOTE]

Actually, I've used Linksys for years now without a single problem. I tried a Netgear wireless router once and the thing totally sucked. It ran real hot and it couldn't put out a signal strong enough to reach the other side of the room.

I'll go with my experience and stick with Linksys. :KS

---

### Post by chopsbuntu on 2006-02-18
Well I just bought the Linksys WRT54GX4 router with SRX400 blah, blah, blah.

Anyway, I was thinking... I can take my old WRT54G router and place that at the other end of the house and use it as a wireless access point, right? 

I think I can configure it that way. If so, in case the new router doesn't reach that far, I'll have the old one there to extend the range.

This will work, no?! :-k

---

