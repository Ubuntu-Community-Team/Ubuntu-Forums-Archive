---
title: "Frustrated with Internet Connnection Sharing"
date: 2009-08-04
forum: Networking &amp; Wireless
---

### Post by BlueVark on 2009-08-04
Hi Folks,

Great forum...I really have learned a lot over the past year and appreciate all the support.  I'm ready to switch over my entire home LAN to Ubuntu, but I've really run into a problem with the Internet Connection Sharing.  I've read so many different posts (with so much conflicting information) and nothing seems to work. I have a fairly simple LAN setup.
1.  Desktop #1 dual booting Win XP & Ubuntu 9.04 with wireless broadband Internet connection (Auto CDMA) and wired Ethernet connection (auto eth0).  
2.  Laptop with Ubuntu 9.04 connected to LAN with wired Ethernet (auto eth0)
3.  Desktop #2 with Vista connected to LAN by wired Ethernet. 

When I run XP on Desktop #1 the entire network works fine and I can share internet with everyone.  
When I run Ubuntu on Desktop #1, I can not share the internet.  I have tried at least a dozen different setups (with firestarter, without firestarter, etc.) and none have worked.  
This should be a simple operation and I have already wasted hours trying to figure it out.  Can someone point me to a current setup/Wiki that works?  Why is this so hard to do?  Shouldn't this be a simple operation if we want folks to use Ubuntu?  
Again, this is a great forum and I really appreciate everyone's help.  MD

---

### Post by superprash2003 on 2009-08-04
does the CDMA connection work in ubuntu? if so , take a look at this [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

---

### Post by roblloyd on 2009-08-12
I feel your pain BlueVark, I want to set up something like this:

Internet -> Desktop ))) Wireless.Devices

Sounds simple, share my nice fast LAN connection using a USB wireless thingy so that I can download big files from the internet onto my shiny new android phone.

But it's not as easy as you'd think from my experience.

There is [this]("http://magazine.redhat.com/2008/10/16/video-fedora-10-connection-sharing/") video from one of the fedora blogs which shows almost exactly what you want to do. I hope it helps.

Personally, even though I don't see any reason why it wouldn't work in Ubuntu, it doesn't seem to for me. 

If anyone has any ideas on how I can get this all working I'd love to know. I've already tried firestarter and it, ironically, wouldn't start. 

My setup is:

Desktop Ubuntu 9.04
Internet from LAN connection. IP assigned by DHCP corporate network. eth0. Works fine
USB Wireless Card. TP-Link TL-WN321G. wlan0. Goes through the motions of the video above but then just doesn't do anything.

I need wireless client IP addresses to be assigned automatically Basically, I just want to add the functionality of a router to my ubuntu box. No, I can't just get a router unfortunately.

Thanks in advance for any advice,

Rob

---

