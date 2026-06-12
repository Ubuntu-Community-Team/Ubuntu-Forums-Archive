---
title: "Security upgrades killed connectivity"
date: 2009-01-28
forum: Networking &amp; Wireless
---

### Post by reisingerw on 2009-01-28
I'm a new user of Ubuntu (v. 8.10) on an Eee PC laptop.  I just did this morning's updates of 44 files.  Now I've lost my wireless connection and hence my internet.  I've right clicked on the network icon in the upper right of the panel, and Enable Networking is checked.  When I selected Edit Connections and then edited the wireless connection, it shows Connect Automatically as checked. I restarted and rebooted several times without the connection being established automatically as it did until the upgrades. 

Suggestions welcome.

---

### Post by Racer-X on 2009-01-28
Here, too.

I restarted using kernel 2.6.27-9 instead of the newly installed kernel 2.6.27-11.

I have an atheros card and it was a bear getting things stable when I first installed, but for the last couple of months it's been stable.

Any word on blacklisting / not blacklisting ath5k?  What about cfg80211 and mac80211 w/ ath9k?  Seems like there's been a change between the kernel versions.

Can anyone reply to this thread to explain?

Thanks!

---

### Post by Mrandoman on 2009-01-28
I've also got this problem. I had ath5k working with my atheros card before the kernel was updated. It was deleted from my /etc/modules list and putting it back in didn't work.

---

### Post by ch33zy on 2009-01-28
If, like me, you had to build the compat-wireless package from source, you probably have rebuild after the kernel upgrade.

From compat-wireless source dir:

make clean
sudo make unload
sudo make install
sudo make load

You might have to reboot before it starts working.

---

### Post by UphillSkier on 2009-01-28
Help! I have the same problem, but with a wired ethernet connection under Ubuntu 8.04 and kernel 2.6.24-23

