---
title: "Broadband USB Modem BP3-USB not Connecting to Internet"
date: 2009-12-18
forum: Networking &amp; Wireless
---

### Post by digitalis49 on 2009-12-18
I run both the 32 and 64-bit version of Ubuntu 9.10 / karmic (kernel 2.6.31.17-generic-pae).
This problem occurs on both systems.

Having read numerous posts about the functionality of the CMOTECH BP3-USB, I felt assured it should be "plug-and-play" on my systems esp when it is mentioned that the firmware for this modem is included in kernels 2.6.24 and later.

FOR ME, at least, IT SEEMS NOT SO ????????
I note, however, the USB modem is recognised when I start the wizard to add a new wireless broadband connection.

I have a Telstra 3G subscription (1gb/month)

The Broadband settings are :
Number :     *99#
Username :  [email]myusername@bigpond.com.au[/email]
Password:    myISPpassword
APN:            telstra.internet
Network:      blank
PIN:             blank

Please, am I doing something wrong here?
Is there anything else I must do/configure?

---

### Post by pdc on 2009-12-19
when 9.10 came out, numerous users of Ubuntu reported that when they changed from 9.04 to 9.10 that their mobile broadband no longer worked; I have some sense that some of this may be being fixed but the betavine folks; who run the vmc software for linux users of vodafone are frustrated

[http://www.betavine.net/bvportal/blog/view.html?blogId=133&postId=ff8080812536062f0125461585066602](http://www.betavine.net/bvportal/blog/view.html?blogId=133&postId=ff8080812536062f0125461585066602)

so they won't support anything over 9.04 and you might be best to download a version of 9.04 as liveCD and see if it will work; I find mandriva 2010 and fedora 12 play well with various mobile broadband and I cannot get things going with 9.10

earlier australian reports

[http://forums.whirlpool.net.au/forum-replies-archive.cfm/1091212.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/1091212.html)

said 8.10 was fine

and this

[http://quozl.netrek.org/bp3-usb/](http://quozl.netrek.org/bp3-usb/)

said it was fine on 9.04

sometimes cutting edge software can leave you with cuts

---

### Post by digitalis49 on 2009-12-20
Thanks, PDC, for your reply.

I am not a systems builder but I have spent some 30 years in the corporate IT industry managing rather large IT departments and bureaus.

I do find it surprising that carried-forward and upgraded operating systems do not, to this day, maintain consistency by including, at the very least, features which are core to the now-accepted concept of "mobile computing.

I would urge the Linux builders to move away from their reliance on wired ethernet connectivity and to focus more on mobility.

Linux does not only run on desktops and servers.

Regrettably, I will take up your suggestion and move forward to the past by re-installing 9.04 !!!!

I did not expect 9.10 to be at the bleeding-edge.

Again, thank you for your reply.

---

### Post by sharke on 2010-02-26
> **digitalis49 said:**
> I run both the 32 and 64-bit version of Ubuntu 9.10 / karmic (kernel 2.6.31.17-generic-pae).
This problem occurs on both systems.

Having read numerous posts about the functionality of the CMOTECH BP3-USB, I felt assured it should be "plug-and-play" on my systems esp when it is mentioned that the firmware for this modem is included in kernels 2.6.24 and later.

FOR ME, at least, IT SEEMS NOT SO ????????
I note, however, the USB modem is recognised when I start the wizard to add a new wireless broadband connection.

I have a Telstra 3G subscription (1gb/month)

The Broadband settings are :
Number :     *99#
Username :  [email]myusername@bigpond.com.au[/email]
Password:    myISPpassword
APN:            telstra.internet
Network:      blank
PIN:             blank

Please, am I doing something wrong here?
Is there anything else I must do/configure?

If you have a bigpond connection.
Username : [email]myusername@bigpond.com[/email]  (no .au )
APN : telstra.bigpond
Regards
Sharke

---

### Post by compsos on 2010-05-14
On 9.1 & 10.04 we found that 2 settings had to be disabled to work with Bigpond using BP3-USB modem

Settings
[email]username@bigpond.com[/email]
password
APN: telstra.bigpond (choose "None of the above" in the choice of Telstra APNs  and type in telstra.bigpond
Right click on the Notification Icon on the bar and select "Edit Connections"
Select Mobile Broadband and select the new connection and click Edit
On the 2nd tab deselect all the compression options except "TCP Header compression"
Exit out and try it.

---

### Post by pdc on 2010-05-14
thanks for this very useful post

---

