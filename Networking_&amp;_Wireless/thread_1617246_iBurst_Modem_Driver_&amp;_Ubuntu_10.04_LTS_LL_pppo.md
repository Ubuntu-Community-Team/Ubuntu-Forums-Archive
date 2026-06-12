---
title: "iBurst Modem Driver &amp; Ubuntu 10.04 LTS LL pppoeconf required after reboot."
date: 2010-11-09
forum: Networking &amp; Wireless
---

### Post by laylow45 on 2010-11-09
Hi forum

I'm a Linux noob an I am really desperate for some top, top, top assistance. :) Been battling a while now with my iBurst USB modem driver and hope there is someone out there that can help? :confused: I have been through umpteen forums and threads and tried literally everything I read, but to no avail. I also realize there aren't many Ubuntu users that use the iBurst modem, but I am appealing to the few out there that do.

I have installed the open source ibriver-2.6.31 for my iBurst USB modem. Initially all went well with fast connection etc., connection everytime I boot,  until... I started updates of 10.04 LTS, that is when I became aware, from the forums, that a re-install of the driver is required after every package update due to no "package management" in the iBdriver. :icon_frown: what a pain in the proverbial to say the least!

Anyways.. now I am the stage where the driver is always installed, but...all of a sudden, I need to run pppoeconf and set up the driver after each boot to get connected!!!! :confused: If I can't find a solution it will force me back to Windoze7 which I dread to do! :frown:  Can a script be written to pppoeconf (rp-pppoeconf.iso is loaded I think) automatically during boot perhaps?

So any top Linux hacker or "notsonoobasIam" user out there with a iBurst modem and similar pains & mis-fortunate experience please share your ideas and thoughts to correct this problem permanently for me please?  (I should maybe mention that the other day I performed the "Grub2 Profile" exercise to try and speed up the boot time, this does not perhaps have something to do with the fact that I need to reconfigure in pppoeconf after every boot does it? I doubt it)  Please help?!?!?

J

---

### Post by wRatte on 2010-11-11
sorry man. couldn't get it to work either. i love linux, but i can't use iburst with it, so i switched back to windows. (cause there's no point in having the OS without internet)

i believe i had the same issue as you (needed to pppoeconf after every boot), and then i guess the system updated and it all became busted again.

to be specific i used linux mint (built from ubuntu). if i come accross usefull info to solve this, i'll post it here - that's if i remember, etc, etc.

---

### Post by dineshs on 2010-11-11
> I need to run pppoeconf and set up the driver after each boot to get connected!!!! Not sure if [this]("http://ubuntuforums.org/showpost.php?p=546310&postcount=15") can help
[COLOR="Red"]OR[/COLOR]
Ref  [http://ubuntuforums.org/showpost.php?p=9611450&postcount=2](http://ubuntuforums.org/showpost.php?p=9611450&postcount=2)
and
1)Follow STEP-I 
2)Reboot 
3)Follow STEP-III or run *sudo pon dsl-provider* to connect and* sudo poff dsl-provider *to disconnect(Do not run sudo pppoeconf)

---

### Post by laylow45 on 2010-11-11
Thanks dineshs!

I will try this solution tonight and really hope it works!:P Will give report.

Just 2 questions, 


1. confirm I skip Step II? 
2. confirm the USB modem must be plugged in during the process and during reboot to Step III?


(this learning curve is going to be loooooooong, but worth it!:))
Thanks

---

### Post by dineshs on 2010-11-11
You may skip step-II .Instead do a reboot
> confirm the USB modem must be plugged in during the process and during reboot to Step III?
I havent tried a USB modem.Let it be plugged.
In your reply please post the contents of```
gksudo gedit /etc/network/interfaces.bak
```

---

### Post by laylow45 on 2010-11-11
thanks again dineshs

another noob question...under NM/DSL connection setup, where you enter username/password etc, what is entered into the "service" cell?

---

### Post by dineshs on 2010-11-11
Anything-say Your service provider

---

### Post by laylow45 on 2010-11-11
Hi dineshs

I bow to you! \\:D/
It really seems that it worked! I have rebooted/powered down about 5 times and the connection has been there everytime!!! Thanks. 

Ok another problem I have with this open source driver is that it has to be re-installed everytime there is a kernel or even, I think,  some other packages update?  I have read on the Ubuntu iBurst related documentation, this is because of the fact that there is no "package management" built into the [ ibdriver-2.6.31]("http://www.z9.co.za/ibdriver/ibdriver-2.6.31.tar.gz").  Is there perhaps a work-around for this problem?

for the record the contents of the interfaces.bak file:

auto lo
iface lo inet loopback
auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig ib0 up # line maintained by pppoeconf
provider dsl-provider
auto ib0
iface ib0 inet manual

Your assistance is highly appreciated.  Thanks!

Johan

---

### Post by dineshs on 2010-11-11
laylow45,
Very happy to hear the problem is solved.(Please mark it solved via thread tools):)
> Ok another problem I have with this open source driver is that it has to be re-installed everytime there is a kernel or even, I think, some other packages update? I have read on the Ubuntu iBurst related documentation, this is because of the fact that there is no "package management" built into the  ibdriver-2.6.31. Is there perhaps a work-around for this problem?I dont know .I believe that as long as you have the source you can compile

---

### Post by cov on 2010-12-13
Has anyone managed to get the USB iburst modem to work?

I have followed dineshs' instructions but cannot connect.

This is the modem:

[IMG]http://media.iburst.co.za/media/iBurstNeuvo/USBNewVersion.jpg[/IMG]

---

### Post by laylow45 on 2010-12-13
try re arranging your  etc/network/interfaces 

like this:

[I][B]auto lo
iface lo inet loopback

auto ib0
iface ib0 inet manual

auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig ib0 up # line maintained by pppoeconf
provider dsl-provider[/B][/I]

After I started picking up problems again, I have found that this works for me:D

---

### Post by psnel on 2012-05-11
There's a PPA available for iburst USB now that handles all the details of installing the driver (Ubuntu 12.04 and on), even when kernel gets updated. Also you don't need RP-PPPOE anymore, just the stock standard pppoe that comes pre-installed.

I've updated the [_Ubuntu Iburst Wiki_]("https://help.ubuntu.com/community/Iburst") with all the info.
(from ppa maintainer posted [_here_]("http://mybroadband.co.za/vb/showthread.php/82091-iBurst-and-Linux-setup?p=8153969&viewfull=1#post8153969"))

It's works, and other's have confirmed it to work.

Also, PPPoE support for wireless devices in NetworkManager is coming...
[https://bugzilla.redhat.com/show_bug.cgi?id=446338](https://bugzilla.redhat.com/show_bug.cgi?id=446338)

Looking good.

---

