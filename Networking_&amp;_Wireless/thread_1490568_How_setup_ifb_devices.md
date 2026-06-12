---
title: "How setup ifb devices?"
date: 2010-05-22
forum: Networking &amp; Wireless
---

### Post by frankabel on 2010-05-22
Hi all,

What I must install or do to get ifb devices running on lucid?

[http://www.linuxfoundation.org/collaborate/workgroups/networking/ifb](http://www.linuxfoundation.org/collaborate/workgroups/networking/ifb)

I see a very nice tutorial of how add imq at [http://www.nme.pl/2010/05/how-to-add-imq-patch-to-ubuntu-10-04-lucid-lynx/](http://www.nme.pl/2010/05/how-to-add-imq-patch-to-ubuntu-10-04-lucid-lynx/) but can't found anything about ifb, may be my googlefu is broken today ;)

Cheers
Frank Abel

---

### Post by SoftwareExplorer on 2011-03-18
I also have the exact same question (except for Maverick). 
According to [[COLOR="DeepSkyBlue"]https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/118580[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/118580"), the kernel should be built with support for this.

---

### Post by SoftwareExplorer on 2011-03-18
I think I found it!!!
I was reading [this question]("http://serverfault.com/questions/248500/qos-on-ubuntu-server"), which was about someone wanting to use imq, which from my understanding was a hackish predescessor to ifb implemented in a patch. Anyway, the person mentioned that that they did 'modprobe imq'. Well, I tried ```
sudo modprobe ifb
``` and then ```
sudo ip link set dev ifb0 up
``` which gave me an ifconfig of ```
<snip!>
he-ipv6   Link encap:IPv6-in-IPv4  
          inet6 addr: 2001:470:a:29f::2/64 Scope:Global
          UP POINTOPOINT RUNNING NOARP  MTU:1480  Metric:1
          RX packets:19072413 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12471919 errors:19688 dropped:0 overruns:0 carrier:19688
          collisions:0 txqueuelen:0 
          RX bytes:24300351228 (24.3 GB)  TX bytes:1366333608 (1.3 GB)

ifb0      Link encap:Ethernet  HWaddr c2:2d:3c:e0:a7:1b  
          inet6 addr: fe80::c02d:3cff:fee0:a71b/64 Scope:Link
          UP BROADCAST RUNNING NOARP  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:32 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20318444 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20318444 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10852639223 (10.8 GB)  TX bytes:10852639223 (10.8 GB)

<snip!>

```
PS:Yes, I did post the previous post less than an hour ago. No, I did not know the answer at the time!

---

### Post by diosney on 2011-06-17
Thanks SoftwareExplorer!

That worked for me too! 

I'm running Ubuntu 11.04.

---

