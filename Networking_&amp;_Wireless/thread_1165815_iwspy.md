---
title: "iwspy"
date: 2009-05-21
forum: Networking &amp; Wireless
---

### Post by faye_valentine on 2009-05-21
Hi,

I'm working on a project where a number of Netbooks running Ubuntu will communicate with each other (they are actually Netbooks sitting on top of/controlling Roombas). For this project I need to get wireless communication details, like the data provided from iwspy. The problem is that iwspy tells me that my wireless interface doesn't support wireless statistic collection or does not accept IP addresses. The wireless chip is the RT2860.

On my main laptop, also running Ubuntu, I can get iwspy to work. I believe that has an Atheros chip (it is a Macbook Pro, 5.1 or the unibody kind). It also tells me "interface doesn't support wireless statistic collection" but after I activate iwspy for that interface (sudo iwspy eth1 IPaddress) it works.

Finally (and oddly enough) on the Netbook, I can view the /proc/net/wireless file, and I DO have an entry for ra0 (the interface) even though iwspy does not work.

Any ideas?

---

### Post by druca on 2012-03-05
This may be a very old thread, sorry for resurrecting if this is true. Anyway, I was trying to do something similar and having the same issue. So I am downloading and installing a new kernel with all of the atheros debugging turned on etc. I think the atheros driver doesn't support iwspy or at least the kernel packaged from Ubuntu doesn't include the driver with the iwspy support turned on. So I am compiling a vanilla kernel myself with all of the debugging turned on. If there is an easier way to do this, let me know anyone! 

Thanks,
Drew

---

### Post by druca on 2012-03-05
Never mind. I did some googling and came up with this:

[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=51e779f0daa5c712439d37b907d58543e4fcf12a](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=51e779f0daa5c712439d37b907d58543e4fcf12a)

SOMEONE phased it out mac80211 support and forgot to announce it. Apparently its an old tool that no one cares about. So why include the command in wireless-tools package if it doesn't work? There may be cards it works with but probably in much older kernels...2.4? That should be fixed, just remove the command if it is defunct and not going to be supported.  

Also you could write your own implementation in C. The aircrack suite can monitor signal strength from other nodes if you put your card in monitor mode: "sudo airmon-ng wlan0" . Just borrow some code from airodump-ng.c, etc, and compile your own iwpsy-like program to get the same functionality.

That's what I am doing. If anyone has better ideas just post it here. 

Also thanks to the aircrack team! 


Thank you,
Drew

---

### Post by gordintoronto on 2012-03-05
Does inSSIDer produce similar output?

[http://www.metageek.net/products/inssider/](http://www.metageek.net/products/inssider/)

I find it useful for picking a WiFi channel.

---

### Post by druca on 2012-03-16
> **gordintoronto said:**
> Does inSSIDer produce similar output?

[http://www.metageek.net/products/inssider/](http://www.metageek.net/products/inssider/)

I find it useful for picking a WiFi channel.


This is a windows program. Thank you for the input anyway. I would rather write C code. I will post my code here when I am done. 

Thanks,
Drew

---

### Post by gordintoronto on 2012-03-16
Sorry, bad link.

[http://www.metageek.net/products/inssider/linux/](http://www.metageek.net/products/inssider/linux/)

I'm using it in Ubuntu.

---

