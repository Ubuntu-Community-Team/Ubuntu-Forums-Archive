---
title: "Ethernet is a joke"
date: 2009-02-05
forum: Networking &amp; Wireless
---

### Post by lonegeek on 2009-02-05
Ubuntu used to be connected from a router, with static ip set. No problems ever.

Router died.

So now i'm trying cable modem to ubuntu.

Nothing works. I've even copied exact ip, subnet, gateway , dns and set it to static ip.

It just never connects.

Any help?

---

### Post by yther on 2009-02-05
Since it's a cable modem, I think maybe you'd need to set up PPPoE.  In my experience, it's much less hassle if you can configure this in the router than in the OS, but since yours is no more...  ;)

I haven't ever done this in any Linux, but I did find [this document]("https://help.ubuntu.com/community/ADSLPPPoE") that seems to relate to what you need.  It may be as simple as "sudo pppoeconf" and plugging in your login info.

---

### Post by lonegeek on 2009-02-05
> **yther said:**
> Since it's a cable modem, I think maybe you'd need to set up PPPoE.  In my experience, it's much less hassle if you can configure this in the router than in the OS, but since yours is no more...  ;)

I haven't ever done this in any Linux, but I did find [this document]("https://help.ubuntu.com/community/ADSLPPPoE") that seems to relate to what you need.  It may be as simple as "sudo pppoeconf" and plugging in your login info.

that is for a dsl modem.

---

### Post by odium1 on 2009-02-05
i'm pretty sure it's a problem with the latest kernal update.. I have a Dell 1501 and my wireless is working but eth0 isn't. it stopped working after I updated last night. I've tried quite a few things but nothing has worked so far. I'm going to keep looking around until *hopefully* someone figures something out.

---

### Post by dmizer on 2009-02-05
Some cable connections (and even FTTH) use PPPoE.

---

### Post by jrusso2 on 2009-02-05
Until you get it setup then use DHCP with the router being the server. Once its working you can change everything to static.

---

### Post by lonegeek on 2009-02-05
1. I used to use a wired connection. Never had problems.

I've never needed to do ppoee (sp?) in the past. Nor do I need it on my mac which I'm currently typing from btw.

---

### Post by dmizer on 2009-02-05
Does your ISP have a [MAC address](http://en.wikipedia.org/wiki/MAC_address) filter on their service? Many ISPs only allow you to have one or two computers registered on their server. If you connected your Mac to the service first after your router died, it's MAC address will be registered with the ISP, and you won't get an IP with Ubuntu.

Are you getting an IP address? To check, please post the output of:
```
sudo ifconfig
```

---

### Post by sedawk on 2009-02-05
Then it should be straight forward:
Open a text terminal on the mac and use standard unix/linux commands
to check/compare configurations,e.g. check the output of

```

ifconfig eth0
route

```

Still I'm surprised that the connection between the modem and
the router/PC/Mac does not require authentication.
So you do not have a username and a password from your cable
company that you had to enter in the router configuration or some
MacOS dialog?

---

### Post by lonegeek on 2009-02-05
> **sedawk said:**
> Then it should be straight forward:
Open a text terminal on the mac and use standard unix/linux commands
to check/compare configurations,e.g. check the output of

```

ifconfig eth0
route

```

Still I'm surprised that the connection between the modem and
the router/PC/Mac does not require authentication.
So you do not have a username and a password from your cable
company that you had to enter in the router configuration or some
MacOS dialog?

That terminal command doesnt work.

I've only had to put account number in when i first got it. That was on a web page however. But that wasn't connecting to computer or something, that was just registering account.

---

### Post by yther on 2009-02-05
Stupid question time for me:  Is the cable that connects your Mac to the "modem" a crossover cable?  I remember having a DSL gateway that required one; plugging directly in with a regular CAT-5 cable wouldn't work.

---

### Post by aesis05401 on 2009-02-05
Or try power cycling the modem after unplugging from the mac and before plugging into your nix box.  

My residential ISP attempts to charge additional fees for every machine at a location, and now that your router is gone you may be getting flagged.  This is assuming you are not working on a static address.

Commercial accounts in my area do not have this limitation, and it is not widely publicized.

---

### Post by jrusso2 on 2009-02-05
> **yther said:**
> Stupid question time for me:  Is the cable that connects your Mac to the "modem" a crossover cable?  I remember having a DSL gateway that required one; plugging directly in with a regular CAT-5 cable wouldn't work.

Modern routers don't seem to require the use crossover cables anymore.

---

