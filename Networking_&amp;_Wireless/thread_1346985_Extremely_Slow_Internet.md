---
title: "Extremely Slow Internet"
date: 2009-12-05
forum: Networking &amp; Wireless
---

### Post by Greg1221 on 2009-12-05
Hey Ubuntu guys, I have a serious problem.

Basically every release since 8.4 or something i have installed ubuntu side by side with windows, used it once then went back to windows. This time with 9.10 I installed it and fell in love, but I now have a problem that if not fixed will force me back to windows like always.

The Internet is unbearably slow. I timed from entering google.com to the site loading up it took 10 + seconds. Its nearly instant on windows 7, along with many other websites taking forever. It freezes at looking for google.com. But for some websites like this once it is loaded up navigating it is nearly instant and at the speed of windows. I have disabled Ipv6 in Firefox and in Ubuntu itself so that's not the issue. The ethernet adapter is built into my Asus P6T, some help would be greatly appreciated!.

---

### Post by mörgæs on 2009-12-06
How do other browsers behave? Opera, for example.

Here are some ideas for Firefox: 
[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

If the problem is related to pages with Flash, you could try
[https://addons.mozilla.org/en-US/firefox/addon/433](https://addons.mozilla.org/en-US/firefox/addon/433)

---

### Post by dajare on 2009-12-06
Could it be this bug?

[https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/417757](https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/417757)

Try the work-around offered in comment #13 in that page, and see if that helps.

I continue to hope that this will get fixed, as I am still on 9.04, simply because of the "slow internet" problem with 9.10.

---

### Post by Greg1221 on 2009-12-06
After much researching last night, I figured out that the problem was the DNS Resolver, I followed a guide on how to download something and make opendns my main servers. Worked like a charm! Now this is faster than windows 7! :D

---

### Post by teamsuperoxide on 2009-12-06
> **Greg1221 said:**
> After much researching last night, I figured out that the problem was the DNS Resolver, I followed a guide on how to download something and make opendns my main servers. Worked like a charm! Now this is faster than windows 7! :D

could you provide a link to the 'guide', cheers

I just upgraded from 8.04 to 9.10 today...... I'm starting to feel it was a big mistake.....

---

### Post by Greg1221 on 2009-12-06
> **teamsuperoxide said:**
> could you provide a link to the 'guide', cheers

I just upgraded from 8.04 to 9.10 today...... I'm starting to feel it was a big mistake.....
[http://ubuntuforums.org/showthread.php?t=1293990#9](http://ubuntuforums.org/showthread.php?t=1293990#9)

---

