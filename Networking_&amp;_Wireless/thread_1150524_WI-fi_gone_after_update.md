---
title: "WI-fi gone after update"
date: 2009-05-06
forum: Networking &amp; Wireless
---

### Post by sleepyenglish on 2009-05-06
This morning i was notified of a update to jaunty, the update manager said to do a partial upgrade for one reason or another. I restarted but now i have no wi-fi, anyone know what could be causing this and how i can fix it?

Ubuntu Jaunty
Dell XPS M1530

Thanks

---

### Post by sleepyenglish on 2009-05-06
In synaptic package manager an item is stared for upgrade, the item is "linux-restricted-modules-2.6.28-12-generic" however i get the below error when trying to apply the update(im hard wired to the web). So i thought the problem might be kernel related so i booted using 2.6.28-11 via Grub and my wi-fi now works. I would still like to know why this happened so i can use the latest kernel.


> linux-restricted-modules-generic:
 Depends: linux-restricted-modules-2.6.28-12-generic  but it is not installable

---

### Post by ernstblaauw on 2009-05-06
On my computer (9.04 with all repo's enabled), the package linux-restricted-modules-2.6.28-12-generic cannot be installed. I did not test the kernel yet, so I don't know if there is a problem with my wireless. Hopefully, the package will be available soon.

---

### Post by timtucker on 2009-05-06
Same problem here on an HP Netbook.  Kinda frustrated about it.

---

### Post by opscure on 2009-05-06
Is your partial upgrade actually finishing?  There was a recent bug report about update-manager having a problem finding ./plugins and the apport module in python.

see: [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/366048](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/366048)

To fix:
```
sudo apt-get install update-manager
```

This should upgrade your update-manager to v. 1:0.111.9 and let you finish the install.  

I hope this is the case. Good luck.

---

### Post by timtucker on 2009-05-06
Update-manager is current, the linux-restricted-modules package is not installable.  Thanks for the attempt though.

---

### Post by ernstblaauw on 2009-05-06
> **opscure said:**
> Is your partial upgrade actually finishing?  There was a recent bug report about update-manager having a problem finding ./plugins and the apport module in python.

see: [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/366048](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/366048)

To fix:
```
sudo apt-get install update-manager
```

This should upgrade your update-manager to v. 1:0.111.9 and let you finish the install.  

I hope this is the case. Good luck.
Here, the partial upgrade did finish here, without installing anything.

```

>apt-cache policy update-manager
update-manager:
  Installed: 1:0.111.9
  Candidate: 1:0.111.9
  Version table:
 *** 1:0.111.9 0
        500 http://nl.archive.ubuntu.com jaunty-updates/main Packages
        100 /var/lib/dpkg/status
     1:0.111.7 0
        500 http://nl.archive.ubuntu.com jaunty/main Packages

```

However, I'm still missing the package linux-restricted-modules-2.6.28-12-generic.

---

### Post by MadAGu on 2009-05-06
same problem here... i haven't a wireless card so i don't know if there is any issue , but i also haven't the above package

---

### Post by ernstblaauw on 2009-05-06
Did anyone filled a bug report on Launchpad? Or found a bug report from someone else? I believe that's the correct way to notify the developers.

[edit]
On [https://launchpad.net/ubuntu/+source/linux-restricted-modules/2.6.28-12.16](https://launchpad.net/ubuntu/+source/linux-restricted-modules/2.6.28-12.16) and [https://launchpad.net/ubuntu/jaunty/+source/linux-restricted-modules](https://launchpad.net/ubuntu/jaunty/+source/linux-restricted-modules) it looks like the package is correctly build. However, on [http://packages.ubuntu.com/jaunty/linux-restricted-modules](http://packages.ubuntu.com/jaunty/linux-restricted-modules) the old version is still shown.

---

### Post by markusf21 on 2009-05-06
I have the same problem with wireless, using an older kernal works. I filed a bug for it. [https://bugs.launchpad.net/ubuntu/+bug/372711]("https://bugs.launchpad.net/ubuntu/+bug/372711")

---

### Post by timtucker on 2009-05-06
As far as I can tell the necessary package has been built for i386, but it does not come up in the repos yet.  Anyone know the status on this?

---

### Post by paranoid_humanoid on 2009-05-06
Same problem. On Dell Inspiron 1525.
Filed this bug report [https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/372876](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/372876) before I found this topic.

---

### Post by wrenchy on 2009-05-06
Same problem here on an HP DV6233se (AMD Turion proc. Broadcom wifi chipset). Selected previous kernel and all was ok again. I see a lot of other people are having this problem too.

---

### Post by paranoid_humanoid on 2009-05-06
[LIST]
[*]Disable jaunty-proposed
[*]sudo apt-get update
[*]Downgrade the package linux from synaptic to 2.6.28.11.5 (downgrade everything else that has the version number 2.6.28.11.6 while you're at it).
[*]Apply, then sudo update-grub from nearest terminal.
[*]From synaptic, remove linux-headers-2.6.28-12, linux-headers-2.6.28-12-generic, linux-image-2.6.28-12-generic and linux-restricted-modules-2.6.28-12-generic.
[*]sudo update-grub again.
[*]Restart.
[/LIST]

That's how I got my wireless back.

---

### Post by Quicksilver_Johny on 2009-05-06
Same problem here on a Dell D630. I updated this morning, and then my wifi was gone.
Wireless card:
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
linux-restricted-modules-generic was held back from updating because linux-restricted-modules-2.6.28-12-generic could not be found
```
qj@ip179-198:~$ sudo apt-get install linux-restricted-modules-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  linux-restricted-modules-generic: Depends: linux-restricted-modules-2.6.28-12-generic but it is not installable
E: Broken packages
qj@ip179-198:~$ sudo apt-get install linux-restricted-modules-2.6.28-12-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-restricted-modules-2.6.28-12-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-restricted-modules-2.6.28-12-generic has no installation candidate

```

---

### Post by nexx on 2009-05-06
Having the same problem after update to kernel 12
What troubles me is that the madwifi driver that I use for my atheros wifi card do not show when I boot with the new kernel but when I load the old kernel the madwifi driver is activated and work.

Is there a way to see the madwifi driver when I boot with the new kernel ?

---

### Post by wrenchy on 2009-05-07
During boot up,just select an older kernel. 2.6.28-11 I think for most...
Somehow this new kernel release buggered wireless for most people.


> **sleepyenglish said:**
> This morning i was notified of a update to jaunty, the update manager said to do a partial upgrade for one reason or another. I restarted but now i have no wi-fi, anyone know what could be causing this and how i can fix it?

Ubuntu Jaunty
Dell XPS M1530

Thanks

---

### Post by tomszyszko on 2009-05-07
It is even worse for me. That update completly broke the ath5k driver for BOTH kernels... I can't even get madwifi 2 work. Also after reverting computer is unstable, gonna upgrade and try and force an install of restricted-modules.

---

### Post by DarkN00b on 2009-05-07
Another confirmation here. The upgrade finished but my wireless is gone, Broadcom restricted driver did not install. Here's my hardware:

```
           *-network
                description: Wireless interface
                product: BCM4312 802.11b/g
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth1
                version: 01
                serial: xx:xx:xx:xx:xx:xx
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=5.10.79.10 ip=192.168.1.34 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
```

---

### Post by Tyson Edwards on 2009-05-07
Same issue over here, this time on 2 laptops.

Common thread is x86_64.

One is Atheros, one is Broadcom.

---

### Post by pastalavista on 2009-05-07
I had the same problem when I updated to the 2.6.28-12 kernel. Before, when running 28-11 I had the madwifi driver in my Hardware Drivers but it worked ok without it. It did, however, seem slightly faster with the madwif so I activated it. After the update, wireless didn't work and no madwifi or any other proprietary drivers showed in the H Drivers list. (ATI-fglrx-drivers still gone.. no 3D) So I rebooted with the 28-11 kernel and deactivated the madwifi. Then when I rebooted with 28-12, wifi worked perfectly. No 3D graphics but I don't need that anyway.

---

### Post by tomszyszko on 2009-05-07
> **pastalavista said:**
> I had the same problem when I updated to the 2.6.28-12 kernel. Before, when running 28-11 I had the madwifi driver in my Hardware Drivers but it worked ok without it. It did, however, seem slightly faster with the madwif so I activated it. After the update, wireless didn't work and no madwifi or any other proprietary drivers showed in the H Drivers list. (ATI-fglrx-drivers still gone.. no 3D) So I rebooted with the 28-11 kernel and deactivated the madwifi. Then when I rebooted with 28-12, wifi worked perfectly. No 3D graphics but I don't need that anyway.

I tried this, I tried compiling a driver I used in Intrepid, maybe all that is left is to compile compat-wireless which when I used in Intrepid did not work well - could not hold a steady signal. I really need this Wifi to work -- but it seems the old ath5k driver is now broken by the update trying to install MADWIFI

---

### Post by tomszyszko on 2009-05-07
> **tomszyszko said:**
> I tried this, I tried compiling a driver I used in Intrepid, maybe all that is left is to compile compat-wireless which when I used in Intrepid did not work well - could not hold a steady signal. I really need this Wifi to work -- but it seems the old ath5k driver is now broken by the update trying to install MADWIFI

I now have a feeling that the actual Wireless support in the new kernel is broken, as I have been able to get Madwifi to recognise the card and configure it, but when you scan there are no networks.:(

---

### Post by nexx on 2009-05-07
Thanks pastalavista !!! I booted with the 11 kernel, deactivated the proprietary wifi driver and then rebooted with the 12 kernel: the wifi is now working perfectly without proprietary drivers.

Fujitsu laptop with intels cpu and graphic card + atheros wifi driver

---

### Post by tomszyszko on 2009-05-07
> **tomszyszko said:**
> I now have a feeling that the actual Wireless support in the new kernel is broken, as I have been able to get Madwifi to recognise the card and configure it, but when you scan there are no networks.:(

FIXED!  After removing madwifi, I used a madwifi unload script to remove all traces of any previous wifi drivers -- booted back into .12 kernel, and opened terminal-- and typed 
```
$sudo modprobe ath5k
```
Wait 30 seconds and network manager will kick in saying your connected!!

---

### Post by netuntu on 2009-05-07
> **Tyson Edwards said:**
> Same issue over here, this time on 2 laptops.

Common thread is x86_64.

One is Atheros, one is Broadcom.
I have the same problem on Jaunty 2.6.28-12-generic and i had to reboot on 2.6.28-11-generic, on my Lenovo Thinkpad T61 :(

---

### Post by tbonedude on 2009-05-07
I have been having the same problem with my jaunty installation.  My solution, was to build the latest upstream kernel with kernelcheck.  Dead simple, and I just had to make sure I enabled the necessary items for nvidia and for my wireless (broadcom).  For me, its the best option until the devs release the restricted modules package for the 12 kernel.

---

### Post by michaeljking on 2009-05-08
I am in the same boat with my laptop, an HP 6720s,   having to boot from the earlier kernel.   Its most disturbing,   this is the sort of thing that leads new users back to windows....they what about all those Dell netbooks with pre-installed Ubuntu....are they immune...and all those the ubuntu derivitives?

---

### Post by oyvinst on 2009-05-08
> **michaeljking said:**
> I am in the same boat with my laptop, an HP 6720s,   having to boot from the earlier kernel.   Its most disturbing,   this is the sort of thing that leads new users back to windows....they what about all those Dell netbooks with pre-installed Ubuntu....are they immune...and all those the ubuntu derivitives?

The update that's causing this is currently in -proposed. You enable -proposed at your own peril, these packages are meant for testing. I guess most normal users wont enable them, so they avoid the problem and wont lose their wireless.

---

### Post by mflint on 2009-05-08
Hmm, similar problem here.

I installed some updates last night, started the machine this morning to find wireless isn't working. *But* the updates didn't change the kernel - my latest installed kernel is "2.6.28-11-generic".

But the timestamp for "/boot/initrd.img-2.6.28-11-generic" has changed, so that might have been updated :-/

On my box, Aptitude has no knowledge of this "-12" kernel that folks are talking about.

Odd...

---

### Post by michaeljking on 2009-05-08
> **oyvinst said:**
> The update that's causing this is currently in -proposed. You enable -proposed at your own peril, these packages are meant for testing. I guess most normal users wont enable them, so they avoid the problem and wont lose their wireless.


Thanks, I will make sure my main laptop has that one unchecked in future!

---

### Post by dBuster on 2009-05-08
> **tomszyszko said:**
> FIXED!  After removing madwifi, I used a madwifi unload script to remove all traces of any previous wifi drivers -- booted back into .12 kernel, and opened terminal-- and typed 
```
$sudo modprobe ath5k
```
Wait 30 seconds and network manager will kick in saying your connected!!

Upon updating the Kernel to .12 I too lost my wifi...  However, the above quoted line works like a charm!  After update I rebooted, waited about a minute or so to see if the wifi was truly down, and it was, then I popped open a terminal window and ran "sudo modprobe ath5k" and voila within about 20 seconds my wifi sprung to life.  

I recommend anyone having lost their wifi on this latest kernel to give it a try.  Especially if you were using the madwifi drivers before!  Since in effect, madwifi was using the ath5k driver.  I am going to go out on a limb and say that they have the ath5k worked out with the latest kernel and you do not need to use the madwifi any longer....

---

### Post by timtucker on 2009-05-08
Linux-restricted-modules is now available for the new kernel. My wireless is working again. :)

---

### Post by iragreene on 2009-05-08
timtucker,

how do I get the linux restricted driver of whcih you spoke?

---

### Post by tomszyszko on 2009-05-08
> **iragreene said:**
> timtucker,

how do I get the linux restricted driver of whcih you spoke?

Ok make sure that you have enabled all options in Software Sources as you need the proposed updates again (just in case you disabled it because of the Wifi problem)

Then just run update manager. The restricted modules should now not be shaded out

PS HAs anyone noticed that there is no update manager icon in the top bar anymore in jaunty - having to manually open update manager -- or maybe its just my setup :(

---

### Post by tomszyszko on 2009-05-08
WARNING -- new ath5k seems to be slightly unstable -- ie  speed really fluctuates and dropped out once 

-- going to reboot and try to clear up some attempted fixes from yesterday be4 filling bug report.

---

### Post by DarkN00b on 2009-05-08
> **iragreene said:**
> timtucker,

how do I get the linux restricted driver of whcih you spoke?

Open Synaptic and type "linux-restricted" (without the quotes) into the Quick search field. Mark linux-restricted-modules for installation. Let Synaptic mark the correct packages for your system. Now - look for any  packages that are marked with a green square with a little yellow star on it. Mark that package for re-installation. Apply and restart. This got me going with the restricted Broadcom drivers. I had to mark that last one manually though because it would not automatically reinstall.

---

### Post by tomszyszko on 2009-05-08
> **DarkN00b said:**
> Open Synaptic and type "linux-restricted" (without the quotes) into the Quick search field. Mark linux-restricted-modules for installation. Let Synaptic mark the correct packages for your system. Now - look for any  packages that are marked with a green square with a little yellow star on it. Mark that package for re-installation. Apply and restart. This got me going with the restricted Broadcom drivers. I had to mark that last one manually though because it would not automatically reinstall.

TBO it is easier just to let update-manager handle it -- it will reinstall the other two restricted packages:

> **tomszyszko said:**
> Ok make sure that you have enabled all options in Software Sources as you need the proposed updates again (just in case you disabled it because of the Wifi problem)

Then just run update manager. The restricted modules should now not be shaded out

PS HAs anyone noticed that there is no update manager icon in the top bar anymore in jaunty - having to manually open update manager -- or maybe its just my setup :(

---

### Post by waspbr on 2009-05-08
I like living dangerously, -proposed packages make the experience a lot more exciting. Sure I have lost the wireless on my hp laptop, but all I had to do was to restart and boot from the previous kernel.  no biggie

---

### Post by benon on 2009-05-09
My partial update also ends ubruptly after a few seconds. What's worse i can't install the new version beccause i have a dpkg error! This is getting frustrating. Wish u guys luck.

---

### Post by ernstblaauw on 2009-05-10
I read somewhere (this thread?) update-manager has a bug concerning the partial update. What you can do:
- open a terminal (Applications > Accessoires > Terminal)
- type 'sudo aptitude update'
- type 'sudo aptitude safe-upgrade'

Now, all packages should upgrade.

---

### Post by dBuster on 2009-05-10
> **tomszyszko said:**
> PS HAs anyone noticed that there is no update manager icon in the top bar anymore in jaunty - having to manually open update manager -- or maybe its just my setup :(

In Jaunty it was setup, from what I have learned during testing, to not display that tray icon when running.  Instead it opens the update program and runs on a pre-determined schedule per your selection.  ie how many days between updates.

There was a solution for those like myself who wanted the tray icon back.  

You can either do the following:
```
gconftool -s --type bool /apps/update-notifier/auto_launch false
```

Or follow these steps...

1.  Applications -> System Tools -> Configuration Editor
2.  Expand APPS then scroll to locate "update-notifier"
3.  Remove the check mark for "auto_launch"

It works just as it did in prior releases after doing this.  I would also change the number of days between checking to what ever number of days you desire your system to check for updates.  Personally I have mine set to 1 day.  So I check daily for updates...  

Check out this link for more info ["Update Notification icon in panel tray"]("http://ubuntuforums.org/showthread.php?t=1122292&highlight=notification+icon+tray&page=1")

---

### Post by vinhtantran on 2009-05-12
> **ernstblaauw said:**
> I read somewhere (this thread?) update-manager has a bug concerning the partial update. What you can do:
- open a terminal (Applications > Accessoires > Terminal)
- type 'sudo aptitude update'
- type 'sudo aptitude safe-upgrade'

Now, all packages should upgrade.

The restricted module has been added to the repo. All you have to do is waiting for your mirror update it and then check the update again.

---

### Post by deankovell on 2009-07-05
> **michaeljking said:**
> I am in the same boat with my laptop, an HP 6720s,   having to boot from the earlier kernel.   Its most disturbing,   this is the sort of thing that leads new users back to windows....they what about all those Dell netbooks with pre-installed Ubuntu....are they immune...and all those the ubuntu derivitives?

I'm one of those new users, like a week or so new, and helpful people like yourselves are gonna keep me around for a while. Thanks.

---

