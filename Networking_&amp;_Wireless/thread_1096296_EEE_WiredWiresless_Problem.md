---
title: "EEE Wired/Wiresless Problem"
date: 2009-03-14
forum: Networking &amp; Wireless
---

### Post by aguyfrumcali on 2009-03-14
Hi All, 

Very new to Linux have played around with different live Distros but never really explored thoroughly.  I have a ASUS 1000HA EEE pc with windows xp and ubuntu 8.04 installed. 

I followed a tutorial online from this website to get Ubuntu installed [https://help.ubuntu.com/community/EeePC](https://help.ubuntu.com/community/EeePC) since I have no optical drive. My first question is, I know this is humiliating but I did the Ubuntu installation a while ago and can't remember if I installed just regular Ubuntu 8.04 of if I installed the EEE edition of Ubuntu.  I googled around and found the command cat /etc/issue which tells you which version of ubuntu is installed but all it returns is Ubuntu 8.04.1 /n /l anyone have any ideas on how I can figure out exactly which distro I installed? 

My other question or problem is I have my netbook hooked up ethernet and am still not being able to get online. I know the EEE Distro is supposed to come with some changes that are optimized for the EEE this is why I am concerned if I installed the correct distro which may be the reason why my Ethernet is not working. 
  
I'm not sure if my drivers are installed or how to check that and if LAN drivers come pre installed with Ubuntu, although my primary goal is to get my wireless working.

 I have gone through this tutorial [https://help.ubuntu.com/community/EeePC/Fixes](https://help.ubuntu.com/community/EeePC/Fixes) although it says you need a Ethernet connection to do it. I have been searching through these forums for a while and also read this thread [http://ubuntuforums.org/showthread.php?t=1056146](http://ubuntuforums.org/showthread.php?t=1056146) I have also been lurking on this forum as well [http://forum.eeeuser.com/](http://forum.eeeuser.com/) 

When I follow the tutorial to get my wireless working  [https://help.ubuntu.com/community/EeePC/Fixes](https://help.ubuntu.com/community/EeePC/Fixes) and I type sudo apt-get update in terminal with the ethernet connected I get a bunch of failed to fetch results and a "you may want to run apt-get update to correct these problems"

 Any help on getting my wireless or wired working would be great. 

Thank you.

---

### Post by chili555 on 2009-03-14
Well, it seems you have a working installation, no matter whether it's EEE-optimized or not. Let's get the ethernet working and then you can work on wireless.> bunch of failed to fetch resultsIt will not work without a working internet connection. 

First, let's see what kind of ethernet card you have. Open a terminal and do:```
sudo lshw -C network
```It will, after thinking for a moment, identify your ethernet and wireless! If your ethernet is what I suspect, Attansic L2, let's try:```
sudo modprobe atl2
ifconfig
```Did an eth0 interface magically appear? If so, please try hooking up the ethernet cable and:```
sudo dhclient eth0
```Did you connect, that is, get an IP address?

---

### Post by aguyfrumcali on 2009-03-14
Awesome thanks for your quick response Chili555 I am currently on my desktop with EEE in front: I think I should probably be careful posting ifconfig on these forums but im not getting an IP if I read the results correctly but when I do I'll be sure not to post them online. Thanks for your help. In the mean time I found this blog [http://kunin.wordpress.com/](http://kunin.wordpress.com/) but am a bit lost with the instructions, I was reading up on how to navigate terminal but haven't quite figured out Kunins instructions fully. Any other help would be greatly appreciated. I can't wait till I get wired/wireless with Ubuntu. 

**markse@markse-laptop:~$ sudo lshw -C network**
  *-network UNCLAIMED     
       description: Ethernet controller
       product: Attansic Technology Corp.
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: b0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0

**markse@markse-laptop:~$ sudo modprobe at12**
FATAL: Module at12 not found.

**markse@markse-laptop:~$ ifconfig**
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1354 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1354 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:68196 (66.5 KB)  TX bytes:68196 (66.5 KB)

[B]
markse@markse-laptop:~$ sudo dhclient eth0[/B]
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
markse@markse-laptop:~$

---

### Post by chili555 on 2009-03-15
> markse@markse-laptop:~$ sudo modprobe at12
FATAL: Module at12 not found.I believe you may have misread this part. We are looking for 'ay tee ell two' and not 'ay tee twelve'.

Please try again.

I looked at the blog you referred me to and he seems to think the correct driver is atl1e. (Ay tee ell one ee) If the atl2 module doesn't do the trick, let's see if we can further identify your card with:```
lspci -vv
```You can omit everything but the data relating to yout Attansic ethernet.

The instructions on the blog are pretty easy, so we can try those if *atl2* doesn't work. Do you have or can you borrow a USB key?

---

### Post by snowpine on 2009-03-15
I would highly recommend installing the eeepc kernel from array.org. It is the same kernel used in all of the eee specific distros (ubuntu eee, eeebuntu, easy peasy, cruncheee, etc). It should solve all of your hardware problems: [http://array.org/ubuntu/setup-hardy-alt.html](http://array.org/ubuntu/setup-hardy-alt.html)

Alternately, if your Ubuntu install is fresh and you don't have much invested in it, just start from scratch with an eee specific distro. eeebuntu seems like the most popular these days.

The problem is that Ubuntu 8.04 simply does not support the eee "out of the box".

---

### Post by chili555 on 2009-03-15
> **snowpine said:**
> I would highly recommend installing the eeepc kernel from array.org. It is the same kernel used in all of the eee specific distros (ubuntu eee, eeebuntu, easy peasy, cruncheee, etc). It should solve all of your hardware problems: [http://array.org/ubuntu/setup-hardy-alt.html](http://array.org/ubuntu/setup-hardy-alt.html)

Alternately, if your Ubuntu install is fresh and you don't have much invested in it, just start from scratch with an eee specific distro. eeebuntu seems like the most popular these days.

The problem is that Ubuntu 8.04 simply does not support the eee "out of the box".
This seems like a very reasonable approach. The instructions seem quite do-able. I suggest you proceed.

---

### Post by aguyfrumcali on 2009-03-15
Thank you all for the responses, Okay so I was sitting here studying for a test tomm, and couldn't stop but wonder if your fixes are going to work.  So lets try. 

I know I probably don't need to post the results of the sudo lshw -C network but I posted all for uniformity. I thought I might have hit the wrong key yesterday so I did the modprobe atl2 today and it worked but the sudo dhclient eth0 returned the same results, The text from terminal is displayed below: 


markse@markse-laptop:~$ **sudo lshw -C network **
  *-network UNCLAIMED     
       description: Ethernet controller
       product: Attansic Technology Corp.
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: b0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
markse@markse-laptop:~$ **sudo modprobe atl2**
markse@markse-laptop:~$ **ifconfig**
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1496 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1496 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:74800 (73.0 KB)  TX bytes:74800 (73.0 KB)

markse@markse-laptop:~$ **sudo dhclient eth0**
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device

Results for the **lspci -vv **(I believe this is the info you requested, it has the ethernet and the wireless) 

01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Unknown device 1a3b:1026
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin A routed to IRQ 0
	Region 0: Memory at f8000000 (64-bit, non-prefetchable) [disabled] [size=64K]
	Capabilities: <access denied>

03:00.0 Ethernet controller: Attansic Technology Corp. Unknown device 1026 (rev b0)
	Subsystem: ASUSTeK Computer Inc. Unknown device 8324
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 10
	Region 0: Memory at fbfc0000 (64-bit, non-prefetchable) [size=256K]
	Region 2: I/O ports at ec00 [size=128]
	Capabilities: <access denied>






Chili555, if I have some free time should I go through and try to figure out the kunin's wordpress blog, even though you think it might be the wrong driver? or should I try his instructions replacing his driver with yours? (I'm not even sure id be able to do that on my own but I could try, am just curious if its worth a try.) I have several flash drives that I can use.

Also, I'm going to try and install the kernel from array.org right now, say I get that installed do you think it would be better off to just install eeebuntu 8.10 rather than run the one I currently have (I figured out that I am running ubuntu eee 8.04, I found the .rar) am I going to run into other problems in the future by running this distro? 

Two other questions if you guys have time, 

1) If I can't get this figured out and decide to uninstall 8.04 and install eeebuntu 8.10 whats the easiest way to do that without screwing up the MBR for my windows partition. Considering I don't have external optical drive and cant easily replace the MBR. I have looked through this [http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm) but was wondering on your opinion, considering i would be reinstalling another distro. 

2) If I decide on doing the above (#1) where would I get eeebuntu 8.10 I checked [http://www.canonical.com/projects/ubuntu/unr](http://www.canonical.com/projects/ubuntu/unr) and it talks about it but there is no download link.  I also checked [http://www.distrowatch.com](http://www.distrowatch.com) and it isn't listed there either, I googled around for a little bit but only found forums of people talking about it. 

Thanks again for all your help, you guys are a wealth of information.

---

### Post by chili555 on 2009-03-15
I strongly suggest trying the eee-specific kernel from array.org before you do anything else. I wouldn't even consider a re-install until you see if the new kernel fixes your wired and wireless, which I believe it will. Are you having any other issues that a re-install would, hopefully fix?

---

### Post by Hobgoblin on 2009-03-15
> **aguyfrumcali said:**
> Awesome thanks for your quick response Chili555 I am currently on my desktop with EEE in front: I think I should probably be careful posting ifconfig on these forums but im not getting an IP if I read the results correctly but when I do I'll be sure not to post them online. 

If you are behind a router then your internal IP is of no use to anyone.

Even your WAN IP isn't a great deal of use (though it is more use than your internal IP) and you give that to every website you visit.

---

### Post by aguyfrumcali on 2009-03-15
No other issues at the moment, I followed the instructions from array.org and it works! I can't thank you guys enough I logged in and wala wireless network works perfectly you guys are amazing. I did a handstand in my room because I was soo excited! Really I would have never figured it out on my own. 

Chili please disregard the questions in the other post, but I do have three questions if you have time.

1) I was browsing firefox thinking I wanted to to install yahoo messenger and was curious if I should download a linux version or windows version and if they are compatible but then remembered Pigdin. If I do download programs can I download an .exe and install and run the program using a gui or for everything application must I use terminal to install them? Do I have to download linux versions or will the windows versions work? Also Since my hd is a single 160 gig and is split 80/80 C being my windows install and D being the linux if I do install programs where should I install them on the D? (Sorry I know this is 10 questions in one but if you can please answer them if you have time or refer me to some documentation where I can read them on my own either would be great, maybe a ubuntu for beginners, I have an article for terminal but nothing for linux/ubuntu in general. I am thinking amazon or Barnes and noble would be a good place to start)

2) The last step on [http://array.org/ubuntu/setup-hardy-alt.html](http://array.org/ubuntu/setup-hardy-alt.html) says to Uninstall the Generic Kernel (Optional)

       1. To remove yourself from Ubuntu's generic kernel updates, run the command:
          sudo apt-get remove linux-generic linux-image-generic linux-restricted-modules-generic 

whats your opinion on this? does it matter if I get updates for the original ubuntu kernel while using the one I updated to? Once I got online it said I have 271 updates and I have NOT ran the command above, should I install all those updates?

3) Compiz fusion or Beryl, I hear this is a pretty cool graphical program, wheres the best place to get information and or learn about and get instructions on how to install this.  I found a link to some documentation from ubuntu.com would this be the best place? 

Sorry for all the questions, but once I get started and learn the basics im sure I will be comfortable enough to research my own questions. Thanks again for all your help, you guys on the forums are a phenomenal resource.

---

### Post by sgosnell on 2009-03-15
1.  There is no such word as wala.  It's voila', and unfortunately the French have no word for it.  ;-)

2. NO Windows program will work in Linux, unless you run it in wine.  Forget .exe completely.  Pidgin will work with just about any IM system you can name, out of the box.

3. Like the array.org site says, removal of the previous kernel is optional.  You can remove it or not.  As long as you have storage space, it's doing no harm.  It's only a few MB.  I have 3 kernels on my system at the moment, and I can revert to any of them at will if one blows up on me.  As for updates, it's again a matter of choice.  Sometimes a large number of updates can destroy your system.  If it ain't broke, don't be in a hurry to fix it.  I would suggest playing with your newly-working system for awhile before doing any updates.

4.  As always, Google is your friend.

---

### Post by chili555 on 2009-03-15
The easiest way to install software is System -> Administration -> Synaptic. Search for whatever you'd like, Pidgin for example, and mark it for installation and click Apply. All dependencies will be handled for you and your software will be installed...wala!

Here is a great FAQ about Compiz: [http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)  I doubt that an EEE has the graphics horsepower to run it. Search carefully before you embark.

---

### Post by sgosnell on 2009-03-15
The Eee will run it, but I don't think it's worth the trouble.  The Eee is in fact a very capable machine, just in a small case.

---

### Post by Hobgoblin on 2009-03-16
> **aguyfrumcali said:**
> 
       1. To remove yourself from Ubuntu's generic kernel updates, run the command:
          sudo apt-get remove linux-generic linux-image-generic linux-restricted-modules-generic 

whats your opinion on this? does it matter if I get updates for the original ubuntu kernel while using the one I updated to? 

Yes, you need to do that otherwise you will get an updated kernel without the EeePC tweaks, and your networking will stop working.

---

### Post by aguyfrumcali on 2009-03-16
sgosnell- haha thanks for the viola I was just so excited that I forgot how to spell for a second. Lol I will also not be in a hurry to update, thanks for your input. 

Chili555- Thanks for the Snaptic option, I can't really think of any software applications that I want to install off the top of my head but just in case. 

If I did find programs online that were designed for ubuntu where you could just download and install them would that be through terminal or through a gui and do programs like this exist? 

Also, where is a good place to start learning ubuntu, not terminal like I said I have a tutorial for that but a place to learn how to navigate and understand ubuntu/linux, maybe like an overview..I guess the equivalent of a windows vista for dummies type book/article/website. 

Thanks

---

### Post by sgosnell on 2009-03-16
The tweaked kernel should still be available for booting, though.

---

### Post by chili555 on 2009-03-16
> If I did find programs online that were designed for ubuntu where you could just download and install them would that be through terminal or through a gui and do programs like this exist?Yes, they exist. However, if they are built for Ubuntu, then they generally in the repositories and available in Synaptic. If you find a *.deb* file out in the far reaches of the internet that is not available in Synaptic, you may be able to install it but it may cause problems; unsatisfiable dependencies, built for the wrong version of g++, built for an older (non-EEE!!!) kernel, etc. It's pretty advanced stuff, so tread carefully.

---

### Post by sgosnell on 2009-03-16
For places to learn about Ubuntu, try these for a start:
[http://www.ubuntulinux.org/wiki/FrontPage](http://www.ubuntulinux.org/wiki/FrontPage)
[https://help.ubuntu.com/](https://help.ubuntu.com/)

---

### Post by aguyfrumcali on 2009-03-16
Alright so I'm pretty sure I have everything squared away and am well on my way to learn just about as much as I can about Ubuntu.  Thanks again for all your help. I would have never been able to get this far without you guys. I have been reading forums and the ubuntu help for the last few days. If I have any other questions I will be sure to come back and give you guys a visit. Thanks 


-aguyfrumcali

---

### Post by sgosnell on 2009-03-17
Anytime.

---

