---
title: "Wireless connection time"
date: 2011-07-04
forum: Networking &amp; Wireless
---

### Post by dlrocket89 on 2011-07-04
Hi everyone,

I just finished installing Ubuntu 11.04 side by side with Win7 on my wife's HP Mini.  So far, my only complaint is that when the computer is suspended in Windows, the wireless connection is picked back up quickly.  By the time you enter your password, the connection is reestablished, so you can open a webpage as soon as you're logged on.  

With 11.04, the connection doesn't start reestablishing until after you're logged in.  Because of that and the fact that it takes 3x's longer to establish the connection, with 11.04 you log in and then sit for a minute.  I know it seems like a small thing, but is there a way to not close the wireless connection when the llid is closed and the computer is suspended?  Thanks!

Dustin

---

### Post by dFlyer on 2011-07-04
I can't answer your question as on my system, I have internet wifi access as soon and my screen appears? It's strange you have to wait a minute. Have you checked your configuration?

---

### Post by dlrocket89 on 2011-07-04
> **dFlyer said:**
> I can't answer your question as on my system, I have internet wifi access as soon and my screen appears? It's strange you have to wait a minute. Have you checked your configuration?

Wouldn't know where to start to check the configuration.  It connects automatically, I know that much.

---

### Post by MaindotC on 2011-07-04
Anything that deals with the video driver (such as the hardware suspend function) has habitually been sensitive in open source systems.  Video quality, power consumption, frequency, suspend/shutdown - all that goes through the video driver and it's millions of components and dependencies.  I don't know of a way to modify this but I would start with the documentation for your video driver.  If you're not using a fully-Linux-compatible-hardware-built system I think you should be thankful it's functioning to the degree that it is.

---

### Post by dlrocket89 on 2011-07-04
> **MaindotC said:**
> Anything that deals with the video driver (such as the hardware suspend function) has habitually been sensitive in open source systems.  Video quality, power consumption, frequency, suspend/shutdown - all that goes through the video driver and it's millions of components and dependencies.  I don't know of a way to modify this but I would start with the documentation for your video driver.  If you're not using a fully-Linux-compatible-hardware-built system I think you should be thankful it's functioning to the degree that it is.

Hah, fair enough.  Didn't know it all went through the video driver.  Using restricted drivers right now, would it help if we switched to the open source version?

---

### Post by MaindotC on 2011-07-04
> **dlrocket89 said:**
> Hah, fair enough.  Didn't know it all went through the video driver.  Using restricted drivers right now, would it help if we switched to the open source version?

That would probably require a lot more support than this forum can offer.  I've always used the restricted drivers and I just pray that the manufacturer is kind and doesn't inject a line of code that jacks up the frequency and power so I get a blowout and they say "hahaha should have gone with Windows loser".

I've heard a lot of great stories about the open source drivers but I've not taken the time to test them.  If you try the open source drivers I advise you allocate time to visit their respective support forums and/or IRC channels.  You may also want to make sure you have a decent list of sites to visit for support, and/or consume documentation.  The answers are there - it's just a matter of how much effort you are willing to put forth to find them.  Obviously I am not willing to put forth that type of effort although I do believe supporting the open-source drivers are the moral thing to do.

If you really want to get the answer quickly I believe you can purchase support from various Linux support operations - especially some LoCo teams that [offer paid support ](http://ubuntu-massachusetts.com/support/paid/)(and I would imagine their terms of service offer some definition of accomplishing what was asked).

---

