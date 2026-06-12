---
title: "Linksys WPC54gs Wireless Card"
date: 2006-06-01
forum: Networking &amp; Wireless
---

### Post by lakerssuperman on 2006-06-01
This card used to work with Breezy.  I did a fresh install of Dapper and tried to setup the card using the ndiswrapper setup.  It doesn't work however.  It says that everything has been installed and the module loaded but i cannot connect to my wireless network. Has anyone gotten this card to work and if so any suggestions.  Thanks.

---

### Post by elemental666 on 2006-06-01
I'm in the same boat.  I haven't tried ndsiwrapper + windows yet.  iwconfig shows a wireless adapter (eth1) with Broadcom chipset.  I set the ESSID and channel with iwconfig. 

when I run sudo ifup eth1 I get:

```
sudo ifup eth1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
Listening on LPF/eth1/00:13:10:47:dd:d2
Sending on   LPF/eth1/00:13:10:47:dd:d2
Sending on   Socket/fallback
receive_packet failed on eth1: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 20
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

I'm using a Linksys WRT54GSV4 router, hardwire works like a charm.  I enabled wireless and set the essid, no WEP or WAP, changed the channel to 11 and told it to broacast the ESSID.

If anyone gets this working please let us know...

---

### Post by jon_herr on 2006-06-01
I'm really, really close to connecting.  I am using Dapper-RC from a fresh install done today...  Started out with everything looking good but no connect.  Did a 'NetworkManager --no-daemon' to debug and found that the card wasn't really found.  So...

I then followed the guide for ripping the firmware to /lib/firmware using fwcutter from the driver as provided on another great post in this forum and now the card is scanning (I think) but no connection is ever established.

The trick is that I am using WPA-PSK.

The sad thing is - I kinda had this working on this exact machine using a breezy install that I upgraded yesterday to Dapper.  I was able to connect using WPA as long as I played games with default gateway device.  

That's why I'm here.  I installed Dapper to get rid of the strangeness with the default gateway device (setting it via System -> Administration ->Network) would make it work until a reboot when Network Manager would no longer work due to uncommented lines in the /etc/network/wpa_supplicant.config.  

I am so close.  The only hint of trouble is that the scanning frequency is 0MHz as listed in the NetworkManager debug window?  

I've tried the drivers that were shipped with the card, WMP54GS, and also the ones posted in this forum.  Any ideas? 

I also have a gig of RAM if that helps.

Jon

---

### Post by jon_herr on 2006-06-02
Here's a quick note...
If I change my router settings - my WRT54G - to be a 'mixed' network as in both wireless b and wireless g standards I can connect just fine.  Setting to 'g-only' results in no connection even though the driver / card can clearly see wireless network traffic.
Other router settings don't seem to matter...   so far.  I tried setting the 'beacon interval' to a lower value to no avail.

---

### Post by elemental666 on 2006-06-02
Mine is set to mixed as well...

I just tested on a windows lappy to see what was out there to be seen and there are 3 access points, including mine, showing just fine in windows.  I don't think its my AP, I think its the pcmcia card.  BCM4306 chipset, Linksys WPC54GS V1.1 card.  I've been looking over the forums at all the 4306 info, look like I might need to try the fwcutter method...

---

### Post by elemental666 on 2006-06-02
ok, so I can now see available APs, but I'm at work so I can't test actual connections.  Here's what I did:

```
sudo su
rmmod ndiswrapper # make sure ndiswrapper is gone
rmmod bcm43xx     # Bring down bcm43xx
apt-get bcm43xx-fwcutter   # installed bcm43xx-fwcutter
bcm43xx-fwcutter -w /lib/2.6.15-23-386/ /home/elemental/wireless/bcmwl5.sys #extracted the firmware from the Linksys driver
modprobe bcm43xx  #brought bcm43xx back up

