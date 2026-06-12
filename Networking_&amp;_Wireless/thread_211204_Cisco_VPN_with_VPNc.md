---
title: "Cisco VPN with VPNc"
date: 2006-07-07
forum: Networking &amp; Wireless
---

### Post by kd7swh on 2006-07-07
I have been trying to get a working vpn tunnel going on my University's wireless.

I am using the Kvpnc front-end (gui) for vpnc and it seems to be straight forward but KVPNc closes itself whenever I try to import the cisco pcf profile. Because of this, I made a new profile with the information from the profile I was given. The only difference was I used the unencrypted version of the group password (instead of the encrypted cisco version) KVPNc connected to the gateway after a lot of trial and error but there was no ip address assigned to the tunnel. 

Is there an easy fix for this? Is it the DHCP sever or the configuration of kvpnc?

Any help would be great!

- Jon

(University of Montana)

---

### Post by ape on 2006-07-08
I would try just using vpnc and see if you're able to connect successfully to rule out problems with kvpnc.

---

### Post by kd7swh on 2006-07-11
the trick in my case was the local port and nat-t. I figured it out

---

### Post by chslaxcoach on 2006-07-18
After struggling for quite a while to get Cisco VPN Client to install, I was able to install this fairly quickly on Ubuntu.  My company, doesn't support the Linux client (groan) especially since Linux is such a huge part of our business.

This is realy complete how-to from the Gentoo folks.  It also shows how to convert your Cisco .pcf to a vpnc convert.

[http://www.gentoo.org/doc/en/draft/vpnc-howto.xml](http://www.gentoo.org/doc/en/draft/vpnc-howto.xml)

I was able to install vpnc painlessly on Dapper with 

sudo apt-get install vpnc

I still haven't done all the routing stuff explained in the how-to, but I can get in and VNC to my work computer.

Good luck all.

---

### Post by tamasgal on 2008-01-23
If vpnc is not working, try this:
vpnc --natt-mode cisco-udp your_config.conf

---

### Post by bingoUV on 2008-03-16
The URL of the gentoo doc has changed. The new one is _[http://www.gentoo.org/doc/en/vpnc-howto.xml](http://www.gentoo.org/doc/en/vpnc-howto.xml)_

---

### Post by SomeGuyOnAForum on 2008-04-25
From the vpnc man page:

```
       (configfile only option)
              your group password (obfuscated)
       conf-variable: IPSec obfuscated secret <hex string>
```

There's no need to decrypt your group password.

---

### Post by Jamie Jackson on 2008-04-26
I had been monkeying around with vpnc config files until I found out that NetworkManager had really slick vpnc support via network-manager-vpnc. No more config files, just an intuitive dialog. Just thought I'd throw that out there in case anyone missed it.

---

### Post by Joel Duckworth on 2008-05-14
Have you tried this with Hardy? I'm unable to get it working

---

### Post by Jamie Jackson on 2008-05-15
> **Joel Duckworth said:**
> Have you tried this with Hardy? I'm unable to get it working

Yes, my configuration continues to work after my Hardy upgrade (from Gutsy).

---

