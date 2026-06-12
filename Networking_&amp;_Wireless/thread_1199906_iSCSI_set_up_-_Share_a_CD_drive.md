---
title: "iSCSI set up - Share a CD drive"
date: 2009-06-29
forum: Networking &amp; Wireless
---

### Post by jdhladky on 2009-06-29
Hello all,
My computer lacks a CD drive (as well as a blu-ray drive), so I thought it would be a good idea to share the drive of a more fortunate computer over iSCSI. Unfortunately, after I installed the iscsitarget program, I discovered I don't actually know anything about how to configure an iSCSI target, and most of the tutorials I googled have been obtuse or very specific. So...
I know to open the configuration file for iscsitarget (/etc/ietd.conf), the actual configuration file is very confusing. One problem is the name of the target: iqn.YYYY-MM.com.example:specific.target.name

Do I actually have to use a xxxxxxx.com domain? Does this domain have to be an actual website, or can I use something like the computer's IP address, and if I can, do I have to reverse the ip address, like i would have to reverse the domain name? 

What exactly does the YYYY-MM part of the name mean?

When I define what users can and can't access the target, if I leave them blank, will that let any computer access the target?

If I define the path of the extent(?) to the location of the cd/dvd/blu-ray/whatever drive, will this work, if it does, will I have to restart the target every time I want to share a different disk?

On the initiator, when I define the target name, is that the full name (w/iqn...), or is it just the part of the name after the ":"?

I am running the iscsitarget program on Ubuntu 9.04 and the initiator on OS X 10.5.7

An answer to ANY of these questions would be very much appreciated. 

Thanks.

---

