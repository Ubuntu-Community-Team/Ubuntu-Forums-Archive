---
title: "Network becoming unresponsive after a few minutes - Asus PCE-AC66, ndiswrapper, 12.04"
date: 2013-07-04
forum: Networking &amp; Wireless
---

### Post by ovymoont on 2013-07-04
Hi,

I've got the AsusPCE-AC66 wireless adapter on my desktop PC and I'm getting some really strange behaviour.

There are no Linux drivers available for this card from Asus so I'm using the WinXP drivers (6.30.77.0) with ndiswrapper (1.58) compiled from source and everything seems to be working fine - almost.

I've set the kernel module to load automatically, so when I boot into Ubuntu it connects straight away and it works  absolutely fine for while, but then the network suddenly become unresponsive - it stays connected but there is no data transfer.

If I just unload and then reload the ndiswrapper kernel module (see code below) it starts working again for a while and then it stops again, and so on...
```
sudo modprobe -r ndiswrapper
sudo depmod -a
sudo modprobe ndiswrapper
```
However, I've noticed that sometimes it works for hours and sometimes it becomes unresponsive after a very short time, and it seems to be directly related to how much data I download. For example, if I just check my e-mail, browse a few basic sites (i.e. no streaming, low data requirement), etc. it keeps working for hours. But if I start downloading something it stops really quickly, after a few MBytes. But in both circumstances it seems to stop after I download roughly the same amount of data. It's almost like there's a data buffer of some sort which gets filled, and when that happens it stops working.

Anyone any ideas as to what might be causing this problem and how it could possibly befixed?

---

### Post by ovymoont on 2013-07-05
Sorry about the bump...

---

