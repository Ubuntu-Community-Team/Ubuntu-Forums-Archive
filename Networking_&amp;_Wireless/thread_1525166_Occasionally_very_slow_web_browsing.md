---
title: "Occasionally very slow web browsing"
date: 2010-07-06
forum: Networking &amp; Wireless
---

### Post by rtruswell on 2010-07-06
Hi,

I'm having a repeated problem where my computer is very slow to view regular web pages, and generally fails to load them. It seems to be a problem specifically with webpages - I can work over SSH, use email, transfer files over FTP connections, with no noticeable problems, but any regular website (including this one) can take an age to load. This happens regardless of the browser I use (at least, it happens on Firefox, Opera, and Chromium), and regardless of wired or wireless connection (though admittedly I've not tried using a wired connection very much). As far as I can tell, it can also happen on any website. It is specific to linux - my computer is dual-boot ubuntu 10.04/Windows XP, and there is no networking problem when I use Windows.

Any idea where I might look to make some progress on this? I'll post any details that might be necessary, but frankly, I don't even know where to start to look.

Thanks in advance,
Rob

---

### Post by mörgæs on 2010-07-07
Welcome to the forum.

Here is everything you need to know about Firefox:
[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

The most common is IPv4/IPv6 - problems.

---

### Post by exploder on 2010-07-07
This worked well for me.

[http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html](http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html)

I manually edited the file because the command given in the tutorial did not work for me. With ipv6 disabled the browser works fine now.

---

### Post by rtruswell on 2010-07-07
Thanks to both of you - much appreciated. Disabling IPv6 seems to have helped - Firefox is still somewhat unhappy, but (touch wood) the other browsers are fine. I'll come back and post again if the problems resurface, but for now, thanks a lot for your help.

Rob

---

