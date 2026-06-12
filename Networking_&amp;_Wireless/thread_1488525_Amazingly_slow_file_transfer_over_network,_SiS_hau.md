---
title: "Amazingly slow file transfer over network, SiS haunting me again!"
date: 2010-05-20
forum: Networking &amp; Wireless
---

### Post by shebaw on 2010-05-20
Hi all, I've fixed almost everything except this problem. My network card worked fine on Windows but since I switched from Windows, file transfer over the network using my network card is horribly slow, 30kbps max on 100mbps wired connection. I know my network card is working fine, and I'm trying to copy files between my Ubuntu PC and windows PC, I've set up Samba as recommended by these forums, I can transfer files when using wireless connection, but I still can't transfer files at a speed faster than 30kbps on a wired connection. And the funny part is, it's fast when copying files from Ubuntu to Windows but it's slow the other way. And I've tried this with more than 4 different Windows computers.

lspci returns this for the network controller
```
Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter
```Is there any way of updating drivers or something that I can do to fix this problem, thanks in advance!

Edit: I've had this problem on both Ubuntu 9.10 and Ubuntu 10.04

---

### Post by shebaw on 2010-05-21
*bump*

I have tried connecting it with a mac and I still can't copy files to my computer at acceptable speed but it's fine the other way round. Any one with the same issue, please I really really need this.
Thanks in advance.

---

### Post by shebaw on 2010-05-22
*bump*
Anyone?

---

### Post by shebaw on 2010-05-24
I guess I have to lock it down then, please anyone this will be my last bump, I really really really need this!

---

### Post by hsoulen on 2010-05-24
> **shebaw said:**
> I guess I have to lock it down then, please anyone this will be my last bump, I really really really need this!

Try this thread: [http://ubuntuforums.org/showthread.php?t=1482851](http://ubuntuforums.org/showthread.php?t=1482851)

Hope it helps.

Cheers,

Hank

---

### Post by shebaw on 2010-05-25
> **hsoulen said:**
> Try this thread: [http://ubuntuforums.org/showthread.php?t=1482851](http://ubuntuforums.org/showthread.php?t=1482851)

Hope it helps.

Cheers,

Hank

Thanks, I will give it a try and post my results.

Edit: I still have slow file sharing speed but I can share at about 3mbps on Wireless connection. Sharing files over wired connection is unthinkable, I still get 30-120kbps over wired connection.

---

### Post by hsoulen on 2010-05-26
Sorry the MTU fix didn't work well for you.

Is this a desktop or laptop? Unfortunately SIS networking support appears to be pretty weak in most Linux distros.

Last recommendation I have in my bag if you are unable to replace the card is to try a custom kernel, it is not for the faint of heart and can be a real bear when new kernels are released but sometimes can be very helpful in supporting hardware that is not readily available in the generic kernels.

This link is a good starter but I would recommend some further reading:

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

Cheers,

Hank

---

### Post by shebaw on 2010-05-26
> **hsoulen said:**
> Sorry the MTU fix didn't work well for you.

Is this a desktop or laptop? Unfortunately SIS networking support appears to be pretty weak in most Linux distros.

Last recommendation I have in my bag if you are unable to replace the card is to try a custom kernel, it is not for the faint of heart and can be a real bear when new kernels are released but sometimes can be very helpful in supporting hardware that is not readily available in the generic kernels.

This link is a good starter but I would recommend some further reading:

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

Cheers,

Hank

Thanks Hank, I guess the custom kernel is the only way to go since I'm using a laptop and I don't think I can replace my network card(Damn you SiS!!!). By the way, does Ubuntu update the kernel regularly, I think I would wait for the updates since I'm only using Ubuntu on my laptop and I don't want to risk the support by using a custom kernel.

---

### Post by hsoulen on 2010-05-26
Shebaw,

Ubuntu is pretty regular as far as kernel updates go, but I would not hold your breath for support for this SIS Lan card. From what I can see it dates from around 2005 and while not exactly "legacy" hardware I am pretty sure support for it will only reduce as opposed to increase.

What I did find is that SIS has an available Linux driver in their downloads section, it is dated from 2005 so it may not work with 2.6.x kernels but it may help, I stress USE AT YOUR OWN RISK as this driver is very dated.

SIS Download Site:
[http://www.sis.com/download/](http://www.sis.com/download/)

Just pick "Linux" then "Network Driver" and select "SIS191 Gigabit & SIS190 LAN"

The driver is for Fedora Core but should work for any 2.6.x kernel.

There is a readme in the archive and I have to tell you, the driver is a kernel module which will require you compile it to get it installed and according to the thread below from 2008 it may still be trouble. Read the below thread before you try anything as the readme gives only very sparse information and no detail on compiling a kernel module (there is no included makefile) so depending on your confidence with linux this may/not be a challenging experience.

Another SIS190 thread with details on compiling the driver:
[http://ubuntuforums.org/showthread.php?t=188060](http://ubuntuforums.org/showthread.php?t=188060)

Sorry I cannot be more helpful.

Cheers,

Hank

---

### Post by mchlor on 2010-05-26
similar problem here.

using built-in realtek, xp = 120 MBytes/sec.  ubuntu = 20 MBytes/sec.  Lost 100 MBytes of throughput going from xp to ubuntu server LOL.


:mad:

---

### Post by shebaw on 2010-05-27
> **mchlor said:**
> similar problem here.

using built-in realtek, xp = 120 MBytes/sec.  ubuntu = 20 MBytes/sec.  Lost 100 MBytes of throughput going from xp to ubuntu server LOL.


:mad:

LOL, it went from 10mbs to 30kbps for me, I could easily settle with 5mbps now but I don't think it's going to happen any time soon.

---

