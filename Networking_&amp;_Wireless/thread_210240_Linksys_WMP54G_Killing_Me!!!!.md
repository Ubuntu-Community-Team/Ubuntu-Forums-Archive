---
title: "Linksys WMP54G Killing Me!!!!"
date: 2006-07-06
forum: Networking &amp; Wireless
---

### Post by steelspyder on 2006-07-06
Computer:  HP AMD64 X2 4200+, 2gb RAM, 250gb SATA HD (Windows XP Media Center), 300gb SATA HD (Ubuntu 64), Integrated Nvidia Video and Audio, Linksys WMP54G PCI Adaptor, Network has WPA security.

I do not have a wired connection to this computer.  Everything works fine in XP.

On one of the Ubuntu Hardware pages it is stated that this Linksys Card works "out of the box".  I can't seem to get it working at all.

When I try System->Administration->Networking... I see the device and it has a red "X" in the lower right corner of the icon.  When I click properties the computer freezes and I have to manually cycle the power.

When I give it the lshw command it shows *-network DISABLED.  I can't seem to enable the -network or get anything else working.

I have found several posts with wireless card issues and everyone has a different fix.  I haven't seen anyone with the *-network DISABLED problem.  I tried editing the /etc/network/interfaces file as was recommended by another post.  This caused my computer to not boot properly and I had to boot into recovery mode and replace the interfaces file with a backup I made.

Any help is greatly appreciated.  I am sick of switching my computer back and forth between Ubuntu and Windows so I can get on the Internet to try to find a solution just to switch back to Ubuntu and have it fail.

PLEASE HELP!!!!

---

### Post by diepruis on 2006-07-06
The problem with the WMP54G is that it has used at least 3 different chipsets accross various versions. The versions using the rt2500 chipsets are supported out-of-the-box (at least in theory). For the ones which use rt61, however, you have to install a few files. I had a hell of a time getting mine to work for this reason, as soon as I figured out what version it was it was as easy as following a simple howto.

Insert the CD that came with the card and navigate to its Drivers subfolder (or some such) there should be some folders in there. Please post those foldernames then I might be able to help you.

If you happen to know the version of your card, or would be able to find out that would be a great help.

---

### Post by steelspyder on 2006-07-06
Thank you dieprius for the reply.  I will look up the Driver foldernames when I go home tonight (I am at work right now).

Where would I go to find out what version of the card I have?  Is it on the box or do I have to query the properties in Windows somewhere?

Thanks again.

---

### Post by diepruis on 2006-07-06
No problem :)

I don't really know where to get that information. That's why it took me so long to find out which chip I was using. What gave it away for me was the folder names in the driver folder mine are "WMP54GV4.0" & "WMP54GV4.1". Inside the former was a file "rt2500.sys" and the latter had a file "rt61.sys". Since iwconfig picked up my card as RT61 and the RT2500 howtos didn't work for me, I concluded I must be running an RT61 chip.

Most pages lump all the WMP54Gs together or only report on the versions before 4.1, which complicated things a bit.

