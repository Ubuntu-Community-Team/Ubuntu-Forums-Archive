---
title: "I cant compile the e1000 driver."
date: 2005-12-22
forum: Networking &amp; Wireless
---

### Post by Cooky on 2005-12-22
Hi,

I've recently bought a new computer ; this one is shipped with an Intel gigabit intergrated network Card. Unfortunatly, the Ubuntu driver for these kind of card (e1000) is outdated, and then I must compile the new one from the intel website in order to make the network working on my Ubuntu computer.
But when I try to compile it, I'm getting this error message :

> cooky@ubuntu:~/Desktop/e1000-6.2.15/src$ sudo make install
make -C /lib/modules/2.6.12-9-386/build SUBDIRS=/home/cooky/Desktop/e1000-6.2.15/src modules
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[1]: gcc-3.4 : commande introuvable
make[1]: entrant dans le répertoire « /usr/src/linux-headers-2.6.12-9-386 »
  CC [M]  /home/cooky/Desktop/e1000-6.2.15/src/e1000_main.o
Dans le fichier inclus à partir de include/asm/system.h:5,
          à partir de include/asm/processor.h:18,
          à partir de include/asm/thread_info.h:17,
          à partir de include/linux/thread_info.h:21,
          à partir de include/linux/spinlock.h:12,
          à partir de include/linux/capability.h:45,
          à partir de include/linux/sched.h:7,
          à partir de include/linux/module.h:10,
          à partir de /home/cooky/Desktop/e1000-6.2.15/src/e1000.h:37,
          à partir de /home/cooky/Desktop/e1000-6.2.15/src/e1000_main.c:29:
include/linux/kernel.h:10:20: erreur: stdarg.h : Aucun fichier ou répertoire de ce type
In file included from include/asm/system.h:5,
                 from include/asm/processor.h:18,
                 from include/asm/thread_info.h:17,
                 from include/linux/thread_info.h:21,
                 from include/linux/spinlock.h:12,
                 from include/linux/capability.h:45,
                 from include/linux/sched.h:7,
                 from include/linux/module.h:10,
                 from /home/cooky/Desktop/e1000-6.2.15/src/e1000.h:37,
                 from /home/cooky/Desktop/e1000-6.2.15/src/e1000_main.c:29:
include/linux/kernel.h:94: erreur: syntax error before ‘va_list’
include/linux/kernel.h:95: attention : function declaration isn’t a prototype
include/linux/kernel.h:98: erreur: syntax error before ‘va_list’
include/linux/kernel.h:99: attention : function declaration isn’t a prototype
include/linux/kernel.h:102: erreur: syntax error before ‘va_list’
include/linux/kernel.h:103: attention : function declaration isn’t a prototype
include/linux/kernel.h:107: erreur: syntax error before ‘va_list’
include/linux/kernel.h:108: attention : function declaration isn’t a prototype
include/linux/kernel.h:119: erreur: syntax error before ‘va_list’
include/linux/kernel.h:120: attention : function declaration isn’t a prototype
In file included from include/linux/if_ether.h:107,
                 from include/linux/netdevice.h:29,
                 from /home/cooky/Desktop/e1000-6.2.15/src/e1000.h:46,
                 from /home/cooky/Desktop/e1000-6.2.15/src/e1000_main.c:29:
include/linux/skbuff.h: In function ‘skb_add_data’:
include/linux/skbuff.h:1067: attention : pointer targets in passing argument 1 of ‘csum_and_copy_from_user’ differ in signedness
In file included from include/linux/ip.h:84,
                 from /home/cooky/Desktop/e1000-6.2.15/src/e1000.h:61,
                 from /home/cooky/Desktop/e1000-6.2.15/src/e1000_main.c:29:
include/net/sock.h: In function ‘skb_copy_to_page’:
include/net/sock.h:992: attention : pointer targets in passing argument 1 of ‘csum_and_copy_from_user’ differ in signedness
/home/cooky/Desktop/e1000-6.2.15/src/e1000_main.c: In function ‘e1000_set_mac’:
/home/cooky/Desktop/e1000-6.2.15/src/e1000_main.c:2187: attention : pointer targets in passing argument 1 of ‘is_valid_ether_addr’ differ in
signedness
make[2]: *** [/home/cooky/Desktop/e1000-6.2.15/src/e1000_main.o] Erreur 1
make[1]: *** [_module_/home/cooky/Desktop/e1000-6.2.15/src] Erreur 2
make[1]: quittant le répertoire « /usr/src/linux-headers-2.6.12-9-386 »
make: *** [default] Erreur 2
cooky@ubuntu:~/Desktop/e1000-6.2.15/src$

In fact I found the compiled driver here :
[http://blog.dataloss.nl/perma/ubuntu-510-breezy-on-dell-dimension-9150/]("http://blog.dataloss.nl/perma/ubuntu-510-breezy-on-dell-dimension-9150/")
but I would be glad if I can compile it myself.
I think that some of you have met this problem and have resolved it...Am I wrong?

---

### Post by towsonu2003 on 2005-12-23
try again after doing this ```
sudo apt-get update
sudo apt-get install build-essential gcc-3.4
``` (or install build-essential and gcc-3.4 using synaptic :) )

other than that, have no idea...

but this > make[1]: gcc-3.4 : commande introuvable means it could not find a compiler (which will compile ;) )

If this fails again with same message, try to find a forum thread where it explains how to make a link from gcc<version> so that 'make install' uses that version... I'm very inexperienced with compiling (thus using debian-based distro :) )

Also, you might want to use 'checkinstall' instead of 'make install' ```
sudo apt-get install checkinstall
``` to make it easier to remove the thing (if needed) later.

---

### Post by Cooky on 2005-12-23
thank a lot, it works now!

---

### Post by mips on 2006-02-16
[http://www.ubuntuforums.org/showthread.php?p=741687](http://www.ubuntuforums.org/showthread.php?p=741687)

Thanks to ubuntulifestyle for the french to english tranlation of the wiki page.

---

