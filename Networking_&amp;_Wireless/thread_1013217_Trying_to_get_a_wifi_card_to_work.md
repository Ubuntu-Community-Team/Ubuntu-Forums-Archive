---
title: "Trying to get a wifi card to work"
date: 2008-12-16
forum: Networking &amp; Wireless
---

### Post by jonsayer on 2008-12-16
Hi, I'm trying to get wifi to work with a strait Vanilla Ubuntu install on a desktop. Wired internet is not an option here. 

When I type "lspci" into terminal I get:

```
00:0c.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev01)
```

Anyone know where I can get the drivers for this kind of wifi card?

I know linux drivers for this card exist because I put a Nimble X LiveCD into this computer and the internet worked fine.

---

### Post by jonsayer on 2008-12-16
So it looks like there is a package in synaptic called linux-wlan-ng that promises to get this thing to work. Looks like that problem is solved. 

Now here is my next problem: this computer currently has no internet access. How do I get these packages off of one internet-enabled computer onto one that is not? Can I burn packages to CD's? How would I do that?

---

