---
title: "Virtualbox networking issues: ubuntu server 9.04"
date: 2009-05-19
forum: Networking &amp; Wireless
---

### Post by daryl314 on 2009-05-19
hello,

does anyone have advice on setting up networking in virtualbox for an ubuntu server 9.04 virtual machine?  (i'm using kubuntu 9.04 as the host, and it is connected to the internet via a wireless connection)

i've tried NAT and bridged networking with both static ip's and dhcp, and neither seems to work.  when i use NAT, the ubuntu installer isn't able to detect the dhcp host.  i also tried setting a static ip of 10.2.2.15 with a 10.0.2.2 gateway with NAT.

could someone point me in the right direction?

thanks!

---

### Post by superprash2003 on 2009-05-20
are you sure thats correct??? 10.2.2.15 ip and 10.0.2.2 as gateway ?? usually gateway would be 10.2.2.x

---

### Post by daryl314 on 2009-05-20
> **superprash2003 said:**
> are you sure thats correct??? 10.2.2.15 ip and 10.0.2.2 as gateway ?? usually gateway would be 10.2.2.x

good catch.  i was using 10.0.2.15 ip and 10.0.2.2 gateway.  a windows xp guest works okay, and this is the ip and gateway it grabs.  it seems that the problem isn't specific to ubuntu server 9.04.  i dug up an old virtual machine using 8.10 that used to work, and it gives me the same problems.

---

### Post by superprash2003 on 2009-05-20
you shouldnt use the same ip for both , it would be a conflict

---

### Post by daryl314 on 2009-05-20
would there be a conflict even if they are only run one at a time?  i didn't try to run them both simultaneously.

---

### Post by superprash2003 on 2009-05-21
no there wouldnt.. are you able to ping the gateway?? post output of ifconfig

---

### Post by daryl314 on 2009-05-21
i can't ping the gateway.  output of ifconfig (i had to use an image because i can't copy the text from the window):

[IMG]http://www.darylstlaurent.com/raw/ifconfig.gif[/IMG]

---

### Post by superprash2003 on 2009-05-22
but your output shows ip like 192.x.x.x but you mentioned 10.x.x.x ??confused...

---

### Post by theozzlives on 2009-05-22
I just set dynamic, specify the workgroup, computer name, etc. and it just works. Try not doing a static IP in your VM.

---

### Post by daryl314 on 2009-05-26
Sorry for the confusion.  I've tried several different configurations, and I wasn't sure which you wanted me to post.  The 192.x.x.x is a static IP for a bridged network connection to tap0, which worked before I upgraded Virtualbox.  10.x.x.x is a static IP for a NAT network connection.

I have also tried dynamic IP's over NAT, bridged to tap0, and bridged to wlan0.  None of these worked either.  When I created a new virtual machine using NAT, the Ubuntu Server installer could not find the network during the autodetect part of the installation.

A virtual machine running Windows XP over NAT using the same VirtualBox install is working without any problems.

---

### Post by daryl314 on 2009-05-27
It looks like the issue came from upgrading my old virtual machines to VirtualBox 2.2.2.  When I created a new virtual machine from scratch (instead of doing a new install of Ubuntu Server over an existing virtual machine), networking worked without any problems.

Thanks for your help!

---

