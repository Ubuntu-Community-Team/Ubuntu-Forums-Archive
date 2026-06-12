---
title: "Jaunty and XP - Ad-Hoc not working"
date: 2009-05-07
forum: Networking &amp; Wireless
---

### Post by Psicolonia on 2009-05-07
Hi everyone,

I've tried to create a network (Ad-Hoc) to share internet connection from XP with ubuntu jaunty.

I must be doing something wrong because the computers never connect to one another. Basically what I want is that Jaunty connects to XP so it can have internet, and I want it to do this automatically everytime it boots up (the connection is always available). I am able to share internet with jaunty over a cable but not Wifi.

Can someone post a step-by-step to do this?

I would like the network to be well protected too as I'll be sharing a LOT between both.

Thank you.

(by the way my XP is ready to share everything, my address is 192.168.0.1 / 255.255.255.0 and it attributes an address to jaunty over the cable, I could not achieve this on wireless.)

---

### Post by Coder543 on 2009-05-07
Ironically... I just decided to look this up myself.
[How to share your internet connection.]("http://gunblad3.blogspot.com/2009/04/howto-share-internet-connection.html")
Knock yourself out. :)
Duly note, however, that step 6 is no longer needed on Jaunty (at least, not on mine).

---

### Post by Coder543 on 2009-05-07
(read the next post)

---

### Post by Coder543 on 2009-05-07
Ok... here's the deal.

Right now, (and I have found no solution) while ipmasq is installed, you are unable to access the internet until you run the command "sudo ipmasq" which seems uncannily difficult. I have seen no solutions that are consistently successful. 

If yours messes up, just uninstall this package to fix your internet.

Links for possible solutions
[https://bugs.launchpad.net/ubuntu/+source/ipmasq/+bug/71468](https://bugs.launchpad.net/ubuntu/+source/ipmasq/+bug/71468)
[http://ubuntuforums.org/archive/index.php/t-333918.html](http://ubuntuforums.org/archive/index.php/t-333918.html)

However, if you kept a copy of the ipmasq somewhere in your home folder, you could theoretically install and uninstall the package as needed. This would give you what is needed when its needed.

edit: "the ipmasq in your home folder" should read "the ipmasq ".deb" installer package in your home folder"

edit2: You are unable to access the internet *after the next restart*. It works fine until then.

---

