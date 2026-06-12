---
title: "Help configuring-Marvell Yukon 88E8040T -Toshiba-Ubuntu 9.10"
date: 2009-11-08
forum: Networking &amp; Wireless
---

### Post by bipinkdas on 2009-11-08
Hi All,

My new Laptop is Toshiba **U400** with **Marvell Yukon 88E8040T** PCI-E Fast Ethernet Controller. I have installed Ubuntu9.10,successfully. But Ubuntu didn't detect this NIC. Can anybody help me to sort out the problem.

Thanks Advance
BipinDas.K

---

### Post by chili555 on 2009-11-08
Please try opening a terminal and do:```
sudo modprobe sky2
ifconfig
```Did a new interface get created, eth0, perhaps? We can make this permanent if it worked.

---

### Post by baggins on 2009-11-09
I have the same laptop (toshiba satelite pro u400).
Unfortunately the problem is a bit bigger than just the driver module just not getting loaded. This is the appropriate, and rather lengthy, launchpad bug [#418933]("https://bugs.launchpad.net/ubuntu/+bug/418933")

To summarize: 
It's a regression in the upstream kernel, a patch has been released, against the 2.6.32 git tree. 
Since karmic was released with a 2.6.31 kernel I guess that a 2.6.32 patch is unlikely to make it in to the regular ubuntu kernel update during the lifetime of Karmic Koala (I would love to be proven wrong here, but I'm not holding my breath :) )
I'm more hopefull that it might make it back as a backport update.

Alternate solutions are:
[LIST]
[*]**Add acpi=off** as a kernel parameter. Unfortunately it sounds as if you did a clean install, which means that you are using grub2, I don't know that yet so someone else will have to help you setting this parameter.
This solution has several drawbacks on a laptop, as it kills powermanagment, and changes several things like the power button behaviour, suspend functionality etc.
[*]**Run with an alternative kernel:** Andy Whitcroft the guy that is assigned to the bug, has released a patched kernel. This is a kernel build to test a specific bug fix, so it probably won't be updated later. You can find the link in the bug report.
[*]**Compile your own kernel:** This is big boys stuff :) Used to be a pretty common thing to do for us linux people, but it's been years since I had to do it. 
My best advice is start by reading [https://help.ubuntu.com/community/Kernel/Compile]("https://help.ubuntu.com/community/Kernel/Compile"), grap the patch from [http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=15b812f1d0a5ca8f5efe7f5882f468af10682ca8]("http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=15b812f1d0a5ca8f5efe7f5882f468af10682ca8") read up on how to patch kernel source (google). 
Then cross your fingers and plunge in to the deep end :D Actually it's a good way to learn more about how the "engine room" of your OS is made up.
[/LIST]

For now I am using the acpi=off method, it works for now, and as long as I remember that I'm running a slightly crippled system I'm fine.
Hoping for a karmic-backports kernel before soon though :)

-- Jon

----------------
[FONT="Arial Black"][SIZE="1"]Read more at:
[https://bugs.launchpad.net/ubuntu/+bug/418933]("https://bugs.launchpad.net/ubuntu/+bug/418933")
[http://bugzilla.kernel.org/show_bug.cgi?id=13940]("http://bugzilla.kernel.org/show_bug.cgi?id=13940")
[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=15b812f1d0a5ca8f5efe7f5882f468af10682ca8]("http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=15b812f1d0a5ca8f5efe7f5882f468af10682ca8")[/SIZE][/FONT]

---

### Post by Senryo on 2009-11-12
baggins,

Do you have any suggestions for a person who does not have any internet capabilities while in Ubuntu?  I'd like to try to get this card working, but my wireless card, Intel Wireless WiFi Link 5100, seems to have it's own problems as well.

Thanks

---

### Post by baggins on 2009-11-13
Did you try the acpi=off kernel parameter?

The bug affects both my network interfaces, wired as well as wireless. 
With acpi=off both works again. So if you have the same problem then the acpi solution ought to work for you as well.

When booting enter grub, select the newest kernel, press e, select the line containing the words "quiet splash" and add "acpi=off", press enter, press b and your machine ought to boot without powermanagment.

And on a brighter note, I was aparently a bit too pesimistic it from launchpad bug [#407824]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/407824") I gather that a fix will be released in a regular kernel update for karmic.
Offcourse net will still be required in order to update to that kernel, but that's where the acpi workarround comes in

-- Jon

---

### Post by chili555 on 2009-11-13
I noticed this in the bug report:> 

Hi,
Kernel from here [http://people.canonical.com/~apw/lp386468-karmic/](http://people.canonical.com/~apw/lp386468-karmic/) fixed this problem for me.

HW: Acer Extensa 5635G (wifi iwlang and ethernet atl1c)

Many thanks, Jiri
I think I would try the *acpi=off* workaround just long enough to download and install the fixed (we hope) kernel. ACPI does so many other things that we want and need that I don't think it's a long term solution.

---

### Post by baggins on 2009-11-16
> **chili555 said:**
> I noticed this in the bug report:I think I would try the *acpi=off* workaround just long enough to download and install the fixed (we hope) kernel.
Yes and no, what I am worried about is that:
1. That kernel is build to test a specific fix, I don't seem to see any info about whether it is otherwise build in the same way as the standard generic kernel (modules, includes etc.)
2. It appears that the fix is nominated for the next SRU, but if I install the deb containing the test/fixed kernel will I get the fixed mainstream kernel automatically?
3. I'm paranoid, ok? :D It just plainly goes against the grain, for me to install something as vital as the kernel from a 3' party. No offence intended to Andy Whitcroft, I really seriously doubt that he would ever provide a bad kernel. He is a member of the ubuntu kernel team, and kudos to him (and all the others) for doing a great job. 
However the fact remains that the kernel comes from an unofficial, unsigned (and therefore unverifiable) location. Yes! I really am that paranoid! ;) 
Had it been a test or lab machine I likely would have gone ahead and installed the fixed kernel, but on my own primary production machine I'm just a bit more careful. So I used the acpi=off fix to get the source, the patch and compiled my own kernel (It was actually a quite cool experience, it's been years since I last did that).

> **chili555 said:**
> ACPI does so many other things that we want and need that I don't think it's a long term solution.
Amen!! and especially on a laptop :)

-- Jon

---

### Post by chili555 on 2009-11-16
> I don't seem to see any info about whether it is otherwise build in the same way as the standard generic kernel (modules, includes etc.)I downloaded it and installed it and the headers and I am running it as we speak. It appears complete in all respects. I don't have the Marvell, so I can't comment on the fix.> will I get the fixed mainstream kernel automatically?I don't know for certain, but I'd assume the usual Update Manager process will continue unchanged.

The beauty of GRUB is that if this kernel doesn't work correctly, you can interrupt the boot process and boot into another later or earlier kernel. Once booted, you can remove the inoperative kernel easily in Synaptic.

Did the patch and kernel compile get your Marvell working?

---

### Post by baggins on 2009-11-19
> **chili555 said:**
> Did the patch and kernel compile get your Marvell working?
Yes, or at least I think so. 
The bug affected both the wireless (iwl5100) and the wired net (marvell). I haven't really tested the wired net yet, as that interface isn't registered in the dhcp at work. However I now see the interface when running ifconfig and I get a green light in the switch when I plug it in (neither was the case without the patch). The wireless on the other hand works like a charm (I'm posting this aren't I :) )

-- Jon

---

### Post by zekikou78 on 2009-11-25
> **chili555 said:**
> I noticed this in the bug report:I think I would try the *acpi=off* workaround just long enough to download and install the fixed (we hope) kernel. ACPI does so many other things that we want and need that I don't think it's a long term solution.

Hello !

I'am a beginner whith Ubuntu.
I have a dual boot whith XP and Karmic => NO ETH0 on Karmic... !
I saw that chili555 said :
> 
Kernel from here [http://people.canonical.com/~apw/lp386468-karmic/]("http://people.canonical.com/~apw/lp386468-karmic/") fixed this problem for me.


Could you help and explain me what I have to do to pach my Ubuntu and fix my network pb?

Thanks a lot!

---

### Post by nobeaner on 2010-01-14
I had the above problems with my wireless (Intel 5100) as well as the wired connection (MY 88E8040T) when I tried to install karmic a few months ago. PC wouldn't boot up into karmic with acpi disabled either. Got it to work by installing jaunty, which recognises the cards fine, and then upgrading to karmic. 32 bit and 64 bit both work. Still couldn't get a fresh karmic install to work from the files provided when you download the live cd though - it seems the problem in the kernel has been fixed, but the kernel provided in the download hasn't been updated, so you can't connect to the internet to download the fix yet! Works great now though :)

---

### Post by emmerc on 2010-08-25
Hi Friends,

I have a Toshiba Satellite P305-S8832 with the aforementioned Marvell Yukon 88E8040T. 

I have installed Ubuntu Linux 10.04 LTS and so far I have managed both the wired and wireless network to work flawlessly with the two flavors 32bits and 64bits.

When I tried the Ubuntu 10.04 live CD everything worked so I did the installation but once I did all the updating, the wired connection went undetected. When I tried the fixes I found in the network, I ended without wired and wireless connection.

I did a new fresh installation and I did all the updates with the exception of the kernel. I am using still the kernel 2.6.32.24.39 because when I updated it to the kernel 2.6.32.24.41 the mess happens.

So I suggest to install 10.04 (either 32 or 64 bits) but retain the kernel 2.6.32.24.39 until some other than 2.6.32.24.41 appears on the horizon. 

I'm writing this post on my Toshiba P305-S8832 connected through the wireless of my machine and the Marvell Yukon 88E8040T is there ready for any wire to come and the Intel Wireless 3945ABG is working just fine!.

Hope this might help you Friends!

---

### Post by mathia on 2010-09-16
Hi,
you do not need to patch the kernel.
Please install the following driver as follows:
[http://www.marvell.com/support.html](http://www.marvell.com/support.html)  -> "88E8040 Search" -> Kernel 2.6.x Linux Driver Install Package for Yukon Devices    Linux 2.6 - Fedora v10.85.9.3

 $ sudo bash ./install.sh

and let me know if it works.

have a lot of fun ...:razz:

---

### Post by mathia on 2010-09-17
Hi,

**[B]Installing Marvell Yukon 88E8040T driver on Toshiba-Ubuntu 9.10**:[/B]

Please install the following driver as follows:
[http://www.marvell.com/support.html](http://www.marvell.com/support.html)  -> "88E8040 Search" -> Kernel 2.6.x Linux Driver Install Package for Yukon Devices	Linux 2.6 - Fedora v10.85.9.3

 $ sudo bash ./install.sh

if it did not work, try to boot with options "noapic nolapic acpi=off" in grub and let me know if it works.

Have a lot of fun ...:razz:

---

### Post by MajinSaha on 2010-09-19
I have a similar problem, although my laptop is Toshiba Satellite M305D-S4829, and Ubuntu is 10.04 LTS.
I followed mathia's advice ( downloading and istalling the driver ), and the connection appeared. But when I turned my computer on next time, there's no connection again. Typing
```
modprobe sk98lin
```only gives "WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/".
After I moved my modprobe.conf file to modprobe.d catalog, the warning disappeared.
What exactly is going on and how can I reactivate my Ethernet card ?

---

### Post by mathia on 2010-09-19
> **MajinSaha said:**
> I have a similar problem, although my laptop is Toshiba Satellite M305D-S4829, and Ubuntu is 10.04 LTS.
I followed mathia's advice ( downloading and istalling the driver ), and the connection appeared. But when I turned my computer on next time, there's no connection again. Typing
```
modprobe sk98lin
```only gives "WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/".
After I moved my modprobe.conf file to modprobe.d catalog, the warning disappeared.
What exactly is going on and how can I reactivate my Ethernet card ?

Hi,
after reboot the sky2 driver has been loaded again. You should remove sky2 from initramfs and use sk98lin for your yukon device.

Please do as follows and let me know if it works:

sudo rmmod sky2
sudo rmmod sk98lin
sudo modprobe sk98lin
sudo echo "blacklist sky2" > /etc/modprobe.d/blacklist-sky2.conf 
sudo update-initramfs -u 
sudo reboot

---

