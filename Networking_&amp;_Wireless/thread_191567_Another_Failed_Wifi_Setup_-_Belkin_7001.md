---
title: "Another Failed Wifi Setup - Belkin 7001"
date: 2006-06-07
forum: Networking &amp; Wireless
---

### Post by Blind-Summit on 2006-06-07
I run a dual boot with XP Media - wifi is fine here.

I had 5.10 working with ndiswrapper / ndisgtk and the wifi was totally fine.

I downloaded the 6.06 torrent -> burnt iso to DVD and verified the disk was ok. All good so far.

Tried to then install the ndiswrapper and ndisgtk to get the net up to help install more packages etc etc as you do. Both deb files failed to install. I grabbed the latest versions from my XP boot and set them to a USB key drive and installed. loaded the drivers up as I did with 5.10 and they appear. The network confog sees the card as a wireless network but I can't use it. It doesn't see the wifi ssid and hence won't connect.

I ran through several topics / help guides on this section, but none helped. Here are some commands I ran through and the output from each. 

```
sudo lshw -businfo

pci@01:07.0     eth2       network     BCM4306 802.11b/g Wireless LAN Controller



sudo lshw -C network


  *-network DISABLED
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 7
       bus info: pci@01:07.0
       logical name: eth2
       version: 03
       serial: 00:11:50:3d:74:7d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.15-23-386 link=no multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:de000000-de001fff irq:217




lspci -v

0000:01:07.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
        Subsystem: Belkin Belkin F5D7001 High-Speed Mode Wireless G Network Card        Flags: bus master, fast devsel, latency 239, IRQ 217
        Memory at de000000 (32-bit, non-prefetchable) [size=8K]




blind-summit@Blind-Summit:~$ sudo dhclient eth2
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
Listening on LPF/eth2/00:11:50:3d:74:7d
Sending on   LPF/eth2/00:11:50:3d:74:7d
Sending on   Socket/fallback
receive_packet failed on eth2: Network is down
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 6
send_packet: Network is down
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 6
send_packet: Network is down
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 8
send_packet: Network is down




blind-summit@Blind-Summit:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11b/g  ESSID:"Ethereal"  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth1      no wireless extensions.

sit0      no wireless extensions.
```


Could someone please please help as this is the only really critical thing I need working. The rest I can sort out mysef once the net is back

Thanks

Alex

---

### Post by nzruss on 2006-06-07
Try ifup command:
```

sudo ifup
sudo iwlist eth2 scan

```

Also, Have you checked your interfaces file? Is your eth2 commented out? (commented with # a the start of the line), try commenting out all those but the ones you are using.  Check your interfaces file by:
```

sudo gedit /etc/network/interfaces

``` 

Then try 
```

sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo iwlist eth2 scan
sudo ifup

```

Any luck?

---

### Post by Blind-Summit on 2006-06-08
:-k no luck so far.

I did a clean install as it would give me better grounds to start on. I have a copy of ndiswrapper-utils_1.8-0ubuntu2_i386.deb and ndisgtk_0.6-0ubuntu1_all.deb and also the bcmwl5.inf, bcmwl5a.inf and the bcmwl5.sys files from the instal cd for my belkin wifi card.

If it makes any difference, I have dual onboard LAN (etho and eth1). Here are the results of the commands after a clean install:


blind-summit@blind-summit:~$ sudo ifup
ifup: Use --help for help



blind-summit@blind-summit:~$ sudo iwlist eth2 scan
eth2      Interface doesn't support scanning : No such device



blind-summit@blind-summit:~$ sudo gedit /etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

The others failed because of the ndiswrapper etc not being installed. I fired up the packages and installed those and here are the same commands:

blind-summit@blind-summit:~$ sudo rmmod ndiswrapper

blind-summit@blind-summit:~$ sudo modprobe ndiswrapper

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-23-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

blind-summit@blind-summit:~$ sudo iwlist eth2 scan
eth2      Interface doesn't support scanning : No such device


I assume fatal = bad! I can't see why it was OK in 5.10 with ndiswrapper and not in 6.06. I hear that it now comes with a default wifi driver? Perhaps this is something strange.

Finally - why is it now eth2 and not wlan0 ? 

Thanks for helping me out nzruss

---

### Post by ComplexNumber on 2006-06-08
for some reason, i got my belkin rt2500 working without typing anything in network manager. it seems to do so on tis own accord. i have wifi-radar installed too, but that comes up with similar errors to what you're saying (eg  eth2      Interface doesn't support scanning : No such device). however, it still works and i can successfully access the internet. some questions:
-have you installed the drivers by placing both the sys and the inf files in the same directory and typing 'ndiswraper -i bcmwl5a.inf'?
-have you run 'modprobe ndiswrapper' each and every time you log in? if not, do so by adding the command to /etc/rc.d/cd.local(?). this is necessary
-have you gone into firefox and disabled IPv6? if not, go into firefox and type 'about:config' in the address bar. then do a search for v6 and set it to true. otherwise, firefox won't resolve names such as [www..](www..)...
-you may need to switch wpa_supplicant OFF

