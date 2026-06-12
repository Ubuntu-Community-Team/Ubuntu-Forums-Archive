---
title: "Firefox not using pdnsd cache"
date: 2009-02-13
forum: Networking &amp; Wireless
---

### Post by paulg1981 on 2009-02-13
Hello,
I have successfully setup pdnsd to cache dns locally and retain them in the event of a reboot.  I have tested this by 'dig yahoo.com' and the results are 50ish ms the first time and 0 ms subsequent times. Yay!  

I used this guide [http://ubuntuforums.org/showthread.php?t=331850](http://ubuntuforums.org/showthread.php?t=331850)

The problem is that I am unable to get firefox to use the local dns cache as opposed to its own.  I can disable firefox caching by setting 'network.dnscacheentries' and 'network.dnscacheexpiration' both to 0 in about:config but I see that this just causes firefox to look up every dns request :(  

I am using firefox 3 and this is driving me nuts.  Any ideas would be welcomed as I have googled to no avail :(


Thanks for your help :)

---

### Post by paulg1981 on 2009-02-13
No one?  :(

This is driving me nuts

---

### Post by paulg1981 on 2009-02-13
It does appear that the requests are going through pdnsd with firefox as they show up in the pdnsd-ctl dump but there is still a delay when firefox shows 'looking up xxxx'


PLZ HELP

---

### Post by paulg1981 on 2009-02-13
bump...

---

### Post by paulg1981 on 2009-02-17
Really?  No one :(

---

