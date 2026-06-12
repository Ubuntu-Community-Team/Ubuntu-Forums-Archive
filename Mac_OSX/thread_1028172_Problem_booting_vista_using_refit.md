---
title: "Problem booting vista using refit"
date: 2009-01-02
forum: Mac OSX
---

### Post by TimH1980 on 2009-01-02
Hi there,

I installed macosx (Leopard), vista and ubuntu intrepid (64 bit) on my macbook rev. 4,1 following this tutorial:

[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

It's this scenario: Mac OSX, Vista, and Ubuntu

So, I first installed macosx, used bootcamp for the win partition, installed vista (ultimate 32 bit) on the bootcamp partition, installed ubuntu on the same bootcamp partition and after that installed refit on OSX.

Refit shows up and I can choose macosx and ubuntu. They both boot normally. 

But when I choose for windows, it says after some time that there is a boot problem. I think my master boot record is broken or something. 

I think Grub is in the way.. I don't know. Can somebody help me out please?

Thanks in advance! Tim

---

### Post by handy on 2009-01-02
Have a look at this link & see if it is of any help:

***_[http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu)_***

---

### Post by TimH1980 on 2009-01-02
Thanks for your reply Handy!

But I fixed it myself.. I fixed it via the partition tool of refit. 

In the boot screen of refit, you can choose for the partition tool. I saw that it needed to do an update of the mbr. So I letted it do it's magic and than started in windows. 

I only needed to fix it further with my windows install disk to repair the mbr in Vista itself. 

Problem solved!

---

### Post by handy on 2009-01-02
Good to hear. :-)

---

### Post by loveandequality on 2009-01-25
Just use virtual box.

---

