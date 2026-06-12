---
title: "can connect to network, but no internet"
date: 2006-07-11
forum: Networking &amp; Wireless
---

### Post by OneSeventeen on 2006-07-11
I'm using network manager on my wireless laptop using the Ubuntu broadcom drivers.  At home, they work perfectly, at work they are okay, but at my parent's house and at my church I can't get on the internet.

I can get on the network quickly and easily, but I can't get on the internet.

If I reboot into windows, it gets on the web fine, but windows tells me it connects, then it tells me it doesn't have an internet connection and I may want to contact the admin, then the notification tray flickers and the internet works (in windows).

Is there some sort of extra handshake going on?  One network was WEP encrypted (which I had the correct password for) and the other was open.

Once again, everything always works at home, but at church it only connects to the network and not the internet.

Any ideas?

---

### Post by Rik Giles on 2006-07-11
I am fairly new to ubuntu, but when ever I have problems with accessing the Net it's usually because I haven't updated my DNS settings..

Windows is quite good with updating DNS records, but when accessing the Net at work i always have to manually update the DNS..

Try pinging 64.233.167.99 (google) when your at your alternate location.. if you get a response it's most likely your DNS is pointing to the wrong address.

---

### Post by OneSeventeen on 2006-07-12
I've tried pinging IP's in the past without any luck.  :(

How would I get Ubuntu to refresh DNS settings anyway?

Are there any other network settings I could refresh/flush?

---

### Post by OneSeventeen on 2006-07-22
I figured it out, apparently network manager was not too worried about not getting a network address, so it just sat there instead of trying to get an IP from the DHCP server.

In windows, it tells me it can't get a network address, but windows networking keeps trying until it gets one.

When I disabled network manager and used the built-in networking tools, it worked.  Of course now I'll probably have to go back to rebooting every time I switch between networks....

Any ideas how to get network manager to try harder to get an IP?

---

