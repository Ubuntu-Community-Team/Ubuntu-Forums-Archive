---
title: "dnsmasq"
date: 2009-06-08
forum: Networking &amp; Wireless
---

### Post by m2.g5ru6y7s on 2009-06-08
I have NOT installed the package netmasq.
The package netmasq-base is installed by default (at least in Jaunty by my knowledge) 
But still I see dnsmasq in the process list appear (ps -efH | grep dnsmasq) at my machine.
I don't want dnsmasq to run, because this cause MAYBE trouble by using XDMCP (This issue I have to find out)
What in the hack starts the process dnsmasq????
I cannot find it anywhere in /etc/*

Of course I can execute a pkill dnsmasq, but I know it must be done on a cleaner way.
/etc/init.d/dnsmasq does not exist for all who claims to use this statement.

Thanks in advance.

---

### Post by m2.g5ru6y7s on 2009-06-08
Anyone :(

---

### Post by Iowan on 2009-06-08
I can't find **dnsmasq** on my Jaunty laptop, but the **man** page is there and mentions some related files near the bottom.  What is the parent process?

---

### Post by m2.g5ru6y7s on 2009-06-09
> **Iowan said:**
> I can't find **dnsmasq** on my Jaunty laptop, but the **man** page is there and mentions some related files near the bottom.  What is the parent process?

Thanks for your answer.

There is no parent process of my dnsmasq process. It is very much on top (very low process ID and started nearly at boot time
Just beneath the  dhclient3 process. 
Unfortunately I have just killed it, so I cannot tell exact where it is anymore.

Even more frustrating: My XDMCP experiment failed. I thought dnsmasq was the cause of my failing XDMCP experiment...

I have created a lot of virtual Jaunty machines (VirtualBox) and ALL those machines works perfectly with XDMCP, EXCEPT the HOST  which refuse XDMCP. Very strange. I have used the same gdm.conf-custom of the working virtual machines and still XDMCP refuses to work on the main machine :-(
When I analyze the packets with Wireshark for example I can see that X do nothing with the XDMCP requests. 
Again thanks for your thoughts! :p

---

### Post by m2.g5ru6y7s on 2009-06-09
I have found the cause :D !
I had installed a custom kernel 2.29.4 ([http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.4/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.4/) )
With this kernel XDMCP does not work properly.
I don't know if I must report this to the kernel developers ?
Maybe it is done on purpose?

If I should report this issue, can anybody tell to who and how?

On the default kernel 2.6.28-11 XDMCP works like a charm. Without any glitches... That must be possible
on a 2.6.29 in my humble opinion ...

---