---

### Post by Blind-Summit on 2006-06-08
I did a clean install but nothing came up. It detected the card as wireless but it doesn't see the SSID - I know the router et al is ok because I have a dual boot with XP (using it now!) and that runs perfectly with a good link connection. The card also ran fine with 5.10 with the ndiswrapper.

I stuck the two deb files, the two inf files and the sys file in the same folder - I will remove the inf files and try again just to be 100% sure but I am certain that they were in the same place.

I ran this modprobe but I'm new to all this Linux / Ubuntu so I don't understand it or how to see if it did anything. I remember there were no errors, but also no wifi! I've not done the mozilla fix yet, but I noticed under network tools that it was there along with the loopback interface (and this wasn't in 5.10 as far as I remember) - I'll give it a shot and will post the results.

Getting it to work is so vital as I'm also trying to fix my dual screens and to also get some sound setup properly :-k 

Thanks for your help - I will post the results here in a sec

Alex

---

### Post by ComplexNumber on 2006-06-08
> I stuck the two deb files, the two inf files and the sys file in the same folder - I will remove the inf files and try again just to be 100% sure but I am certain that they were in the same place. just type 'ndiswrapper -l'(the lower case letter L) to see if they're installed or not.

cheers.

---

### Post by Blind-Summit on 2006-06-08
Yeah, they both appeared. I installed the ndisgtk and loaded them from there. I also tried directly from ndiswrapper with the -i command. They loaded but same problem.

does the var/network/interfaces have anything to do with it? (var or /etc - I forget)!

---

### Post by ComplexNumber on 2006-06-08
>  does the var/network/interfaces have anything to do with it? (var or /etc - I forget)! no idea. don't bother going in there.i don';t think its necessary - i never did.

btw did you mention that you have placed 'modprobe ndiswrapper' statement in the etc/ec.d directory? thats something that you'll have to do.

the  bulk of the work in getting it to successfully connect to the internet seems to be done by network manager and network manager supplicant behind the scenes. i don't think its even necessery to enter any info in the GUI, because i haven't tryped any info about what driver i'm using or anything. it didn't even have ndiswrapper present after i'd selected 'wirelesss card'. it just had 'other network card'. so i ngave up on it. i entered the details using a package called wifi-radar, but that doesn't seem to do much (or maybe it did).
its also a few other little tips such as the IPv6 thing with firefox and switching OFF wpa_supplicant service.

---

### Post by Blind-Summit on 2006-06-08
I've not added the line to the etc/ec.d yet - I will add it.

I can't sem to instal network manager as that needed me to download a load of stuff from the repositories and clearly this is hard to do with no wifi connection. I can grab it all from my XP boot but there seems to be a load of dependency files.

The router broadcasts the wifi with no security - I know this is bad, but I live in the middle of nowhere and not likely to have people steal my connection!

Run me through what I should do then. I have my 6.06 DVD (i grabbed the iso from a torrent and only had a DVD-RW to hand!) and I have XP boot for the net should I need to download anything.

You'll have to write commands out for me as I'm not to hoot on that.

Thanks for sticking with me on this - most appreciated :)

---

### Post by ComplexNumber on 2006-06-08
is it possible for you to download it and the dependencies manually from the repositories, burn them to a multisession disk? thats what i did on fedora core before i had an internet conenction to it. thats why i can't use ubuntu because it doesn't supply the distro on more than 1 disk as fedora does.

---

### Post by Blind-Summit on 2006-06-08
I can get hold of the network manager and the dependency files and put them on a FAT32 shared drive (can read / write from XP and Ubuntu) if that's any use? Or do you mean get Ubuntu 6.06 and the files all on one DVD? (I ran out of CDR's!)

Alex

---

### Post by ComplexNumber on 2006-06-08
[quote=Blind-Summit]I can get hold of the network manager and the dependency files and put them on a FAT32 shared drive (can read / write from XP and Ubuntu) if that's any use? Or do you mean get Ubuntu 6.06 and the files all on one DVD? (I ran out of CDR's!)

Alex[/quote]
then copy them over using drag and drop onto your linux partition. if you can't see the windows partition from linux, see the thread that aysui wrote on how to rectify that. it should be a 'pychocats' thread. i can't remember extactly.

---

### Post by Blind-Summit on 2006-06-08
Give me a few days! I just tried to do the same for some nvidia drivers (because I am not online under dapper - I tried to get them manually) it depends on about 20 files - and then these depends on loads more:

[http://packages.ubuntu.com/dapper/net/network-manager-gnome](http://packages.ubuntu.com/dapper/net/network-manager-gnome)

I may actually cry

---

### Post by ComplexNumber on 2006-06-08
>  I may actually cry
i know the feeling ;). i've been there.

---

### Post by Blind-Summit on 2006-06-08
OK, I plugged everything into damn long leads and I have internet over my lan. 

What do I need to grab to install that network manager?

sudo apt-get network-manager? I don't think I have all the right repositories - I checked them all :S

---

