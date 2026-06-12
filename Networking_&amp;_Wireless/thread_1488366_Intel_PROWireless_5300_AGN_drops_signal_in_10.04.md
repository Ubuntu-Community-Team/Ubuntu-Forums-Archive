---
title: "Intel PRO/Wireless 5300 AGN drops signal in 10.04"
date: 2010-05-20
forum: Networking &amp; Wireless
---

### Post by xjgnsdof on 2010-05-20
My laptop runs 32-bit Lucid and has an Intel PRO/Wireless 5300 AGN [Shiloh] wifi card. At random times, the connection drops. This never happened in Karmic and even affects me on other networks in my building. Ideas?

---

### Post by JohnDoe365 on 2010-05-20
Can somebody, please, after more thant two weeks that the problem is known, add a sticky note, that the vanilla kernel of 10.04 has a serious WiFi regression, without any cure but a backported kernel (which is beeing worked on)?

Sorry, but search for slow wireless. Since 10.04 LTS has been released the spoiled kernel found widespread use and people keep complaining.

Please try the following:

disable WIFI
re-enable WifI and wait for re-association? If speed is back to  normal PLEASE leave a comment at 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/539794](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/539794)

Find more info at the WiFi mailing list:
[http://thread.gmane.org/gmane.linux.kernel.wireless.general](http://thread.gmane.org/gmane.linux.kernel.wireless.general)

Please note, that this bug persists since September 2009 but was not noticed as at this time no distribution used the 2.6.32 kernel which contains the bug
I heard rumor that this bug is not going to be fixed until 10.10!!! at least not properly backported and a permanent fix is planned for 2.6.34.9999, sic!

---

### Post by sureshsamuel on 2010-05-22
I too face the same problem... This is frustrating :-(
[http://ubuntuforums.org/showthread.php?t=1486657](http://ubuntuforums.org/showthread.php?t=1486657)

---

### Post by gofishel on 2010-06-06
I too have this problem

---

### Post by ProN8 on 2010-07-11
It looks like this is a windows problem as well.  Here is how someone fixed it in Win7[ http://tinyurl.com/29x85bv]("http://tinyurl.com/29x85bv").  I'm not sure if Ubuntu is haveing the same problem, or how to implement the solution if it is.  Any ideas?

---

### Post by JanusDC on 2010-08-22
> **JohnDoe365 said:**
> Can somebody, please, after more thant two weeks that the problem is known, add a sticky note, that the vanilla kernel of 10.04 has a serious WiFi regression, without any cure but a backported kernel (which is beeing worked on)?

Sorry, but search for slow wireless. Since 10.04 LTS has been released the spoiled kernel found widespread use and people keep complaining.

Please try the following:

disable WIFI
re-enable WifI and wait for re-association? If speed is back to  normal PLEASE leave a comment at 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/539794](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/539794)

Find more info at the WiFi mailing list:
[http://thread.gmane.org/gmane.linux.kernel.wireless.general](http://thread.gmane.org/gmane.linux.kernel.wireless.general)

Please note, that this bug persists since September 2009 but was not noticed as at this time no distribution used the 2.6.32 kernel which contains the bug
I heard rumor that this bug is not going to be fixed until 10.10!!! at least not properly backported and a permanent fix is planned for 2.6.34.9999, sic!

I have the same problem. I do not understand how it is related to a bug in rt2500pci. I am not using such a module. Is there a mistake in the link or are you refering to another problem?

---

### Post by xjgnsdof on 2010-08-22
> **JohnDoe365 said:**
> Can somebody, please, after more thant two weeks that the problem is known, add a sticky note, that the vanilla kernel of 10.04 has a serious WiFi regression, without any cure but a backported kernel (which is beeing worked on)?

Sorry, but search for slow wireless. Since 10.04 LTS has been released the spoiled kernel found widespread use and people keep complaining.

Please try the following:

disable WIFI
re-enable WifI and wait for re-association? If speed is back to  normal PLEASE leave a comment at 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/539794](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/539794)

Find more info at the WiFi mailing list:
[http://thread.gmane.org/gmane.linux.kernel.wireless.general](http://thread.gmane.org/gmane.linux.kernel.wireless.general)

Please note, that this bug persists since September 2009 but was not noticed as at this time no distribution used the 2.6.32 kernel which contains the bug
I heard rumor that this bug is not going to be fixed until 10.10!!! at least not properly backported and a permanent fix is planned for 2.6.34.9999, sic!

This isn't a problem of speed, so searching for "slow wireless" as you suggested is pointless. Relevant searches have turned up nothing but complaints and people like you saying "we know! we know!" It doesn't hurt to ask again, so I posted this thread. Also, most of us don't follow Ubuntu news because we don't care about kernels and modules and backports. We just want other people to tell us how to fix our computers.

It has been several months since I posted this problem, and I just decided to install Karmic. This is just unacceptable. I've disabled e-mail notification for this thread a long time ago. I'm not surprised to find a dearth of solutions here.

---

### Post by JanusDC on 2010-09-19
I have the same problem. I will continue trying to find a solution, by collaborating with the developers at least by reporting the bug (here it is btw: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/622166](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/622166))

This kind of speech is useless:

> **elgilicious said:**
> Also, most of us don't follow Ubuntu news because we don't care about kernels and modules and backports. We just want other people to tell us how to fix our computers.

If you want somebody to tell you how to fix it, you could collaborate by paying for the service. Since this is a forum free of charge about a free-of-charge OS, you cannot ask in that way.

---

