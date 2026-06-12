---
title: "How to find LAN contents"
date: 2012-04-03
forum: Networking &amp; Wireless
---

### Post by jemvyc on 2012-04-03
I am lost about how to get my Local Area Network working again.  It used to work before Unity, and it might still work, but I don't know how to access it.

I am working with a wired network.  2 dual boot laptops, windowsXP and ubuntu, and 2 single boot windowsXP stand alone systems.  The laptops can access ethernet from either operating system and the standalones from XP.

My current effort is to see out to another LAN member from this laptop, named laptop a HP Presario 2100 running Ubuntu.  ifconfig on laptop gives the following:

-Laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0b:cd:32:39:42  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:cdff:fe32:3942/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:815 errors:0 dropped:0 overruns:0 frame:0
          TX packets:835 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:676701 (676.7 KB)  TX bytes:117043 (117.0 KB)
          Interrupt:10 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2080 (2.0 KB)  TX bytes:2080 (2.0 KB)

It can ping the other laptop (AcerX) and it shows up as samba 3.5.11 from AcerX running windowsXP.  laptop's drives show as c: e: and f: which are the xp designations on laptop.

Can somebody help me see what I am missing?  Maybe if I knew what I was doing, this might work.

---

### Post by gordintoronto on 2012-04-03
"My current effort is to see out to another LAN member from this laptop..."

Perhaps you could say this again using different words, please? Do you want to access shared folders? No one has responded to your question, perhaps because they don't understand what you want to do, or what is not working.

---

### Post by jemvyc on 2012-04-04
From this computer I am not able to see that there are any other computers in the LAN.  Before Unity I used to be able to click on network in the files list and it would list the computers in the LAN.  Now there is nothing and I don't know where to look for it.

If I try to print using another computer in the LAN all I get is an error about the printer not being found.  All this used to work before the change to Unity last fall.

---

### Post by jemvyc on 2012-04-04
I am continuing to try to figure this out.  I followed the instructions to use the gnome classic and from there I can see a network entry in the places title.  In file manager I can browse to "windows network" which then contains "my home" but when I try to open my home I get "unable to mount location"  "failed to retrieve share list from server".

Now that leaves 2 questions:
1 why can't I get to that dialog from Unity?

2 where to I look to fix the network problem?

Thanks

---

### Post by gordintoronto on 2012-04-04
I assume you have samba installed? You say you installed Unity, does this mean you upgraded to Ubuntu 11.04? I abhor upgrades, too many things go wrong.

If you run "printers," then select "network printer," and wait a few seconds, the printer might show up. It always does for me, and I've tried half a dozen distros/versions this year. (Brother laser connected to my router.)

You didn't make any change to your router? Some routers block communication between computers in the LAN.

---

