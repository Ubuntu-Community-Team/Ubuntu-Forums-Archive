---
title: "blank login screen with fglrx not default drivers"
date: 2006-11-05
forum: Multimedia &amp; Video
---

### Post by weizilla on 2006-11-05
I recently upgraded from dapper to edgy and it went pretty smoothly . Only problem is with xserver but I ran the reconfigure command line and that fixed the problem.

After playing around in edgy, I decided to upgrade my ati video card drivers to the ones from the ati website like I did with dapper. I followed the directions here exactly:
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Troubleshooting_for_Method_2](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Troubleshooting_for_Method_2)

However, after rebooting, I ended up with a blank screen where the login screen would normally appear. I get the exact symptoms here:
[http://ubuntuforums.org/showthread.php?t=290655&highlight=blank+screen+ati](http://ubuntuforums.org/showthread.php?t=290655&highlight=blank+screen+ati)
except that article said that using fglrx would fix the problem, not cause it.

I looked in my /var/log/xorg.0.log (I think that's what it's called. my computer is not with me now) and everything is fine until this line:
"Error: Chipset 0x4c66 is not recognized".

I even tried the the drivers which comes with edgy using method 1 of the first link and it still gives me the same problem.

I finally gave up and went back to using the Mesa drivers because  at least they worked.

Can anyone help me with this problem? I am using an IBM T40 laptop with built in ATI video card.

---

