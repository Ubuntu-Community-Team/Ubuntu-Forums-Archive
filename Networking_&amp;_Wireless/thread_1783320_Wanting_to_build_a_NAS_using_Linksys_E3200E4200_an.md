---
title: "Wanting to build a NAS using Linksys E3200/E4200 and a USB HDD."
date: 2011-06-15
forum: Networking &amp; Wireless
---

### Post by stchman on 2011-06-15
Just wanting to know if anyone has had any issues.

It has been my experience that Samba is great for Windows PCs to connect to a Linux share, but not for a Linux machine to connect to a Linux share (I personally use NFS for my Linux - Linux shares).

Does the e4200/e3200 use Samba?

Any thoughts?

Thanks.

---

### Post by starman38 on 2011-07-29
I was searching for help on my soho system that is mixed with win xp and debian squeeze and ubuntu 11.04.  My xp machines all see the the e3200 and the usb hd share, but I can't get to it with my linux boxes.  Not much response on this post, thought I'd post here before trying elsewhere.

---

### Post by mcellius on 2011-09-15
I set up a USB hard drive on my E3200 just last week, and it worked fine.  I could see it from both of my Ubuntu computers.  Yes, it appears the E3200 uses Samba to share drives.

Getting it working right was a bit of a pain since I had to specify a folder on the drive, but I just wanted to share the whole thing.  I can't remember exactly how I did it (I took it off a few days after doing it, although it worked just fine; I needed it elsewhere), but I do recall that what I had been thinking was the name of the drive turned out to be what I had to specify as the folder.

---

### Post by rlauzon on 2011-09-17
> **starman38 said:**
> I was searching for help on my soho system that is mixed with win xp and debian squeeze and ubuntu 11.04.  My xp machines all see the the e3200 and the usb hd share, but I can't get to it with my linux boxes.  Not much response on this post, thought I'd post here before trying elsewhere.

I'm having the same issue.

I can connect to the storage share, but I can't authenticate.  So it always passes me in as "guest" which cannot update anything.

---

