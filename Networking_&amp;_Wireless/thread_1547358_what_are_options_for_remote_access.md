---
title: "what are options for remote access?"
date: 2010-08-06
forum: Networking &amp; Wireless
---

### Post by bdemers on 2010-08-06
I am on road alot, and not always with my laptop.  I want to set up a server that I can remote into and utilize the peripherals of whatever client box I happen to be on.  I would be willing to have a bootable thumb drive(its on my keyring) with an opsys on it that would hook into the printer, cdrom, etc of the host hardware and also act as the client to the server at my office, that server being in a virtual environment. I am aware of, but not familiar with, a number of terminal server clients.  Would someone be able to help me whittle down my options?  Like I said, I really need the peripherals client side.  Oh ya, needs to be gui based, as the server side has various opsys options, xp being one of them. Each option is inside a vm.  If I need to limit my opsys options at the server side, I will do that, as long as I get the client side running well.

---

### Post by endotherm on 2010-08-06
I have to nominate FreeNX/NeatX. it's nice and solid (doesn't have the wobbly feeling that VNC usually has) and runs over ssh so is rather secure both on the server end (with a standard secure configuration), and in transit. clients are available on most major platforms from nomachine.org.

I'm not entirely sure how it will work with host peripherals. surprisingly the longer I'm in IT, the less I work with peripherals. I'd smash every printer in the office were it up to me. why would anyone want to take a perfectly good document and then go an ruin it by putting it on an immutable media like paper?

---

### Post by bdemers on 2010-08-06
Thanks much for the reply.  I'm a hardware engineer and things like schematics are sometimes printed out for explanation or troubleshooting.   >>>>just an example.

---

