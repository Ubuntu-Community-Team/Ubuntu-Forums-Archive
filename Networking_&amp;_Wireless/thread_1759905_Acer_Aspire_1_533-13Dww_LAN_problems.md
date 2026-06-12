---
title: "Acer Aspire 1 533-13Dww LAN problems"
date: 2011-05-16
forum: Networking &amp; Wireless
---

### Post by Happibun on 2011-05-16
Hi,

I've just installed Ubuntu 10.4 as a dual boot on my Acer Aspire 0ne 533. I have to keep the Windows partition for work, or I'd have just installed Ubuntu. I'm used to plugging in an ethernet cable for the first round of updates until I get the WiFi working, but it just isn't working for me this time. I have a horrid feeling that Windows has a way of hogging the Ethernet card.

I had a look in the forums, and could not find anything referring to this specifically, which is unusual because as far as I can tell the AA1 is a popular machine and lots of people dual boot it. Perhaps it is an easy fix that's been buried in the archives?

I ran a few queries:
> jo@Iota:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:76 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5840 (5.8 KB)  TX bytes:5840 (5.8 KB)

jo@Iota:~$ /etc/network/interfaces
bash: /etc/network/interfaces: Permission deniedIs this any use?

Please help. 

Thanks, Jo

---

### Post by chili555 on 2011-05-16
Let's see what kind of wireless card you have. Please run and post:```
lspci -nn
rfkill list all
```

---

### Post by Happibun on 2011-05-16
Hi [chili555]("http://ubuntuforums.org/member.php?u=35909"),

Thank you for replying. I really appreciate it.

> jo@Iota:~$ lspci

01:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
02:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)> rfkill list allReturns nothing but the prompt.

Thanks, Jo

FYI - Full lspci -nn info:-
> Full :~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation N10 Family DMI Bridge [8086:a010]
00:02.0 VGA compatible controller [0300]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a011]
00:02.1 Display controller [0380]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a012]
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation NM10 Family LPC Controller [8086:27bc] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation N10/ICH7 Family SATA AHCI Controller [8086:27c1] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
01:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1)
02:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4727] (rev 01)

---

### Post by chili555 on 2011-05-16
Not lspci, but lspci -nn, please.

---

### Post by Happibun on 2011-05-16
Ah, it seems that we were thinking along the same lines, I edited the post above to include the lspci -nn output. It took some time to track down my USB stick to transfer the output on, so I posted the ethernet and network stuff first.

Thank you, Jo

---

### Post by chili555 on 2011-05-16
>  Network controller [0280]: Broadcom Corporation Device [[COLOR="Red"]14e4:4727[/COLOR]] (rev 01) Please do:```
sudo apt-get install bcmwl-kernel-source
```After it's done, detach the ethernet cable and reboot. You should be all set!

---

### Post by Happibun on 2011-05-16
Hi,

Unfortunately the stricken laptop has no Internet connection at all, and if I'm guessing right, it seems that the fresh un-updated install of 10.4 does not have the right file. 

> jo@Iota:~$ sudo apt-get install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package bcmwl-kernel-sourceI'm using a different machine to post to the forum, so I think I need to find another way?

So sorry if I am being thick here.

Cheers, Jo

---

### Post by chili555 on 2011-05-16
You're not being thick at all. apt-get requires internet connectivity.

You could download the package here. Be sure to get the version (Maverick, Natty, etc.) and architecture (32- or 64-bit) to match your installation.

[http://packages.ubuntu.com/search?keywords=bcmwl&suite=default&section=all&arch=any&searchon=names](http://packages.ubuntu.com/search?keywords=bcmwl&suite=default&section=all&arch=any&searchon=names)

You'll also need dkms.  [http://packages.ubuntu.com/maverick/dkms](http://packages.ubuntu.com/maverick/dkms)

Again, be sure to get the version (Maverick, Natty, etc.) and architecture (32- or 64-bit) to match your installation.

Transfer them on a USB key and install the .debs with:```
sudo dpkg -i bcmwl*.deb dkms*.deb
```If the install fails for other dependencies, go grab those, too.

---

### Post by Happibun on 2011-05-16
Thank you chili555,

you are being very kind and patient. We sort of got there, the installs started up ok and then threw out a load of licence errors. Is there something else I need or have missed? I could not see anywhere to input keys or checksum stuff. Also, I know the laptop has a dual core processor, but I've deliberately installed a 32 bit version of Ubuntu on it because I'm still using a lot of 32 bit stuff. So I went for the lucid 32 bit version. 

So here's the output:

> jo@Iota:~$ sudo dpkg -i bcmwl*.deb dkms*.deb
Selecting previously deselected package bcmwl-kernel-source.
(Reading database ... 122910 files and directories currently installed.)
Unpacking bcmwl-kernel-source (from bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb) ...
Selecting previously deselected package dkms.
Unpacking dkms (from dkms_2.1.1.2-3ubuntu1_all.deb) ...
Setting up dkms (2.1.1.2-3ubuntu1) ...

Processing triggers for man-db ...
Setting up bcmwl-kernel-source (5.60.48.36+bdcom-0ubuntu3) ...
Loading new bcmwl-5.60.48.36+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 2.6.32-24-generic
Building for architecture i686
Building initial module for 2.6.32-24-generic
/usr/sbin/dkms: line 35: patch: command not found

Error! Application of patch 0001-MODULE_LICENSE.patch failed.
Check /var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/ for more information.
Traceback (most recent call last):
  File "/usr/share/apport/package-hooks/dkms.py", line 47, in <module>
    report['SourcePackage'] = apport.packaging.get_source(package)
  File "/usr/lib/python2.6/dist-packages/apport/packaging_impl.py", line 106, in get_source
    if self._apt_pkg(package).installed:
  File "/usr/lib/python2.6/dist-packages/apport/packaging_impl.py", line 66, in _apt_pkg
    raise ValueError, 'package does not exist'
ValueError: package does not exist
dpkg: error processing bcmwl-kernel-source (--install):
 subprocess installed post-installation script returned error exit status 6
Errors were encountered while processing:
 bcmwl-kernel-source


Thanks again for being so patient.

Cheers, Jo

---

### Post by chili555 on 2011-05-16
I think it wants the package patch. Remember chili's favorite song: "Be sure to get the version (Maverick, Natty, etc.) and architecture (32- or 64-bit) to match your installation."

[http://packages.ubuntu.com/search?keywords=patch&suite=default&section=all&arch=any&searchon=names](http://packages.ubuntu.com/search?keywords=patch&suite=default&section=all&arch=any&searchon=names)

---

### Post by Happibun on 2011-05-16
Riiiight...

Closer, but still no cigar.

I went to the [SIZE=1]Download Page for patch_2.6-2ubuntu1_i386.deb on Intel x86 machines[/SIZE] and moved it in to the same directory as the other files, then:

> jo@Iota:~$ sudo dpkg -i bcmwl*.deb dkms*.deb
[sudo] password for jo: 
(Reading database ... 123004 files and directories currently installed.)
Preparing to replace bcmwl-kernel-source 5.60.48.36+bdcom-0ubuntu3 (using bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement bcmwl-kernel-source ...
Preparing to replace dkms 2.1.1.2-3ubuntu1 (using dkms_2.1.1.2-3ubuntu1_all.deb) ...
Unpacking replacement dkms ...
Setting up dkms (2.1.1.2-3ubuntu1) ...

Processing triggers for man-db ...
Setting up bcmwl-kernel-source (5.60.48.36+bdcom-0ubuntu3) ...
Loading new bcmwl-5.60.48.36+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 2.6.32-24-generic
Building for architecture i686
Building initial module for 2.6.32-24-generic
/usr/sbin/dkms: line 35: patch: command not found

Error! Application of patch 0001-MODULE_LICENSE.patch failed.
Check /var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/ for more information.
dpkg: error processing bcmwl-kernel-source (--install):
 subprocess installed post-installation script returned error exit status 6
Errors were encountered while processing:
 bcmwl-kernel-sourceSo I go and look in /var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/ and there is a file 0001-MODULE_LICENSE.patch, and this is what it is:

0001-MODULE_LICENSE.patch
> index 0f81236..c9968df 100644
--- src/src/wl/sys/wl_linux.c.orig
+++ src/src/wl/sys/wl_linux.c
@@ -163,6 +163,8 @@ struct wl_if *wl_alloc_if(wl_info_t *wl, int iftype, uint unit, struct wlc_if* w
 static void wl_free_if(wl_info_t *wl, wl_if_t *wlif);
 static void wl_get_driver_info(struct net_device *dev, struct ethtool_drvinfo *info);
 
+MODULE_LICENSE("MIXED/Proprietary");
+
 static struct pci_device_id wl_id_table[] = {
     { PCI_VENDOR_ID_BROADCOM, 0x4311, PCI_ANY_ID, PCI_ANY_ID, 0, 0, 0 }, 
     { PCI_VENDOR_ID_BROADCOM, 0x4312, PCI_ANY_ID, PCI_ANY_ID, 0, 0, 0 }, 
So, I'm running a 32 bit OS on a 64 bit machine (probably a bit stoopid, but check and check) I'm going for LTS Lucid (cause I don't want to be bleeding edge, I just want it to work), check. 

Hmmm. Package patch is not available, but is referred to by another package.
This may mean that the package is missing, is obsolete, or
is only available from another source

I'm needing another patch aren't I? Or do I need to move the patch in to another directory?

Sorry if TL DR, My brain is mushy and I've had to gaffer tape the kids to the ceiling so I can try to think... I'm so not good at multitasking.

Um, cheers, Jo

---

### Post by chili555 on 2011-05-16
Please first try:```
sudo dpkg -i patch*.deb
```Then proceed as before.

Someday, you will read on a forum about "dependency he**." You may now say, "Oh, yeah, I've been there and done that."

---

### Post by Happibun on 2011-05-16
So it really is a bit of a s*d then, and not just down to general keyboard / seat interface problems? 

That makes me feel so much better, thanks :)

I'll also point out that with your assistance it's more of an evenings interesting sleuthing than a headache, and I'm learning some of the stuff instead of it all going over my head.

I did this:-
> jo@Iota:~$ sudo dpkg -i patch*.deb
[sudo] password for jo: 
Selecting previously deselected package patch.
(Reading database ... 123004 files and directories currently installed.)
Unpacking patch (from patch_2.6-2ubuntu1_i386.deb) ...
Setting up patch (2.6-2ubuntu1) ...
Processing triggers for man-db ...An exclamation mark appeared in the notifications panel which informed me that bcmwl had failed to install. So, akin to doing a handbrake turn round Marble Arch in the rush-hour, I stuck this in again:

> jo@Iota:~$ sudo dpkg -i bcmwl*.deb dkms*.deb
(Reading database ... 123015 files and directories currently installed.)
Preparing to replace bcmwl-kernel-source 5.60.48.36+bdcom-0ubuntu3 (using bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement bcmwl-kernel-source ...
Preparing to replace dkms 2.1.1.2-3ubuntu1 (using dkms_2.1.1.2-3ubuntu1_all.deb) ...
Unpacking replacement dkms ...
Setting up dkms (2.1.1.2-3ubuntu1) ...

Processing triggers for man-db ...
Setting up bcmwl-kernel-source (5.60.48.36+bdcom-0ubuntu3) ...
Loading new bcmwl-5.60.48.36+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 2.6.32-24-generic
Building for architecture i686
Building initial module for 2.6.32-24-generic
Done.

wl.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.32-24-generic/updates/dkms/

depmod.......

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-24-generic 

I swear I could hear the lappy gurgle and splutter as I forced the modules in (and I'm rather chuffed it had to do a sanity check).

End result: WiFi is up and I'm logged in to my internets.

You are a star sir! (I'm also geeking out on your turntable pron avi, I have a Rega too)

Cheers, Jo       ):P

---

### Post by chili555 on 2011-05-16
> End result: WiFi is up and I'm logged in to my internets.Awesome! I'm glad it's working. After wireless is up and running Ubuntu is pretty easy, all click-click GUI stuff. Sometimes getting it going can be a bit of a challenge.> I'm also geeking out on your turntable pron avi, I have a Rega tooI also have a Linn Axis (Bold as Love, I call her), a few arms and too many carts. I love my Rega! 

Enjoy and post back if we can help you further.

---

### Post by Happibun on 2011-05-16
Well, there is a little bit 8-[

Believe it or not, I've used 'buntu and derivatives as my main OS since Gutsy 7.10, and I've had my battles with those lovely Broadcom cards many times, though never something that I could not solve with an ethernet cable and a certain amount of swearing before. I should by rights be a proper code monkey by now, but I'm dyslexic, and I really struggle remembering CL stuff, and I'm really bad at working out how to interpret the MAN pages.

I'm trying to work out what I just did there. I downloaded some drivers, and stuffed them in to the/a kernel right? Did I downgrade the kernel or update it? Did I rebuild it? There is where I get confused. Whenever I see the term kernel, I usually shy away because that's major brick the machine stuff, right?

I guess what I'm saying is the whoop whoop moment of getting the lappy going would be so much more significant if I know why and how it happened. At the moment I'm feeling very grateful, but also somewhat helpless, and in awe of everyone else's knowledge out here on the forum. I would love to know more so I could give more back.

Turntable geekery follows:
> On another tack - You have a Linn? Niiiiice. A friend of mine had a Linn Sondek, that's going back quite a bit, but he was the guy I bought my Rega Planar 3 from, and the reason he was selling the P3. To be honest, I don't think that the acoustics of his room were that great because I could not hear much difference between the two, both sound solid and crisp and ...warm.

Rega have wonderful after sales service too. My boxed P3 got stored upside down in a disastrous house move and all the oil drained out of the bearings.  I wrote to Rega, asking for a parts list and explaining the situation. They sent me a rescue kit of oil and bearings and a couple of lid hinges (one had been broken by the previous owner) - *for free!*

You can never have too many arms or cartridges IMO, if only I could have a few. They always were a bit of a niche market, but I guess even more so now everyone has gone digital. Cheers, Jo

---

### Post by chili555 on 2011-05-16
Essentially, all we did is download and install a driver and firmware. I'm not all that proficient in what exactly bcmwl-kernel source, dkms and patch do. All I know is what package gets what Broadcom card going. And I don't know it by any Merlin-like magic. I look at the pci.id (in your case 14e4:4727) and search the three Broadcom drivers for a match. ```
modinfo wl | grep 4727
alias:          pci:v0000[COLOR="Red"]14E4[/COLOR]d0000[COLOR="Red"]4727[/COLOR]sv*sd*bc*sc*i*
```Winner, winner, chicken dinner!

Then I tell the poster to install it! Really scientific, eh? Frankly, the only time it's even a bit challenging is in cases like yours. "I need to download and install a driver...but I have no means to download!"

I'm glad it's working!

---

### Post by Happibun on 2011-05-17
Well, I can do a proper victory dance now. Whoop, whoop, woot!

I can honestly say that though I've had lots of problems with WiFi and Broadcom cards (thanks to having to work with a lot of laptops), especially before Intrepid, I have never had a problem with wired connections. I thought 'buntu was rock solid on that one, and as long as I had access to an ethernet port and cable, I could solve stuff with the repos without having to think too hard.

Thank you so much for guiding me through that one and taking the trouble to explain it too. 

Lappy has cycled up and down about 10 times now, updated and downloaded my environment, and is behaving itself beautifully. 

:KS Jo

---

