---
title: "YouTube won't load... bizarre"
date: 2012-03-19
forum: Multimedia Software
---

### Post by sodoscar on 2012-03-19
Hi all, 

I'm having a very peculiar thing going on thats got me stumped and I'm hoping someone maybe able to shed some light on the problem for me... 

The problem started a few days ago, and I can't be sure but feel it may be related to an update as this never used to be a problem.  

The issue is that YouTube will not load on any browser, nor will any embedded youtube clips load.  Every other site I use on a daily basis will load fine, including Flash based sites.

By uninstalling and re-installing flash youtube will load and work momentarily but I can't watch vids as same problem occurs again.   

I have not blocked the site on my machine, nor at the router; and the only other thing I've done to my machine configuration is install Opera.

Anyone else having this problem?  

I've tried other machines on my network, (Ubuntu, Mac, and Windows) and they seem to work fine, although none have been updated in a while.

I have no idea how to approach this problem so any suggestions are appreciated.

----------------------------------------------------------------

sod@omicron:~$ cat /etc/issue
Ubuntu 11.04 \n \l

sod@omicron:~$ uname -a
Linux omicron 2.6.38-13-generic #56-Ubuntu SMP Tue Feb 14 12:39:59 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by lovinglinux on 2012-03-20
Try [Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

---

### Post by sodoscar on 2012-03-20
That did the trick by installing latest beta version.  Thanks heaps.

how do i mark this solved?

---

### Post by lisati on 2012-03-20
> **sodoscar said:**
> That did the trick by installing latest beta version.  Thanks heaps.

how do i mark this solved?

Click on "Thread tools" near the top of the page and from there "Mark as solved"

---

### Post by sodoscar on 2012-03-20
Thanks lisati.. i had originally tried that but i wasn't logged in at the time so the option didn't appear.  All sorted now though.  Thanks again.

---

### Post by lovinglinux on 2012-03-22
> **sodoscar said:**
> That did the trick by installing latest beta version.  Thanks heaps.

how do i mark this solved?


:guitar:

---

### Post by sodoscar on 2012-03-23
I've marked this unsolved again as the problem has occured again.  Certainly, the firefox plugin did the trick, but now it doesn't work with any version of flash.

Could this be a result of taking part in the HTML5 trial and now youtube pulling that option and reverting back to this god awful Flash crap?

is it a buggy update?

is it installing Opera thats stuffed something?

endless questions, endless frustrations.

Still no youtube

---

### Post by lovinglinux on 2012-03-23
Try to disable hardware acceleration in flash settings. You can access that while watching a YouTube video, right-clicking on it.

---

### Post by sodoscar on 2012-03-23
It won't actually load any page from youtube at all... browser just reports: ...waiting for [www.youtube.com](www.youtube.com)

---

### Post by lovinglinux on 2012-03-23
> **sodoscar said:**
> It won't actually load any page from youtube at all... browser just reports: ...waiting for [www.youtube.com](www.youtube.com)

Disable ipv6.

[LIST]
[*]Type *about:confi*g in the address bar, press Enter.
[*]Find *network.dns.disableIPv6* in the list.
[*]Right-click -> Toggle.
[*]Restart Firefox and try again.
[/LIST]

---

