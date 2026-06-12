---
title: "Problems with pci wifi card (GN-WP01GS)"
date: 2009-11-27
forum: Networking &amp; Wireless
---

### Post by QuintusFabius on 2009-11-27
Hi all,

I'm having some problems and would really appreciate help. I'm putting together a new machine, and got an AirCruiser G PCI Gigabyte wireless card (GN-WP01GS).

It has basically worked under windows, but there were minor intermittent problems. I've updated the drivers and hopefully that will help. Under karmic however, i've had NO more than a few minutes of working internet - and even then at 5kbps-type speeds. For the most part, ubuntu has said that it's connected (only 55% or so) but I'm unable to establish a connection to websites or other computers. My NC10 netbook has a perfect (95%+) connection another 30ft away from where this computer is...

Reading online, it seems that many claim this card works perfectly under ubuntu and a few people seem to be having problems similar to mine. If I can avoid returning this card, that would be so great!

Any suggestions for getting this to work? Thanks!

---

### Post by QuintusFabius on 2009-11-27
To clarify: it seems to work perfectly under ubuntu for under a minute each time I boot up, but it soon fails. I just tried ndisgtk and got an error "Unable to see if hardware is present" when trying to install the rt61.inf file for my windows drivers. I saw someone mention this exact problem on newegg - though most people were saying it works fine under ubuntu.

Any Ideas?

---

### Post by dearingj on 2009-11-27
I've heard that using [WICD]("http://packages.ubuntu.com/karmic/wicd") rather than Ubuntu's default Network Manager can help with wifi problems. Perhaps you should try that.

---

### Post by QuintusFabius on 2009-12-10
> **dearingj said:**
> I've heard that using [WICD]("http://packages.ubuntu.com/karmic/wicd") rather than Ubuntu's default Network Manager can help with wifi problems. Perhaps you should try that.

Ok. I switched to wicd and it hasn't fixed the problem - though I like its interface a bit better than the default wireless manager. It turns out that my Internet works on two other wifi routers i've used, just not the one at my folks' place. FYI, their router is on the older side, probably 5-6 years old now. The other two i've used are around 1.5 and .5 years old.

Now I've started noticing a smaller problem - this is on my home router (TEW-631BRP). Every 1-5 minutes or so, all applications loose connectivity (even though wicd never reports an interruption, 92-98% solid 24/7). Every so often there is this 10-30 second period where firefox, empathy, etc, all are unable to use the Internet. Firefox just sits saying "connecting to ..." or "waiting for ..." for the full half minute and then finally finishes loading. When it starts working again, speeds are lightening fast... until it happens again.

I've tried disabling ipv6 (using "sudo su" and then "echo 1 > /proc/sys/net/ipv6/conf/all/disable_ipv6"); no effect. What should I try for these problems?

Thanks,

---

### Post by dearingj on 2009-12-14
Maybe you should post your new problem in a separate thread. It doesn't seem to be getting much exposure here.

---

