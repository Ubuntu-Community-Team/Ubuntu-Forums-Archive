---
title: "What VPN to use?"
date: 2011-02-11
forum: Networking &amp; Wireless
---

### Post by Jimmypooh on 2011-02-11
I want to set up a VPN (encrypted) on my Ubuntu box. I'm trying to decide what I should use. I will eventually be connecting Windows XP, Windows 7, Windows Vista and Android. I originally wanted to go with PPTP because I can connect natively with all my devices. I know a lot of people are parital to SSH, but that's not native on Anrdoid. Only PPTP, L2TP, L2TP/IPSec PSK, and L2TP/IPSec CRT are the Native options in Android. 
 
I was able to serve up with my windows laptop, but not my Ubuntu box. I tryed using pptpd but I couldn't get it to make a connection. not sure what I am doing wrong, but maybe there is a better connection out there I should be using. Does anyone have any suggesions what I should be using and a decent HowTo?
 
TIA!!!

---

### Post by Jimmypooh on 2011-02-11
Bump.

---

### Post by Jimmypooh on 2011-02-15
Bump.

---

### Post by dmizer on 2011-02-15
> **Jimmypooh said:**
> I want to set up a VPN (encrypted) on my Ubuntu box. I'm trying to decide what I should use. I will eventually be connecting Windows XP, Windows 7, Windows Vista and Android. I originally wanted to go with PPTP because I can connect natively with all my devices. I know a lot of people are parital to SSH, but that's not native on Anrdoid. Only PPTP, L2TP, L2TP/IPSec PSK, and L2TP/IPSec CRT are the Native options in Android. 
 
I was able to serve up with my windows laptop, but not my Ubuntu box. I tryed using pptpd but I couldn't get it to make a connection. not sure what I am doing wrong, but maybe there is a better connection out there I should be using. Does anyone have any suggesions what I should be using and a decent HowTo?
 
TIA!!!
SSH is the easiest on all devices including android as you do not need root to run ssh on an android phone. Also most google market file manager apps have a built in SSH client.

It is also exceptionally easy to set up and properly configure a secure SSH server whereas all the rest will require lots of config file edits.

That said, what you decide to use may be more dependent on what you need to do with the said secure connection. If all you need to do is transfer files, then SSH should be sufficient. If you need to have the remote client act like a member of the LAN, then you'll need a VPN server.

Whatever you do, I would strongly suggest avoiding PPTP VPN as the protocol isn't exactly secure. More here: [http://en.wikipedia.org/wiki/Point-to-Point_Tunneling_Protocol#Security_of_the_PPTP_protocol](http://en.wikipedia.org/wiki/Point-to-Point_Tunneling_Protocol#Security_of_the_PPTP_protocol)

---

### Post by Jimmypooh on 2011-02-15
> **dmizer said:**
> SSH is the easiest on all devices including android as you do not need root to run ssh on an android phone. Also most google market file manager apps have a built in SSH client.
 
It is also exceptionally easy to set up and properly configure a secure SSH server whereas all the rest will require lots of config file edits.
 
That said, what you decide to use may be more dependent on what you need to do with the said secure connection. If all you need to do is transfer files, then SSH should be sufficient. If you need to have the remote client act like a member of the LAN, then you'll need a VPN server.
 
Whatever you do, I would strongly suggest avoiding PPTP VPN as the protocol isn't exactly secure. More here: [http://en.wikipedia.org/wiki/Point-to-Point_Tunneling_Protocol#Security_of_the_PPTP_protocol](http://en.wikipedia.org/wiki/Point-to-Point_Tunneling_Protocol#Security_of_the_PPTP_protocol)
 
That's good information.  Am I able to VNC through an SSH tunnel?  I'm pretty new to VPN etc, so I'm not sure what the capabilities of SSH are.  Currently I use my PPTP VPN connection to transfer files and VNC to all machines on my network (1 Linux and 2 Windows).  I basically want access as if I was behind my firewall so I can do anything I need on the computers from elsewhere.

---

