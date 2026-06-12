---
title: "Realtek rtl8192su vs Ralink RT3070"
date: 2013-03-04
forum: Networking &amp; Wireless
---

### Post by arnarg on 2013-03-04
I'm looking for a wifi adapter for my desktop machine. I have found two adapters on ebay I'm currently looking at. One has rtl8192su chipset and the other RT3070, would you guys recommend either one for Ubuntu?
[rtl8192su]("http://www.ebay.com/itm/400423431445?ssPageName=STRK:MEWAX:IT&_trksid=p3984.m1423.l2649")
[RT3070]("http://www.ebay.com/itm/400424910647?ssPageName=STRK:MEWAX:IT&_trksid=p3984.m1423.l2649")

Thanks :)

---

### Post by arnarg on 2013-03-05
bump

---

### Post by kurt18947 on 2013-03-05
I have no experience with any recent Ralink devices but I have 2 8192SU adapters and both truly are plug 'n' play.  They do have one annoying but easily cured fault.  If you put a machine with an 8192SU adapter attached into suspend then reawaken it, the network adapter will be missing. If you unplug the adapter, wait a second and reinsert, the adapter will work.  The workaround is:

Open a terminal in an account with SUDO privileges.  You're going to create a one line file using a text editor.  Do something like this:

```
sudo gedit /etc/pm/config.d/config
```

a new blank editor will open.  Add one line:

```
SUSPEND_MODULES="r8712u"
```

Save and exit.

You'll need to restart in order for the change to take effect.

There is one caution. One of my devices is a Dlink DWA-131.  It's perfect.  There is a thread about someone who recently purchased a DWA-131 and it was either v.2 or v.B.  It did not work, even with NDIS wrapper.  Dr. Chili was on the case last I knew.  I also have a TrendnetTEW-649UB which is a twin of the DWA-131 v.1.  I've also used rtl-8192SU as search criteria in Ebay and got some hits.  The adapters I have are N150.  I've seen Ebay offerings advertising N300 with supposedly rtl-8192SU chip sets.  I'm not sure what the difference is and if it affects recognition and function.

---

### Post by arnarg on 2013-03-06
Thank you for your reply, I think I'll just order the rtl8192su one and hope for the best, it won't be the end of the world if it won't work I guess.

---

### Post by arnarg on 2013-03-13
I just want to bring an update, I recieved Horntek Janus (rtl8192SU) and it works well without any hassle.

---

### Post by kurt18947 on 2013-03-13
> **arnarg said:**
> i just want to bring an update, i recieved horntek janus (rtl8192su) and it works well without any hassle.

Good deal!  RealTek 8192SU chip set seems to be a stable, fast choice.

---

