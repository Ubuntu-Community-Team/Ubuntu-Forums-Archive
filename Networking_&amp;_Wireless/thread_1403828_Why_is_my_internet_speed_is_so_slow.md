---
title: "Why is my internet speed is so slow?"
date: 2010-02-10
forum: Networking &amp; Wireless
---

### Post by Jenkins1 on 2010-02-10
Hello,

When using launchpad and the ubuntu daily build website it is very slow. I get 1.2mb/s normally and the speed drops quickly to 0kb/s This is the case from any version of ubuntu that is installed on my laptop. 

In windows it is no problem, equally there is no problem from a live cd or an install on my external hard disk. Is canonical blacklisting/slow listing my ip? 

I am behind a university network but am sure this problem occurs at home .I did a clean install and had no problem until about an hour ago. 

When I tried to re download a project using bzr my speed instantly ropped.I had downloaded it fine a couple of hours ago. I hope that someone can shine some light on this, its very hard to work on projects if I can't download them.

Any thoughts or ideas would be appreciated, thanks in advanced.

---

### Post by The Toxic Mite on 2010-02-10
Hey!

So you say that you are attached to your university network?

How far is the uni from your home?

-TTM-

---

### Post by Jenkins1 on 2010-02-10
Hey :)

It is about 70 miles. Yes I am attached to my university network, also when on the wifi the speed to launchpad and ubuntu daily build site is fine. Its mostly that depending what I boot depends on what speed I get but it only effects some websites. I know sites can change but not by 1.2mb/s in about 2 minutes.

---

### Post by The Toxic Mite on 2010-02-10
Hmm, no internet in your home then?

I don't understand how the uni's WiFi can transmit that far... :?

---

### Post by Jenkins1 on 2010-02-11
Sorry for the confusion.

The problem occurs both at home and uni. But only occurs when on the wired connection at uni and not wifi. It occurs on both at home (the rare time that I am there)

---

### Post by Jenkins1 on 2010-02-11
Well adding 
```
alias ipv6 off 
alias net-pf-10 off
```

to

```
gedit /etc/modules

```

fixes it silly ipv6

---

