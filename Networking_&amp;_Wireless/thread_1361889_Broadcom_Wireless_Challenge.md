---
title: "Broadcom Wireless Challenge"
date: 2009-12-22
forum: Networking &amp; Wireless
---

### Post by BandeAli on 2009-12-22
Alright I have an HP laptop and I have installed Ubuntu through Wubi. 

I have a broadcom 802.11 b/g WLAN card. The wireless card isn't currently working on ubuntu but is working on Windows 7. I have been trying to read the way to get this working but all require me to be connected to the internet, but the problem is I don't have access to wired internet. To make this worse, I am completely new to ubuntu (or Linux system for that matter) so I have no idea what I am doing. 

My usb disk is also broken but I do have the cd/dvd drive. So is there a way that I can put all the files i need on cd through windows and then use the same cd to get the stuff working on ubuntu?

---

### Post by jml on 2009-12-22
Broadcom cards are notoriously difficult to get to work in Linux because the company refuses to give the Linux community access to their proprietary drivers.  Ubuntu has a very good chance of working.  Using the Windows 7 partition, log on to the Ubuntu web site and download an iso. image of Ubuntu 9.10.  Use whatever Windows application you have to burn the .iso to disc.  Then reboot your computer with the CD in place.  Once the live version is installed, see if your wireless card is working.  If it is, then a re-install would be one way to get up and running.

Joe

---

### Post by coffeecat on 2009-12-22
> **BandeAli said:**
>  I have been trying to read the way to get this working but all require me to be connected to the internet, but the problem is I don't have access to wired internet.

I have no personal experience of Broadcom wireless, but from what I have read, the Broadcom firmware you need cannot be included for licensing reasons. So you need to install the b43-fwcutter package which is a script to extract and install the firmware. Trouble is, as you've discovered, you need a wired connection because the script downloads another file from which it extracts the firmware. Catch-22 if you don't have a wired connection.

The alternative is the bcmwl-kernel-source package for the STA driver. But again, you need a wired connection.

I have two suggestions;

1 - in Windows 7, go to:

[http://archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/](http://archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/)

...and download the bcmwl-kernel-source deb package appropriate for your architecture (i386/32-bit or AMD64/64-bit). Transfer the deb file to your Ubuntu desktop and simply double-click on it. If all dependencies are met, it will install. (**Edit:** you'll probably need to reboot.) If it complains about missing dependencies, post back with details and I'll point you to a download site.

2 - Can you prevail upon a neighbour, friend or relative to use their wired connection? Then you could try installing the b43-fwcutter package.

---

### Post by BandeAli on 2009-12-22
1. It did return a dependency error: 
```
Error: Dependency is not satisfiable: dkms
```Is there a way I can install the ndiswrapper thing by downloading in on windows and then sending it to ubuntu?

> 2 - Can you prevail upon a neighbour, friend or relative to use their wired connection? Then you could try installing the b43-fwcutter package.2. Where is the challenge in that? :)

---

### Post by coffeecat on 2009-12-23
OK. dkms first. For Karmic, download the dkms_2.1.0.1-0ubuntu1_all.deb package:

[http://archive.ubuntu.com/ubuntu/pool/main/d/dkms/](http://archive.ubuntu.com/ubuntu/pool/main/d/dkms/)

Try that first.

> **BandeAli said:**
> Is there a way I can install the ndiswrapper thing by downloading in on windows and then sending it to ubuntu?

I'd urge you to go down that route very much as a last resort. One of the two different "official" ways ought to work. Your difficulty is a compound of Broadcom's restrictive licensing and your lack of a wired connection. Having said that, you would need the packages ndisgtk, ndiswrapper-common and ndiswrapper-utils-1.9. Back-navigate the above link till you get to .../pool/main, and then it's fairly obvious. You'd need the latest deb packages appropriate for your architecture.

> **BandeAli said:**
> 2. Where is the challenge in that? :)

True. :wink: But joking aside - is there anyone that can help? There's no point making things difficult for yourself..

---

### Post by BandeAli on 2009-12-23
I assumed that even with wired connection it would take me a few hours to get it working thats why I was just considering to find a way to get it without the wired connection, but if it is that much easier I can try to find internet connection. However, I don't want to spend hours hogging my friends internet, can you please direct me to a concise tutorial of how to get the card working with a wired connection.
Thanks

---

### Post by coffeecat on 2009-12-23
> **BandeAli said:**
> I assumed that even with wired connection it would take me a few hours to get it working

:shock:

No - a wired connection, not a carrier pigeon! :wink:

The two alternative methods should only take minutes. Try this:

Connect with a wired connection. Open System > Administration > Synaptic and click on reload. This is just to refresh the package metadata because you don't need to update yet. Now go to System > Administration > Hardware Drivers. Is it prompting you for the Broadcom STA driver? If so, let it do its stuff and reboot. Click on network manager and see if it's detecting any nearby wireless networks. If it is, then hopefully you are OK. If not, re-establish the wired connection and use Synaptic to install the  b43-fwcutter package which, don't forget, itself downloads a file from which to extract the firmware.

All of this shouldn't take long at all and will involve a download of only a few megabytes - perhaps tens of megabytes.

By the way - I don't know whether it's best to use the STA driver or run b43-fwcutter. Here's a useful post with some information. 

[http://ubuntuforums.org/showpost.php?p=8371562&postcount=3](http://ubuntuforums.org/showpost.php?p=8371562&postcount=3)

The comment about the "minor issue" with the STA driver may or may not apply to you depending on whether your ethernet controller is also Broadcom.

---

### Post by PRC09 on 2009-12-23
If you have no wired connection try post #1 on the following link...

[http://ubuntuforums.org/showthread.php?t=1288865](http://ubuntuforums.org/showthread.php?t=1288865)

Also this as well for Broadcom info...

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