I applied todays updates and lost connectivity. My windows laptop works but not the linux system. Everything worked fine before the install.  As far as I can tell these are the packages upgraded ( output from
cat /var/log/dpkg.log | grep 2009-01-28 | grep upgrade

2009-01-28 08:45:19 upgrade libldap-2.4-2 2.4.9-0ubuntu0.8.04.1 2.4.9-0ubuntu0.8.04.2
2009-01-28 08:45:19 upgrade acpid 1.0.4-5ubuntu9 1.0.4-5ubuntu9.1
2009-01-28 08:45:20 upgrade ess 5.3.10-1hardy0 5.3.11-1hardy0
2009-01-28 08:45:22 upgrade evolution-data-server 2.22.3-0ubuntu2 2.22.3-0ubuntu3
2009-01-28 08:45:22 upgrade evolution-data-server-common 2.22.3-0ubuntu2 2.22.3-0ubuntu3
2009-01-28 08:45:23 upgrade libedataserver1.2-9 2.22.3-0ubuntu2 2.22.3-0ubuntu3
2009-01-28 08:45:23 upgrade libcamel1.2-11 2.22.3-0ubuntu2 2.22.3-0ubuntu3
2009-01-28 08:45:23 upgrade libebook1.2-9 2.22.3-0ubuntu2 2.22.3-0ubuntu3
2009-01-28 08:45:23 upgrade libecal1.2-7 2.22.3-0ubuntu2 2.22.3-0ubuntu3
2009-01-28 08:45:24 upgrade libedata-book1.2-2 2.22.3-0ubuntu2 2.22.3-0ubuntu3
2009-01-28 08:45:24 upgrade libedata-cal1.2-6 2.22.3-0ubuntu2 2.22.3-0ubuntu3
2009-01-28 08:45:24 upgrade libegroupwise1.2-13 2.22.3-0ubuntu2 2.22.3-0ubuntu3
2009-01-28 08:45:24 upgrade libgdata1.2-1 2.22.3-0ubuntu2 2.22.3-0ubuntu3
2009-01-28 08:45:24 upgrade libgdata-google1.2-1 2.22.3-0ubuntu2 2.22.3-0ubuntu3
2009-01-28 08:45:25 upgrade libedataserverui1.2-8 2.22.3-0ubuntu2 2.22.3-0ubuntu3
2009-01-28 08:45:25 upgrade libexchange-storage1.2-3 2.22.3-0ubuntu2 2.22.3-0ubuntu3

I really need to get connectivity back. Any suggestions?

[edit] On further investigation this doesn't seem to be a software problem. The 8.10 live cd finds a wired  network connection on my laptop but not on the desktop.  So the upgrade seems not to be the problem. It could be the network card, I suppose.  There are two: an integrated ethernet connection on the mother board and another on a dlink wireless connection card I stuck in there a while back.  Can anyone point me to the right diagnostic  tests to run or suggest a fix?  Would a new network board help?  This is an old machine and Idon't want to spend too much on it.

Thanks

---

### Post by Racer-X on 2009-01-28
Ok, so here's where I'm a little fuzzy bear:

In /lib/modules I have my three kernels' modules directories, 2.6.27-7, -9, and -11.

In 2.6.27-7-generic and 2.6.27-9-generic I have a /net directory immediately under the kernel's main directory, so: /lib/modules/2.6.27-7-generic/net, for example, and in those directories are my atheros and wlan drivers.  This holds true for both 2.6.27-7-generic and 2.6.27-9-generic.

This directory does not exist in 2.6.27-11-generic.

Is the new kernel missing atheros modules altogether?


...btw, too, I did not to a source install of compat-wireless.

---

### Post by jadoti on 2009-01-28
Thanks for replying to my other thread, Racer-X.

I tried booting back to the previous kernel (-9) and it's still no go for me.  My external usb adapter works fine, but the internal one still will not work for some reason.

[edit] Guess I lied, after unplugging the usb adaptor I still have connectivity, so I'm guessing the internal is working.  I'll go reboot and see what happens.

[edit2] - After another reboot, my wireless networking came back up, no problem. (using the -9 kernel).

So when/how will we know when this issue has been fixed/patched?

---

### Post by Brian Vaughan on 2009-01-28
I found that wireless networking was not working under 2.6.27-11, but still works fine under 2.6.27-9. (That's how I'm reading this forum right now.)

Specifically, NetworkManager works, it tries to log on to the usual wireless networks, and fails. It seems to fail some time after the upper dot goes green, when the mouseover says, "Acquiring network address from [network]."

---

### Post by qewrtyuiop on 2009-01-28
I have a similar issue.  After I restarted following the patch, I lost all networking completely until I reverted back to -9.  At first I thought this was an Atheros-specific issue but it it appears to be broader than that.  Didn't anyone test this first?!

---

### Post by JDaWg0415 on 2009-01-28
I had the same issue, i have Ubuntu 8.10 installed on a Acer one series netbook with an atheros wireless card. I am a new user to Ubuntu but i removed the following software package for the system and my connection continued to work. 

Go to System-->Administration-->Synaptic Package Manager, search for the following package "linux-restricted-modules-2.6.27-11-generic(2.6.27-11.16)" right click on the package and click "Mark for Removal" after removal restart the system and you should be able to connect to your wireless network.

**I am no expert on Ubuntu but this worked for so I thought I would share, i can't guarantee how long this will work but at least you can connect to your wireless until an official fix comes out**

Good luck

---

### Post by mylo9000 on 2009-01-29
i tried removing the linux-restricted... but it made no difference.

i'm using a D-Link DWL-G132 USB Wifi adapter via ndiswrapper and the most current windows driver for it.

I can see the networks in my area (mine included) but i cannot connect to any of them. i dropped network manager a while ago for wicd and it just doesn't connect. it buggs me if i remove the use encryption option but even when trying to connect to my home wifi it just doesn't connect.

i have a EEEpc 701 that is running intrepid and can connect. (which is how i'm posting this message.)

i know it has to be something that changed with the latest updates because, on my main system i can dual boot into windows xp and it can connect no problem with the same device.

I've tried booting back into the 2.6.27-9 kernel and it makes no difference. still can't connect.

any other ideas out there?
i need to get this system in some way connected so when an official update comes out that fixes the issue, i can acquire it.

---

### Post by dg_102 on 2009-01-29
Hi,

I have done the upgrade from 2.6.27-9 to 2.6.27-11 and the wireless connection is gone. Looking in restricted drivers the Broadcom STA Wireless is gone. If I reboot in 2.6.27-9, everything is fine and dandy as it was before the upgrade. 

Any quick solution to fix this?

Thanks,

dg

---

### Post by Mimfort on 2009-01-29
I'm chiming in with this as well.  I was running just fine 'out of the box' prior to this morning's update.  Now I get no wireless connectivity at all.

        Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
        Subsystem: Hewlett-Packard Company Device 137a
        Flags: fast devsel, IRQ 16
        Memory at f2000000 (64-bit, non-prefetchable) [disabled] [size=64K]
        Kernel modules: ath_pci

Is there a quick way to roll this back?  I'm uncertain as to which package I need to be looking at.

I'm astonished that the package manager doesn't have rollback functionality.  I understand that the software is free, but I would have assumed that rollback functionality would have been integral to the whole 'Ubuntu Way'.  I hope that I'm just missing it.

---

### Post by Racer-X on 2009-01-29
JDaWg0415, I don't have linux restricted modules installed.  I used to awhile back while trying to resolve Atheros issues, but it didn't work so I uninstalled (that was months ago).

I notice that there are more updates out this morning (1/29/2009), some of which include updates for linux headers & image for 2.6.27-11.  In looking at the description I'm not seeing anything about "fixing wireless network connectivity issues".  I suppose I might as well give it a go; I can keep booting into 2.6.27-9 to get connectivity.

As for the previous posting immediate to this one, you can get an install history easily in Synaptic Package Manager.  Open it (System -> Administration -> Synaptic Package Manager), then click on 'File -> History'.  You'll get what you installed by date.  For yesterday's (1-28-2009) updates, the apparent offending updates are located at the bottom, where it details Installed Packages linux-*-2.6.27-11 (2.6.27-11.25).  Hope this helps w/ your question.

I noticed that most of us are "First Cup of Ubuntu" posters, does anyone have any idea of how we can this communicated to developers upstream? (In case they're not noticing this thread or connectivity issues)

---

### Post by amadeus266 on 2009-01-29
It figures that this would happen TODAY. The day I decide to put Ubuntu on my work laptop that I need to be able to use networking with. I hope they fix it soon.

---

### Post by Racer-X on 2009-01-29
Remember:  You can boot into your previous kernel that worked (e.g. 2.6.27-9), assuming you've got that installed.

In the meantime, I just installed the backports package for 2.6.27-11-generic, going to reboot to see if that fixes anything....

---

### Post by tseckler on 2009-01-29
Same thing happened to me last night. I have a ralink rt2760 card.
I corrected the problem by modprobeing my card driver.

---

### Post by Racer-X on 2009-01-29
Right.  So I've got things working in 2.6.27-11, at least for Atheros 242/5xxx series wireles...

I'm not sure if it was this morning's (1/29/2009) updates that did it, or if it was adding the backports package (as I mentioned I did in a previous post).

Regardless, I noticed after my last reboot that in the /lib/modules/2.6.27-11-generic directory there existed an 'updates' subdirectory.  In that subdirectory was ath5k.ko.  I was trying to modprobe ath5k yesterday, but the driver didn't exist.  It seems that the update has now included the driver, or maybe the next set of updates did.

Note: at time of boot, I had this module blacklisted in /etc/modprobe.d/blacklist (and/or blacklist-local), so make sure you've got this commented out (in your blacklist file, make sure youve got a '#' in front of it, or just remove the blacklist altogether)

To load the driver, I modprobe'd it:

me@mysystem:/home/me$ sudo modprobe ath5k

...at that point wireless came back up again.

To make sure ath5k (or whatever you need for your wireless, etc.) is being loaded at boot, make sure you have that module listed in /etc/modules (just put the module name, in this instance 'ath5k', in that file).  You'll need sudo to edit, so: sudo nano /etc/modules

Hope this helps.

My next question is:  Was it backports or this morning's (1/29/2009) updates of the kernel?  Can anyone confirm that they have the updates subdirectory under /lib/modules/2.6.27-11-generic after only doing this morning's updates?

My next next question is:  Is this helping for other people that don't have Atheros cards?

---

### Post by zika on 2009-01-29
it seems that this was an dkms issue. in yesterday's kernel it was unsupported (in a way).

---

### Post by tpauth on 2009-01-29
> **Racer-X said:**
> Remember:  You can boot into your previous kernel that worked (e.g. 2.6.27-9), assuming you've got that installed.


How do you boot into the previous kernel?

---

### Post by Brian Vaughan on 2009-01-29
After today's updates, under 2.6.27-11, my wireless card is no longer recognized. Under 2.6.27-9, everything is still fine.

Shortly after your computer boots up, you should see a menu for a few seconds -- the GRUB loader. You can choose between different versions of the kernel. Most likely, 2.6.27-9 will be the third one from the top.

---

### Post by Bylund951 on 2009-01-29
So Ive had the same problem as you all of losing connectivity after the updates, and I have only tried this,

"Go to System-->Administration-->Synaptic Package Manager, search for the following package "linux-restricted-modules-2.6.27-11-generic(2.6.27-11.16)" right click on the package and click "Mark for Removal" after removal restart the system and you should be able to connect to your wireless network."

Which did not work for me, I tried reverting to a previous Kernel, However, upon start up Im never given the opprotunity to do this. 

Im new to Ubuntu running 8.04 on a Toshiba Satellite...
Any help would be greatly appreciated, right now Im running off a hardwire connection.

---

### Post by Piraja on 2009-01-30
> **tpauth said:**
> How do you boot into the previous kernel?

> **Brian Vaughan said:**
> Shortly after your computer boots up, you should see a menu for a few seconds -- the GRUB loader. You can choose between different versions of the kernel. Most likely, 2.6.27-9 will be the third one from the top.
In some cases you might have to press the ESC button during the couple of seconds after the POST phase in order to see the GRUB menu.

---

### Post by Brian Vaughan on 2009-01-31
I seem to have fixed my problem, at least.

There were two major problems, from what I can tell. The original problem, which I first encountered right after the initial upgrade to 2.6.27-11, was that Network Manager would indicate it was trying to connect to my usual wireless networks, but would fail after the point when it tried to obtain an IP address. This problem was solved when I followed the instructions for wireless troubleshooting in yelp, which were edit a file to disable IPv6.

[INDENT]gedit /etc/modprobe.d/aliasesdprobe.d/aliases[/INDENT]

then find the line

[INDENT]alias net-pf-10 ipv6[/INDENT]

and change it to

[INDENT]alias net-pf-10 off[/INDENT]

then reboot. After that, my wireless connects, as normal.

The second problem, which showed up after one of the succeeding patches in the last couple of days, and which I had to fix before I could fix the first problem, was that my wireless driver disappeared. (Only when running 2.6.27-11 -- everything was fine under 2.6.27-9.) I use the Broadcom STA restricted driver, and it shows up as the wl module. I'm less sure which of the things I tried to fix it actually did it, so I wouldn't recommend following what I did without checking things first. I'm mostly posting this part for the sake of experts who can figure out more clearly how to describe what the problem is and how to fix it.

I think the key things were that somehow, the ndiswrapper module was loaded, and displacing the wl module, and that somehow, the wl module was no longer in modprobe's database. So, I unloaded the ndiswrapper module using

[INDENT]sudo modprobe -r b43 b44 ssb ndiswrapper[/INDENT]

and rebuilt the database for modprobe using

[INDENT]sudo depmod[/INDENT]

then reloaded the modules for my wireless card using

[INDENT]sudo modprobe wl
sudo modprobe b44[/INDENT]

---

### Post by zika on 2009-01-31
> **Brian Vaughan said:**
> This problem was solved when I followed the instructions for wireless troubleshooting in yelp, which were edit a file to disable IPv6.
[INDENT]gedit /etc/modprobe.d/aliasesdprobe.d/aliases[/INDENT]then find the line
[INDENT]alias net-pf-10 ipv6[/INDENT]and change it to
[INDENT]alias net-pf-10 off[/INDENT]then reboot.
while You're at it, to complete that issue, You might also edit **/etc/modprobe.d/blacklist** and add line *blacklist ipv6*. that is the other side of the same coin that goes with what You've done.
in FireFox (if You use it) in **about:config** turn on *network.dns.disable.IPv6*.

---

### Post by Piraja on 2009-01-31
Hmm... Below you can see screenshots from kernel 2.6.27-9 (left) and kernel 2.6.27-11 (right). As you can see, it's the proprietary Broadcom STA wl driver that is missing in the 2.6.27.11 shot.

At the moment I guess I'm too lazy to try and fix this manually, so I'll simply just keep booting the old kernel for a while.

Actually there was an interesting detail in this update, because the GrUB menu was not automatically updated (no *.11 item in menu.lst), so I tried adding it manually. Could it be that the update process had such a smart feature that a system with this specific proprietary driver would automatically disregard the new kernel and boot the old *.9 kernel instead?

Just a wild guess.

---

### Post by bayvista on 2009-01-31
I have the same problem with 8.10 on a desktop. I followed your advice and removed 2.6.27.11 in Synaptic, and installed 2.6.27.9 which seems to work OK. However, how do I fix GRUB, which still shows 2.6.27.11?

---

### Post by Brian Vaughan on 2009-02-01
> **Piraja said:**
> Hmm... Below you can see screenshots from kernel 2.6.27-9 (left) and kernel 2.6.27-11 (right). As you can see, it's the proprietary Broadcom STA wl driver that is missing in the 2.6.27.11 shot.

That's the problem I ran into, that I fixed by mucking about with modprobe. Once I did, the Broadcom STA driver showed up in Hardware Drivers, already activated.

---

### Post by ItsManaged on 2009-02-01
Going back to 2.6.27.9 kernel fixed wireless. Thanks for the hint.
Funny thing with my Aspire One - both wireless and LAN were killed. Luckily I have an HSPA modem too! 

An easy way to choose another kernel to boot by default is to run (install if not already installed) StartUp-Manager. You can set the default kernel in that.

I have an Aspire One, these use an atheros chipset, and with Intrepid at least it does not work out of the box - There are two methods described in the AspireOne ubuntu forum [**here**]("https://help.ubuntu.com/community/AspireOne110L"). Whichever method one chooses it most likely will need to be re-applied after a kernel upgrade.

I'll be doing that soon with the new kernel 2.6.27.11 - I will let you know.

**OK - done and working!**
I used the "ath5k method" in the above link. Basically, install new driver
sudo aptitude install linux-backports-modules-intrepid
Then select the new driver using "Hardware Drivers" and deslect any previous hardware drivers that are activated - reboot and all is well!

---

### Post by onthenarrowpath on 2009-02-02
Thanks a lot, ItsManaged, for the key link to the community-page of the aao ([https://help.ubuntu.com/community/AspireOne110L](https://help.ubuntu.com/community/AspireOne110L)).

Being new with ubuntu, I was just happy to get that wlan working (with madwifi), but overread what it tells about the procedure necessary after every kernel update. I'll cite it here for all AAO and madwifi-users:

"Every time there is a kernel update you will need to perform the following steps to make the wireless work. Go to the directory (madwifi-hal-0.10.5.6-r3835-20080801) and run:

make clean
make
sudo make install"
(from: [https://help.ubuntu.com/community/AspireOne110L](https://help.ubuntu.com/community/AspireOne110L))

The great thing: You can perform it easily without internet connection (which you'll lack, since that driver broke down).

Thanks again, ItsManaged!

---

### Post by rogmorri on 2009-02-02
Just to echo what two previous posters said, I also lost _wired_ connectivity on my Acer One with 2.6.27-11.   (Though wireless is okay, for me.)

---

### Post by Piraja on 2009-02-07
> **Brian Vaughan said:**
> disable IPv6.[...] unloaded the ndiswrapper module [...] rebuilt the database for modprobe [...] reloaded the modules for my wireless card

> **zika said:**
> while You're at it, to complete that issue, You might also edit **/etc/modprobe.d/blacklist** and add line *blacklist ipv6*. that is the other side of the same coin that goes with what You've done.
in FireFox (if You use it) in **about:config** turn on *network.dns.disable.IPv6*.
Thank you for these; Brian's instructions worked. I also followed Zika's instructions, except for the Firefox part.  I'm not sure how to access "**about:config** [in order to] turn on *network.dns.disable.IPv6*". Where is the appropriate file located?

---

### Post by zika on 2009-02-07
just enter about:config in Your firefox address bar. in serach bar of the page You get enter "ipv6" and by clicking on one and only found option You will change its value.

---

### Post by Piraja on 2009-02-07
> **zika said:**
> just enter about:config in Your firefox address bar. in serach bar of the page You get enter "ipv6" and by clicking on one and only found option You will change its value.
Thanks! One less item of ignorance in my list...

---