### Post by ComplexNumber on 2006-06-08
yeah, something liek that. i never use the command line for software. i've always used a GUI. try smart or synaptic

---

### Post by Blind-Summit on 2006-06-08
I got it installed and although I don't see it in my Applications -> Internet menu - it is in the taskbar bit up the top of my screen. The LAN connection showed up fine and connected instantly - but the wifi SSID was not displayed at all. The wireless list was empty. I tried to connect to my SSID by manually entering in the name - but nothing semed to happen. Perhaps it took a while for the DHCP to give me an IP - but I doubt this is the case  -> the other network config is just the same -> can't see the SSID

:(

---

### Post by ComplexNumber on 2006-06-08
good stuff ;). glad you've got it connected. i'm surprised the name of the network doesn't show up. i can't see any reason why it wouldn't.
i found it very temperemental. it would work sparodically. but now it works evertime i log in. i can't understand it :confused:. when it was working sparodically, i found really difficult to isolate the exact actions of what i was doing right. success seems to be largely an accident when it comes to getting wifi to work

---

### Post by TheWorldJoker on 2006-06-08
Alternate method (I solved this same problem not even 5min ago):

Find driver bcm43xx.ko, delete it (or rename it, such as bcm43xx.ko.bak).  Then restart the computer, log in, and use ndisgtk to install the Windows driver normally.  

Now everything works for me just like it did in 5.10.

---

### Post by Blind-Summit on 2006-06-09
[QUOTE=ComplexNumber]good stuff ;). glad you've got it connected. i'm surprised the name of the network doesn't show up. i can't see any reason why it wouldn't.
i found it very temperemental. it would work sparodically. but now it works evertime i log in. i can't understand it :confused:. when it was working sparodically, i found really difficult to isolate the exact actions of what i was doing right. success seems to be largely an accident when it comes to getting wifi to work[/QUOTE]

Noooo - It works because I plugged my router upstairs, ran the phone line into my mums room and plugged a network cable into my PC - I couldn't face grabbing all those files under XP - there were going to be hundreds!! I plugged the LAN in so that I could get a few packages and then try and fix the wifi as normal.

It's still not working but I will try your idea TheWorldJoker - any idea where that file is?

Thanks :)

---

### Post by Blind-Summit on 2006-06-09
[QUOTE=TheWorldJoker]Alternate method (I solved this same problem not even 5min ago):

Find driver bcm43xx.ko, delete it (or rename it, such as bcm43xx.ko.bak).  Then restart the computer, log in, and use ndisgtk to install the Windows driver normally.  

Now everything works for me just like it did in 5.10.[/QUOTE]


damn and blast. I made a copy called bcm43xx.old and then deleted the original. Now it won't boot - just hangs on the "configuring networks" bit.

I tried to boot to recovery mode to restore the file, but I get:

modprobe[3974] exited with preempt_count 1 and just stops!

Heeeeeelp!

---

### Post by Blind-Summit on 2006-06-09
Right - dunno what went wrong there. I used Ctrl + C to ignore the network configuration on boot. I restored the driver to .ko from .old and rebooted.

Also tried the blacklist then install of the ndiswrapper with -i xxx.inf etc but nothing again

I'm now back to square 1 - wifi not working, removing the bcm43xx.ko doesn't work, and neither does the blacklisting

Why is this so difficuly in 6.06 yet 5.10 was so very easy and I had it setup in a few seconds!!!

Please - surely someone can help get this working

---

### Post by Blind-Summit on 2006-06-11
Does anyone have any new / better ideas?

Where csn I get paid support for this because NOTHING I have read or tried on the forums has worked at all. 

This is getting too silly now

---

### Post by Blind-Summit on 2006-06-13
OK, so I looked into the problem a bit more.

Most Belkin cards use the broadcom chipset, apart from some linux specific cards that use the RaLink chipset (open source lovlies!) What puzzles me is that the stock Ubuntu driver seems to be aimd at the broadcom chipset - yet my card still won't work with it.

Surely someone knows a decent fix for this?

---

### Post by Notclive on 2006-06-25
I have the same card as you (i think belkin f5d7001?) and cant get it to work. Where was the bcm43xx.ko file and how can i delete it?

also you know on this page [http://packages.ubuntu.com/dapper/net/network-manager-gnome](http://packages.ubuntu.com/dapper/net/network-manager-gnome) you made it sound as if u downloaded each file seperatly. If you did you could have gone to the botom where it says Download network-manager-gnome and clicked on amd64, i386 or powerpc.

---

### Post by rengolin on 2006-07-28
[QUOTE=Blind-Summit;1111190]:-k no luck so far.

blind-summit@blind-summit:~$ sudo modprobe ndiswrapper

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-23-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument



Could you make ndiswrapper work ? Even removing bcm43xx I still have this message (so rebooting won't be any good). Every thing I did was to install using ndiswrapper -i inffile and modprobe ndiswrapper, should I have done the opposite ? Should I remove all ieee802.11 stuff before loading ndis ?

cheers,
--renato

---

