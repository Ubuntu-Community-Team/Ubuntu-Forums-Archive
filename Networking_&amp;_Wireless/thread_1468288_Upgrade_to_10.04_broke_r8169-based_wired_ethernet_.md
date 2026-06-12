---
title: "Upgrade to 10.04 broke r8169-based wired ethernet (working only at 10Mbps)"
date: 2010-05-01
forum: Networking &amp; Wireless
---

### Post by Roivai on 2010-05-01
Greetings!

After upgrading from karmic to lucid yesterday made my RTL 8111 -network card die. It's integrated on Intel D510mo mini-itx board. 

dmesg:
```

[ 3138.346117] r8169: eth0: link down
[ 3138.346758] ADDRCONF(NETDEV_UP): eth0: link is not ready

```After some googling I found out a lot of forumposts about the same problem from year 2007, but the troubles seem to disappear on the newer versions and seem to be back now? With those posts I managed to get the link up by using ethtool by setting autoneg off and setting speed to be 10mbps and half duplex. Any other speed/duplex combination fails.

One suggestion I found was to install r8168-driver from Realtek instead of the r8169. It didn't help, result was very much the same.

I booted to 9.10 live-cd and there the network worked as intended (100Mbps, I dont have a gigabit switch)

Any suggestions? I really wouldn't like to fall back to 9.10, but my file server is not very usable with 10mbps. :)

---

### Post by David Stodolsky on 2010-05-01
I am seeing this issue after installing Lucid on a Gigabit P55A-UB5 MB. Dual Realtek RTL8111/8168B 

Tried to download latest drivers from Realtek, but site wants password.

---

### Post by Tuxist on 2010-05-02
same issue with r8169

---

### Post by David Stodolsky on 2010-05-02
Restarting the DSL bridge is bring up the network interface for me.

---

### Post by frank36 on 2010-05-02
mii-tool works for me where ethtool has bugs with r8169.
kernel 2.6.34
 # mii-tool -A 10baseT-FD

I checked with dstat and flood pings to see bandwith is real fullduplex.
ethtool -r didn't work and setting duplex to full seemed to work,but dstat showed congestion. dont trust ethtool

---

### Post by dillzz on 2010-05-25
All,

I am having the same issues as well with the Realtek cards.  Check the following post:

[http://ubuntuforums.org/showthread.php?t=1022411](http://ubuntuforums.org/showthread.php?t=1022411)

Installed 10.04 hoping for a fix. Still having the exact same issue. Network will be very sporadic. Only fix that seems to work is to put this in /etc/rc.local.

/etc/init.d/networking stop && /etc/init.d/networking start

---

### Post by gladroger on 2010-05-25
I have the same problem with Realtek 8111 and the issue didnt exist on 9.04

---

### Post by lidra on 2010-05-29
I was joyfully removing Vista from my Media Center and VMware server. I booted from the 10.04 live CD, and the world was at peace. 
Once I installed 10.04 , I rebooted and then this happens. 
I have the same issue. Funny enough the network card works perfectly fine under the live CD. Should I say it was working perfectly fine under Vista for the last year ? 

Anyway, I am hoping to use the stop start script and hopefully it works and remains working. Alternatively I have a gigabit network card doing laying around , hope that works as last resort. 
Will let you know.  

Cheers, 

Lidra

---

### Post by lidra on 2010-05-29
So far so good. The trick has worked. 
I will let you know how it goes in the next couple of days under use. 
Thank you for posting the trick with the start and stop. 

Cheers, 

Lidra

---

### Post by superspost on 2011-01-30
i just wanted to mention that i had similar problems with my 10.04 installation. Somewhere i read that after a power off and disconnecting all power cables, waiting some time then reconnecting is solving the problem with the network adapter.

It worked for me...

I should mention that i did this after i had installed the driver from the manufacturer since it was still not working.

hope it helps someone.

N

---

### Post by daddyfix on 2011-07-02
Powering off my fresh install and upgrade of ubuntu 10.04 and waiting for a moment seemed to work for me too.

Hope this helps someone also.

---

