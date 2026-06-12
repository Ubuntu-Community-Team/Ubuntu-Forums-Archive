---
title: "xawtv doesn't start."
date: 2007-04-25
forum: Multimedia &amp; Video
---

### Post by glore2002 on 2007-04-25
Hello!

I've installed xawtv, scantv and fbtv in Ubuntu 7.04. When I run scantv in terminal, after selecting the tv standard and country, I get the following message:

vbi: open failed [/dev/vbi]
open /dev/vbi: No such file or directory

So, I will really appreciate any help. Steps to follow?

Let me mention that I hava  a 878 tv-card (pinnacle) that works ok with tv time and it used to work ok in earlier versions of ubuntu and linux in general too.


Thanks again.

---

### Post by saperduper on 2007-05-06
same problem here :(
any ideas?

---

### Post by Random Numbers on 2007-10-28
Has anyone got a solution.  I have the same problem.  Mine died with the Gutsy upgrade.

---

### Post by val67 on 2007-10-28
not working here either ...

this _IS_ really frustrating.

How on earth can Ubuntu win the Desktop if it keeps breaking things from one release ti the next :confused:

---

### Post by Shadowline on 2007-10-29
this worked for me.... [http://tvremote.sourceforge.net/index.php](http://tvremote.sourceforge.net/index.php)
It's a little bit of a hack but it works since the build for xawtv is so borked for ubuntu, of course I assume you want to veiw tv from your tv card....

---

### Post by saperduper on 2007-11-07
> **glore2002 said:**
> Hello!

I've installed xawtv, scantv and fbtv in Ubuntu 7.04. When I run scantv in terminal, after selecting the tv standard and country, I get the following message:

vbi: open failed [/dev/vbi]
open /dev/vbi: No such file or directory

So, I will really appreciate any help. Steps to follow?

Let me mention that I hava  a 878 tv-card (pinnacle) that works ok with tv time and it used to work ok in earlier versions of ubuntu and linux in general too.


Thanks again.

I ran ```
scantv -C /dev/vbi0
``` and the problem was solved ;)
Apparently, the default vbi device file is /dev/vbi but the right one is /dev/vbi0...

---

### Post by stmiller on 2007-11-09
Gutsy killed off my tv card also.

All of the video programs look for /dev/vbi, BUT Gutsy lists the devices as '/dev/vbi0', '/dev/vbi1', etc.

So make a link:

```

sudo ln -s /dev/vbi0 /dev/vbi

```

and that should work. Testing now...

---

