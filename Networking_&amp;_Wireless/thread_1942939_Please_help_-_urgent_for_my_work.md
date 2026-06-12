---
title: "Please help - urgent for my work"
date: 2012-03-18
forum: Networking &amp; Wireless
---

### Post by revoice on 2012-03-18
Hello All,

I am new to linux since we started using it at work, I've been using it through a virtual machine and everything was great, so much that I started loving ubuntu more than windows for my homework.

So I decided to install an independant copy of ubuntu in my main computer instead of window, and made a backup of my virtual machine, so I rescue information from there, access and share some files in there, etc

So, I have ubuntu 11.10 with a virtualbox image of ubuntu 10.04.

The fact is that they seem both to use the same network address information, so when I run virtual box,, both host and guest start loosing packages and internet connectivity, to the point that internet is unusable in anyway.

This remains "broken" even after I shut down virtualbox, so I have to reboot. Sometimes networking restart does the job for me.

I am a newbie in linux and have no network knowledge either I just tried both NAT and Bridged Connection with the exact same results.

Internet works fine and network manager connects correctly, it just drops out (for example I ping [www.google.com]("http://www.google.com") and after 5 retries it stops getting any response until 2 o 3 minutes later, repeating this behavior)

I am connected directly to a broadband wired connection. No router. Direct IP.

Here is my IFCONFIG

---

### Post by d.atanasov on 2012-03-18
Hi revoice, 

First of all a good thing that you chose to switch to linux :) You will find a great things about it (if you want). I don`t understand what are you trying to do but if I am not wrong you want to make a fresh install on your personal computer and after that to take every important file from the virtual machine. For the first thing I would suggest to you a live cd/usb from ubuntu.com and install ubuntu using it. Second you can use different methods to synch your virtual machine and the fresh installation. As one example is "rsync" command and another is this post 
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)
So I hope that I helped :) 

cheers 
dinko

---

### Post by revoice on 2012-03-18
thanks! but I have already made a fresh install of ubuntu, and brought my virtual box image. This is what's going on:

I installed virtual box and loaded my old Ubuntu 10.04 from work. I need this one alive and working since I have my job stuff loaded in there and I cannot transmit it to my desktop (at least not yet).

1. I had issues sharing folders between ubuntus virtual machine and ubuntus host. Usually when I google information to do so, most of cases are windows - ubuntu, or mac - ubuntu, etc. I can't seem to find step by step guides to share files between ubuntu and ubuntu

2. An alternative was sharing those files through internet sources, but it seems I have trouble with internet connection when I run Ubuntu 10.04 virtual machine. It seems related to conflicting network configuration or something like that, since it works great until the moment I run the virtual machine. Once I turn it on, internet connection experiences sporadic and very frequent drops, so it is unusable, until I restarte the whole system.

---

### Post by matt_symes on 2012-03-18
Hi

As a test, try setting a static IP address on the host that you know will be different than the guest.

You can do this with network manager by right clicking on the connection and selecting edit connections->edit->ipv4 settings->method->manual, before you start up the guest in virtual box.

This will make sure it's not some IP address conflict. You are behind a router ?

Kind regards

---

### Post by revoice on 2012-03-18
Hi matt, thanks for the reply

I am directly connected to the internet. Can I set a static ip anyways?

---

### Post by d.atanasov on 2012-03-18
For the Sharing options is odd because some time ago I have tried such sharing and it worked flawless. You probably installed VirtualBox Guest Addition. This is what I found about setting manually a sharing folder 
[https://help.ubuntu.com/community/VirtualBox/SharedFolders](https://help.ubuntu.com/community/VirtualBox/SharedFolders)

> **matt_symes said:**
> 

This will make sure it's not some IP address conflict. You are behind a router ?

Kind regards
Well he said its static IP with no home router.

Yep you know this :) 
[http://tuxtweaks.com/2009/06/share-folders-linux-host-linux-virtual-machine-virtualbox/](http://tuxtweaks.com/2009/06/share-folders-linux-host-linux-virtual-machine-virtualbox/)

best regards

---

### Post by revoice on 2012-03-18
> **d.atanasov said:**
> For the Sharing options is odd because some time ago I have tried such sharing and it worked flawless. You probably installed VirtualBox Guest Addition. This is what I found about setting manually a sharing folder 
[https://help.ubuntu.com/community/VirtualBox/SharedFolders](https://help.ubuntu.com/community/VirtualBox/SharedFolders)


Well he said its static IP with no home router.

Yep you know this :) 
[http://tuxtweaks.com/2009/06/share-folders-linux-host-linux-virtual-machine-virtualbox/](http://tuxtweaks.com/2009/06/share-folders-linux-host-linux-virtual-machine-virtualbox/)

best regards

yay! that worked out flawlessly !

I am halfway to heaven now... hope I can manage to fix my network connectivity issues

---

### Post by revoice on 2012-03-18
I Think I have found the reason of my problem. And it was not only related to virtual box. Seemd to be more a permanent issue of intermittent package loss. An issue of the RTL8111/8168B PCI Express Gigabit Ethernet controller drivers

[http://ubuntuforums.org/showthread.php?p=11776291](http://ubuntuforums.org/showthread.php?p=11776291)

Will diagnose and confirm

---

### Post by revoice on 2012-03-20
Everything works great! I had some issues but the community is amazing I managed to solve them all..!!

second day on ubuntu, able to do everything I need here..!

Thx!

---

