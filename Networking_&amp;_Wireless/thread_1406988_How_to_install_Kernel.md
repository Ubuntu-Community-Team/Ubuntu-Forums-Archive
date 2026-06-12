---
title: "How to install Kernel"
date: 2010-02-14
forum: Networking &amp; Wireless
---

### Post by Dukes24 on 2010-02-14
Alright, I figured out how to get connection, however now my system  won't boot without the CD, it just goes straight to a black screen, and  when I do get it to boot with the CD, it'll freeze after about 10  minutes of usage.

After uninstalling, and reinstalling, I've come to the conclusion that  the update that I do to get connection is the cause of the problem.  One  of the files that I am updating is causing an error with my system, so  my question now is, how do I install just the one file.  

After I reinstalled 9.10, my system booted up no problem, and was not  freezing, then I did this:

Went to the system repository, loaded the CD update, hit reload, and had  some files, 7/15 install, the rest went to error because I'm still not  connected to the internet at that point.  Once that finished, I loaded  the BCMWL Kernel Source, which is what I need to get the system to  recognize my wireless card, and rebooted my computer.  Now my system  won't boot up again without the CD, and freezes when I boot with the CD.   What I think will work is if I can somehow just download and install  that BCMWL Kernel file, without the rest.  I can't imagine that being  that hard, so can someone help me out with this.

I've got the WMP54G Card if that helps.

---

### Post by Dukes24 on 2010-02-14
Well I must say I am disappointed with the zero help I received on this subject, however I was able to figure things out on my own.  I hope in the future people will be a little more helpful. 

If anyone has the same problem as myself, feel free to send me a message and I will GLADLY try and provide you as best as I can.

Cheers

---

### Post by northd_tech on 2010-02-14
Sorry Dukes- I was up to my elbows in carburetor this afternoon and not by the computer.  From what I remember, I think that BCMWL is a Broadcom wireless driver.  Are you using the proprietary Broadcom STA wireless driver by any chance?  Are your network connections working now?

What you are describing sounds like either a module conflict or a video/X server problem to me.

I'm glad you were able to get it fixed though.  Maybe your inquiry might have gotten a better response in a forum other than Networking & Wireless (although that "BCMWL" does sound like a Broadcom driver from what I remember, and I've run a Broadcom  card under Linux for a couple of years now).

The output of these commands might be informative, if it is a network problem:

```
lspci

lsmod

uname -a

sudo lshw -C network 

ifconfig

iwconfig
```

---

### Post by nadra on 2010-02-14
Hi

I am really new to UBUNTU and facing a problem with the internet connection. The wireless internet was connected but the browser wont connect to any webpage server. Why is that? Anyone can help?

---

### Post by northd_tech on 2010-02-14
Hi nadra,

Can you run those same commands above from a terminal window in ubuntu and post the results here?

---

