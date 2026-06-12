---
title: "vpnc stopped working after upgrading to 9.04"
date: 2009-04-29
forum: Networking &amp; Wireless
---

### Post by bryonak on 2009-04-29
My vpnc was working last week with 8.10, after upgrading to 9.04 I get ```
vpnc: no response from target

```
I've tried the NAT traversal trick and also changing the port...
The VPN server responds to ping and it's VPN port is open.
It doesn't matter if I enter the correct password or not, it simply times out.
No luck with vpnc 0.3.3 and 0.4 either...

My current .conf looks like this:
```

Interface name tun0
IKE DH Group XXX
Perfect Forward Secrecy nopfs
IPSec gateway XXX
IPSec ID XXX
IPSec secret XXX
NAT Traversal Mode cisco-udp
Xauth username XXX

```

Commenting out the IKE, Forwarding or NAT lines doesn't help (as well as changing the port).

Could it be some permissions (AppArmor/SELinux) issue? I didn't fiddle with those, but read somewhere that allowing vpnc to communicate with dbus solved a similar problem, but that was about 3 years old...

---

### Post by jonobr on 2009-04-29
Hello


Did you ever get to the bottom of this?

This is one thing which is stopping me from going to 9.04

---

### Post by bryonak on 2009-04-30
> **jonobr said:**
> Did you ever get to the bottom of this?

This is one thing which is stopping me from going to 9.04

Nope, I'm out of ideas right now.


Tried to recompile it with SSL, nothing. Besides, it shouldn't be needed, as the same binary works on another 8.10 machine without problems. So I guess it's a 9.04 specific problem...

I don't use the default nm-applet... it might work with it's vpnc module, but that's no use to me because it drops the connection all the time.

Starting with --application-version "Cisco Systems VPN Client 0.3:WinNT" doesn't help either.

Running vpnc as root makes no difference.

Next thing I'll try is Cisco's proprietary client, though I've never been able to get it to run before.

I suspect it has something to do with permissions, since I've tried all the suggestions on Launchpad's vpnc tracker except the dbus stuff, because that refered solely to the NetworkManager.

Anyone got an idea about what could help?

---

### Post by bryonak on 2009-04-30
SOLVED (where's that button gone?!)


With a conf file like the one in my OP you should have no problems connecting via vpnc (most people have difficulties because they miss the cisco-udp entry)...


I've spent a lot of time figuring things out until a friend suggested double checking the connection settings on the university site. They changed them and did a really awesome job of communicating it to us -.-

---

### Post by jonobr on 2009-05-01
Thanks for the reply,
I did the upgrade before checking the response, 
Im running kvpnc.
I dont know If I am being a but sensitive but have notice the thing stall on me a few times, and I had to disconnect and reconnect.
Im seeing it is working, but Ill be watching for reliability

Cheers

---

