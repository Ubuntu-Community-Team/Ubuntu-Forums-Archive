---
title: "Ubuntu 9.10 Ralink RT2870 - Won't connect to hidden WPA2 network"
date: 2009-12-31
forum: Networking &amp; Wireless
---

### Post by own3mall on 2009-12-31
No matter what I do, I cannot get my Ralink RT2870 USB adapter to connect to my hidden wpa2 aes max character password network.  It just sits there all day, and continues to ask me for the password.  The password is correct, as all my Windows machines can connect to it.

I followed this guide:

[http://art.ubuntuforums.org/showthread.php?t=1342593](http://art.ubuntuforums.org/showthread.php?t=1342593)

Blacklisted some entries, compiled the official RT2870 drivers, and deleted the ubuntu default driver.  I think compilation and everything was smooth.  

I can connect to my network when it is visible and using WEP 64-bit.  I cannot connect to it when it's visible and using a WPA2 key.  

What is going on here?  I can't get NDISWrapper to work either, as the hardware isn't found even though I gave it an inf driver from the CD to play with.  

Any ideas?  I am using Ubuntu 9.10

---

### Post by skeetre on 2010-01-03
I'm having the same issue, but with 2 different wireless adapters. 
Here's a website with a fix:

[http://jsdelfino.blogspot.com/2009/11/connecting-to-wpa2-network-with-ubuntu.html](http://jsdelfino.blogspot.com/2009/11/connecting-to-wpa2-network-with-ubuntu.html)

There's also this [thread]("http://ubuntuforums.org/showthread.php?t=318539") that mentions a specific issue with Ralink adapters.

---

### Post by aextance on 2010-01-03
Hi own3mall,

I've been getting a similar experience to you, only my RT2870 sometimes connects. It did ask for the password a lot, and still does ask if I want to try to my connect several times. I used the howto you link to, and it kind of worked. I've noticed that the list of drivers to blacklist has changed quite recently, and I certainly only got my RT2870 adapter to work after including all of them.

I just checked out the fix that skeetre referred to, and the bug that the fix itself also refers to. I had this bug, as well as the repeated asking for passwords that you mention. I guess they might be part of the same thing. The reported bug is pretty widespread by the sounds of it, and is slated to be sorted in a future update to Network Manager. 

I couldn't figure out how to use the fix that skeetre linked to, but there is a way to test a fix from the NetworkManager team PPA through Update Manager. What you do is go to System > Administration > Software Sources, click on the "other sources" tab, and add the following two sources:

deb [http://ppa.launchpad.net/network-manager/trunk/ubuntu](http://ppa.launchpad.net/network-manager/trunk/ubuntu) karmic main 
deb-src [http://ppa.launchpad.net/network-manager/trunk/ubuntu](http://ppa.launchpad.net/network-manager/trunk/ubuntu) karmic main 

Then the update manager popped up for me, and installed the fix.

My current network manager now remembers the password when trying to connect, and connected on the third attempt, which is better than it was before. 

As far as "known problems" with RT2870 chipsets mentioned in the other location Skeetre links to, this was certainly the case with older drivers, but in the past six-nine months the drivers have undergone a revamp and there are people claiming to use RT2870 smoothly with WPA2. I do have it working myself, albeit not exactly smoothly. 

Hope this helps,
Andy

---

### Post by own3mall on 2010-01-10
Thanks for all of your help.  However,  I tried both methods, and I am still unable to connect.  I did this though:

```

root@eric-desktop:~# git clone git://git.gnome.org/network-manager-applet
Initialized empty Git repository in /root/network-manager-applet/.git/
remote: Counting objects: 10565, done.
remote: Compressing objects: 100% (3328/3328), done.
remote: Total 10565 (delta 8440), reused 8962 (delta 7229)
Receiving objects: 100% (10565/10565), 3.80 MiB | 182 KiB/s, done.
Resolving deltas: 100% (8440/8440), done.
root@eric-desktop:~# ./autogen.sh
-bash: ./autogen.sh: No such file or directory
root@eric-desktop:~# ./configure
-bash: ./configure: No such file or directory
root@eric-desktop:~# make

```

Not sure what I did wrong.

I also added the network manager to my software sources and updated Ubuntu.  Now, do I still use the network icon in the top right next to the volume icon to configure my network, or what program do I use now?

---

### Post by aextance on 2010-01-10
I didn't try and do any of that git stuff - way too confusing for me. 

If you go through my update manager suggestion, you do still use network manager. The first thing to happen though - assuming you still have a wired network - is that an automatic update should install itself. Then when you try and connect to your hidden WPA2 network, you should at least advance from being asked your password all day (eg having to type in the password) to just being told it needs to reconnect all day (not having to type in the password)? That's what I had, and was eventually able to connect. Although now it seems like my adapter won't connect again. 

Both the fixes shown in this thread seem to be for password issues more than lack of connection issues. I'm planning another investigation right now to see if I can get any further. I'll keep you updated.

---

### Post by bgiannes on 2010-01-18
This post fixed this problem for me, i get N and wpa2.  Never loss connection.

[http://ubuntuforums.org/showpost.php?p=8346399&postcount=9](http://ubuntuforums.org/showpost.php?p=8346399&postcount=9)



Note: i didn't update network-manager to the ppa version, just added the /etc/Wireless/RT2860STA/RT2860STA.dat file.  I did change any of the values in the file.  I'm using the driver that is in the 9.10 kernel.

---

### Post by aextance on 2010-02-15
Thanks bgiannes,

I tried that but it didn't work. Do you have a RT2870 adapter or an RT2860? 

What do you get when you type:

lshw -C network

in the terminal?

According to this page:

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#check](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#check)

I should get an entry saying "driver=" next to the configuration entry, but I don't. Seems unlikely that I don't have a driver, seeing as the actual adapter shows up and tries to connect, but I'm running out of ideas...

---

### Post by bgiannes on 2010-02-15
snip 
> 
description: Wireless interface
       product: RT2860
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: ra0
       version: 00
       serial: XX
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 ip=192.168.1.115 latency=0 multicast=yes wireless=RT2860 Wireless
       resources: irq:19 memory:febf0000-febfffff
snip


but any rt2800 chip-set should work the same?

---

### Post by aextance on 2010-02-16
So, I unhid my network and it worked. Not sure what that's about. 

Turns out that if I have my SSID hidden, I can't connect even if it's unencrypted. When it's broadcast, I can connect when both encrypted and unencrypted. 

I'm also using WPA (mixed) or WPA and WPA2 personal, depending upon whether you're talking to my router or laptop. 

Still don't have any drivers showing for the rt2870 entry when I type lshw -C network in the terminal, but I guess this could mean it's using onboard rather than proprietary drivers?

Are you using a hidden or a broadcast SSID own3mall? It's kind of irritating that it doesn't work when hidden, but it's nice to get it to work.

---

### Post by hopstah on 2010-04-15
I just fixed this issue I was having with the RT2860 by setting my router to use WPA2 instead of "Auto WPA or WPA2."  It works both with and without broadcasting my SSID.  Maybe this will help someone else.

---

### Post by dborg on 2010-04-16
> **aextance said:**
> So, I unhid my network and it worked. Not sure what that's about. 

Turns out that if I have my SSID hidden, I can't connect even if it's unencrypted. When it's broadcast, I can connect when both encrypted and unencrypted. 

I'm also using WPA (mixed) or WPA and WPA2 personal, depending upon whether you're talking to my router or laptop. 

Still don't have any drivers showing for the rt2870 entry when I type lshw -C network in the terminal, but I guess this could mean it's using onboard rather than proprietary drivers?

Are you using a hidden or a broadcast SSID own3mall? It's kind of irritating that it doesn't work when hidden, but it's nice to get it to work.

I too am suffering from this issue, When the SSID is hidden the network-manager will attempt to connect and timeout, then the password/wpa key screen will pop up again asking for the key and will loop like this until I disconnect it from the network-manager.

I tried using the git package, regardless of the dependencies I installed I seemed to still have make issues.

Just wondering if there are any definitive fixes for this as I am now extremely frustrated and am also paranoid about making my network as secure as possible from script kiddies (while I know WPA2 and hiding SSID won't stop the ones that REALLY want to access my network, it stops the lazy ones).

Thanks

---

