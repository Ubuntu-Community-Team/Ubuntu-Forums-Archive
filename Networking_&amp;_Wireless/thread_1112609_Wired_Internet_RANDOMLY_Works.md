---
title: "Wired Internet *RANDOMLY* Works"
date: 2009-03-31
forum: Networking &amp; Wireless
---

### Post by AbsentHarvest on 2009-03-31
I'm running 8.10 Ubuntu.  I have a wired ethernet connection.  When I first installed this operating system, I don't believe I had this problem, but after various updates and installations... I believe something triggered this.

BASICALLY, I turn the computer on, log in and oddly enough I have no connection, or sometimes I do.  If the internet doesn't work, I keep rebooting until it works again.  Anywhere from 1-4 boots.  Logging out doesn't reset this, only rebooting seems to work.

What do I have to do to give you more information when this occurs again?
Do you need a ifconfig and iwconfig report?
If anyone knows how to help me in this situation, it'd be greatly appreciated. :popcorn::popcorn:

---

### Post by AbsentHarvest on 2009-04-01
Bump

---

### Post by superprash2003 on 2009-04-01
yes.. posting an ifconfig output when it works and when it doesnt could help..

---

### Post by AbsentHarvest on 2009-04-03
Working:

eth0      Link encap:Ethernet  HWaddr 00:21:9b:07:3b:41  
          inet addr:192.168.0.103  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::221:9bff:fe07:3b41/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1322908 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1319552 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:1317738130 (1.3 GB)  TX bytes:357972449 (357.9 MB)
          Memory:fdfc0000-fdfe0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:728 (728.0 B)  TX bytes:728 (728.0 B)

Not working:

eth0      Link encap:Ethernet  HWaddr 00:21:9b:07:3b:41  
          inet6 addr: fe80::221:9bff:fe07:3b41/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:51 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:3717 (3.7 KB)  TX bytes:2178 (2.1 KB)
          Memory:fdfc0000-fdfe0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1128 (1.1 KB)  TX bytes:1128 (1.1 KB)

Any ideas?

---

### Post by AbsentHarvest on 2009-04-03
Sorry. :/ Bump.

---

### Post by pgmer6809 on 2009-04-04
> **AbsentHarvest said:**
> Working:

eth0      Link encap:Ethernet  HWaddr 00:21:9b:07:3b:41  
          inet addr:192.168.0.103  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::221:9bff:fe07:3b41/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1322908 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1319552 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:1317738130 (1.3 GB)  TX bytes:357972449 (357.9 MB)
          Memory:fdfc0000-fdfe0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:728 (728.0 B)  TX bytes:728 (728.0 B)

Not working:

eth0      Link encap:Ethernet  HWaddr 00:21:9b:07:3b:41  
          inet6 addr: fe80::221:9bff:fe07:3b41/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:51 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:3717 (3.7 KB)  TX bytes:2178 (2.1 KB)
          Memory:fdfc0000-fdfe0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1128 (1.1 KB)  TX bytes:1128 (1.1 KB)

Any ideas?

if you look at your output you will see that in the working case you have an ip(version4) address assigned (192.168.0.103) and in the non working case you have no such address. 
I have posted on this topic, extensively.(do a search in this forum for pgmer6809) I believe it to be a bug in the kernel. Finally a day or so ago I sent an email to kernel.org describing the problem.
bgerlich has now posted a link ([http://tjworld.net/ubuntu/bugs/lp284377/](http://tjworld.net/ubuntu/bugs/lp284377/)) to a page where you can download patches for your kernel apply them and presumably recompile.
Here's hoping Ubuntu provides a patched version of the kernel in their repositories.
The text describing the patches at the above link seems to match your symptoms; 
pgmer6809

---

### Post by AbsentHarvest on 2009-04-04
My only question is how do I activate/install .patch files in that link you sent?

---

### Post by pgmer6809 on 2009-04-05
> **AbsentHarvest said:**
> My only question is how do I activate/install .patch files in that link you sent?

The short answer to your question is that I dont know. I never really patched the kernel myself. It is not that straightforward. You have to DL the source of the kernel, DL the patch file, run the patch program, recompile the kernel (which will probably require DLing some more dependencies etc. etc.)
Then once the kernel is recompiled you have to make it 'active' and bootable without screwing up your current setup in case it does not work. 

All of which I know NOT how to do.
(There might be a detailed HOWTO at the Linux Documentation Project [http://tldp.org/](http://tldp.org/)


In my post of two days ago, I give a list of drivers some of which work and some of which dont.

I have solved my problem in one of two ways:
a) I don't use any version of Ubuntu later than GUTSY (which does not have this kernel bug.)
b) I use an add-on LAN card (they are pretty cheap) of slightly older vintage (SMC or 3Com for example) from a no longer active computer. The older drivers do not seem to have this problem either.

In the meantime I am waiting for UBUNTU to provide a patched kernel in their IBEX or HARDY repository.

Good luck.

See this thread:

[http://ubuntuforums.org/showthread.php?p=7003301&highlight=pgmer6809#post7003301](http://ubuntuforums.org/showthread.php?p=7003301&highlight=pgmer6809#post7003301)

---

### Post by pgmer6809 on 2009-04-05
> **AbsentHarvest said:**
> My only question is how do I activate/install .patch files in that link you sent?

Part two of the answer.
Go to the installation and upgrades forum and do a search for Kernel Patch.
You will find a thread that refers to a Marvell Yukon chip not working.
Follow that thread.

This thread in the Installation forum, describes about 90% of what you would need to do.
The only thing left is to actually run the patch program.
that should be pretty simple,; type man patch from the cmd line and it looks straightforward.

pgmer6809
[http://ubuntuforums.org/showthread.php?t=781022&highlight=patch+kernel](http://ubuntuforums.org/showthread.php?t=781022&highlight=patch+kernel)

---

### Post by AbsentHarvest on 2009-04-29
I haven't replied for awhile.  I had given up on stopping this random occurrence.  I upgraded to Ubuntu. 9.04 hoping that would fix the problem.  It fixed all the other problems I've had with the operating system.  This is the only issue now.  Same symptoms as before, any idea how to do this on the 9.04?  Or is it the same steps as described above?

---