Come to think of it, you should post the .sys files contained in each of the directories under Drivers/* and your iwconfig output.

---

### Post by steelspyder on 2006-07-06
OK... I called home and had my wife look in the drivers folder.  She said there are 2 folders "wmp54gv4.0" and "wmp54gv4.1".

Hope that helps.

---

### Post by diepruis on 2006-07-06
You probably have the same problem as I did. When you get home have a look at your iwconfig output. If it reports your card as RT61 something then follow [this howto]("http://www.ubuntuforums.org/showthread.php?t=132980"). Solved it for me in no time. Let me know how it turns out.

---

### Post by steelspyder on 2006-07-06
In the "wmp54gv4.0" folder there is rt2500.sys.
In the "wmp54gv4.1" folder there is rt61.sys.

iwconfig:
ra0 RT61 Wireless ESSID:""
Mode:Auto channel:0
RTS phr=0 B Fragment thr=0 B
Link Quality:0 Signal level:0 Noise level:113
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

---

### Post by diepruis on 2006-07-06
This appears identical to the problem I had, visit the link I posted above, should fix the problem.

---

### Post by steelspyder on 2006-07-06
Thanks a lot for the help and quick replies.  I will get on this as soon as I get home.  Hopefully this will help me get online so I can get all the other updates I need to fix my other problems!!!

Thanks again.

---

### Post by steelspyder on 2006-07-08
I have tried 3 times now... No progress.  My box keeps freezing when I try to obtain IP from DHCP.  After reading the howto further I think my problem is that I have Ubuntu 64.

Has anyone got this to work with the 64-bit version.  If not I may switch to 32 until this issue is resolved.

Any help is greatly appreciated.

Thanks

---

### Post by adana on 2006-07-10
anyone else have trouble with the rt61 instructions?

I get the following error when running the "make all" step:


mypc@home:~/Desktop/rt61/RT61_Linux_STA_Drv1.0.4.0/Module$ make all
make -C /lib/modules/2.6.15-25-386/build SUBDIRS=/home/adana/Desktop/rt61/RT61_Linux_STA_Drv1.0.4.0/Module modules
make: *** /lib/modules/2.6.15-25-386/build: No such file or directory. Stop.
make: *** [all] Error 2

---

### Post by diepruis on 2006-07-10
[QUOTE=adana]make: *** /lib/modules/2.6.15-25-386/build: No such file or directory. Stop.[/QUOTE]

It sounds like you don't have the header / build files for the kernel you're using.

Try doing ```
sudo aptitude install kernel-headers-'uname -r'
sudo aptitude install kernel-build-2.6.15-25
```

More importantly, if you're running the current version of Ubuntu (version 6.06 Dapper Drake) then you don't need to do that bit, skip to the section that says "rt61 in Dapper". If you're running Breezy then you are on the right track and I apologize.

[QUOTE=steelspyder]My box keeps freezing when I try to obtain IP from DHCP. After reading the howto further I think my problem is that I have Ubuntu 64.
[/QUOTE]

I had the same problem when I tried (unsucessfully) to upgrade my kernel.. It has to do with the drivers not being properly installed. In other words, I think it might very well be a problem with the 64 bit version. 32 bit ought to work. *keeps fingers crossed*

---

### Post by adana on 2006-07-10
Thanks for the response!

Yes, I have  dapper and it looks like rt61.ko is aleady present:


sudo find . -name rt61.ko
Password:
./lib/modules/2.6.15-23-386/kernel/drivers/net/wireless/rt2600/rt61.ko
./lib/modules/2.6.15-25-386/kernel/drivers/net/wireless/rt2600/rt61.ko


I have followed the other instructions but I don't think the system is picking up the info I have put in /etc/Wireless/RT61STA.
[B]
iwconfig returns the following:[/B]

ra0       RT2500 Wireless  ESSID:""
          Mode:Managed  Frequency=2.412 GHz  Bit Rate:11 Mb/s   Tx-Power:-2 dBm
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-120 dBm  Noise level:-206 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


How can I tell if the rt61.ko driver has loaded?

---

### Post by diepruis on 2006-07-11
> **adana said:**
> How can I tell if the rt61.ko driver has loaded?

Err... I don't think your card uses the rt61 chipset. In fact it appears to be using the rt2500 one.

> **adana said:**
> 
ra0       RT2500 Wireless  ESSID:""


See that line that says RT2500? That's the chipset you're using. Are you sure it's not already working? If you're running a DHCP server on your router (see router documentation) you can try to just type

```
sudo dhclient ra0
```

wait for it to complete (there should be a line like "bound to 10.0.0.3") then test it by typing

```
ping 4.2.2.2
ping www.google.com
```

---

### Post by adana on 2006-07-11
ah, that explains some things. Sorry, after reading so many posts about wireless problems, I got confused about what drivers go with what chipsets.

I have tried the DHCP command (I do have DHCP, not a static ip), and it runs but doesn't get an ip. I assume I don't have my SSID,PSK info in the right place since /etc/Wireless/RT61STA doesn't apply to me.

From other posts, it seems /etc/network/interfaces is the right place?

I will try it.

---

### Post by diepruis on 2006-07-11
Yup, that would be the right place to start. Avoid the graphical configuration tools, they seem broken to me. If you have further problems please post /etc/network/interfaces and I'll see if I can help you.

---

### Post by IronGryphon on 2006-07-11
Try the solution in this post, it worked for me without installing anything. 

[http://ubuntuforums.org/showthread.php?t=75448&page=4](http://ubuntuforums.org/showthread.php?t=75448&page=4)

---

### Post by adana on 2006-07-12
Thank you everyone for your continued support!


Well, here is what I added the the /etc/network/interfaces file (I have left out my ssid and pks):


# for wireless
auto ra0
iface ra0 inet dhcp
        pre-up ifconfig ra0 up
        pre-up ifconfig ra0 down
        pre-up ifconfig ra0 up
        pre-up ifconfig ra0 down
        pre-up iwconfig ra0 essid "<ssid>"
        pre-up iwconfig ra0 mode Managed
        pre-up iwpriv ra0 set AuthMode=WPAPSK
        pre-up iwpriv ra0 set EncrypType=TKIP
        pre-up iwpriv ra0 set WPAPSK="<my key>"
        pre-up ifconfig ra0 up


Does this look correct?  I am not getting a successful connection. 

I have seen some posts indicate that the PSK must be entered in hex rather than ASCII. I have tried both.

Here is the output of  **sudo ifup ra0**

$ sudo ifup ra0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/ra0/00:0f:66:73:e3:6a
Sending on   LPF/ra0/00:0f:66:73:e3:6a
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Any ideas?

---

### Post by adana on 2006-07-13
anyone?

---

### Post by diepruis on 2006-07-14
Sorry for the late reply - classes. You could try the raLink configuration tools. Otherwise that file seems fine.

EDIT: Please try and connect with security disabled on the router, if you can do that we know we're doing something right.

---

### Post by wieman01 on 2006-07-14
If I were you, I'd try NDiswrapper together with the native Windowns driver for your card. I had so many issues in connection with my "wusb54g v4" that I decided to go for the "ndiswrapper" solution which works flawlessly even with WPA2 (RSN).

The RTxxx drivers are a real hassle according to my experience. If you were using NDiswrapper and wpa-supplicant v0.4.8 (default in Dapper), I could help you with network encryption & authentication (WPA / WPA2).

I experienced that "ndiswrapper" is the easiest way to go... Others may disagree with me here.

---

### Post by neveceral on 2006-07-14
> **wieman01 said:**
> If I were you, I'd try NDiswrapper together with the native Windowns driver for your card. 
for rt61 chipset don't use driver that ships with card, it didnt work with ndiswrapper.
look here [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#L](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#L)

---

### Post by wieman01 on 2006-07-14
Well, I cannot see why it should not work. I would try because the latest native Windows driver might be ok. 

Try it out first, then ditch it. It is worth it. That's what they said about the driver for "wusb54g v4" as well but eventually it turned out to be no problem at all.

---

### Post by diepruis on 2006-07-14
Okay, now I have more time to reply. The posters above me have a good idea. I've heard of many people's problems being solved this way. Here's [a link]("http://ndiswrapper.sourceforge.net/") to the ndiswrapper homepage for reference. And here's a link to a (somewhat outdated) [howto]("http://www.netdigix.com/downloads/debian-linksys-wireless-howto.html") on getting the Linksys WMP54G to work on Debian. Since Ubuntu is based on Debian it might work. You might want to search for a more up to date howto on this forum.

You could also try the open source rt2500 driver. I seem to remember that raLink is working with the open source community to develop it. Anyway, you can find that [here]("http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page"). I don't have a howto for that one though, search their wiki or the ubuntu forums. (Note: when I checked their server was down.)

I haven't tried these solutions, however, so I will be pretty much unable to help you. Someone will know what you have to do however. Keep trying :)

---

### Post by ravindran.k on 2006-07-27
Hello Guys..

I have wmp54G 4.1 RT61 based. I have tried Ndiswrapper with the windows drivers.. A few mins after loading the driver and trying ifconfig wlan0.. I get a driver crash.. when I see dmesg..I can see that it is related to a IRQ setting..(I think I shared IRQ 11 with various devices) and mentions to use pollirq option while booting. I tried and the results are same. I suspected some kind of conflict and removed the tv tuner card. No change. changed the pci slot ..no change..Will post the exact error soon. Meanwhile, planning to use the latest beta rt61 driver but need to confgure the kernel header..Will try and let you know.

Regs
Ravindran

---

### Post by diepruis on 2006-07-27
You should probably post this in a separate thread. You have a sperate problem and most people will be disinclined to read 50 odd posts to get to your problem. Trust me, that way your post won't be lost in the background noise.

---

