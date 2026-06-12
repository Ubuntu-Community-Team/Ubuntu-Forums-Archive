---
title: "Calix Media Converter with PPPo(E/A?)"
date: 2010-07-02
forum: Networking &amp; Wireless
---

### Post by bcb9153 on 2010-07-02
I recently got fiber internet from our local ISP (Frontier).  They provided me with a Calix media converter that appears to literally convert the fiber signals to ethernet.  The ethernet connection then goes into a Siemens Gigaset router, which has ATM circuit information in it and also a PPPoE/A username and password.

The Gigaset router is awful, has a terrible wifi range, and has very few options for port forwarding etc.  I tried using the business class Linksys router that I'd been using with my cable ISP for the past couple of years, but there's no PPPoA option, which seems to be what I need to use.

My next attempt was going to be setting up my Ubuntu file server, which already has two network cards, to double as a router.  I know there's PPPoA support built into the kernel, but all I can find online is guides to set up PCI or USB ATM cards and the statement "PPPoA over ethernet is impossible".

Well, seems that it's not, since (apparently) the Calix MC isn't doing the ATM work, the Gigaset router is.  Does anyone have any general information on setting up a PPPoA connection on an ethernet link?

---