### Post by chili555 on 2013-07-05
Are there any clues in the syslogs run immeadiately after an incident?```
cat /var/log/syslog | grep -e ndis -e etwork | tail -n25
```Have you seen this? [http://askubuntu.com/questions/315950/drivers-for-wireless-card-asus-pce-ac66](http://askubuntu.com/questions/315950/drivers-for-wireless-card-asus-pce-ac66) 

I'm not sure what package we might install for 12.04.

---

### Post by ovymoont on 2013-07-06
Hey, thanks for your response.

I've had a look through the other thread that you pointed out and after some research I found out that the latest **bcmwl-kernel-source** package (i.e. bcmwl-kernel-source_6.30.223.30+bdcom-0ubuntu3_amd64.deb) does have support for the Asus PCE-AC66 (i.e. chipset Broadcom BCM4360, PCI-ID 14e4:43a0), even if somewhat incomplete (it only connects at 130 Mbps, whereas with ndiswrapper and the WinXP driver it went up to 270 Mbps). The catch is that this package will be part of the upcoming **Saucy** release (i.e. Ubuntu 13.10) so for now it needs to be installed manually in **Precise** (i.e. Ubuntu 12.04).

Once I get some time I'll write a separate thread to explain how to install this package and get this network card working. But for now, for those who are more knowledgeable and know what to do with it, the relevant deb file can be downloaded from here:

 Download page: [https://launchpad.net/ubuntu/saucy/amd64/bcmwl-kernel-source/6.30.223.30+bdcom-0ubuntu3](https://launchpad.net/ubuntu/saucy/amd64/bcmwl-kernel-source/6.30.223.30+bdcom-0ubuntu3)
Download deb: [http://launchpadlibrarian.net/143917424/bcmwl-kernel-source_6.30.223.30%2Bbdcom-0ubuntu3_amd64.deb](http://launchpadlibrarian.net/143917424/bcmwl-kernel-source_6.30.223.30%2Bbdcom-0ubuntu3_amd64.deb)

---

### Post by artscoop on 2013-07-06
I seem to have the exact same problem but with an Hercules HWNUp150 USB Wifi adapter (Realtek RTL8188CUS/8192CU).
The wifi dies on me sometimes after a few seconds of wlan0 inactivity, and it does not matter if I use ndiswrapper or the kernel driver, the behaviour is the same. Unplugging and plugging the adapter again restores the connection, which dies again a few minutes later (network manager thinks the connection is still active, yet transfers nothing, not even in the LAN environment).

I've found that opening a terminal and pinging (with an interval of 5 seconds, for example) any machine, preferably one in the local network, allowed me to stay connected endlessly. Stop the ping and the connection dies quickly (less than 10 minutes).
Absolutely no answer could be found on the internet, yet it seems to be a very frequent problem.

@ovymoont, if ever you happen to find a solution or if your issue gets solved, don't forget to tell us ;)

---

### Post by chili555 on 2013-07-06
> **ovymoont said:**
> 
Once I get some time I'll write a separate thread to explain how to install this package and get this network card working. But for now, for those who are more knowledgeable and know what to do with it, the relevant deb file can be downloaded from here:

 Download page: [https://launchpad.net/ubuntu/saucy/amd64/bcmwl-kernel-source/6.30.223.30+bdcom-0ubuntu3](https://launchpad.net/ubuntu/saucy/amd64/bcmwl-kernel-source/6.30.223.30+bdcom-0ubuntu3)
Download deb: [http://launchpadlibrarian.net/143917424/bcmwl-kernel-source_6.30.223.30%2Bbdcom-0ubuntu3_amd64.deb](http://launchpadlibrarian.net/143917424/bcmwl-kernel-source_6.30.223.30%2Bbdcom-0ubuntu3_amd64.deb)It should be as easy as downloading the package appropriate to your architecture; either 32- or 64-bit, to your desktop and then:```
sudo dpkg -i Desktop/bcmwl*.deb
```The process is a little lengthy to execute, so please be patient.

I don't currently have a 12.04 installation so I can't test it and tell you it works as expected. I *have* tested it in 13.04 and it installs without any problem, although I don't have the Broadcom device so I can test no further.

Frankly, if it's working as expected for you with ndiswrapper, I'd be happy and stop there.```
chili@Think410:~$ lsb_release -d
Description:	Ubuntu 13.04
chili@Think410:~$ sudo dpkg -s bcmwl-kernel-source | grep Version
Version: 6.30.223.30+bdcom-0ubuntu3
```

---

### Post by chili555 on 2013-07-06
> **artscoop said:**
> I seem to have the exact same problem but with an Hercules HWNUp150 USB Wifi adapter (Realtek RTL8188CUS/8192CU).
The wifi dies on me sometimes after a few seconds of wlan0 inactivity, and it does not matter if I use ndiswrapper or the kernel driver, the behaviour is the same. Unplugging and plugging the adapter again restores the connection, which dies again a few minutes later (network manager thinks the connection is still active, yet transfers nothing, not even in the LAN environment).

I've found that opening a terminal and pinging (with an interval of 5 seconds, for example) any machine, preferably one in the local network, allowed me to stay connected endlessly. Stop the ping and the connection dies quickly (less than 10 minutes).
Absolutely no answer could be found on the internet, yet it seems to be a very frequent problem.

@ovymoont, if ever you happen to find a solution or if your issue gets solved, don't forget to tell us ;)This doesn't relate at all to the subject of the original post. You haven't the same Broadcom device, nor, I don't believe, need to use ndiswrapper. I suggest you start your own new thread.  I suspect your issue is either related to power management or probe response from the router. Check /var/log/syslog and Google.

---

### Post by ovymoont on 2013-07-06
> **chili555 said:**
> Frankly, if it's working as expected for you with ndiswrapper, I'd be happy and stop there.

Well, that's exactly the point, it wasn't working as expected with ndiswrapper, that's why i started this thread... :-|
Anyway, thanks for your help.

---

### Post by chili555 on 2013-07-06
So, are you going to try the .deb?

---

### Post by ovymoont on 2013-07-06
> **chili555 said:**
> So, are you going to try the .deb?

Huh? :confused: What do you mean am I going to try the deb???

I've already got rid of ndiswrapper and installed the deb and it works absolutely fine! Otherwise I wouldn't have made so much fuss about it.

The only thing, which for me is not a relevant issue anyway, is that with this deb driver the wireless only connects at 130 Mbps whereas with ndiswrapper and the WinXP driver it connects at 270Mbps and so does in Windows 7. But now at least the connection is stable and it doesn't freeze anymore.

---

### Post by chili555 on 2013-07-06
> **ovymoont said:**
> Huh? :confused: What do you mean am I going to try the deb???

I've already got rid of ndiswrapper and installed the deb and it works absolutely fine! Otherwise I wouldn't have made so much fuss about it.

The only thing, which for me is not a relevant issue anyway, is that with this deb driver the wireless only connects at 130 Mbps whereas with ndiswrapper and the WinXP driver it connects at 270Mbps and so does in Windows 7. But now at least the connection is stable and it doesn't freeze anymore.Sorry if I misunderstood. In any event, I'm glad it's mostly working.

---

### Post by ovymoont on 2013-07-06
No worries, I'm just happy it works! :-)

---

### Post by whylose on 2013-07-18
I have the same configuration as the OP and the same issue. Using the package listed by the OP and following the instructions from Chili555, and rebooting, and then manually loading the module, I got this to work. Moreover, I'm connected at 216Mbps as reported by Connection Information; this is the same speed I got when using the XP driver with ndiswrapper.

I will say that I felt compelled to cleanup those former elements and there are existing posts which cover that, so I won't repeat it. I am using the Unity interface and took one extra step which I didn't see explicitly enumerated herein, and found a simpler method for download and install, so I'll summarize, including the work of OP, Chili555 and my work:

* The original config works for a while, so why not take advantage of it to download the new package/module which we'll use later.
* Click the Settings icon in the top right -> System Settings -> Hardware -> Additional Drivers
- A new window will open, listing available proprietary drivers (not otherwise available through Software Center)
* Select Broadcom STA wireless driver and Install and then close the window
* Now that you've downloaded all you'll need, cleanup former config of XP driver and ndiswrapper (Search the Interwebs...I don't have a direct link to this procedure)
* At this point, I rebooted, but I suspect it's not necessary
* If the new Broadcom STA wireless driver does not load automatically, which mine did not, then load it manually with "modprobe wl"
- At this point, you should be up and running and connected to the network
* To make the module automatically load at reboot, add the module name, wl, on a line of its own, to /etc/modules

-tl

---

