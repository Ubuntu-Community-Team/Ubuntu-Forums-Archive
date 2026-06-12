---
title: "Monitoring network traffic"
date: 2010-05-25
forum: Networking &amp; Wireless
---

### Post by wigglestix on 2010-05-25
I am looking for a way to monitor my upload and download for my whole network not just my computer. I am using a laptop that is connected wirelessly to my router, i am able to monitor the upload and download for my laptop but i would like to view the statistics for for the whole network without being connected to the router.

Any help is appreciated.

kristian

---

### Post by noper2 on 2010-05-26
I'm not sure if there is a purely local, software solution -- that is, a program you can install on your laptop to monitor all traffic. Have you looked at your router settings? They might offer such functionality. If not, I think something such as the DD-WRT firmware for your router may do what you're looking for ([http://www.dd-wrt.com/wiki/index.php/Main_Page](http://www.dd-wrt.com/wiki/index.php/Main_Page)). However, it is entirely possible to ruin your router when installing custom firmware!

---

### Post by cariboo on 2010-05-26
Have a look at [Bandwidthd]("http:///bandwidthd.sourceforge.net/"), it is in the repositories.

---

### Post by wigglestix on 2010-05-26
> **cariboo907 said:**
> Have a look at [Bandwidthd]("http:///bandwidthd.sourceforge.net/"), it is in the repositories.


Yes this seems to be what i was looking for. I am having trouble setting it up though. I set the capture interface to wlan0 and used the default ip settings it recomended and when i typed bandwidthd in the terminal it gave an error saying cannot access the bandwidthd.conf file so i used "chmod 644 bandwidthd.conf" and now when i try and open the program nothing happens.??

---

### Post by cariboo on 2010-05-26
You access the html pages that bandwidthd creates in /var/lib/bandwidthd/htdocs/index.html. See screenshot.

---

### Post by wigglestix on 2010-05-26
> **cariboo907 said:**
> You access the html pages that bandwidthd creates in /var/lib/bandwidthd/htdocs/index.html. See screenshot.
AHA!...thank you this is exactly what i was looking for. Now all i need to do is figure out how to display some of the statistics in conky...

---

### Post by Hadi_lq on 2010-08-12
I have Ubuntu 10.04 and love it :p
I installed  [Bandwidthd]("http://bandwidthd.sourceforge.net/") too but I cannot configure it to monitor my upload and download for my whole network not just my computer! 

The pages in /var/lib/bandwidthd/htdocs seems to monitor my local network! and I cannot find any help in /etc/bandwidthd/bandwidthd.conf  !


Could you help me to configure it?

Tnx
Hadi

---

