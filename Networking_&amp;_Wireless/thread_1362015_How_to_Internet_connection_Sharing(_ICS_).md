---
title: "How to Internet connection Sharing( ICS )"
date: 2009-12-22
forum: Networking &amp; Wireless
---

### Post by ibrahim.k on 2009-12-22
On my laptop I have a wireless connection to the internet.

Can I share this connection with my desktop computer ? i am using ubuntu 9.10


and can you please tell me whats the difference between xubuntu, kubuntu and ubuntu ??

did not see it anywhere

---

### Post by Iowan on 2009-12-23
> **ibrahim.k said:**
> and can you please tell me whats the difference between xubuntu, kubuntu and ubuntu ??

did not see it anywhere
[Here]("http://en.wikipedia.org/wiki/Ubuntu_(Linux_distribution)#Variants") is the wikipedia version.  There's a more "official" version I'm still trying to locate.
[Another]("http://www.psychocats.net/ubuntu/whichbuntu") description.
Maybe [this]("https://help.ubuntu.com/community/CommonQuestions") is the one I was thinking of...

---

### Post by ibrahim.k on 2009-12-23
Thank you [Iowan]("http://ubuntuforums.org/member.php?u=65323") that was use full still the Internet connection thing

---

### Post by zaphod777 on 2009-12-23
> **ibrahim.k said:**
> On my laptop I have a wireless connection to the internet.

Can I share this connection with my desktop computer ? i am using ubuntu 9.10


and can you please tell me whats the difference between xubuntu, kubuntu and ubuntu ??

did not see it anywhere

Xubuntu uses a lighter interface for older machines
Kubuntu uses KDE instead of gnome for the desktop environment
Ubuntu is the default distribution using Gnome for the desktop environment.


Personally I prefer Gnome.

I have never setup internet connection sharing on ubuntu but here is the documentation:

