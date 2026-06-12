---
title: "BIND9, AppArmor and WOE!"
date: 2010-03-09
forum: Networking &amp; Wireless
---

### Post by pokeyoats on 2010-03-09
If you already know this then my apologies but I just wanted to put a post up with some nicely searchable strings in case any poor buggers (like me) suddenly find themselves with a broken BIND9 post Ubuntu "upgrade".

If you are running Ubuntu 9.1, installed BIND9 around about kernel level 2.6.31-14 to 2.6.31-17 had it working perfectly as either a master or slave server and then suddenly find yourself getting SERVFAILs it's because of AppArmor.

I hope, if like me you have struggled with this problem that you end up here because I could not find a documented solution.

Here are some errors you will get if AppArmor is interfering:

dumping master file: /etc/bind/zones (or other directory)/tmp-FDGDSFDS open: permission denied

refresh: could not set file modification time of '/etc/bind/XXXXX': permisison denied

failed while receiving responses: permission denied

kernel: [   61.952539] type=1503 audit(1268157790.971:34): operation="mknod" pid=960 parent=1 profile="/usr/sbin/named" requested_mask="w::" denied_mask="w::" fsuid=114 ouid=114 name="/etc/bind/zones/tmp-9wPWFDSJ"

All of these problems are being caused by AppArmor. Here are your choices, you can learn all about AppArmor here:

[https://help.ubuntu.com/8.04/serverguide/C/apparmor.html]("https://help.ubuntu.com/8.04/serverguide/C/apparmor.html")

OR if you just wnat to get BIND9 going then navigate to:

/etc/apparmor.d

note the file: usr.sbin.named

Disable AppArmor enforcement on it with the command:
[as root]: aa-complain usr.sbin.named
[as user]: sudo aa-complain usr.sbin.named

/etc/init.d/bind9 start (restart, whatever) and your BIND9 will now work.

Basically, you need to disable AppArmors enforcement rules else your bind9 will fail (as mine did because I put my zone files in /etc/bind/zones) - what a crime!! BAD ME!!!

Here's the history of my problem. My workplace is replacing a secondary name server because that particular verson is no longer supported and patched so we are changing to Ubuntu. 

When I installed and setup BIND9 everything worked fine. The server has then been sitting waiting for the appropriate outage schedule so that it can be changed over. 

After the 2.6.31-20 kernel was released (still pre-test2prod for me) I upgraded and decided to make sure that bind was still working. Imagine my surprise when it wasn't. 

Hours of effort later I'm writing this post in the hope that the information will spare someone else from the pain!

Thanks kindly.

---

### Post by jgree on 2011-04-22
Thanks for the post, it led me in the right direction but to a different answer. The alternative is to edit and specifically list /var/cache/bind/<zone> in /etc/named.conf for the slave zone files...

zone "someslave.org"{
        type slave;
        masters { xxx.xxx.xxx.xxx; };
        file "/var/cache/bind/zone.someslave.org";
};

This allows the cache apparmor to do its job without modification. 

My mistake was believing that the "default" would be used (substituted) by the daemon during the zone transfer, when in fact the appropriate/secure location for slave zone transfer files had been changed by developers, but no note I could find mentioned the need to edit the named.conf to point to that location.

---

