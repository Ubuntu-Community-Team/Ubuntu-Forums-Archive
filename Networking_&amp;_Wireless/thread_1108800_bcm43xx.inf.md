---
title: "bcm43xx.inf"
date: 2009-03-28
forum: Networking &amp; Wireless
---

### Post by Eidolons on 2009-03-28
I am the owner of a bcm4328 chipset wireless card which seems to mean that it is not supported on the new kernel or API or whatever it was that switched (new driver being b43).  I have heard some suggest just using the windows drivers still works.  I tried to find those but it seems that the bcm43xx.inf file isn't there any longer.  There is bcm43xx.cat and bcmwl6.inf.  Is my memory bad or did it used to be bcm43xx.inf?  I tried installed bcmwl6.inf and it didn't do anything.

Has there been any known ways to get this working for sure or is it just unfixable until they reverse engineer it again?  I've tried b43legacy as well.

---

### Post by superprash2003 on 2009-03-28
go to your terminal and type **sudo lshw -C network** and post output.Also post output of
1)iwlist scanning
2)iwconfig

---

### Post by Eidolons on 2009-03-28
I really don't feel like diagnosing the problem.  It's quite obvious that bcm4328 is not supported so I need to use the wrapper.  Are there any old copies of the driver floating around out there.  Ones that actually use bcm43xx.inf because that is what has worked for me up until now.

---

### Post by nush on 2009-03-28
have you connected to internet with ethernet cable and updated repos
i use the bcmwl5.inf driver and the above worked for me after i activated the driver
you also have to blacklist other bcm drivers
hope this helps

---

### Post by Eidolons on 2009-03-28
I don't have a wired connection which is half the problem.  I rent and the landlord has a house-wide wi-fi.

---

### Post by Eidolons on 2009-03-30
> **nush said:**
> have you connected to internet with ethernet cable and updated repos
i use the bcmwl5.inf driver and the above worked for me after i activated the driver
you also have to blacklist other bcm drivers
hope this helps

Are there any packages that you need to load for sure other than the wrapper?  I've seen so many variations on what you need.

---

