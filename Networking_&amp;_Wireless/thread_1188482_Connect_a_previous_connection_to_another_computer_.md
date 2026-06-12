---
title: "Connect a previous connection to another computer by ethernet."
date: 2009-06-15
forum: Networking &amp; Wireless
---

### Post by dragos240 on 2009-06-15
Hello!

It's dragos240 again, I wanted to know how to do this:

1. Have a previous internet connection on one computer,

2. Plug in an Ethernet cable to that computer and to another,

3. And somehow send the internet connection into the other computer as if it were a router.

I have a wireless connection, and my netbook has arch, it doesn't have any wireless connectivity yet, and I'm trying to figure that out through the arch wiki. I just need a solid ethernet connection delivered from another computer to this one. How can this be done?

---

### Post by scrooge_74 on 2009-06-15
There are tutorials to make the first box into a router. Look for instructions on the net, I did that a few years ago, but I dont have it at hand. 

The first box will give address to the second either dynamically or static IP.  If I remember correctly you can give the wired card an IP and then tell the second box to use that IP as its gateway, plus also you need to give the second box an IP in the same range.  Also you need to configure the 1st box firewall to let traffic go to the second box (i did that using firestarted).

I do remember I never managed to get the DNS server working (so it would assign IPs to the second PC automatically, but I was a big NOOB then)

First box will act as a proxy server and will route traffic to the second one, you can even block traffic to the second one using the first one.

---

### Post by dragos240 on 2009-06-15
> **scrooge_74 said:**
> There are tutorials to make the first box into a router. Look for instructions on the net, I did that a few years ago, but I dont have it at hand. 

The first box will give address to the second either dynamically or static IP.  If I remember correctly you can give the wired card an IP and then tell the second box to use that IP as its gateway, plus also you need to give the second box an IP in the same range.  Also you need to configure the 1st box firewall to let traffic go to the second box (i did that using firestarted).

I do remember I never managed to get the DNS server working (so it would assign IPs to the second PC automatically, but I was a big NOOB then)

First box will act as a proxy server and will route traffic to the second one, you can even block traffic to the second one using the first one.

Could you give me a link, or at least tell me what you searched for?

---

### Post by scrooge_74 on 2009-06-15
The wonders of keeping bookmarks from years past.

I think this is the [one]("http://users.telenet.be/mydotcom/howto/lanconnect/router/linux.htm") I used to get me started.

Is old, but should give you an idea

---

### Post by dragos240 on 2009-06-15
> **scrooge_74 said:**
> The wonders of keeping bookmarks from years past.

I think this is the [one]("http://users.telenet.be/mydotcom/howto/lanconnect/router/linux.htm") I used to get me started.

Is old, but should give you an idea
I tried it, and with no success :(

---

### Post by superprash2003 on 2009-06-16
you could use firestarter to setup internet connection sharing or use this [http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

---

### Post by dragos240 on 2009-06-16
> **superprash2003 said:**
> you could use firestarter to setup internet connection sharing or use this [http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)
Firestarter nor that guide worked, I'm thinking it has something to do with this ethernet cord. Is there another way I can do this, assuming the issue is just me not doing it right?

---

### Post by superprash2003 on 2009-06-27
do you get any error when trying?? we could troubleshoot!!

---

