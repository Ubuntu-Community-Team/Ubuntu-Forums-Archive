---
title: "That Wireless Thang..."
date: 2006-02-24
forum: Networking &amp; Wireless
---

### Post by Griff on 2006-02-24
I've used Ubuntu for awhile on my PC, but just recently got it installed on my Compaq Presario 2100 laptop.  All is good except for the wireless.  What info do I need to get in order to begin the process of configuring the wireless?  I did a dxdiag and sent the file to my gmail acct so I would have a printout of all the physical data of this laptop.
I.E. I want wireless working, but am not sure of where to begin. ;)

---

### Post by ltmon on 2006-02-24
I have just gone through this process, but luckily was able to buy a wireless card that I knew was problem free in Ubuntu.  Hopefully you can have some good luck also.

First, go here: [https://wiki.ubuntu.com/WirelessNetworkCards](https://wiki.ubuntu.com/WirelessNetworkCards)

Try and find your wireless card model on the table there.  Also do a search on the wiki for your laptop model - there might be some good information from the laptop testing team.

Once you have this information post back.

L.

---

### Post by Griff on 2006-02-24
Well I have this: HP WLAN 54g W450 Network Adapter, which I got from my dxdiag file.  The command listed on that link to show the chipset either listed in in terms that I don't understand or it wasn't listed at all.  I'll post the results if you want it.  I know it's not detected under admin/networking.  Not sure if that means anything though.  I did a search for my comp and a similar pentium version was tested, but not the wireless.  So no luck there.  The only HP driver I saw was for a PCI card...  I'm not sure what to do from here.  Any guidance greatly appreciated.

---

### Post by ltmon on 2006-02-24
Well, at a guess I would say there are no native Linux drivers for your card.  This necesitates the use of 'ndiswrapper', which is a wrapper around the windows drivers making them usable by Linux.

The documentation for installing a driver with ndiswrapper is: [https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper)

Try following that, and see how far you can get.

L.

---

### Post by jasper24 on 2006-02-24
What model is the laptop? The card you are describing is most likely Broadcom, depending on how new it is. I am having a problem as well with mine, I have an HP dv8120.

Let me know, if you find a solution.

---

### Post by vincebelofte on 2006-02-25
Hai, Nice thread to begin with, I have an HP zv5000 laptop with an broadcom wireless. Ubuntu is recognizing that allright but it still doesn't work...so there's work to do today. :) 
I must say that my Linux experience is very modest but finding all the HOWTO's must give some idea...
I'll be back on this one

Vince

---

### Post by Griff on 2006-02-25
[QUOTE=jasper24]What model is the laptop? The card you are describing is most likely Broadcom, depending on how new it is. I am having a problem as well with mine, I have an HP dv8120.

Let me know, if you find a solution.[/QUOTE]
It's a compaq presario 2100 laptop w/ an AMD athlon XP 2000.  I can't find any other info within the computer, but I will continue the search tonight to figure something out.  I'll post back with more relevent data later.  Thanks all.

---

### Post by Griff on 2006-02-25
Yea, so appartently I needed to scroll down some more on the hardware list. :rolleyes: 
I've got a Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller.

---

### Post by jasper24 on 2006-02-25
You are now in the same boat as I am. My card is being acknowledged but can't be activated. I found drivers (windows based of course) by doing a search in google.com/linux for the model number. 

I know that it is *supposed* to work with ndiswrapper and people have successfully configured them, but I am not having any luck. 

You mentioned that you are running an AMD.....Is it by chance a 64-bit? (Turion, Athelon, etc) If so, I have the windows drivers and a howto for that. I picked them up a few weeks back on linuxquestions.org. Let me know if you could use them. I haven't tested them, because (even though I have a 64-bit proc) I am running 32-bit. At anyrate, I am going to continue working on mine as best I can and will let you know if I get anywhere. 

Goodluck,

Jasper

---

### Post by ltmon on 2006-02-25
I don't have a 64 bit machine myself, but it seems there are some subtle differences when using ndiswrapper on one.

See: [https://wiki.ubuntu.com/HowtoUseNdiswrapperOnAmd64Ubuntu](https://wiki.ubuntu.com/HowtoUseNdiswrapperOnAmd64Ubuntu)

L.

---

### Post by jasper24 on 2006-02-25
I'm going to breakdown and *try* to compile ndiswrapper and do it that way. I did find a few resources for the drivers and confirmation that the cards to work with ndis here:

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B)

Thought it might be useful.

---

### Post by Griff on 2006-02-26
Well, I found some drivers for my broadcom chipset but I still don't have wireless working.  I used arnieboys Automatix to install ndisgtk (a graphical frontend for ndiswrapper).  I used it and it looks like the hardware is detected, but it doesn't show up under system/administration/networking.  Hmmmm...
edit: My 100th post! Yay!

---

### Post by jasper24 on 2006-02-26
I just compiled ndiswrapper and used the bcmwl5.inf driver, reconfigured ndiswrapper, still nothing.

I'm starting to wonder if this driver is just not the right one (even though it's the one that came with it.)

I can see my card in network settings in KDE, just can't get it to enable. I have exhausted most of my options. At this point, I'm ready to beg for help.

iwconfig looks like this:

```
eth0      IEEE 802.11b/g  ESSID:"jasper"  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          Tx-Power=off
          RTS thr:off   Fragment thr:off
```

I am using the laptop now via ethernet, and that works just fine. 

This is what I get when I ifup eth0:

```
SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
Listening on LPF/eth0/00:14:a5:6a:48:d5
Sending on   LPF/eth0/00:14:a5:6a:48:d5
Sending on   Socket/fallback
receive_packet failed on eth0: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

I just did dmesg and noticed something, I think that is my problem:

```
[4296612.430000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[4296612.457000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available
```

It look like it's missing the driver file.....what is an "fw" file though? Isn't that fwcutter (which I cannot for the life of me figure out how to use.)

Any insight? Or help with using fwcutter.

---

### Post by jasper24 on 2006-02-26
Ok, i compiled and used fwcutter against bcmwl5.sys and now I have lights on my wireless..... THANK GAWD!

Although, I still can't connect (but it's trying) just need to do some tweaking and see why it's not connecting.

---

### Post by Griff on 2006-02-26
Ok.  This is what I've done.  Everything seems to be working.  I am picking up signals and all that jazz.  I'll find out for sure later when I go to the school and try to pick up the network there.

1. Got ndisgtk (graphical frontend for ndiswrapper) through arnieboys Automatix (it installs ndiswrapper-utils as well)

2. Got the Windows drivers from somewhere on the 'net (just did a google search for Broadcom BCM4306 blah blah).

3. Installed the .inf file for my chipset through ndisgtk

4. In terminal: ```
sudo modprobe ndiswrapper
```
That's it.  I think the only problem here is that 'sudo modprobe ndiswrapper' needs to be executed every time you log into a new session.
Thanks for the help everyone.  I'll continue to try to help anyone else here who is having similar problems, but my scope of knowledge for these kinds of things is very limited.

edit: went to school and jumped on the network with no problems!
edit: modprobe does NOT need to be executed for each session, so it's all good :)

---

