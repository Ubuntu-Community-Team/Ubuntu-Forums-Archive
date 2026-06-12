---
title: "Print server/management"
date: 2013-02-18
forum: Networking &amp; Wireless
---

### Post by bcm37 on 2013-02-18
I'd like some advice. 

I've recently found myself managing a small lab, 20 Macs, and I'd like to set up some kind of basic print server that would provide a catch-and-release kind of queue to help prevent people from wasting paper. I'm a bit unfamiliar with it all, I've never had any kind of print server.

It doesn't need to be anything sophisticated, we don't charge for printing or do any accounting with it. It's just some human engineering where I'm looking for an intermediate step where someone will have to get up and release the job to the printer. I'm hoping someone knows of a piece of software we can load on an older computer that can be physically next to the printer.

Thanks for your time.

---

### Post by tgalati4 on 2013-02-18
CUPS is the C Unified Printing System, that is now owned by Apple.  Just install cups and go to [http://localhost:631](http://localhost:631) to see the basic administration features.  You can configure cups to run custom scripts with submitted jobs, but you first have to set it up and have your macs see the shared (published) printers.  Once that is done, then you can get into the job control features.

On any linux server, cups is already installed.  You just have to add some printers and publish them.

---

### Post by bcm37 on 2013-02-19
> **tgalati4 said:**
> CUPS is the C Unified Printing System, that is now owned by Apple.  Just install cups and go to [http://localhost:631](http://localhost:631) to see the basic administration features.  You can configure cups to run custom scripts with submitted jobs, but you first have to set it up and have your macs see the shared (published) printers.  Once that is done, then you can get into the job control features.

On any linux server, cups is already installed.  You just have to add some printers and publish them.

That's a pretty good start. Do I have to build my own print station interface for it, or is there one available? I found some links to others that had set up CUPS to do that, but no one mentioned what they were using to provide users access.

---

### Post by tgalati4 on 2013-02-19
I don't understand the question, but here is the documentation:

[http://www.cups.org/documentation.php](http://www.cups.org/documentation.php)

You question sounds like:

In Printer Accounting Basics:

Quota Support

CUPS supports page and size-based quotas for each printer. The quotas are tracked individually for each user, but a single set of limits applies to all users for a particular printer. For example, you can limit every user to 5 pages per day on an expensive printer, but you cannot limit every user except Johnny.

------------------

Since you have a lab of macs, all of them are running CUPS already.  You just have to set up some configuration files and publish printers that are attached.

---

### Post by bcm37 on 2013-02-19
> **tgalati4 said:**
> I don't understand the question, but here is the documentation:

[http://www.cups.org/documentation.php](http://www.cups.org/documentation.php)

You question sounds like:

In Printer Accounting Basics:

Quota Support

CUPS supports page and size-based quotas for each printer. The quotas are tracked individually for each user, but a single set of limits applies to all users for a particular printer. For example, you can limit every user to 5 pages per day on an expensive printer, but you cannot limit every user except Johnny.

------------------

Since you have a lab of macs, all of them are running CUPS already.  You just have to set up some configuration files and publish printers that are attached.

I think I can run the virtual printer on one machine and then point it to the printer. I don't know that we want a quota yet.

I really want something simple, something where there is no web interface, no browser to close. Just the list of print jobs with the document title and a print button. The CUPS browser interface has way too many options for the lab patron.

I imagine after everything I've read so far it would just be a front end for CUPS, I've even read about a few different ones people installed, but they did not mention what front end they used for it. I was hoping that there was a project that did this kind of printer spool manager and release.

It doesn't make sense that people would just keep building this kind of thing from scratch, but whatever I search for I cannot find anything online but a couple of big money programs that do everything except read email. :confused:

Our university IT department recommends a big copy machine which is way overkill for our print volume, but I understand the interface. You print, walk up to the printer, select your job, then press the button on the printer that prints the job. I'm looking for this running on an old Linux box next to a workgroup printer we already have.

---

