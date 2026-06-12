---
title: "Networkmanager not giving me WPA passphrase, lots of TLS/LEAP/etc. options instead"
date: 2010-02-21
forum: Networking &amp; Wireless
---

### Post by telex4 on 2010-02-21
I've set-up a Linksys WPC54G v5 wireless card using ndiswrapper and the appropriate Marvell driver. It seems to work ok. On my other laptop running Kubuntu with built-in wireless the routing all works fine - I just get prompted by Network Manager for the WPA passphrase and I'm away. 

However, when I try to connect to my wireless router on thix Xubuntu-based laptop I get really odd security options.

When I try to connect I get a security prompt asking me for a bewildering array of information. There are four basic authentication options under "WPA & WPA2 Enterprise": TLS, LEAP, Tunnelled TLS and Protected EAP. None of those offers a simple passphrase, they all have some combination of username & password with certificates and keys. If I try to connect to other networks in my area, some do just ask for a WPA passphrase, not that I know them to check!

Where am I going wrong?

---

### Post by kwatson512 on 2010-03-02
Are you sure you need "WPA/WPA2 Enterprise"?  Try "WPA/WPA2 Personal" and you will only be prompted for a passphrase.

---

