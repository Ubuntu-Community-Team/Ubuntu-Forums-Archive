---
title: "What IP address do i need in order to connects SSH from an outside network?Thanx"
date: 2013-03-16
forum: Networking &amp; Wireless
---

### Post by Aphexlog on 2013-03-16
And how is it labeled and how do i find it? Im noobish guys so be gentle with the slang.
    Thanx

---

### Post by TheFu on 2013-03-16
First be certain you did this stuff: [https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

Don't run on port 22 or use your router to translate from some other port on the WAN side to port 22 internally. This makes life easier.

You need to know the public IP for your router. It may be mostly static or DHCP with changes happening every 12 hours.  Most people use a dynamic DNS service to make finding their home WAN IP address easier.  I setup Mom's router with DynDNS, so I could remotely access her Linux machine easier.  It is a no-brainer.  Many home/SOHO router firmwares have this capability built-in - dd-wrt, tomato and openWRT have it too.  Those are aftermarker, F/LOSS firmwares for popular routers. Usually running dd-wrt or the other after-marker firmwares are much more secure than running whatever the router maker provides.

You can make a note of the public IP and just use that if you like too.  Of course, if your "public IP" is not really a public IP - like most cellular data networks provide, then there is nothing you can do to remote into your home PC. RFC 1918 [https://tools.ietf.org/html/rfc1918](https://tools.ietf.org/html/rfc1918) is where you can see which IPs are meant for private network use, hence those will not be routed over the public internet.

I wrote up a "how to secure ssh" article here [http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures) that might be useful too. It may not be easy to understand, so have wikipedia open to look up any terms you do not understand.  Google is your friend too.

Clear as mud?

---

