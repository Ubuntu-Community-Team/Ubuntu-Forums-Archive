---
title: "Broadcom  BCM4318 not working 9.10"
date: 2009-12-06
forum: Networking &amp; Wireless
---

### Post by msbohn on 2009-12-06
I've been following the directions given by [Samuel Barrett]("http://sampbar.com/2009/04/broadcom-bcm4318-ubuntu-intrepid/") but have hit a roadblock.  The author of that link has not responded to queries since last April and his link with scripts and .inf files no longer works.

I get as far as his step 3 which is to enter the following command:

echo -e ‘blacklist bcm43xxnblacklist wl’ | sudo tee -a /etc/modprobe.d/blacklist
mkdir ~/bcm43xx; cd ~/bcm43xx

and terminal accepts my pwd for the sudo but then reports back the following

/home/mark/bcm453xx: Not a directory

I entered the command by hand from his post so I quadruple checked my command and believe it is ok.  It *is* creating a file called bcm453xx with the following single line in it:

blacklist bcm43xxnblacklist wl

(I repeated the command replacing xx with 18 but get the same results  with the output having xx replaced with 18 )

In Step 4 I'm supposed to find  from " the file which came with my cd" bcmwl5a.inf.  I assume that is the Ubuntu cd he is referring to but I don't know where to look for that .inf on the cd.

Here's the result of running the lspci -v | less command
.
.
.
.

03:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev02)
        Subsystem: Dell Device 0005
	Flags: bus master, fast devsel, latency 64, IRQ 17
	Memory at dfbfe000 (32-bit, non-prefetchable) [size=8K]
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb

Thanks for any help.

---

### Post by bkratz on 2009-12-06
> **msbohn said:**
> I've been following the directions given by [Samuel Barrett]("http://sampbar.com/2009/04/broadcom-bcm4318-ubuntu-intrepid/") but have hit a roadblock.  The author of that link has not responded to queries since last April and his link with scripts and .inf files no longer works.

I get as far as his step 3 which is to enter the following command:

echo -e ‘blacklist bcm43xxnblacklist wl’ | sudo tee -a /etc/modprobe.d/blacklist
mkdir ~/bcm43xx; cd ~/bcm43xx

and terminal accepts my pwd for the sudo but then reports back the following

/home/mark/bcm453xx: Not a directory

I entered the command by hand from his post so I quadruple checked my command and believe it is ok.  It *is* creating a file called bcm453xx with the following single line in it:

blacklist bcm43xxnblacklist wl

(I repeated the command replacing xx with 18 but get the same results  with the output having xx replaced with 18 )

In Step 4 I'm supposed to find  from " the file which came with my cd" bcmwl5a.inf.  I assume that is the Ubuntu cd he is referring to but I don't know where to look for that .inf on the cd.

Here's the result of running the lspci -v | less command
.
.
.
.

03:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev02)
        Subsystem: Dell Device 0005
	Flags: bus master, fast devsel, latency 64, IRQ 17
	Memory at dfbfe000 (32-bit, non-prefetchable) [size=8K]
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb

Thanks for any help.

I think it has all changed since that was written and it should now be easily supported with the B43 driver.

See the following:

[http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices](http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices)


See the section Known PCI devices

---

### Post by msbohn on 2009-12-06
> **bkratz said:**
> I think it has all changed since that was written Might be a good idea if [_this_]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4318") Ubuntu.com link stopped pointing to it

> .and it should now be easily supported with the B43 driver.

See the following:

[http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices](http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices)


See the section Known PCI devices

That link indicates my PCI device is supported.  But it doesn't work.  I've looked at a bunch of posts on this problem (in addition to the Barrett blind alley) and have tried what they suggested but no luck.

I installed 9.10 along side XP and the wireless works fine on XP and I verify it is on before booting to Ubuntu.  The upper right corner of my Ubuntu desktop shows a grayed-out antenna.  That seems to indicate there is no wireless connection so even tho I've tried to set up my SSID and WEP parameters that seems like a waste of time.

---

### Post by bkratz on 2009-12-06
> **msbohn said:**
> Might be a good idea if [_this_]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4318") Ubuntu.com link stopped pointing to it



That link indicates my PCI device is supported.  But it doesn't work.  I've looked at a bunch of posts on this problem (in addition to the Barrett blind alley) and have tried what they suggested but no luck.

I installed 9.10 along side XP and the wireless works fine on XP and I verify it is on before booting to Ubuntu.  The upper right corner of my Ubuntu desktop shows a grayed-out antenna.  That seems to indicate there is no wireless connection so even tho I've tried to set up my SSID and WEP parameters that seems like a waste of time.



I don't understand the comment about link pointing to!, but a gentlemen with you exact same device went there yesterday and was able to connect simply by installing b43 fwcutter.
I will find that thread and send it to you, perhaps a PM with him will help you.

