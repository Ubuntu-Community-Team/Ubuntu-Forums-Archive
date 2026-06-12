---
title: "HELP - how share my ubuntu wifi connection with a macintosh"
date: 2010-06-07
forum: Networking &amp; Wireless
---

### Post by grikdog on 2010-06-07
I have a Dell Inspiron 1525 running Jaunty Jackalope.  I have a good working wireless connection.

My daughter has a lot of iPod tunes stored on an old white chiclet Macintosh, which she needs to download to her iPod.  Because the iPod is "corrupt" (meaning it was last connected to Windows!), we need to connect to internet.

Simplest way to do that would SEEM to be to plug an Ethernet cord between the two machines and let her Mac access internet via this Dell.

My experience with ethernet is, either it works out of the box, or it doesn't.  If it doesn't, I have no idea how to make the connection work.

What do I have to do on BOTH the Jaunty and OSX sides to make the connection?  Thanks!!

I have a deadline.  I must solve this before my daughter takes a school trip to Japan on SATURDAY.

Please help!

---

### Post by Iowan on 2010-06-07
Hey, another Iowan - and only ~30 miles away! I've probably bugged you already... but I digress.
Are you using straight or crossover cable? Some gigabit cards will auto-configure, the rest (probably) require a crossover cable.

---

### Post by grikdog on 2010-06-07
> **Iowan said:**
> Hey, another Iowan - and only ~30 miles away! I've probably bugged you already... but I digress.
Are you using straight or crossover cable? Some gigabit cards will auto-configure, the rest (probably) require a crossover cable.
I just plug my standard Ethernet cable into both the Dell and the Mac.  The Mac I can trust to find a connection, if it's there.  Mac-to-Mac ethernet is just plug the cable ends into the right socket.

I don't know how to configure the Ubuntu end.  Or what to configure.  Etc.

It's not like a null-modem cable, it's pure Ethernet.  I think it's eth0, whatever that is, but no idea what my IP settings are, or why DHCP isn't setting this up for me.  Of course, the docs on the 'net are ancient, and expect Feisty-friendly, not Jackalope-friendly, dialogs.

Not to mention the ubiquitous "Consult your System Administrator."  By default, I AM my system administrator.  I qualified for the title by downloading Ubuntu. ::-))

---

### Post by Iowan on 2010-06-07
Do you, perchance, have a hub/switch (and another cable) that you could throw between the two boxes - just to see if it makes a difference?

---

### Post by grikdog on 2010-06-09
I got this old iBook onto the internet by ethernet-ing directly to the DSL modem.  There's no setup, it seems to work just by discovery.

I'm still interested in knowing how to configure a local LAN with Ubuntu on this end and OSX 10.3.9 on that end.  

Nothing wrong with the cable.  I had it between two Macs a few years ago, and it worked like a charm, out of the box.

---

