---
title: "Is it dangerous not to put Network Manager to sleep &quot;properly&quot;?"
date: 2009-06-11
forum: Networking &amp; Wireless
---

### Post by aysiu on 2009-06-11
So there's this bug that cropped up in Intrepid and has persisted into Jaunty whereby some folks have had wireless take a very long time (sometimes over 30 seconds) to come back after a resume from suspend to RAM.

You can see the Launchpad bug here:
[network manager slow to reconnect after suspend/resume](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274405)

I thought I had a good workaround (adding *iwlist scanning* to one of the resume scripts), but it seems to work only intermittently.

A better (in terms of practical results) workaround altogether seems to not put Network Manager to sleep at all. Would that damage Ubuntu in the long-term somehow if I did that?

By the way, if I take it out altogether, I get weird error messages about sky2, so my workaround for that is to ```
rmmod sky2
``` during suspend and ```
insmod sky2
``` during resume.

---

### Post by aysiu on 2009-06-12
Bump

---

### Post by Iowan on 2009-06-12
Once you get a high post count or Staff designation, people (me for one - sorry) assume you know more about the subject than they (I) do. I've been avoiding letting my laptop hibernate or sleep - seems to cause issues...
G'luck.

---

### Post by kerry_s on 2009-06-12
its the dhclient that actually causes the problem, go into /etc/dhcp3/dhclient.conf read the "man dhclient.conf" and try some of the settings.

i don't use a network manager & mines connected instantly on resume. my wireless is a usb zd1211rw chip, i take it out at suspend or it will hang the system.
in dhclient.conf i use:
[B]timeout 30;
initial-interval 1;[/B]

i don't think not putting the network manager to sleep would hurt & if it works, go for it. that is the way suspend & resume is suppose to work, but then again nm has always had issues.

---

### Post by aysiu on 2009-06-12
> **Iowan said:**
> Once you get a high post count or Staff designation, people (me for one - sorry) assume you know more about the subject than they (I) do. Yeah, I've noticed that. It's kind of annoying. Most of the staff are really knowledgeable. Unfortunately, I am not. > **kerry_s said:**
> its the dhclient that actually causes the problem, go into /etc/dhcp3/dhclient.conf read the "man dhclient.conf" and try some of the settings.

i don't use a network manager & mines connected instantly on resume. my wireless is a usb zd1211rw chip, i take it out at suspend or it will hang the system.
in dhclient.conf i use:
[B]timeout 30;
initial-interval 1;[/B] Unfortunately, that's a bit above my head (both the file and its *man* page). I have no idea what any of that means.

> i don't think not putting the network manager to sleep would hurt & if it works, go for it. that is the way suspend & resume is suppose to work, but then again nm has always had issues. Thanks for the reassurance. So far I haven't *noticed* any issues...

---

