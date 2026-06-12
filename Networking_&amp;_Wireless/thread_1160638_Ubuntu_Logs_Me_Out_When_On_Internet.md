---
title: "Ubuntu Logs Me Out When On Internet"
date: 2009-05-15
forum: Networking &amp; Wireless
---

### Post by gamefreak3o3 on 2009-05-15
I have installed Ubuntu to an old computer, 128 mb of RAM about 500MHz processor, and when ever I've done something online it just logs off my Ubuntu account. All I've done on the internet though is try to log on to GMail and google search and when I do either of those it decides to be a bully and log me out. How can I resolve this problem?

---

### Post by moddedcomputers on 2009-05-15
> **gamefreak3o3 said:**
> I have installed Ubuntu to an old computer, 128 mb of RAM about 500MHz processor, and when ever I've done something online it just logs off my Ubuntu account. All I've done on the internet though is try to log on to GMail and google search and when I do either of those it decides to be a bully and log me out. How can I resolve this problem?
So which version of Ubuntu are you using? You may need an older kernel for that old machine!
I would hit [distrowatch]("http://distrowatch.com/") and look for some versions of Linux more appropriate for your 500MHz machine.

---

### Post by gamefreak3o3 on 2009-05-16
Thanks, if I feel like it I'll try that.

---

### Post by Crafty Kisses on 2009-05-17
It actually sounds like your X is crashing. What are the results of the following command?
```
sudo cat /var/log/Xorg.0.log
```
You also might be interested in a lighter distribution of Linux like Puppy or Xubuntu, I'll provide links for both distributions.

[CENTER][LIST]
[*]Xubuntu: [http://www.xubuntu.org/](http://www.xubuntu.org/)
[*]Puppy: [http://www.puppylinux.org/](http://www.puppylinux.org/)
[/LIST][LIST]
[/LIST][/CENTER]

---

