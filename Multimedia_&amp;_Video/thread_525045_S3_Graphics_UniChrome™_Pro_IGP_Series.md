---
title: "S3 Graphics UniChrome™ Pro IGP Series"
date: 2007-08-13
forum: Multimedia &amp; Video
---

### Post by iamjfarrell on 2007-08-13
I recently got a new motherboard and it has S3 Graphics UniChrome™ Pro IGP Series internally and I was wondering how I could get the graphics card to its optimum capacity... It only see's it as a generic card. Thanks! I have tried a few things but nothing seems to help it.

---

### Post by PaulFr on 2007-08-13
Have you looked at the drivers download page at VIA **[http://www.viaarena.com/default.aspx?PageID=2&OSID=45&CatID=3220](http://www.viaarena.com/default.aspx?PageID=2&OSID=45&CatID=3220)** ? These are drivers for Ubuntu Linux 6.10 and 7.04.

---

### Post by iamjfarrell on 2007-08-14
Thanks. I found the one I need only question is how do I install it?

---

### Post by PaulFr on 2007-08-14
I thought there were links on the download page for the install guide and application note. I also see kernel building instructions for Ubuntu 6.10. Please scroll down the page you get after clicking on the right link - the type of downloads is in the blue header just above each "Click here to begin free download".

---

### Post by iamjfarrell on 2007-08-14
I did download the install guide but it is hard to follow and the code it tells me to use doesn't seem to work. :confused:

---

### Post by PaulFr on 2007-08-14
Could you post the specific card for which you downloaded the driver, so we can help you out.

---

### Post by iamjfarrell on 2007-08-14
[This]("http://www.viaarena.com/default.aspx?PageID=420&OSID=45&CatID=3220&SubCatID=150") is the place where I got the driver from it has some installation guides that just don't seem to work.

Edit* I was wondering if I should just go buy a new better video card... I don't think this one does 3D does it?!

---

### Post by UNHOLYwoo on 2007-08-14
I have the same graphics card in my lappy, and its really been a hassle to get that working, though ive only tied under breezy and dapper... might try this out.

---

### Post by PaulFr on 2007-08-15
Wow, extremely confusing instructions as you have already noted.

As I see it, first you want to try their compiled drivers for Ubuntu 7.04 or 6.10:

1. Use the first link (named **linux-fbdev-kernel-bin_2.6.00.03a.tgz**) for the actual binary driver files, and the fourth link on the page (named **UniChrome FBD V2.6.00.03a Application Note**) for instructions - relevant sections in the Application Note pdf file are 1, 2, 4, 8, 9, and 10. Ignore section 3, 5 (and 7?). Please make sure to read sections 8, 9 and 10 before starting on section 4.

2. In section 4, please change the mode in the **modprobe** command to a reasonable one for your system from section 8.

Hope this helps.

Regarding 3D, if the above works, then you need to run the command **glxinfo** and look for **direct rendering: Yes** in the output. If that is present, then 3D acceleration is working. You can then run **glxgears** to compute your FPS rate.

---

