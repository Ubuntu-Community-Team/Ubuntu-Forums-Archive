---
title: "Noob question about interfaces"
date: 2009-01-17
forum: Networking &amp; Wireless
---

### Post by tiamet on 2009-01-17
2 IP's on eth0

Am I correct in assuming that I can have eth0 handle two separate IP's by using eth0 static for the first and eth0:1 (static)for the second?

If so, what other areas have to be changed to accommodate this?

I have inherited a WISP and it is all based on Ubuntu.  I'm trying to learn ASAP but there is a second network he left mid stream and it needs to be connected.

We would even be willing to hire/pay someone to help get this finished.

Thanks

---

### Post by uzo on 2009-01-17
Yes you can, is the system a acting as a gateway router? what other function does the gateway perform? with these information, one can tell every possible areas you would need to change to make it work.

---

### Post by tiamet on 2009-01-17
Thank you Uzo.  Your quick response is vry much appreciated. 

The entire system is comprised of three servers.  Basically, one for DNS, one for LAMP and one for email.
They are each backed up to each other and can take over if one fails.  Now mind you this is what I found written down, and I am going to assume correct.

The area we are trying to finish is:

fiber backbone===>servers===>router===>AP (900Mhz Access Point)=== >Users

The second area is the same but with different IP's

The first area, that is up and running is as follows:

router IP is 192.168.100.1
IP Pool start .151
IP Pool end   .254
 Router settings:
Allocation Mode: static mode
IP Address: 65.254.167.50
Subnet Mask: 255.255.255.224
ISP Gateway: 65.254.167.33
Primary DNS: 65.254.167.34
2ndary DNS: 65.254.167.23

Access Point IP: 192.168.100.100

This AP provides dynamic addresses to the end users.

The second AP should essentially be a "copy" of the first except that it's IP is 192.168.200.100 and it should give dynamic IP's from the .200.151 to .200.254

Please let me know what additional info I can provide that will be helpful.
To make matters worse I am going through chemotherapy now and I tend to have "chemo brain", so I will do my bet, but forgive me if I seem really slow at times.

Uzo, the more I use Ubuntu and read about it, and the more I see people like yourself that are willing to help, just makes me want to learn all I can!  

Thank you again for replying!  
If it would help I can post my email address.  Just let me know.

---

### Post by tiamet on 2009-01-17
Noob question:  I have inherited a WISP and need some help to finish the last portion.  
I realize that I can set eth0: static and etho:1 static, with the appropriate IP's, but will that be all that's required to get the second network running?
Are there other places that should have changes as well?

The entire system is comprised of three servers. Basically, one for DNS, one for LAMP and one for email.
They are each backed up to each other and can take over if one fails. Now mind you this is what I found written down, and I am going to assume correct.

The layout of the system is:

fiber backbone===>servers===>router===>AP (900Mhz Access Point)=== >Users

The second area is the same but with different IP's

The first area, that is up and running is as follows:

router IP is 192.168.100.1
IP Pool start .151
IP Pool end .254
Router settings:
Allocation Mode: static mode
IP Address: 65.254.167.50
Subnet Mask: 255.255.255.224
ISP Gateway: 65.254.167.33
Primary DNS: 65.254.167.34
2ndary DNS: 65.254.167.23

Access Point IP: 192.168.100.100

The second AP should essentially be a "copy" of the first except that it's IP is 192.168.200.100 and it should give dynamic IP's from the .200.151 to .200.254

I would really appreciate any and all help.
Thanks

---

### Post by Sef on 2009-01-17
Merged threads.

---