### Post by SeijiSensei on 2011-02-15
[OpenVPN]("http://openvpn.net/") runs on Linux [servers]("http://openvpn.net/index.php/access-server/download-openvpn-as-sw.html"), has official [clients]("http://openvpn.net/index.php/open-source/downloads.html") for Windows and Linux, and an unofficial one for [Android]("https://github.com/fries/android-external-openvpn/downloads").

The easiest way to get up and running with OpenVPN is to use a [shared static key]("http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html").

There is a PPTP [client]("http://packages.ubuntu.com/lucid/pptp-linux") and [server]("http://pigtail.net/nicholas/pptp/") for Linux, but the protocol itself has [weak security]("http://www.sans.org/security-resources/malwarefaq/pptp-vpn.php"), especially when compared to OpenVPN's use of proven SSL technologies and powerful open encryption algorithms like Blowfish or AES.

---

### Post by Jimmypooh on 2011-02-15
> **SeijiSensei said:**
> [OpenVPN]("http://openvpn.net/") runs on Linux [servers]("http://openvpn.net/index.php/access-server/download-openvpn-as-sw.html"), has official [clients]("http://openvpn.net/index.php/open-source/downloads.html") for Windows and Linux, and an unofficial one for [Android]("https://github.com/fries/android-external-openvpn/downloads").
 
The easiest way to get up and running with OpenVPN is to use a [shared static key]("http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html").
 
There is a PPTP [client]("http://packages.ubuntu.com/lucid/pptp-linux") and [server]("http://pigtail.net/nicholas/pptp/") for Linux, but the protocol itself has [weak security]("http://www.sans.org/security-resources/malwarefaq/pptp-vpn.php"), especially when compared to OpenVPN's use of proven SSL technologies and powerful open encryption algorithms like Blowfish or AES.
 
Great.  I will try to follow some HowTo's on setting up Open VPN.

---

### Post by dmizer on 2011-02-15
> **Jimmypooh said:**
> That's good information.  Am I able to VNC through an SSH tunnel?  I'm pretty new to VPN etc, so I'm not sure what the capabilities of SSH are.  Currently I use my PPTP VPN connection to transfer files and VNC to all machines on my network (1 Linux and 2 Windows).  I basically want access as if I was behind my firewall so I can do anything I need on the computers from elsewhere.
Yes, you would be able to VNC through an SSH tunnel. VNC also tends to be faster over SSH than through OpenVPN or other VPN solutions. Here's an example with the Windows SSH client (Putty): [http://helpdeskgeek.com/how-to/tunnel-vnc-over-ssh/](http://helpdeskgeek.com/how-to/tunnel-vnc-over-ssh/)

That said, I don't think you'd be able to use VNC over SSH with Android. So if that's a deal breaker for you, you'll need to consider it.

> **Jimmypooh said:**
> Great.  I will try to follow some HowTo's on setting up Open VPN.

The OpenVPN client for Android requires root. Also, even though I have a rooted device I've never actually gotten the OpenVPN client to work with my Android phone. I know it works, I just haven't taken the time to figure out why mine doesn't.

---

### Post by Jimmypooh on 2011-02-17
> **dmizer said:**
> Yes, you would be able to VNC through an SSH tunnel. VNC also tends to be faster over SSH than through OpenVPN or other VPN solutions. Here's an example with the Windows SSH client (Putty): [http://helpdeskgeek.com/how-to/tunnel-vnc-over-ssh/](http://helpdeskgeek.com/how-to/tunnel-vnc-over-ssh/)
 
That said, I don't think you'd be able to use VNC over SSH with Android. So if that's a deal breaker for you, you'll need to consider it.

Yes that would be a deal breaker.  I'll have to work on OpenVPN
 
 
 
> **dmizer said:**
> 
The OpenVPN client for Android requires root. Also, even though I have a rooted device I've never actually gotten the OpenVPN client to work with my Android phone. I know it works, I just haven't taken the time to figure out why mine doesn't.
Not a problem, I'm rooted.  Gotta love the new GB 2.3.  
 
I tried openVPN yesterday but it looked like the HowTo was missing a step.  I'll try this one tonight and see if I have any luck.  [[COLOR=#1c51a8]http://ubuntuforums.org/showthread.php?t=1685884&goto=newpost[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1685884&goto=newpost")

This will require me to download a client on both my phone and Windows machines correct?

---

