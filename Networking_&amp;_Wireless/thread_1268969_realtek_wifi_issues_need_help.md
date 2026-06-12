---
title: "realtek wifi issues need help"
date: 2009-09-17
forum: Networking &amp; Wireless
---

### Post by _787_ on 2009-09-17
today i dual booted my computer from vista to vista + ubuntu 9.04
im not new to ubuntu but im not great at it
my issue is i cant connect to internet
i have a realtek rt8192U usb 802.11n chip
but i cant get it to work 
i isntalled ndiswrapper
got the vista driver. inf file 
now
when i open sys>admin> windows wireless driver 
i get the message
unable to see if hardware is present 
on the list on the left side it says
hardware present: yes
also when i click connect to network it says
cound not find network config tool

ndiswrapper -l returned : net8192U device installed and gave an adress 

ive checked everything twice over the only issue i can find is the .inf directory does not have the .sys file under the same name in the directory

thanks for reading i know this post is long
but im fresh out of ideas 
any help?
thanks

---

### Post by MaindotC on 2009-09-18
I don't understand why you are using the windows driver when that chipset is specifically supported by kernels 2.6.24-24-generic and above.

---

### Post by _787_ on 2009-09-18
can you explain that

---

### Post by MaindotC on 2009-09-18
You just plug in the adapter and the driver loads.  It just works.

---

