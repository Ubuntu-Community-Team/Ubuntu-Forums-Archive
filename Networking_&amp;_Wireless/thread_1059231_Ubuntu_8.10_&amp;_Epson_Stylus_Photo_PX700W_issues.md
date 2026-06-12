---
title: "Ubuntu 8.10 &amp; Epson Stylus Photo PX700W issues"
date: 2009-02-03
forum: Networking &amp; Wireless
---

### Post by bratters123 on 2009-02-03
Help,

I can not connect wirelessly to my PX700W. I'm a newbie to Ubuntu and Linux so please keep it simple. I cannot find a driver.

---

### Post by cariboo on 2009-02-03
Have a look at this [this]("http://openprinting.org/show_printer.cgi?recnum=Epson-Stylus_Photo_PX700W") page. Follow the instructions at the open of the page to install the drivers.

Jim

---

### Post by MikSam on 2009-02-13
Does it work now?
I'm keen to know, postman just brought me a PX700W too...

---

### Post by GaryUK on 2009-03-25
> **MikSam said:**
> Does it work now?
I'm keen to know, postman just brought me a PX700W too...

Hi MikSam, yes it does!! Woo Hoo!!

As per the post from cariboo907, get the latest pipslite driver and install following the readme instructions on the avasys.jp site that he directs you to.

Then follow the instructions in post #4 on this thread at linuxquestions.org:

[]("http://www.linuxquestions.org/questions/linux-wireless-networking-41/epson-px700w-and-fedora-89-689808/")[http://www.linuxquestions.org/questions/linux-wireless-networking-41/epson-px700w-and-fedora-89-689808/](http://www.linuxquestions.org/questions/linux-wireless-networking-41/epson-px700w-and-fedora-89-689808/)

My socket command that I used in CUPS was socket://<IP_Address> where <IP_Address> was the IP I had reserved on my router for the printer.

I printed a test page and hey presto - wireless printing !!

I will post more once I figure out how I can achieve wireless scanning - anyone figured that one out yet?? (Yes!! Me!! if you want Artisan 700/Stylus Photo PX700W scanning working over a network then look at this post: [http://ubuntuforums.org/showthread.php?t=1258616]("http://ubuntuforums.org/showthread.php?t=1258616"))

Regards,

Gary.
:)

---

### Post by nautec on 2010-03-09
Thanks, that works on 9.04 to. 
Type at url field:      socket://<IPaddress>      
and should work for you.

---

