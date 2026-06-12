---
title: "Forcing 60Hz refresh rate"
date: 2006-08-09
forum: Multimedia &amp; Video
---

### Post by Explodinglemur on 2006-08-09
Intel i945 onboard video, 17" 1280x1024 analog-interface LCD.  Ubuntu defaults to 75Hz which causes some fuzziness in the display (gotta love that D->A->D conversion!)
I've followed the instructions of step 10 in this guide, which did not help: [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

I've tried it with useFBdev enabled and disabled, and I've tried setting my vertical refresh to 60 and 60-60.  What else can I try?

---

### Post by computergroove on 2006-08-09
> I've tried setting my vertical refresh to 60 and 60-60

Are you doing this in xorg.conf?

---

### Post by Explodinglemur on 2006-08-10
> **computergroove said:**
> Are you doing this in xorg.conf?

Yes.

---

### Post by hadding on 2006-08-11
sudo dpkg-reconfigure xserver-xorg

---

### Post by tseliot on 2006-08-11
Try this guide:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)


OR this one (read where it says "Getting the Right Mode for an LCD monitor"):
[https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration](https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration)

---

### Post by Explodinglemur on 2006-08-11
> **hadding said:**
> sudo dpkg-reconfigure xserver-xorg

Did that multiple times, couldn't get the right settings to make it  work.  Any suggestions for what to feed the xconfig tool?  It's near-impossible to get any of the vertical/horizontal refresh rate ranges for monitors these days, making advanced use of the tool nearly impossible.

> **tseliot said:**
> Try this guide:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)


OR this one (read where it says "Getting the Right Mode for an LCD monitor"):
[https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration](https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration)

Used the second guide, the modeline that gtf gave me locked my monitor at 61Hz...so close!  I'll work with the other guide some on Monday (work computer).  Thank you!

---

