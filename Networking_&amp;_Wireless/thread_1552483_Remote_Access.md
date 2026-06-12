---
title: "Remote Access?"
date: 2010-08-13
forum: Networking &amp; Wireless
---

### Post by telmore007 on 2010-08-13
I like playing around in linux. I have Windows 7 Home Premium which does not have Remote access. I want to be able to control my computer from my android phone. Which verison would be best. I was going to try out Linux Mint 9.

Thanks,

---

### Post by paulisdead on 2010-08-13
Well you'd need to install openssh-server for a remote command line, or a vnc server for an actual remote desktop.  This will only work in your internal network.  If you want to access it via the internet you have to configure your router or cable/dsl modem to forward the appropriate ports to the machine you want to access remotely.  Then you'll have to find your external IP address, and hit that with ssh or vnc.  You might look into dyndns so you can access it by a hostname instead of an IP.  There's plenty of guides and documentation for this so hopefully that gets you going.

Things like SSH and VNC are really standardized, so the distro is pretty much irrelevant, so sure give mint a shot if you want.

As for the apps, I use connectbot for SSH access.  I have android vnc viewer installed, but still haven't bothered using it, as ssh is faster.  I also recommend gmote, so you can use the touchscreen on your phone as a remote control to a pc over wifi.  Also Transdroid is friggin' awesome!  Control the transmission bittorrent app from your phone.

---

### Post by mikewhatever on 2010-08-14
> **telmore007 said:**
> I like playing around in linux. I have Windows 7 Home Premium which does not have Remote access. I want to be able to control my computer from my android phone. Which verison would be best. I was going to try out Linux Mint 9.

Thanks,

What does Linux Mint has to do with your Android phone?

---

