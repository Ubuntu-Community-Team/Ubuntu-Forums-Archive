---
title: "Different names for wireless interfaces"
date: 2006-01-30
forum: Networking &amp; Wireless
---

### Post by alamba on 2006-01-30
Just wondering why different wireless interfaces are recognized in ubuntu with different names. My wireless card on my HP laptop is recognized as eth1, I've seen wlan0 on a friends system and I've seen al*0 on few posts on the forum. 

While the last one might be due to the fact that ndiswrapper was being used, I dont understand why the difference in names in the other cases. 

Also, what is the implication of the same? Does eth1 mean I'm using a generic driver and hence might not be using the resource to its full potential?

Akshay

---

### Post by Lambert on 2006-01-30
It's just a name and has no affect on device capabilities. If using ndiswrapper you'll find the interface is named wlanX, if using an atheros chipset you'll find it named athX, using an intel 2200bg you'll see ethX etc....


It's just used as an identifier so the kernel knows what device is being called upon and where to route the data.

---

### Post by alamba on 2006-02-04
Got it. Thanks!

Akshay

---

