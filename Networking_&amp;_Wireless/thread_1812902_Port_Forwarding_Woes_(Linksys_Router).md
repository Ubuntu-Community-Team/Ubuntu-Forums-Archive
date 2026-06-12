---
title: "Port Forwarding Woes (Linksys Router)"
date: 2011-07-26
forum: Networking &amp; Wireless
---

### Post by ve4cib on 2011-07-26
I am trying to set up my home internet connection to forward a couple of ports to my home server so that I can access some applications while I'm on campus.  Specifically I'm trying to forward ports 65000 and 65080.  Unfortunately I feel like I'm beating my head against a wall, and am having no luck.

The problem seems to be twofold.  First, my router:

I've got a Linksys WRT45G (version 6).  Firmware is the latest version.  I've gone to the "Applications and Gaming" tab, and told it to forward ports 65000 and 65080 to the host at 192.168.1.106 (see attached screenshot).

(In case it makes any difference, I have Apache listening on 65080 and am using that as the public HTTP port since my ISP apparently blocks port 80, and my Minecraft server is listening on port 65000.)

When I run nmap on that particular host it shows:
```
PORT      STATE SERVICE
...
65000/tcp open  unknown
65080/tcp open  unknown
```

However, when I scan the router (*.1), the ports are reported as being closed.  If I try to connect to 192.168.1.1:65000 it simply times out, as opposed to forwarding the request to the server.

Frankly at this point I am stumped.  I've spent the last two days going through how-to's on Google, and have had no luck.  Does anyone else own one of these routers and gotten port-forwarding working?


__________________

The second issue I'm having is that packets from the outside world appear to be being dropped at the modem.  I've resigned myself to having to phone my ISP and ask for their help on that one.  This is lower-priority right now though.  If I can't get the port-forwarding on the router to work then there's no point worrying about the rest of it.

---

### Post by newbie-user on 2011-07-27
Port forwarding only works in the direction of wan -> lan on those home routers, I think, so you'd probably have to port scan your router from outside your home network.

Coming from my own bag of screw-ups (so please don't take this the wrong way), did you save and apply your port forwarding settings?  Once before on my own router, I clicked save, but not apply, and I couldn't figure out what was wrong for too long a time.

Also, if you have a dynamic IP at home, make sure it hasn't changed when you're trying to connect remotely.

---

### Post by ve4cib on 2011-07-27
I made sure to click "Save Settings," and even rebooted the router a couple of times to make sure.  The settings appear to have been applied.

I've got the server set up with a no-ip account, so the dynamic DNS from my ISP isn't an issue.

I hadn't thought of the WAN-->LAN only issue.  I suppose this requires solving issue #2 first.  Off to call my ISP tomorrow, I suppose.

Thanks for the input!

---

### Post by lanmangler on 2011-08-13
192.168.1.xxx would be an unusual external/public address. Normally you are forwarding from a 192.168.1.xxx to a more public domain address that your ISP serves up to you. This is the direction of the LAN-->WAN comment above.

---

### Post by ve4cib on 2011-08-13
I got everything working.  My ISP was useless at helping me, but they at least told me how to log into the modem, at which point it was easy for me to configure the modem to forwards ports to the router.  It turns out the router was configured properly the whole time, but the port-forwarding only works when the request is being sent from the WAN side of the router.

But my server is all up and running.  The web server is slow (especially when it comes to loading images), but Minecraft is running very well.

---

