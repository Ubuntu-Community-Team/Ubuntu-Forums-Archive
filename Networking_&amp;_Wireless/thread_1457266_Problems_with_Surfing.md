---
title: "Problems with Surfing"
date: 2010-04-18
forum: Networking &amp; Wireless
---

### Post by kony on 2010-04-18
Hello Guys

I open Firefox, Some Website Works, on some other Website Firefox Says "Connecting to...", but all the Site´s I have Tested working on my Windows 7.

What´s the Problem?

Thank you for Help!
(Sry **** English-->German)

---

### Post by nitstorm on 2010-04-18
type about:config in your address bar in mozilla firefox
then in the filter search for IPv6
double-click on the line network.dns.disableIPv6 and change the boolean value to false
then restart firefox and see if that helped

Cheers!

---

### Post by kony on 2010-04-18
Thank you!

But the Value was on "False", i changed it to "true" and it works!

But, in the Software Center it&#347; maybe the Same Problem, What i have to do?

---

### Post by Iowan on 2010-04-18
MTU is another possible culprit. [This]("http://ubuntuforums.org/showthread.php?t=1376506") thread goes through checking MTU.

---