[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

[http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html](http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html)

---

### Post by ibrahim.k on 2009-12-23
Thank you zaphod I will try it

---

### Post by zaphod777 on 2009-12-23
Let me know how it goes I can try and help with general network troubleshooting if needed.

I can also try and test it here if you run into too much trouble.

---

### Post by ibrahim.k on 2009-12-24
Reading this article was too much for me I didn't understand most of the things since I am not that professional user thank you in advance zaphod

---

### Post by zaphod777 on 2009-12-24
After some hunting around I found two articles that I was looking for yesterday they both look pretty good and not as confusing.

this one is for sharing a wired connection 

[http://bigbrovar.wordpress.com/2008/12/18/how-to-share-your-internet-connection-on-ubuntu/](http://bigbrovar.wordpress.com/2008/12/18/how-to-share-your-internet-connection-on-ubuntu/)

this one is for creating a wireless network for the other machine to use.

[http://bigbrovar.wordpress.com/2009/01/17/share-you-internet-wirelessly-on-ubuntu/](http://bigbrovar.wordpress.com/2009/01/17/share-you-internet-wirelessly-on-ubuntu/)

---

### Post by ibrahim.k on 2009-12-24
OMG !!!! I feel stupid after seeing this two threads I found out that current settings for my ethernet connection are not the way it should be
before:
192.168.10.1
255.255.255.0
192.168.10.1
now
192.168.10.1
255.255.255.0
0.0.0.0
and I can use wireless and wired connection at the same time thank you zaphod and according to the ICS it didn't work I will try doing it once again thnx again

---

### Post by ssl432 on 2010-01-10
If this question has already been answered I couldn't find it but a link would be welcomed.

Here goes:

I have an ancient laptop with a broken screen that I would like to use as a wireless Internet receiver.  I want it to receive Internet over a usb wireless nic (wlan0) and share it along with dhcp and dynamic ip addressing service through it's built in nic (eth0) to the rest of my network via a 4 port Ethernet switch with an up-link port (it is just a dummy switch, it doesn't do dhcp or anything else like that).  I have followed the instructions from the link shown above.  Here is my difficulty; If I connect eth0 to a regular port on the switch firestarter starts up just fine and reports no errors, however in order to share the Internet out to the rest of my network I believe I need to plug into the up-link port and this causes firestarter to tell me "Failed to start firewall, the device eth0 is not ready...." as if it was completely disconnected.  I have been using a newish (windows vista) laptop that belongs to my work to get to the internet up to this point and everything works ok with it hooked to the up-link port on the switch using m-sft's ics.  I had hoped that I could just slip this ubuntu machine in in it's stead but I am stymied.

This might be just a basic networking problem and not an Ubuntu issue at all, but as I said, it works somehow with my current setup but the ubuntu laptop just won't do it.  I am not a particularly command line savvy person which is why I'm trying to use firestarter, so if this can be explained without a long series of command line references I'll love Ubuntu forever,  if not I'll just like Ubuntu as a friend and try to muddle through somehow.  Any help at all will be welcome.

---

### Post by zaphod777 on 2010-01-10
> **ssl432 said:**
> If this question has already been answered I couldn't find it but a link would be welcomed.

Here goes:

I have an ancient laptop with a broken screen that I would like to use as a wireless Internet receiver.  I want it to receive Internet over a usb wireless nic (wlan0) and share it along with dhcp and dynamic ip addressing service through it's built in nic (eth0) to the rest of my network via a 4 port Ethernet switch with an up-link port (it is just a dummy switch, it doesn't do dhcp or anything else like that).  I have followed the instructions from the link shown above.  Here is my difficulty; If I connect eth0 to a regular port on the switch firestarter starts up just fine and reports no errors, however in order to share the Internet out to the rest of my network I believe I need to plug into the up-link port and this causes firestarter to tell me "Failed to start firewall, the device eth0 is not ready...." as if it was completely disconnected.  I have been using a newish (windows vista) laptop that belongs to my work to get to the internet up to this point and everything works ok with it hooked to the up-link port on the switch using m-sft's ics.  I had hoped that I could just slip this ubuntu machine in in it's stead but I am stymied.

This might be just a basic networking problem and not an Ubuntu issue at all, but as I said, it works somehow with my current setup but the ubuntu laptop just won't do it.  I am not a particularly command line savvy person which is why I'm trying to use firestarter, so if this can be explained without a long series of command line references I'll love Ubuntu forever,  if not I'll just like Ubuntu as a friend and try to muddle through somehow.  Any help at all will be welcome.

uplink port is only needed for connecting switch to switch. You laptop can connect to the normal switch port. Most uplink ports also have a button next to it if you push the button then it will change from uplink to normal switch port.

---

### Post by sldavid on 2010-08-10
thanks Zaphod777. 

I followed the first of the two links ([https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)) and from there used the option - GUI Method via Network Manager (Ubuntu 9.10 and up). And....
I was sharing my wireless laptop Internet connection with the rest of my home network. Still can't believe is was that easy.

---

### Post by ibrahim.k on 2010-08-11
thnx for sharing knowledge with us.
may I ask what settings did you use on the desktop ?
as to me i want to share my laptop wireless internet with my desktop via ethernet.
from ipv4 i  choose the shared to other computers option.


> **sldavid said:**
> thanks Zaphod777. 

I followed the first of the two links ([https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)) and from there used the option - GUI Method via Network Manager (Ubuntu 9.10 and up). And....
I was sharing my wireless laptop Internet connection with the rest of my home network. Still can't believe is was that easy.

---

### Post by zaphod777 on 2010-08-11
> **sldavid said:**
> thanks Zaphod777. 

I followed the first of the two links ([https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)) and from there used the option - GUI Method via Network Manager (Ubuntu 9.10 and up). And....
I was sharing my wireless laptop Internet connection with the rest of my home network. Still can't believe is was that easy.

Glad to help there is a lot of good documentation in the official documentation pages. I think a lot of people don't even know it is there.

---

### Post by gvoima on 2010-08-14
Just a reminder..

I'm sharing a ppp connection on Karmic to my local network through the onboard nic. The network sharing described in the ubuntu documentation works fine, except that I start my ppp connection after bootup. It uses the package dnsmasq-base and it doesn't poll the connections correclty.
So restarting dnsmasq **after** initializing the ppp connection, it works fine.

If anyone is having this problem on Karmic, this might be the possibility.

---

### Post by Schuby007 on 2011-02-02
Hi,

I'm trying to share my wireless internet connection via my laptop running 10.10 with my desktop running 10.04.

I followed [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing) "GUI Method via Network Manager" and set my eth0 connection on my laptop to "Shared To Other Computers". I then plug an ethernet cable into my eth0 port on my laptop and into the eth0 port on my desktop and my laptop pops-up and says Auto eth0 Connection Established but nothing happens on my desktop, and when I try to connect to Auto eth0 on my desktop I see the wireless meter flash for about 30 seconds and then it says Wired connection disconnected".

Anyone know what's going on? Do I need to use a crossover cable?

---

### Post by mips on 2011-02-03
> **Schuby007 said:**
> 
Anyone know what's going on? Do I need to use a crossover cable?

If you are using 10/100Mb's Ethernet yes, 1Gb/s Ethernet no as far as I remember.
[http://en.wikipedia.org/wiki/Ethernet_crossover_cable#Automatic_crossover](http://en.wikipedia.org/wiki/Ethernet_crossover_cable#Automatic_crossover)

---