---

### Post by bkratz on 2009-12-06
Here is the link I was mentioning

[http://ubuntuforums.org/showthread.php?t=1347026](http://ubuntuforums.org/showthread.php?t=1347026)

Good luck

---

### Post by msbohn on 2009-12-06
> **bkratz said:**
> Here is the link I was mentioning

[http://ubuntuforums.org/showthread.php?t=1347026](http://ubuntuforums.org/showthread.php?t=1347026)

Good luck

Thanks.  

Is there a way I can download the b43 driver to my Mac and then move it (USB stick or CD) to the Ubuntu machine?  The Ubuntu machine has no internet access (obviously).

If not, the instructions for "No Alternate Internet Access" has the following first step that I don't understand:

> 1.   Install b43-fwcutter (without the firmware downloading and being set up) which should be located on the Ubuntu 9.04 install disc (add it as a repository in Synaptic) or from /var/cache/apt/archives on an Ubuntu computer with b43 installed.

What is a *repository in Synaptic*??

---

### Post by bkratz on 2009-12-06
> **msbohn said:**
> Thanks.  

Is there a way I can download the b43 driver to my Mac and then move it (USB stick or CD) to the Ubuntu machine?  The Ubuntu machine has no internet access (obviously).

If not, the instructions for "No Alternate Internet Access" has the following first step that I don't understand:



What is a *repository in Synaptic*??


So far I have not found where you are in the page, I must be blind!

Anyway,

What they are referring to is the vast warehouse of software that is available for download, some is open source some is restricted but available.

They want you to put in the Cd that had the installation of Ubuntu (the .iso file) in your drive, and go to 
System--administration--Synaptic Package Manager ( requires password to get here ) and select 
Settings--repositories and place a checkmark in CDROM towards the bottom.  What you need must be on the disk already, but like I said I have not found exactly where you are!

---

### Post by northd_tech on 2009-12-06
You might want to watch this thread:

[http://ubuntuforums.org/showthread.php?t=1339560&highlight=4318](http://ubuntuforums.org/showthread.php?t=1339560&highlight=4318)

I didn't see if that person was able to get that 4318 working yet, but hopefully they will come back with an update.

---

### Post by northd_tech on 2009-12-06
> **msbohn said:**
> 
Is there a way I can download the b43 driver to my Mac and then move it (USB stick or CD) to the Ubuntu machine?  The Ubuntu machine has no internet access (obviously).

If you are able to search and locate the correct ".deb" files, then you should just be able to double click or right-click "open with Package Manager" and install them directly after mounting the USB stick.  You will want to make sure you've got the right one (ubuntu version, 32 vs. 64-bit, etc.).

Here is an older HOWTO on that 4318 though:

[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

---

### Post by msbohn on 2009-12-06
> **bkratz said:**
> So far I have not found where you are in the page, I must be blind!

A
They want you to put in the Cd that had the installation of Ubuntu (the .iso file) in your drive, and go to 
System--administration--Synaptic Package Manager ( requires password to get here ) and select 
Settings--repositories and place a checkmark in CDROM towards the bottom.  What you need must be on the disk already, but like I said I have not found exactly where you are!
I got all that going but when I installed b43-fwcutter (at least I think that's what I did) I get the following error

b43-fwcutter:subprocess installed post-installation script returned error exit status 1

---

### Post by bkratz on 2009-12-06
> **msbohn said:**
> I got all that going but when I installed b43-fwcutter (at least I think that's what I did) I get the following error

b43-fwcutter:subprocess installed post-installation script returned error exit status 1



Googled the reported error (which I really don't know what it means--but it appears to relate to dependencies and found this

[http://www.linuxforums.org/forum/wireless-internet/146665-solved-wireless-setup-ubuntu-9-04-a.html](http://www.linuxforums.org/forum/wireless-internet/146665-solved-wireless-setup-ubuntu-9-04-a.html)


Here the whole google link
[http://www.google.com/search?hl=en&q=b43-fwcutter:subprocess+installed+post-installation+script+returned+error+exit+status+1&start=10&sa=N](http://www.google.com/search?hl=en&q=b43-fwcutter:subprocess+installed+post-installation+script+returned+error+exit+status+1&start=10&sa=N)



He at least gives a link

---

### Post by bkratz on 2009-12-06
> **northd_tech said:**
> You might want to watch this thread:

[http://ubuntuforums.org/showthread.php?t=1339560&highlight=4318](http://ubuntuforums.org/showthread.php?t=1339560&highlight=4318)

I didn't see if that person was able to get that 4318 working yet, but hopefully they will come back with an update.



This was all in 8.04.  ndiswrapper is no longer required for the Broadcom cards which utilize B43.

---

### Post by northd_tech on 2009-12-06
I haven't heard from anyone yet whether the proprietary "STA" Broadcom Linux driver will work for the 4318 yet (but it is a really easy fix for the Broadcom 4311 and my 4321AG which is sometimes identified as a "4328" under Linux).

There is a download link for that at post #6 on this thread:

[http://ubuntuforums.org/showthread.php?t=1336676](http://ubuntuforums.org/showthread.php?t=1336676)

It might be worth a shot (but it could also cause some other problem too).

---

### Post by bkratz on 2009-12-06
> **northd_tech said:**
> I haven't heard from anyone yet whether the proprietary "STA" Broadcom Linux driver will work for the 4318 yet (but it is a really easy fix for the Broadcom 4311 and my 4321AG which is sometimes identified as a "4328" under Linux).

There is a download link for that at post #6 on this thread:

[http://ubuntuforums.org/showthread.php?t=1336676](http://ubuntuforums.org/showthread.php?t=1336676)

It might be worth a shot (but it could also cause some other problem too).



See the link in my first posting  "repeated here"

[http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices](http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices)

---

### Post by msbohn on 2009-12-10
Following this thread:

[http://ubuntuforums.org/showthread.php?t=1350828&highlight=broadcom](http://ubuntuforums.org/showthread.php?t=1350828&highlight=broadcom)

I got the wireless to work in 5 easy steps:

Made a wired connection.
Looked in System/Admin/Hardware Drivers
It offered to download the B43 driver
Disconnected ethernet cable
Double clicked the wireless icon on top and selected my network

Thanks, all!

---

### Post by msbohn on 2009-12-11
> **msbohn said:**
> Following this thread:

[http://ubuntuforums.org/showthread.php?t=1350828&highlight=broadcom](http://ubuntuforums.org/showthread.php?t=1350828&highlight=broadcom)

I got the wireless to work in 5 easy steps:

Made a wired connection.
Looked in System/Admin/Hardware Drivers
It offered to download the B43 driver
Disconnected ethernet cable
Double clicked the wireless icon on top and selected my network

Thanks, all!

Well, it looks like I spoke too soon.  My wireless connection worked long enough to download one web site and then it quit (or maybe it was cached from when I was wired to the router?).  Rebooting Ubuntu doesn't help.  I can't even ping my own router.  I am connected to it tho.

---

### Post by msbohn on 2009-12-13
I've got a network connection now using my ethernet cable.  So I can log onto my router's admin page and compare wireless setting with that of Ubuntu's Network Connections edit window.  The parameters they have in common look good but some on the router's admin page do not appear on the Ubuntu edit window, e.g. "Wireless Network Mode" set to g only appears on the admin page but there is no equivalent on the Ubuntu edit window.  

I don't know where to go next with this wireless issue.

---

### Post by msbohn on 2010-01-10
Nothing worked on this wireless problem until I replaced my Linksys WRT54g router with an Apple Airport Extreme.  Have no idea why but Wicd quickly and easily connected with the AE and all is good now.

Just need to get my network printer working and I'll have a fully functional Ubuntu system!

---

### Post by bkratz on 2010-01-10
> **msbohn said:**
> Nothing worked on this wireless problem until I replaced my Linksys WRT54g router with an Apple Airport Extreme.  Have no idea why but Wicd quickly and easily connected with the AE and all is good now.

Just need to get my network printer working and I'll have a fully functional Ubuntu system!

Have been noticing lately a lot of users of the WRT54g updated some software in the router resulting in functionality. I wouldn't toss it just yet. I will look for one of the threads and send a link

---

### Post by bkratz on 2010-01-10
Here is one of them mentioning DD-WRT in post 2

[http://ubuntuforums.org/showthread.php?t=1375932&highlight=WRT54g](http://ubuntuforums.org/showthread.php?t=1375932&highlight=WRT54g)

---

### Post by Bucky Ball on 2010-01-10
Plug in an ethernet cable and get all updates. That card should be picked up now and you'll possibly be offered the drivers and firmware.

Check in 'System->Administration->Hardware Drivers'.

There's also no reason to use wicd for it either, unless you prefer that or you get better connectivity using it. Doesn't seem to make much difference nowadays.

---

### Post by bkratz on 2010-01-10
> **Bucky Ball said:**
> Plug in an ethernet cable and get all updates. That card should be picked up now and you'll possibly be offered the drivers and firmware.

Check in 'System->Administration->Hardware Drivers'.

No his wireless card works--this was just a comment about his old router.

---

### Post by Bucky Ball on 2010-01-10
Perhaps mark as solved?

---

### Post by msbohn on 2010-01-10
> **Bucky Ball said:**
> Perhaps mark as solved?

How do I do that?

---

### Post by bkratz on 2010-01-10
> **msbohn said:**
> How do I do that?

Go to the thread tools at the top and select it

---

