---
title: "How can I Copy from camcorder to PC with firewire"
date: 2010-06-23
forum: Multimedia Software
---

### Post by b-boy on 2010-06-23
Hi Guys


How can I Copy from camcorder to PC with firewire. What application can I allow me to do this I am running Ubuntu 10.04 and I have a firewire cable connected between My Laptop and Camcorder.

---

### Post by hsoulen on 2010-06-23
> **b-boy said:**
> Hi Guys


How can I Copy from camcorder to PC with firewire. What application can I allow me to do this I am running Ubuntu 10.04 and I have a firewire cable connected between My Laptop and Camcorder.

Hi,

I use Kino and I like it a bunch. Very compatible, captures in DV1/DV2 profiles and other formats as well, and very comparable to packages for the MS products.

[http://www.kinodv.org/](http://www.kinodv.org/)

Only one small caveat, Linux is very, very picky when it comes to firewire connections. Do yourself a favor and read this little bit of advice on the Kino page (even if you use a different capture package) as proper permissions for the 1394 dev have been an issue in Linux forever...

> How to fix FireWire capture in Ubuntu 10.04  (Lucid) 
  	 	 ( 26.05.2010 22:36 )
   	   	In a Terminal, enter 'gksu gedit  /etc/modprobe.d/blacklist-firewire.conf'. 
 Uncomment (remove the #-character at the beginning of the line)  ohci1394, sbp2, dv1394, raw1394, and video1394. Then, comment (add a  #-character to the beginning of the line) out the firewire-ohci and  firewire-sbp2 lines. Save and Quit gedit. 
 Next, run 'sudo update-initramfs -k all -u' and finally reboot. 
  
 Now, when you plugin your camcorder, it should have permission by  default (unlike in the past). [Vote]("https://bugs.launchpad.net/bugs/6290") for this  to become the default by indicating that this bug affects you.   

Cheers,

Hank

---

