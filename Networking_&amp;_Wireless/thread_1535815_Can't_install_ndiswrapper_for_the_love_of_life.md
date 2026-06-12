---
title: "Can't install ndiswrapper for the love of life"
date: 2010-07-21
forum: Networking &amp; Wireless
---

### Post by graphikeye on 2010-07-21
Hi All,
I've usually never had much of a problem setting up wireless with ndiswrapper and ubuntu. I decided to give KUduntu a try, and for the love of me I cannot install ndiswrapper:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ndiswrapper-utils is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However, the following packages replace it:
  ndiswrapper-common
E: Package ndiswrapper-utils has no installation candidate
```

I'm pretty sure I've added all the repositories in the sources. What am I doing wrong?

---

### Post by tpow on 2010-07-22
I'm having the same problem.

I type in this: "sudo apt-get install ndiswrapper-common" and I get this error message when I attempt to install it: "E: Couldn't find package ndiswrapper-common"

I should mention that I am attempting this on an old Acer TravelMate 2413LCi with a Broadcom BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev02) with a history of wireless driver problems.

Any help would be much appreciated.

@graphikeye
How have you attempted to install ndiswrapper? (ie through the terminal or the software manager)

---

### Post by cariboo on 2010-07-22
If you have a Live CD, enable it in /etc/apt/sources.list, you should then be able to install ndiswrapper.

---

### Post by tpow on 2010-07-22
Ok. I've done that and successfully installed ndiswrapper, and it recognizes that there is a wireless driver. Thank you. However, when I try to activate the driver it gives me this error message:

"Sorry, installation of this driver failed. Please have a look at the log file for details: /var/log/jockey.log"

I have looked at the file, but I can't make heads or tails of it other than it says the activation failed.


edit: i found a way to solve my wireless woes here (it doesn't use ndiswrapper): 

[https://wiki.ubuntu.com/Testing/Laptop/Lucid/Reports/AcerAspireOneD150](https://wiki.ubuntu.com/Testing/Laptop/Lucid/Reports/AcerAspireOneD150)

---

