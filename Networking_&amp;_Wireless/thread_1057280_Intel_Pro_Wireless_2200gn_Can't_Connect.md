---
title: "Intel Pro Wireless 2200gn Can't Connect"
date: 2009-02-01
forum: Networking &amp; Wireless
---

### Post by jcoman on 2009-02-01
I can't seem to get my Intel Pro Wireless 2200GN which is on a HP Pavilion to connect via my wireless network.

I have searched many of the messages and a number of them report that the 2200gn works great right out of the box.

I have never been able to ping my network with this card although I HAD the little icon in the upper right reporting I had good strength and it showed a connection.

I am using 8.1.  

I have tried so many commands in terminal mode that perhaps I have it sooo messed up it will never work.  

Just a couple of questions.  Any way to get this computer network back to square one?  Any other suggestions would also be appreciated.

Thanks,

jcoman

---

### Post by mikewhatever on 2009-02-01
Wireless by intel usually works out of the box. It's hard to advise how to undo the changes, given we don't know what's been done.
What was the problem exactly? Did you get an IP? Was the authentication refused? Did you get connected but couldn't browse?

---

### Post by jcoman on 2009-02-01
> **mikewhatever said:**
> Wireless by intel usually works out of the box. It's hard to advise how to undo the changes, given we don't know what's been done.
What was the problem exactly? Did you get an IP? Was the authentication refused? Did you get connected but couldn't browse?

I have had many problems because I have been trying many things over the last few days.

As it stands right now I am trying to setup my MythTv front end.  It works fine using wired ethernet.

I can ping my backend with wired.  I can also ping my router.

Frontend, backend and router use fixed IP.  Backend = 10.0.0.119, Fronend wired = 10.0.0.112, frontend wireless = 1.0.0.113.  Router = 10.0.0.201.

When I view my setting using network connections all seems to be okay.
subnet = 255.255.255.0
Gateway = 10.0.0.201

Wireless is set to "Auto 'my network name'
SSID = 'my network name'
Mode = Ad-hoc
BSSID = blank (no information)
MAC address = 00:0E:35:F3:24:FB

I don't know how to tell if I got authentication.

I am using a fixed IP, but the IP doesn't show up when I run the command ifconfig. My IP does show up on the wired connection.

Thanks in advance for any help.


jcoman

---

