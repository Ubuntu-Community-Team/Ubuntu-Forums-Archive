---
title: "Can't connect to home wifi upon upgrading to 13.04 with Atheros AR9485 NIC"
date: 2013-05-02
forum: Networking &amp; Wireless
---

### Post by grey.kingsley on 2013-05-02
Shortly after I upgraded I noticed I was getting kicked off my wireless network fairly frequently(i.e. more often than *never*)

I looked around a few forum threads that google lead me to, but where there were proposed solutions, they didn't work.

I figured it might be an issue with the Atheros drivers included in the new kernel(I saw it downloading 3.8 in the distribution upgrade dialogue).

I rebooted and from the grub menu, I selected "Ubuntu with advanced options" and saw that I could choose to boot with the 3.5 kernel.

I booted with the 3.5 kernel and my problem was solved. I'm now going to use synaptic to uninstall the 3.8 kernel but keep the 3.5 kernel and try rebooting. With any luck I wont bork my laptop and I can get back to my software engineering homework. 

UPDATE: Synaptic complained when I tried to uninstall the 3.8 kernel image. Attempting to make grub use the 3.5 kernel by default instead of 3.8. Standby

UPDATE2: Followed the advice [here]("http://askubuntu.com/questions/216398/set-older-kernel-as-default-grub-entry") to make grub use the older kernel version by default. This works, but I see this more as a temporary patch than a permanent solution.

Hopefully people googling the same problem I had will find this thread and solve their problem too.

---

### Post by matt7195 on 2013-05-14
Thanks for the update.  I'm havign the same problem.  I'm running an Asus S500c with Atheros AR9485 Wireless and an AzureWave Device 2126 subsystem. But is switching back to the old kernel a safe solution?  I assumed I always want to have the most up-to-date kernel.  I know you're saying it's just a temporary patch, but I'm a little hesitant to implement this method.  I'd still be in the market for a more long-term answer, as I'm guessing you would.  Do you think it might be worth taking the [SOLVED] out of the post? Sorry if I'm just being negative.  Good work finding a patch!

---

### Post by wildmanne39 on 2013-05-14
Hi, I use 3.8 kernel with my 9485 and I have no issues but the kernel is installed on 12.04 so I wonder if it could be an update to network manager possibly causing the problem.

I do use a driver parameter and I have ipv6 set to ignore.
Thanks

---

### Post by grey.kingsley on 2013-05-24
Sorry it took me so long to get back to this! I had to go graduate. 

I'll try tolling back network manager to an older version and see if using the 3.8 kernel works.

Edit: it looks like there isn't an older version of network manager in the repositories, and I'm too lazy to go get it from gnome.org. If matt7197 is feeling squirrelly, then this link might save him a google

[http://ftp.gnome.org/pub/GNOME/sources/NetworkManager/0.9/](http://ftp.gnome.org/pub/GNOME/sources/NetworkManager/0.9/)

> **Wild Man said:**
> Hi, I use 3.8 kernel with my 9485 and I have no issues but the kernel is installed on 12.04 so I wonder if it could be an update to network manager possibly causing the problem.

I do use a driver parameter and I have ipv6 set to ignore.
Thanks

Any idea which version of network manager 12.04 uses?

---

### Post by wildmanne39 on 2013-05-25
Mine is 0.9.4.1 in 12.04.

---

