---
title: "Amarok no longer sees my music collection"
date: 2010-06-27
forum: Multimedia Software
---

### Post by The Flying Penguin on 2010-06-27
I was just using Amarok 2-3 days ago and everything was working fine. Now every time I launch Amarok it shows 0 songs in my collection. Under my collection properties, it still shows I have the correct folder selected. When I try to rescan my collection, absolutely nothing happens. Also, when I quit the program, it stays in the top gnome bar. When I click on it, the exit option is gone and I have to manually kill the process.

Any ideas?

I'm running 10.04 with the 2.6.34-5 kernel.

---

### Post by mc4man on 2010-06-27
This seems to be a semi issue with amarok 2, here's a bug from quite some time ago in lucid, (and somewhat ignored

[https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/523269](https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/523269)

Basically try installing this
```
sudo apt-get install mysql-server-core-5.1
```

---

### Post by cybergrrl on 2010-06-27
> **mc4man said:**
> This seems to be a semi issue with amarok 2, here's a bug from quite some time ago in lucid, (and somewhat ignored

[https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/523269](https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/523269)

Basically try installing this
```
sudo apt-get install mysql-server-core-5.1
```


that worked like a charm! thanks :)

---

### Post by The Flying Penguin on 2010-06-27
That fixed both my problems.

Thanks!

---

### Post by mc4man on 2010-06-27
Glad it worked - why the bug has been ignored is beyond me, even if it can't be fixed, as I suggested, a recommend would resolve.

(I believe in maverick it's no longer an issue, at least on the install I had, not to say it may not still affect some.

---

### Post by zcacogp on 2010-06-29
OK, I have just tried this, and while it has fixed the problems with the music collection not being seen (thanks!) it has also scuppered Amarok such that it no longer plays anything. As in, it appears to play but no noise comes out of the speakers. 

Any suggestions? (Should I start a new thread?) 


Oli.

---

### Post by zcacogp on 2010-06-29
In fact, to update this, I now can't get any sound out of the computer while running Ubuntu. It will make a noise if I log out (it makes the usual double-tap noise), but won't make nay noise once I have logged in (doesn't even make the usual login noise.) 

The sound icon on the top panel has also changed - it is now an icon of a speaker (as usual), with "---" after it. And if I click on it then it doesn't show a volume slider and "sound preferences" as it did before. 

All help welcomed - thanks!


Oli.

---

### Post by The Flying Penguin on 2010-06-29
Maybe try going to System>Preferences>Sound and see if you can change the settings that way?

You could also try removing mysql-server-core-5.1 and see if that helps. Sorry, I'm still a Linux noob so I can't help you out much.

---

### Post by zcacogp on 2010-07-01
FP, 

Thanks. Neither of your suggestions worked, so I think I'll probably start a new thread and see what response I get to that. 

Thanks for trying tho'. 


Oli.

---

