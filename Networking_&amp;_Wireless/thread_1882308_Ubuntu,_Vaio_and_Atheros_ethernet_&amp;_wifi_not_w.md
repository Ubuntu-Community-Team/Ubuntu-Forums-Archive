---
title: "Ubuntu, Vaio and Atheros ethernet &amp; wifi not working"
date: 2011-11-17
forum: Networking &amp; Wireless
---

### Post by fmmarzoa on 2011-11-17
Hello,

I've bought yesterday a Sony Vaio in an special offer on a commerce of muy city. It comes with Windows 7, but I wan to run it with Ubuntu like my other computers.

Once again, I found problems with network drivers, but this time none of web devices works, no wifi but neither ethernet. :-|

On lspci only the Ethernet device is showed, but not the wifi one :-? so I gather this information from windows 7 device administrator:

WiFi: Atheros AR9485WB-EG
Ethernet: Atheros AR8151PCI-E

I need a solution for the WiFi at least.

I've problems in the past with two other laptops wifi devices, but I managed to solve it using ethernet interface.

But in this case, since I've no ethernet device, I cannot use aptitude nor apt-get for install packages like buildessential.

So... what can I do??

TIA,

---

### Post by fmmarzoa on 2011-11-17
Sorry, I've put AR985WB-EG where it should be AR9485WB-EG. Now I've edited it.

---

### Post by fmmarzoa on 2011-11-17
Hello,

Can any administrator or moderator move this post to Networking/Wireless forum? I didn't notice it before.

Thanks in advance and excuse me,

---

### Post by coffeecat on 2011-11-17
> **fmmarzoa said:**
> Can any administrator or moderator move this post to Networking/Wireless forum? I didn't notice it before.

Done! :)

If you ever need a thread moved, you can click on the "Report Abuse" button in your post and send a message. Don't worry that it says abuse. It can be used to communicate with staff about any matter concerning a post or thread. I only happened across your post - the report button means that it is sure to be seen by staff.

Good luck with your wireless problem.

---

### Post by fmmarzoa on 2011-11-17
Thanks coffecat. :-)

---

### Post by fmmarzoa on 2011-11-17
I managed to make work Ethernet device, thanks to APTonCD, but still no luck with Atheros AR9485WB-EG.

I've tried with ndiswrapper but it didn't work. I'm not sure the drivers are correct, since I've downloaded them from a non-authorized webpage, because I couldn't found official driver download page on Atheros official website.

I really need wifi to work, so... any hint on this?

Thanks a million in advance,

---

### Post by coffeecat on 2011-11-17
Which version of Ubuntu are you running? I only have experience of the Atheros 9285 and 928X chipsets which work OK for me. I wonder if the AR9485 chipset is a recent one.

---

### Post by fmmarzoa on 2011-11-17
10.04LTS

I've been navigating around, and have found ath9k driver. It's on my kernel, I try to modprobe it, it loads but no network devices are created.

Now, I think that I need to update my kernel a lot:

[http://wireless.kernel.org/en/users/Drivers/ath9k#Available_devices](http://wireless.kernel.org/en/users/Drivers/ath9k#Available_devices)

Since it is the latest one on that list, it seems like I need to build a 2.6.39 kernel (currently I'm runing 2.6.32-35).

So my next step is try to install that kernel version on my laptop.

Thanks

---

### Post by coffeecat on 2011-11-17
> **fmmarzoa said:**
> 10.04LTS

Yes, that would not have drivers for newer chipsets as default.

The ath9k driver that comes with the 10.04 kernel would be an old one. You are right to look at the kernel. Before you try compiling newer modules or whatever, I'd suggest downloading the 11.10 ISO and trying that live and see if that runs your wireless device. 11.10 comes with a more recent kernel, hence a more recent version of ath9k.

If you've been put off by negative publicity surrounding 11.10, don't be. :) There are always a lot of threads citing problems after every release. Many people are running 11.10 without significant issue (myself included) so it may very well run just fine on your hardware. Also - if you don't like the Unity desktop, don't worry about that at the moment. My suggestion to run 11.10 live is simply to test the wireless driver. If the wireless driver works OK and you don't want the Unity desktop, then there are alternatives.

---

### Post by fmmarzoa on 2011-11-17
Hi,

I've turned into conservative with the years, that's the cause I installed 10.04LTS instead of last cutting edge version. And now that I've yet running at least ethernet, I'm a bit afraid of change the whole system...

Well, anyway latest available kernel is linux-image-2.6.38-12-generic-p... I've no luck with nothing X-D

I'll see if I can install 2.6.39 on 10.04LTS in anny manner after lunch, and if it's not possible, take a look on 11.10.

Regards,

---

### Post by fmmarzoa on 2011-11-17
Hmmmm...

There's a 2.6.39 here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

Although it's not showed on aptitude...

I'll download deb pages and give it a try

---

### Post by praseodym on 2011-11-17
Hi,

please show the outputs of:

```
uname -a
lspci -nnk | grep -iA2 net
lsmod
ifconfig -a
iwconfig
cat /etc/network/interfaces
cat /etc/resolv.conf
rfkill list
```
You can c/p them into a text file and upload it. Do you still have the installation CD/DVD?

---

### Post by fmmarzoa on 2011-11-17
IT WORKS!!!

In that order, and it works like a charm. :-)

I've followed the instructions found here:

[http://www.ramoonus.nl/2011/05/linux-kernel-2-6-39-installation-guide-for-ubuntu-linux/](http://www.ramoonus.nl/2011/05/linux-kernel-2-6-39-installation-guide-for-ubuntu-linux/)

But changing those packages for these ones most recent:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39.4-oneiric/linux-headers-2.6.39-02063904_2.6.39-02063904.201108040905_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39.4-oneiric/linux-headers-2.6.39-02063904_2.6.39-02063904.201108040905_all.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39.4-oneiric/linux-headers-2.6.39-02063904-generic_2.6.39-02063904.201108040905_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39.4-oneiric/linux-headers-2.6.39-02063904-generic_2.6.39-02063904.201108040905_i386.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39.4-oneiric/linux-image-2.6.39-02063904-generic_2.6.39-02063904.201108040905_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39.4-oneiric/linux-image-2.6.39-02063904-generic_2.6.39-02063904.201108040905_i386.deb)

Thanks folks, :-)

---

### Post by praseodym on 2011-11-17
:popcorn:

In 10.04 LTS there is a backported kernel 2.6.38-12 (always the latest from 11.04) which can also (now with working connection) be installed via the metapackages:

```
sudo apt-get install linux-image-generic-lts-backport-natty linux-headers-generic-lts-backport-natty
```
This kernel will be automatically updated by this. But you would need to change the boot order with the package **startupmanager**, the mainline kernel (2.6.39) can still be used and left installed as comfort installation.

---

### Post by KvltBryce on 2012-01-05
Thank you so much for all of your help on this thread! Just the answer that I needed, and learned a lot doing it. I'm on 10.04LTS as well, as that is the distro that they want us to use at work.

---