```
iwconfig now sees eth1 (my WPC54GS), network config tool now shows the eth1 wireless card and when I check properties it lists available APs. Will try to connect when I get home and update

---

### Post by elemental666 on 2006-06-02
And she works, posting wirelessly on my home AP, no WEP or anything yet...

Here's a post that is pretty much what I did:

[http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

if you have ndiswrapper installed, deactivate it and remove it.  the bcm43xx works for the wpc54gs.  at least for me.

---

### Post by lakerssuperman on 2006-06-02
I finally got mine working using the fwcutter method instead of ndiswrapper.  I can see  all networks using the standard gnome network panel applet, i havent tried using network manager yet with this config

---

### Post by lynxus on 2006-06-02
[QUOTE=elemental666]And she works, posting wirelessly on my home AP, no WEP or anything yet...

Here's a post that is pretty much what I did:

[http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

if you have ndiswrapper installed, deactivate it and remove it.  the bcm43xx works for the wpc54gs.  at least for me.[/QUOTE]




WOW!!!
Great stuff. Thanks Sooooooo Much.
Worked PERFECTLY!!!!

This needs to be sticky or summat! :D

---

### Post by Anthem on 2006-06-05
I'm using that card with ndiswrapper, and haven't had any problems.

Other than installing it around Flight 4, I don't know what I did differently than you guys.  I'm sorry!

---

### Post by linuxa on 2006-06-09
I used ndiswrapper to get my WPC54G (v1.2, BCM4306) going on Breezy.

Also had some weird results when upgraded to Dapper recently. 

I start off trying to get the card working using the Network Settings that came with Dapper. It associated eth1 with the card, but couldn't get it to go after I had inputted all of the info.

I then turned to the latest version of ndiswrapper (v1.17) and followed the wiki for it just as I did for Breezy.

modprobe ndiswrapper went fine, but card was still attached to eth1. 

when I 
**ifup eth1 **
I always get: SIOCSIFFLAGS: No such file or directory

I tried modprobe -r for ndiswrapper, but it wouldn't remove it. Came across this thread (thanks guys). Issued the first two lines in the code snippet:
[B]
rmmod ndiswrapper 
rmmod bcm43xx     [/B]

It brought ndiswrapper down this time (weird?!).  modprobed ndiswrapper again. And THIS time my card got associated with wlan0.

Now it's up and running.

So I'm happy :D

EDIT: the linux kernal used by Dapper has bcm43xx drivers (for WPC54G) included. Which will be loaded at startup and interfere with ndiswrapper. if you want to use ndiswrapper, add a line to /etc/modprobe.d/blacklist **BEFORE** installing ndiswrapper:
**blacklist bcm43xx**
Your ndiswrapper should go unhindered this time.

In other words if you want to use the bcm43xx drivers that came with Dapper. follow the commands given in the earlier posts. If you want to use ndiswrapper instead, disable bcm43xx as outlined here.

---

### Post by jbolm on 2006-06-10
Thank you so much!  I was really having quite a time of it, but you explained this quite well, so that now I understand why it didn't work.  The internet connection is really quite important, and I was quite frustrated at not being able to access it from my ubuntu machine after upgrading to Dapper.  Thank you, again!  You people are wonderful.

---

### Post by linuxa on 2006-07-07
> **jbolm said:**
> Thank you, again!  You people are wonderful.

Aw, Shucks :D

Glad to be of help **jbolm**, and welcome to the forum.

---

### Post by hypnus on 2006-08-16
I am very close in connecting but are not able to get a real connection with exactly the same card 1.2, using ndiswrapper. (and samen ubuntu release)

When I try to connect my router(logging) sees my laptop(wifi-radar) <-> but no DHCP is done.  (router works, dhcp is configured properly)

Even with fixed ip the connection is not working!

Getting desperate, I feel that this shoud have something to do with some internal problem, but I do not know what, because I have no idea where to look.  In windows terms it looks like a BINDING problem..

Does anybody have any ideas?  (also did the blacklist tip)

> **linuxa said:**
> I used ndiswrapper to get my WPC54G (v1.2, BCM4306) going on Breezy.

Also had some weird results when upgraded to Dapper recently. 

I start off trying to get the card working using the Network Settings that came with Dapper. It associated eth1 with the card, but couldn't get it to go after I had inputted all of the info.

I then turned to the latest version of ndiswrapper (v1.17) and followed the wiki for it just as I did for Breezy.

modprobe ndiswrapper went fine, but card was still attached to eth1. 

when I 
**ifup eth1 **
I always get: SIOCSIFFLAGS: No such file or directory

I tried modprobe -r for ndiswrapper, but it wouldn't remove it. Came across this thread (thanks guys). Issued the first two lines in the code snippet:
[B]
rmmod ndiswrapper 
rmmod bcm43xx     [/B]

It brought ndiswrapper down this time (weird?!).  modprobed ndiswrapper again. And THIS time my card got associated with wlan0.

Now it's up and running.

So I'm happy :D

EDIT: the linux kernal used by Dapper has bcm43xx drivers (for WPC54G) included. Which will be loaded at startup and interfere with ndiswrapper. if you want to use ndiswrapper, add a line to /etc/modprobe.d/blacklist **BEFORE** installing ndiswrapper:
**blacklist bcm43xx**
Your ndiswrapper should go unhindered this time.

In other words if you want to use the bcm43xx drivers that came with Dapper. follow the commands given in the earlier posts. If you want to use ndiswrapper instead, disable bcm43xx as outlined here.

---

### Post by linuxa on 2006-08-18
hi **hypnus**. 

Have you tried disabling everything in your router and starting from there. E.g. DHCP, no Wireless security, broadcast ssid etc.

In other words, start with barebones configuration on the router. And as you get a connection on your laptop, tighten the connection criteria on router and set up the laptop to match.

Stop when you hit a point where the Router's config becomes too stringent for the clients on the wireless network to handle (this varies according to what your wireless card supports - it might even be possible that you will never hit that point if your card supports more feature than what the Router offers).

Tell us how it goes.

---

### Post by hypnus on 2006-09-01
Hello, 

Sorry for the late respons, I somehow missed this respons.

I used the fwcutter method, for the sake of those still looking in these messages this is what I used and works:

[http://www.ubuntuforums.org/showthread.php?t=185174](http://www.ubuntuforums.org/showthread.php?t=185174)

I am having good results with ubuntu, exept it hangs after a long standby, I am thinking this could be because of the wireless card hanging the computer, but have no proof and not testing at the moment..


I already tried with disabling all security on the router but it does not help...  IT just does not CONNECT with NDISWRAPPER in my case.  (it connects, but stops further negotiation)

Hopefully this helps someone else.

---

### Post by linuxa on 2006-09-03
**hypnus**, glad you got it working (regardless of method). I personally have problems with standby myself on Ubuntu, in that it simply does NOT work :p

Regards

---

### Post by Kodiak3000 on 2006-09-03
> **linuxa said:**
> 


EDIT: the linux kernal used by Dapper has bcm43xx drivers (for WPC54G) included. Which will be loaded at startup and interfere with ndiswrapper. if you want to use ndiswrapper, add a line to /etc/modprobe.d/blacklist **BEFORE** installing ndiswrapper:
**blacklist bcm43xx**
Your ndiswrapper should go unhindered this time.

In other words if you want to use the bcm43xx drivers that came with Dapper. follow the commands given in the earlier posts. If you want to use ndiswrapper instead, disable bcm43xx as outlined here.

Can I ask what might be a stupid question: how do I know whether I want to use the bcm43xx drivers or not? I don't know what they are; sorry.

I'd like to try this method, since nothing else I've tried has worked, but I'm a little scared to in case I mess up something I'll want later on...

Thanks

---

### Post by guest5 on 2006-09-03
i purchased this card because it is natively supported, and although it recognizes the card it doesn't start at boot.  i have to manually start the wireless service every boot.

anyone else have this problem, esp looking for the solution, of course.

---

### Post by linuxa on 2006-10-05
> **Kodiak3000 said:**
> Can I ask what might be a stupid question: how do I know whether I want to use the bcm43xx drivers or not? I don't know what they are; sorry.

I'd like to try this method, since nothing else I've tried has worked, but I'm a little scared to in case I mess up something I'll want later on...

Thanks

Not really a stupid question. 8) 

Just go with with works for you. I'm used to ndiswrapper, so I went with that. Not to mention I couldn't get bcm43xx going.

bcm43xx are the linux binary drivers for Broadcom 43xx wireless chipsets (the chip thats inside of your wireless card). This is the chip that WPC54G(S) uses.

It's up to you how you wanna go...

---

### Post by linuxa on 2006-10-05
> **guest5 said:**
> i purchased this card because it is natively supported, and although it recognizes the card it doesn't start at boot.  i have to manually start the wireless service every boot.

anyone else have this problem, esp looking for the solution, of course.

add the line:

**auto wlan0**

to your /etc/network/interfaces file (you'll need root access)

replace wlan0 with whatever device name assigned to your card.

---

