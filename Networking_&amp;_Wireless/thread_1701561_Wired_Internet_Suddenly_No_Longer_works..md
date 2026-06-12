---
title: "Wired Internet Suddenly No Longer works."
date: 2011-03-06
forum: Networking &amp; Wireless
---

### Post by Cean on 2011-03-06
Hello. My wired internet was working fine and dandy under Maverick until today. For no apparent reason, it stopped. The router works fine. All other computers are able to connect. I've tried using different cables with no luck. I have a [Biostar A785G3 ]("http://www.biostar.com.tw/app/en/mb/content.php?S_ID=459")motherboard with an integrated Realtek RTL8111DL ethernet controller. 

My problem sounds very similar to this guy's: [http://ubuntuforums.org/showthread.php?t=1692390&highlight=wired+connection+disconnected](http://ubuntuforums.org/showthread.php?t=1692390&highlight=wired+connection+disconnected). But his strange solution didn't seem to work in my case. 

Help is much appreciated.

-Cean

---

### Post by Cean on 2011-03-06
I tried installing the new drivers from Realtek. Still no luck. It seems so strange that it would suddenly stop working after having worked without any problems. Perhaps it may have been triggered by a recent update? Has anyone else had this problem recently?

---

### Post by deceaseddolphin on 2011-03-06
I've the same problem. Wired or wireless internet wouldn't work!

I updated this afternoon and the network-manager was removed in the update.

i tried enabling networking but didn't work. posted in the forum, i'm waiting for some replies!

---

### Post by JBAlaska on 2011-03-06
Have you tried to ping your router (Gateway) address. if you have other computers on the router, you might have a internal IP collision (2 computers with the same IP address).
First run **ifconfig** and see if you have **eth0**, and post the output here.

---

### Post by deceaseddolphin on 2011-03-06
Hi JBAlaska,

ifconfig command gives:

root@dolphin-laptop:/var/lib/NetworkManager# ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)


there is no eth0 here.

Thanks!

---

### Post by deceaseddolphin on 2011-03-06
I added just two lines:

auto eth0
iface eth0 inet dhcp

to existing

auto l0
iface l0 inet loopback

in /etc/network/interfaces

and wired internet worked like a miracle!

although the issue of wireless internet remains.

---

### Post by ToFue on 2011-03-06
check the status of ```
 # ifconfig -a 
``` Also, try ```
# sudo ifconfig eth0 up
```

You can plug in the ip's manually if need-be, if just to get network manager back with apt-get.
 check out ```
# info ifconfig 
``` for details on that..
 off hand, I'm not sure where to add DNS numbers, but it should be somewhere in /etc if i'm not mistaken..
Hope this points you to the right place, and keep looking for other forum posts to hint to the solution..

---

### Post by Cean on 2011-03-06
ifconfig output:

```
eth0      Link encap:Ethernet  HWaddr 00:30:67:58:ff:a9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:42 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

```

An IP conflict was one of my first guesses. I shut down all computers and reset the router. Then I started only the problem computer. This didn't seem to work.

---

### Post by JBAlaska on 2011-03-06
Glad you got it working, although I see no mention of wireless in your OP. Please give us all the info on your wireless, Brand, model number, type (USB, PCI etc).

---

### Post by deceaseddolphin on 2011-03-06
> **JBAlaska said:**
> Glad you got it working, although I see no mention of wireless in your OP. Please give us all the info on your wireless, Brand, model number, type (USB, PCI etc).
I installed WICD to handle wireless networks and as I rebooted Ubuntu, default networking icon displayed!

Thanks for the help! It's solved now :-)

here's the information:


eth0      Link encap:Ethernet  HWaddr 00:24:be:3e:78:9c  
          inet addr:10.3.73.134  Bcast:10.3.79.255  Mask:255.255.240.0
          inet6 addr: fe80::224:beff:fe3e:789c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10250 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7133 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10714737 (10.7 MB)  TX bytes:792909 (792.9 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:443 errors:0 dropped:0 overruns:0 frame:0
          TX packets:443 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:39684 (39.6 KB)  TX bytes:39684 (39.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:26:5e:f4:55:32  
          inet6 addr: fe80::226:5eff:fef4:5532/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:71 errors:0 dropped:0 overruns:0 frame:0
          TX packets:91 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5886 (5.8 KB)  TX bytes:9566 (9.5 KB)

---

### Post by Cean on 2011-03-06
I'm happy your problem has been solved, dolphin. I tried your solution but it didn't work in my case. Adding those lines results in the network connection icon dissapearing completly.

---

### Post by deceaseddolphin on 2011-03-06
> **Cean said:**
> I'm happy your problem has been solved, dolphin. I tried your solution but it didn't work in my case. Adding those lines results in the network connection icon dissapearing completly.
did you update anything?

I'm not sure why it didn't work in your case, may be its something else.

---

### Post by Cean on 2011-03-10
Yeah, I've updated quite a few things. Problem is I don't know which update might have caused the problem. I've been trying to find time to sift through a sea of posts that could be related to my problem, but It's starting to look more and more like the quickest and easiest solution will be to downgrade to 10.04. Not really a solution, I guess, but it works.

---

### Post by Cean on 2011-03-10
Not quite ready to downgrade yet.

Tried [this solution]("http://ubuntuforums.org/showpost.php?p=9394915&postcount=26") to no avail. Apparently this is a huge bug that mostly affects people with dual boot systems. My computer has allways been 100% Linux. 

Has anyone come across any other solutions I can try?

---

### Post by Cean on 2011-03-11
Success!


After installing WICD, I am able to connect to the internet.

---

