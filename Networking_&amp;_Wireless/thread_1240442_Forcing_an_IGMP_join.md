---
title: "Forcing an IGMP join"
date: 2009-08-14
forum: Networking &amp; Wireless
---

### Post by jpdw on 2009-08-14
Hi,

Is there a command-line means to get a Linux/Ubuntu client PC to send an IGMP joins and leaves ?  -- *without* having to install a full-on client such as VLC.

In case this sounds a strange request, I'm trying to perform some specific testing that needs m/casts being routed by the L2/3 switch - but I'm not interested in actually using the m/cast streams and the device I need to use is, while running Linux, quite .. er.. "computationally challenged" (headless embedded type system).

Thanks.

---

### Post by nixscripter on 2009-08-15
I bet you could write one if you knew a little bit of C.

[http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/html_single/Multicast-HOWTO.html#ss7.1](http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/html_single/Multicast-HOWTO.html#ss7.1)

Unfortunately, that's the best I can do.

---

### Post by jpdw on 2009-08-16
I'd thought about that but I was hoping to avoid that if there was a command line tool readily available.  Not just through lazyness but also because that adds another set of tasks needed before I can get on with the actual m/cast tests I want to do. 

And it's been a while (years) since I did much with C....!

---

### Post by nixscripter on 2009-08-16
There are also libraries for all the major scripting languages (Perl, Python, Ruby, TCL, etc.) which allow mangling of IP packets. If you know one of these, it might be easier to write one that way...

---

### Post by jpdw on 2009-08-19
I might look in that direction -- been a while since I did Perl also, but a good excuse to learn a bit of Ruby sounds fun!

However, having re-read the M/CAST docs & IGMP spec (I was on a long journey !) , I think it might be more difficult so possibly the longer C route might be a way to go - even with the re-learning curve.

Thanks all for the suggestions.

---

### Post by bab1 on 2009-08-19
> **jpdw said:**
> Hi,

Is there a command-line means to get a Linux/Ubuntu client PC to send an IGMP joins and leaves ?  -- *without* having to install a full-on client such as VLC.

In case this sounds a strange request, I'm trying to perform some specific testing that needs m/casts being routed by the L2/3 switch - but I'm not interested in actually using the m/cast streams and the device I need to use is, while running Linux, quite .. er.. "computationally challenged" (headless embedded type system).

Thanks.

Just a guess on this, but have you looked at [[COLOR="DarkSlateGray"]_nemesis-igmp_[/COLOR]]("http://manpages.ubuntu.com/manpages/intrepid/man1/nemesis-igmp.1.html")

---

