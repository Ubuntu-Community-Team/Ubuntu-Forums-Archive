---
title: "Where Are the Maverick Printer Drivers?"
date: 2010-07-25
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by LaneLester on 2010-07-25
I just installed a fresh copy of 64-bit Alpha2. Everything looks good, except when I added a printer, there were no printer drivers displayed. I had added the foomatic-db and foomatic-db-gutenprint packages, which usually provide the drivers I need.

Is there a fix, or am I not going to be able to print in 10.10 for now?

Lane

---

### Post by cariboo on 2010-07-26
What make/model of printer do you have?

My Brother HL-5250dn automagically downloads the drivers from the manufacturer.

---

### Post by LaneLester on 2010-07-26
I have a Samsung ML-2151N. It has its own network card, so it's accessed through the LAN. The drivers showed up with Maverick Alpha 1, so it's very strange.

This time the list of drivers had only a "Generic" manufacturer. Usually a host of makers is listed from which you select your own and then get the model number's driver.

Based on your answer I tried the option to search for drivers to download. I entered my printer model, and it returned it in the pulldown list (which had only that model). But the next window had no drivers listed where they were supposed to be.

Another strangeness is I can't log on to the CUPS system through Firefox, something I've done for a long time. When I enter my username/password, the prompt comes back like I've entered the wrong stuff... I haven't.

Lane

---

### Post by philinux on 2010-07-26
> **LaneLester said:**
> I just installed a fresh copy of 64-bit Alpha2. Everything looks good, except when I added a printer, there were no printer drivers displayed. I had added the foomatic-db and foomatic-db-gutenprint packages, which usually provide the drivers I need.

Is there a fix, or am I not going to be able to print in 10.10 for now?

Lane

I had this in yesterdays updates. This was from my chroot and I've not rebooted yet. Try reinstalling cups. This might not have been bugged yet.
```
Setting up cups-common (1.4.4-2) ...
Setting up cups-client (1.4.4-2) ...
Setting up cups-bsd (1.4.4-2) ...
Setting up cups (1.4.4-2) ...
 * Starting Common Unix Printing System: cupsd                                                                                FATAL: Could not load /lib/modules/2.6.32-24-generic/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/2.6.32-24-generic/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/2.6.32-24-generic/modules.dep: No such file or directory

```

---

### Post by LaneLester on 2010-07-26
Thanks, Phil. Synaptic thinks the cups 1.4.4-2 is just fine. Interestingly, CUPS installed my local Epson automatically without my doing anything at all. It just showed up in the printer list. I've never that before.

Other than not being able to log in at [http://localhost:631/admin/](http://localhost:631/admin/) CUPS seems to be working. Therefore, it seems more a driver package error than a CUPS error.

But what do I know? :o

Lane

---

### Post by cariboo on 2010-07-26
There were quite a few cups updates on the 24th, so that may be the cause of your problem. I would suggest reporting a bug against cups.

My Brother is also a networked printer, and the drivers show up in jockey.

---

### Post by philinux on 2010-07-27
Just rebooted into Mav and yes my epson r200 is missing and a load of others, there are only a handful of Epson drivers available. Must be cups not configured properly yet.

It must be the package cups-driver-gutenprint I guess. I reinstalled the package anyway.
```
Preparing to replace cups-driver-gutenprint 5.2.5-1ubuntu1 (using .../cups-driver-gutenprint_5.2.5-1ubuntu1_amd64.deb) ...

Unpacking replacement cups-driver-gutenprint ...

Processing triggers for man-db ...

Setting up cups-driver-gutenprint (5.2.5-1ubuntu1) ...

**No Gutenprint PPD files to update.**

 * Reloading Common Unix Printing System: cupsd

   ...done.
```

Bugged [LP 610428]("https://bugs.launchpad.net/ubuntu/+source/gutenprint/+bug/610428") Could someone confirm it cheers.

---

### Post by awam66 on 2010-07-27
> **LaneLester said:**
> 

Other than not being able to log in at [http://localhost:631/admin/](http://localhost:631/admin/) CUPS seems to be working.
Lane

Hi,
I have this problem not being able to log in to CUPS on my 32bit system.
So I can't therefore share my printer which is accessed from my laoptops over the network. Any one filed a bug on this?

---

### Post by philinux on 2010-07-28
The original problem is now fixed.

[https://bugs.launchpad.net/ubuntu/+source/gutenprint/+bug/610428](https://bugs.launchpad.net/ubuntu/+source/gutenprint/+bug/610428)

I can also get to this [http://localhost:631/admin](http://localhost:631/admin)

---

### Post by LaneLester on 2010-07-28
Today's Synaptic update brought with it the missing drivers. So I can finally print with the network printer.

I had to use system-config-printer to set things up, because I still can't log on to [http://localhost:631/admin/](http://localhost:631/admin/)

Lane

---

### Post by philinux on 2010-07-28
> **LaneLester said:**
> Today's Synaptic update brought with it the missing drivers. So I can finally print with the network printer.

I had to use system-config-printer to set things up, because I still can't log on to [http://localhost:631/admin/](http://localhost:631/admin/)

Lane

Have you bugged this?

---

### Post by LaneLester on 2010-07-28
I confess I have not. My experience with bug reporting systems is almost totally confusing and nonproductive.

Lane

---

### Post by philinux on 2010-07-28
> **LaneLester said:**
> I confess I have not. My experience with bug reporting systems is almost totally confusing and nonproductive.

Lane

Terminal

```
ubuntu-bug cups
```

---

### Post by LaneLester on 2010-07-28
OK, OK, Phil, you're not going to let me get away with it.

I had to install some stuff for ubuntu-bug to work. I run a Ubuntu Minimal CD with just wanted stuff added.

I went through the whole process to report the bug, and as I expected it had already been reported a number of times.

But all the time spent has a good ending. One of the sufferers reported a workaround that makes logging on possible. And it worked for me! :)

Lane

---

### Post by philinux on 2010-07-28
> **LaneLester said:**
> OK, OK, Phil, you're not going to let me get away with it.

I had to install some stuff for ubuntu-bug to work. I run a Ubuntu Minimal CD with just wanted stuff added.

I went through the whole process to report the bug, and as I expected it had already been reported a number of times.

But all the time spent has a good ending. One of the sufferers reported a workaround that makes logging on possible. And it worked for me! :)

Lane

There you go Result!

---

