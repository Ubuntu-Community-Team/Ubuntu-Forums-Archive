---
title: "Lost wireless after update"
date: 2011-06-13
forum: Networking &amp; Wireless
---

### Post by Karen Vincent on 2011-06-13
Hi, after giving me no problems whatsoever (currently 10.04 Lucid Lynx) I lost wireless connectivity on my laptop after the following updates were processed yesterday:

Commit Log for Sun Jun 12 16:18:28 2011   

 Upgraded the following packages:  
 dkms (2.1.1.2-2fakesync1) to 2.1.1.2-2ubuntu1  
 flashplugin-installer (10.3.181.14ubuntu0.10.04.1) to 10.3.181.22ubuntu0.10.04.1  
 flashplugin-nonfree (10.3.181.14ubuntu0.10.04.1) to 10.3.181.22ubuntu0.10.04.1  
 initscripts (2.87dsf-4ubuntu17.3) to 2.87dsf-4ubuntu17.4  
 libimobiledevice0 (0.9.7-1ubuntu1) to 0.9.7-1ubuntu1.1  
 libldap-2.4-2 (2.4.21-0ubuntu5.4) to 2.4.21-0ubuntu5.5  
 libsvn1 (1.6.6dfsg-2ubuntu1.2) to 1.6.6dfsg-2ubuntu1.3  
 linux-generic (2.6.32.32.38) to 2.6.32.33.39  
 linux-headers-generic (2.6.32.32.38) to 2.6.32.33.39  
 linux-image-generic (2.6.32.32.38) to 2.6.32.33.39  
 linux-libc-dev (2.6.32-32.62) to 2.6.32-33.66  
 subversion (1.6.6dfsg-2ubuntu1.2) to 1.6.6dfsg-2ubuntu1.3  
 sysv-rc (2.87dsf-4ubuntu17.3) to 2.87dsf-4ubuntu17.4  
 sysvinit-utils (2.87dsf-4ubuntu17.3) to 2.87dsf-4ubuntu17.4  
 xserver-xorg-video-openchrome (1:0.2.904+svn827-1) to 1:0.2.904+svn827-1ubuntu0.1  
 

  Installed the following packages:
linux-headers-2.6.32-33 (2.6.32-33.66)  
     	 	 	 	pre.cjk { font-family: "DejaVu Sans",monospace; }p { margin-bottom: 0.21cm; }  
