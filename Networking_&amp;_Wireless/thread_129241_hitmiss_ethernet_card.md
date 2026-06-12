---
title: "hit/miss ethernet card"
date: 2006-02-13
forum: Networking &amp; Wireless
---

### Post by woedend on 2006-02-13
posted this in dapper guess it goes better here sorry.  Hi, I put in a second ethernet card to bridge the connection out. miraculousy, thanks to previous posts here, it was super easy. The only thing I come across that troubles me is that about half the time I try to bridge the connection using ifup I get an error message along the lines of "interface eth1 not found". I can ifdown it and try again but from then on it will tell me eth0 is already in a bridge and cannot be bridged. So I just restart and try again. And its definetely a boot thing, if I get it bridged successfully once it will not give me that error again no many how many times I ifup and ifdown it, unless of course I restart. about half the time it works, half the time it doesnt and I can't find a correlation. Any idea what could be going on?

---

### Post by bscbrit on 2006-02-13
I'm just guessing but if you reverse the order that they appear in your interfaces file does the problem go away?  I'm just wondering if there is a timing problem with the way that they are initiated.  But I stress that it is just a guess......

---

