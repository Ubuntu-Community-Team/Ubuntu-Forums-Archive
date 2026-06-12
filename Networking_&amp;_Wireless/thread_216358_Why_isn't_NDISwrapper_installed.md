---
title: "Why isn't NDISwrapper installed?"
date: 2006-07-15
forum: Networking &amp; Wireless
---

### Post by Throne777 on 2006-07-15
The last time I re-installed Breezy Badger on my computer after updating to Dapper Drake messed up my wireless, NDISwrapper wasn't present on the computer, even though it's supposed to be installed by default, and it was the first time I installed it.
Now I have the Dapper Drake disc and after having finally been able to install it, NDISwrapper isn't present. Why is this? Am I going to have to install it myself?
Even so, shouldn't it be installed?
(Why me?)
Help would be greatly appreciated.
Thanks.

Throne777

---

### Post by rbalfour on 2006-07-15
No. NDISWrapper is a "workaround" for cards that don't play nice with Linux.
You will find, by getting a card that works with Linux, you get more options. I know ppl moan and groan about it, but by supporting the maker who support Linux, show M$, we the USERS aren't going to take it anymore.

---

### Post by Throne777 on 2006-07-15
> No. NDISWrapper is a "workaround" for cards that don't play nice with Linux.
You will find, by getting a card that works with Linux, you get more options. I know ppl moan and groan about it, but by supporting the maker who support Linux, show M$, we the USERS aren't going to take it anymore.

I'm using an adapter, a US Robotics one. I'm not made of money and nor, at the time, was I considering switching to Linux. Instead of moaning about Microsoft, I'd appreciate it if you'd help me out.

Throne777

---

### Post by stupidkid on 2006-07-15
Are you sure it's not on the dapper disc? Did you add cd rom to your repositories?

---

### Post by Throne777 on 2006-07-15
> Are you sure it's not on the dapper disc? Did you add cd rom to your repositories?

What do you mean by adding the CD-ROM to the repositories?

Throne777

---

### Post by shortbus on 2006-07-16
> **Throne777 said:**
> The last time I re-installed Breezy Badger on my computer after updating to Dapper Drake messed up my wireless, NDISwrapper wasn't present on the computer, even though it's supposed to be installed by default, and it was the first time I installed it.
Now I have the Dapper Drake disc and after having finally been able to install it, NDISwrapper isn't present. Why is this? Am I going to have to install it myself?
Even so, shouldn't it be installed?
(Why me?)
Help would be greatly appreciated.
Thanks.

Throne777

Not sure exactly why you don't have Wireless supported. I know when I enstalled Dapper on my laptop I found that my wireless card was already supported. I've gone through FC4 and FC5 and had to fight with NDISwrapper with no success and was nearly giddy when I discovered that Dapper support my Linksys wireless card "right out of the box" (so to speak).  But, if you want to use NDISwrapper try going here, pretty good instructions: [Installation-NDISwrapper]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation")

[www.google.com/linux](www.google.com/linux) is your friend. Lemme know how it goes. Feel free to drop me a PM if needed.

---

### Post by Throne777 on 2006-07-16
> Not sure exactly why you don't have Wireless supported. I know when I enstalled Dapper on my laptop I found that my wireless card was already supported. I've gone through FC4 and FC5 and had to fight with NDISwrapper with no success and was nearly giddy when I discovered that Dapper support my Linksys wireless card "right out of the box" (so to speak). But, if you want to use NDISwrapper try going here, pretty good instructions

OK, I plugged in my wireless adapter and Dapper Drake picked it up. I went into properties and typed in the ESSID and then activated it. It activated, and then I clicked OK for the box to close, when that was done I opened up Firefox and lo and behold the connection isn't working. I open up Networking again to find that the connection isn't active ](*,) 
I typed in 
```
lsusb
```
and it acknowldged that the adapter was there, so why isn't it working?

Throne777

---

### Post by rbalfour on 2006-07-17
> **Throne777 said:**
> I'm using an adapter, a US Robotics one. I'm not made of money and nor, at the time, was I considering switching to Linux. Instead of moaning about Microsoft, I'd appreciate it if you'd help me out.

Throne777

It ain't that hard.

1) open a terminal
2) **sudo su **
3) **vi /etc/apt sources.list**
4) remove the # in front of deb and deb-src repos
5) save and close file
6) **apt-get clean**
7) **apt-get update**
8) **apt-get install ndiswrapper-utils**
9) **apt-get install ndisgtk**
10) **apt-get clean**
11) **ndisgtk**
12) setup the network via the gui that pops up.

* bold are commands 
* vi quick commands i = insert / esc = quit edit mode / :w = save file / :q = exit no save / :wq = save and exit / :q! = force exit no save / :wq! = force save force exit
note: this has works spot on. If your card still dosen't work. The card isn't supported in 6.06

---