linux-headers-2.6.32-33-generic (2.6.32-33.66
linux-image-2.6.32-33-generic (2.6.32-33.66)


My wireless card hardware info from lshw is now:
*-network DISABLED
                 description: Wireless interface
                product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: wlan0
                version: 00
                serial: 00:1e:65:c7:cf:58
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
                resources: irq:31 memory:f5100000-f5101fff 
 
I know the 'DISABLED' part looks easy to solve BUT the 'Wireless Networks' option accessed from the network connections applet is greyed out giving no option to enable/disable. I run a Lenovo G550 laptop which has a 'hard switch' to enable/disable wireless (this is usually left on and would have been on when I restarted after the updates) and if I restart with this off then switch it on the Wireless Network status changes from 'Disconnected' to 'Device not ready'. Previously used wireless networks are still sitting in System> Network Connections with no apparent changes.

From reading other threads I have carried out the following today: 

Commit Log for Mon Jun 13 08:49:00 2011

Installed the following packages:
b43-fwcutter (1:012-1build1)

Reinstalled the following packages:
bcmwl-kernel-source (5.60.48.36+bdcom-0ubuntu3)
bcmwl-modaliases (5.60.48.36+bdcom-0ubuntu3)

AND

Commit Log for Mon Jun 13 10:16:33 2011

Installed the following packages:
broadcom-sta-common (5.10.91.9.3-3)
broadcom-sta-source (5.10.91.9.3-3)
cvs (1:1.12.13-12ubuntu1)
debhelper (7.4.15ubuntu1)
diffstat (1.47-1build1)
gettext (0.17-8ubuntu3)
html2text (1.3.2a-14build1)
intltool-debian (0.35.0+20060710.1)
libmail-sendmail-perl (0.79.16-1)
libsys-hostname-long-perl (1.4-2)
module-assistant (0.11.2ubuntu1)
po-debconf (1.0.16)
quilt (0.48-5)

but as it all worked fine before and this was just an update not an upgrade I suppose drivers etc are all OK anyway.

Also, rfkill showed nothing was blocked to need unblocking, and ifconfig gives a permissions error

I have a wired connection operating without any problems at all.

No luck so far on the wireless. Any other suggestions of what to try for a fix would be much appreciated. Please spell things out for me, I'm no geek but can follow instructions! :p

Thank you,

Karen

---

### Post by Sergio PC on 2011-06-13
Karen:
I had the same problem after update.
Update or downgrade to a new Kernel and you should be fine.
Here you have Ubuntu Kernels:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by Karen Vincent on 2011-06-13
Thank you! :KS

Only had to go back to the kernel before the update shown in Synaptic History and it worked instantly. I'll keep an eye on the forums for a while and avoid kernel updates for the time being; there are bug reports for the combination I use of Lenovo laptop with Linux for just this issue and at the moment the workarounds out there are far more complicated than your solution. Thanks again,

Karen :D

---

### Post by frisbee-gr on 2012-06-14
Hello,

Can one of you be a bit more precise on how you downgraded?

Did you uninstall the latest kernel via synaptics or you just used something like grub to choose a different kernel on boot?

Please elaborate a bit!

Thanks in advance,

Larry

---

### Post by Karen Vincent on 2012-06-15
I reversed the update using the Synaptic Package Manager by simply selecting and removing the package update (previous updates to the kernel were still showing as installed so I was confident I would be 'going back' not leaving a hole). I then ignored the Update Manager requests for the kernel for a while - I set it to autocollect the update options but do not autoinstall anything ever - and waited for a further update to be available. A couple of weeks later the next package number was on offer and I upgraded with that with no problems.

As a general rule when there are kernel updates I take a look at the issues being raised before installing - I know there are some areas where my system is not generic (graphics and wireless mainly) so avoid conflicts whenever possible. At the moment I am waiting for the '3 months later' version of the Ubuntu 12.04 LTS to be available to reduce the 'fiddling to get it all working' possibilities. I'm a cautious Linux user still on 10.04 LTS who has limited computer knowledge but I try!

Also, with kernel updates and upgrades is there a 'live cd' option to download and try before changing the system? It at least enables a check with basic functions before committing.

Hope this is helpful Larry,

Karen

---

### Post by kurt18947 on 2012-06-15
> **Karen Vincent said:**
> 
<snip>
Also, with kernel updates and upgrades is there a 'live cd' option to download and try before changing the system? It at least enables a check with basic functions before committing.

Hope this is helpful Larry,

Karen

As far as I know, all Ubuntu-esque .debs are 'live cd'.  If your machine supports booting from USB hard drives, you can create a 'live USB' which can be a bit quicker than CDs/DVDs.  Live USB drives can also support 'persistence'; you get the live install plus a variable size ext2 partition which can  remember settings.  CDs won't 'remember' anything between restarts.

I don't know how common my experience is but I tried updating a live USB install and apparently damaged it so haven't tried that recently.  A live USB may work for things like 3rd party drivers e.g. Broadcom and video drivers but I have experience with them.  Definitely recommended for machines with 'non-standard' hardware, though.

---

### Post by chili555 on 2012-06-15
> **Karen Vincent said:**
> I reversed the update using the Synaptic Package Manager by simply selecting and removing the package update (previous updates to the kernel were still showing as installed so I was confident I would be 'going back' not leaving a hole). I then ignored the Update Manager requests for the kernel for a while - I set it to autocollect the update options but do not autoinstall anything ever - and waited for a further update to be available. A couple of weeks later the next package number was on offer and I upgraded with that with no problems.

As a general rule when there are kernel updates I take a look at the issues being raised before installing - I know there are some areas where my system is not generic (graphics and wireless mainly) so avoid conflicts whenever possible. At the moment I am waiting for the '3 months later' version of the Ubuntu 12.04 LTS to be available to reduce the 'fiddling to get it all working' possibilities. I'm a cautious Linux user still on 10.04 LTS who has limited computer knowledge but I try!

Also, with kernel updates and upgrades is there a 'live cd' option to download and try before changing the system? It at least enables a check with basic functions before committing.

Hope this is helpful Larry,

KarenIf it's still not working, please post:```
lspci -nn | grep 0280
dmesg | grep iwl
rfkill list all
```If you indeed have this:> product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:04:00.0
logical name: wlan0Then these packages have nothing to help you as they are for Broadcom wireless chips and not Intel; you may as well remove them:> Installed the following packages:
b43-fwcutter (1:012-1build1)

Reinstalled the following packages:
bcmwl-kernel-source (5.60.48.36+bdcom-0ubuntu3)
bcmwl-modaliases (5.60.48.36+bdcom-0ubuntu3)

AND

Commit Log for Mon Jun 13 10:16:33 2011

Installed the following packages:
broadcom-sta-common (5.10.91.9.3-3)
broadcom-sta-source (5.10.91.9.3-3)They don't hurt anything, but they are just taking up space.

Thanks.

---

