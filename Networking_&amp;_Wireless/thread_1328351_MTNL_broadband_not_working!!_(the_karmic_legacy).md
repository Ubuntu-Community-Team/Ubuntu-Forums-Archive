---
title: "MTNL broadband not working!! (the karmic legacy)"
date: 2009-11-16
forum: Networking &amp; Wireless
---

### Post by rahilm on 2009-11-16
Hello,
I got my Ubuntu 9.10 Karmic Koala Live-CD with a  few grand although unlikely changes. Ran in through the first graphic problem in the first 10 seconds, fortunately, people here helped me and it is almost solved.. So I ask you guys to help me through this ..

My MTNL broadband (triband) does not work. It didn't work in the Live-CD but I installed it anyway.
But, it doesn't work. The notification area shows Auto Eth0 connected also the lights on the router are fine. But firefox forever shows Connecting to [www.google.com]("http://www.google.com") ...
Somehow, I got back into 9.04 (fortunately, i hadn't removed it yet), after tackling a lot of serious grub issues to post this message.

---

### Post by rahilm on 2009-11-16
bump...

---

### Post by rahilm on 2009-11-16
i forgot to add this important information.
My broadband worked out of the box in 8.04 8.10 9.04..no need to even see any settings
I also have installed ubuntu 9.04 9.10 Xp triple boot
It is only in 9.10 the net doesn't work

---

### Post by utc271 on 2009-11-16
perhaps u can look at this thread   .[http://nixcraft.com/ubuntu-debian/12...em-ubuntu.html]("http://nixcraft.com/ubuntu-debian/12020-usb-modem-ubuntu.html")      .
  with a little bit of modifictions it helps mine to get online.
  cheers

---

### Post by rahilm on 2009-11-16
> **utc271 said:**
> perhaps u can look at this thread   .[http://nixcraft.com/ubuntu-debian/12...em-ubuntu.html]("http://nixcraft.com/ubuntu-debian/12020-usb-modem-ubuntu.html")      .
  with a little bit of modifictions it helps mine to get online.
  cheers

doesn't help..plus i have an ethernet router

---

### Post by pdc on 2009-11-16
9.10 is new software and has issues

you have two choices:

1) stay with 9.04 and remain connected to the internet via mobile broadband

2)install 9.10 and likely be unable to access the internet via mobile broadband

don't you just hate it when you have choices like that? We would all love that all software just hums all the time; the world would be a really fun place

---

### Post by beyboo on 2009-11-16
There is no reason for Triband not to work on a particular OS as the D-link DSL router has its own OS which connects to the MTNL server. The box simply does not know anything beyond itself !!

In all probability you have a  DNS configuration issue. 
Navigate to the box using firefox using its IP and check for the status if the PPPoE is connected. If the connection is on, then your DHCP server on  the box will give you a dynamic IP, but if you have not configured DNS either on the DHCP or on your local machine you will see your problems.

Solution : Configure NetworkManager with DNS entries and auto fetch ip via dhcp. This will get it working.

Edit :  Since all the magic is on the Triband DSL router, there is no script or any configuration needed on the local machine except for DNS entries.

---

### Post by rahilm on 2009-11-16
> **beyboo said:**
> There is no reason for Triband not to work on a particular OS as the D-link DSL router has its own OS which connects to the MTNL server. The box simply does not know anything beyond itself !!

In all probability you have a  DNS configuration issue. 
Navigate to the box using firefox using its IP and check for the status if the PPPoE is connected. If the connection is on, then your DHCP server on  the box will give you a dynamic IP, but if you have not configured DNS either on the DHCP or on your local machine you will see your problems.

Solution : Configure NetworkManager with DNS entries and auto fetch ip via dhcp. This will get it working.

Edit :  Since all the magic is on the Triband DSL router, there is no script or any configuration needed on the local machine except for DNS entries.


that was all greek to me!!!
but the so called D-Link DSL router OS works ootb for all linuxes and windowses i have seen.. ( in puppy, i clicked connect, configre eth0, and then a button with something related to DHCP, all went automatically and i was connected)

---

### Post by rahilm on 2009-11-17
anyone knows how to configure a D-Link 502T ??

---

### Post by rahilm on 2009-11-17
I guess all this is going to become a very bad karmic testimonial........................

i'll wait for lucid.

thnx

---

### Post by running_rabbit07 on 2009-11-18
> **rahilm said:**
> doesn't help..plus i have an ethernet router

USB modems are ethernet.

---

### Post by Dougie187 on 2009-11-20
> **rahilm said:**
> anyone knows how to configure a D-Link 502T ??

That doesn't appear to the a full model number for a dlink router.

Also, I don't know if you tried actually testing to see if it's a DNS issue or not. But if you didn't try this, Since you previously said that [www.google.com](www.google.com) doesnt do anything, try navigating to this inside firefox or something.

74.125.65.105

If you really do have a DNS issue, then this should take you to google. 

If you want to check the model number I'd be happy to look into how to configure your router for you.

EDIT: To start, what is the IP address that you are given by your router. That should help telling us how to configure it.

---

### Post by running_rabbit07 on 2009-11-20
Best way to fond the Gateway IP, would be to run ```
ifconfig
``` Once you do this, you should be able to enter the Gateway IP into your browser and be able to connect to the router to make changes, if that will fix the issue.

---

### Post by rahilm on 2009-11-21
> **Dougie187 said:**
> That doesn't appear to the a full model number for a dlink router.

Also, I don't know if you tried actually testing to see if it's a DNS issue or not. But if you didn't try this, Since you previously said that [www.google.com]("http://www.google.com") doesnt do anything, try navigating to this inside firefox or something.

74.125.65.105

If you really do have a DNS issue, then this should take you to google. 

If you want to check the model number I'd be happy to look into how to configure your router for you.

EDIT: To start, what is the IP address that you are given by your router. That should help telling us how to configure it.

Thanx a lot for replying...
i did what u said and it did redirect me to google..
so it is a DNS issue...
i'll be back with more information
I've been finding a solution in this thread too..got more replies though

[http://ubuntuforums.org/showthread.php?t=1330641](http://ubuntuforums.org/showthread.php?t=1330641)

---

### Post by rahilm on 2009-11-21
hey.. i configure my DNS servers and Internet is working.
I m posting this inside ubuntu 9.10

thanx 4 the help guys.. marking this thread as solved

---

### Post by RobotChubby on 2009-11-24
Hi

As someone who's only skated on the surface of various distros over the past 12 months or so, I'm really trying to get into Linux properly now with Karmic Koala in one hand and a copy of Micro Mart in the other. 

Unfortunately, I have hit this same problem as above, confirming that it seems to be a DNS issue by navigating to Google using the 74.125.65.105 code mentioned above.

Trouble is, I don't know how to configure my DNS as suggested, and I'm hoping one of you kind people can help?  I'm not terribly clued up with networks or network terminology, I'm afraid.

For what it's worth though, all the Linux flavours I've played with so far seem preferable to Windows 7 to me.  I'd sooner have a bit of an (interesting) headache sorting this out than be bored and irritated by a bloated MS revenue generator any day!

Hope you can help, and thanking you in advance

RC
;)

---

### Post by RobotChubby on 2009-11-24
Er, reading the posts above properly, I see that configuring my DNS is something I have to do on the router.  So, if anyone can help, my router is a DLink DSL-G624T.  Sorry for the oversight.

---

