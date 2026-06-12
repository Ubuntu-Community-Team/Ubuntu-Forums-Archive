---
title: "upgraded to 9.10, wireless stopped working"
date: 2009-06-11
forum: Networking &amp; Wireless
---

### Post by Dj TweeX on 2009-06-11
i have run 9.10 before with the wireless working so i am not sure what is going on. it seems like ubuntu is just not recognizing my wireless card any ideas?

Hp Mini Netbook 1030NR 
1.6 Ghz Duel thread Intel Atom
1 Gb ram + 1 Gb swap*
16 Gb SSD (/home)
8 Gb JetFlash Flash drive (/)(*1 Gb Swap)

---

### Post by superprash2003 on 2009-06-11
post output of **lshw -C network**

---

### Post by Dj TweeX on 2009-06-11
```
gabe@Funky-Town:~$ sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 00
       serial: 00:22:64:6f:c8:d8
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A ip=192.168.1.108 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 72:7f:ff:fb:84:58
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

looking at it i can see my wireless card, but the system acts like its not there...

---

### Post by MaindotC on 2009-06-11
As you can see from the output, the driver being used is b43-pci-bridge.  Make sure it is loaded by posting the output of:
```

lsmod | grep b43

```
Also check to make sure this is the proper driver to use for your device.

---

### Post by marconeuro on 2009-09-07
Just Installed the latest daily build of 9.10, exactly the same error on dell mini 10v, same BCM4312, same error, no no wired or wireless network working. Any clue?

---

### Post by MaindotC on 2009-09-07
No one said anything about an error.  He said his card wasn't being detected.  Are you receiving any output that indicates an error?  Do you have the proper driver loaded?

---

### Post by ukozok on 2009-09-08
In case you found a solution to your problem please let me know as I am facing exactly the same problem. I have the same card on a Dell Inspiron. Many thanks,

---

### Post by MaindotC on 2009-09-08
Please follow the [Wireless Troubleshooting Guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide) and explain WHERE you are having difficulty.  I can't help you if you just say "I'm having the same problem."

---

### Post by Cuba71 on 2009-09-08
This link may have the answer to your Broadcom adapter

[http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices]("http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices")

---

### Post by onerbe on 2009-10-09
Hi 

I had the same problem when I updated to 9.10, and the only way to get the wireless working was set the DNS servers and search domains to manual configuration.

This is not a fix, but will help you to get wireless working until the final release.

Hope it helps!

Kind Regards

---

### Post by Larry Weber on 2009-10-29
I have a Dell 1521 wireless that worked beautifully under 9.1.  With the 9.10 upgrade the wireless quit.  Installing the Broadcom STA wireless driver DID NOT work initially.  The wireless troubleshooting sect 5.2.2 would not give any "claimed, unclaimed, enabled or disabled" indications. 5.2.7 IPv6 told me that aliases was NOT installed on my machine.

I uninstalled and reinstalled the Droadcom STA driver twice more and the second install worked.  Why, I don't know, but try re-installing the driver.

Larry

---

### Post by inforfang on 2009-10-30
i have same problem ... i use Dell Inspiron 1525 ... I install the lastest version of 9.10 . in 9.04 wireless worked fine , but in 9.10 stop working ...:(

---

### Post by levi99 on 2009-10-30
Same problem with the Dell Studio 1737.  Wireless worked great in 9.04, but am unable to connect in 9.10.  I have a Broadcom BCM4312 [14e4:4315].  On one of the previous links in this thread, it was stated this model was currently having drivers developed for it, but why did it work before and now it doesn't?

---

### Post by levi99 on 2009-10-30
This worked for me.  Hopefully it will help some of you:  [http://ubuntuforums.org/showthread.php?t=1288865](http://ubuntuforums.org/showthread.php?t=1288865)

---

### Post by vauge on 2009-10-30
> **levi99 said:**
> This worked for me.  Hopefully it will help some of you:  [http://ubuntuforums.org/showthread.php?t=1288865](http://ubuntuforums.org/showthread.php?t=1288865)

Thank you!!

---

### Post by ninjatiger422 on 2009-10-30
Another way is System > Administration > Hardware Drivers

Pick a driver and activate.

Don't forget to restart (it'll tell you this.)

---

### Post by Bebo Ariwo on 2009-11-03
Had the same problem after doing the upgrade from 9.04 to 9.10. I'm using an old Dell Inspriron 4100 with a Linksys USB wireless adapter (WUSB54G version 4).

Tried various solutions (eg searching for drivers for  the device), but none worked. 

Then I backed up my mail (Evolution) data, and files (via dropbox), and tried a fresh install from an Ubuntu 9.10 disk. 

That worked for me!

---

### Post by Al Soper on 2009-11-19
I was a completely new user to Ubuntu. Installed on a partition next to XP and everything worked ... apart from wireless !

Must of read and tried a hundred suggestions on the subject and I was clearly going round in circles. It got to the stage where I literally couldn't remember what I'd tried and what I hadn't. Started copying suggestions into a doc so I could at least be methodical. Finally got round to one which suggested installing wicd. This is actually a really friendly GUI alternative to Network Manger ... and it worked perfectly for me. Followed the instructions and ... bingo ! It now all works perfectly.

Excerpt from post is shown below. Apologies to whoever posted it as I didn't keep a record of their name. Like I said, I was getting desperate. After following the steps below, when I opened wicd (Applications/Internet/Wicd Network Manager), my network was shown and I just had to configure the connection under Properties button (put in the key for the router). I also had to set it to "WPA 1/2 (preshared key)" to get it to work (if you try this, you'll see what I mean

Original Post: (bold text is what I followed)

                                  [FONT=Arial Narrow][SIZE=3][COLOR=#000000]On Jaunty, Wicd is in the Universe Repository. To install: [/COLOR][/SIZE][/FONT] 
  [FONT=Arial Narrow][SIZE=3][COLOR=#000000]. First, reintstall network manager in case you wish to switch back.[/COLOR][/SIZE][/FONT]
[FONT=Arial Narrow][SIZE=3][COLOR=#000000]
 [/COLOR][/SIZE][/FONT] 
  [FONT=Arial Narrow][SIZE=3][COLOR=#000000]**sudo apt-get install -d --reinstall network-manager network-manager-gnome**[/COLOR][/SIZE][/FONT]
 
  [FONT=Arial Narrow][SIZE=3][COLOR=#000000]This will download the packages for network manager. If you don't do this, you won't be able to do it after you install wicd, because you may not have the packages available, and maybe you can't get the network working either. [/COLOR][/SIZE][/FONT] 
 
[LIST]
[*]**[FONT=Arial Narrow][SIZE=3][COLOR=#000000]sudo aptitude install wicd[/COLOR][/SIZE][/FONT]**[FONT=Arial Narrow][SIZE=3][COLOR=#000000]     [/COLOR][/SIZE][/FONT]
[/LIST]
  [FONT=Arial Narrow][SIZE=3][COLOR=#000000]Aptitude will attempt to remove network-manager and gnome-network-manager. Allow it to do so ... [/COLOR][/SIZE][/FONT]

---

### Post by mhansens on 2009-11-19
I am having a similar issue with my desktop.  I upgraded to 9.10 and wireless worked for a while and all was well.  Now I cannot connect to the AP.  The wireless card appears to work and can see different access points. I enter the WEP key for mine, but it never connects.  I have tried restarting the router.  Removing the AP entry and letting it rediscover.  Unplugged and reseated the wireless adapter (this is a linksys USB adapter - never had any issues before the upgrade.)  None of the other troubleshooting tips I have found have done anything.  Any ideas?

  *-network:1
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:0f:66:14:ea:7b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b

ifconfig output:
eth0      Link encap:Ethernet  HWaddr 00:1f:d0:d1:d9:19  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:27 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1440 (1.4 KB)  TX bytes:1440 (1.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0f:66:14:ea:7b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-0F-66-14-EA-7B-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by alextee on 2009-11-21
My wireless failed to work after I did a completely fresh install on my Acer 5720 laptop from an ISO image I burned to CD. 

I had previously been running 8.10 without any problems. I spent hours trying most of the fixes mentioned earlier and none worked for me.

By chance on my third fresh install I left a wired Ethernet connection plugged into my PC and wireless came up fully working when the install finished. On my previous installs I had no physical connection as I normally only use wireless.

To check I tried a fourth install without the cable and wireless failed. I then installed for a fifth and last time with an active physical Ethernet cable plugged in and wireless works.

---

### Post by RoboJ1M on 2009-11-25
Likewise, Ubuntu 9.10 UNR on a Dell Mini 10v with BCM4312.
Nothing in driver manager until we did an update over ethernet.
Then we had the choice of b43 and STA.
b43 didn't work, STA does (except for chnl 13, wpa1, etc, etc, grumble)

Should b43 work with this card? Ubuntu certainly *thinks* it should.

J1M.

---

### Post by spinnaker5 on 2009-12-03
And what about the atheros cards?I have a laptop with an ar5b91 card,works smotth under 9.04 and mint 7.when i install 9.10 or ,mint 8 ...it stops working after a few seconds.Best scenario i get nearly a minute.
Anyone any helpfull ideas?

---

### Post by spinnaker5 on 2009-12-04
in synaptic search for backports wireless,it might help you out.At least for me it did

---

### Post by dfritter4 on 2009-12-27
heres what i did to fix this problem on my Dell Inspiron 1720:

when i first installed 9.10, the wireless worked fine. it was only after applying the very first set of updates when it broke.

anyways, plug yourself into a wired ethernet, and simply re-install the "**network-manager**" package by going into the Synaptic Package Manger, doing a quick search for "network" and checking "network-manager" for re-installation.

if that doesnt work installing **wicd** will fix your wireless problems:

 [http://packages.ubuntu.com/jaunty/all/wicd/download](http://packages.ubuntu.com/jaunty/all/wicd/download)

(after installing that package, run an update check to get the latest version)

---

### Post by martinshort on 2009-12-31
hi...

i've done a lot of installation and re-installation of drivers and all kinds of network managers and wicd and whatnot. i can't make the driver for the broadcome to stop dropping packets. and it's freakin annoying cause slows up everything. 

what can i do to make it run smooth?!
[http://ubuntuforums.org/showthread.php?p=8564414#post8564414](http://ubuntuforums.org/showthread.php?p=8564414#post8564414)

---

### Post by jtpoole99 on 2010-01-01
I just upgraded to 9.10 and my wireless will disconnect from and when I try to reconnect it shows no wifi hosts.  When I right click on the network manager, I see that Wireless has been disabled.  Why is my wireless being disabled?  This is the 4th time this has happened since I've upgraded to 9.10.  Does anyone have any clue to why I'm being disconnected and then the wireless option of network manager is being disabled?  I would appreciate any help in fixing this issue.  Thanks in advance...

---

### Post by karthick ayyapillai on 2010-03-07
i upgraded to 9.1 version and the wireless stopped working for me .
I am using a siemens laptop I tried the following 
sudo apt-get update (with wired connection)
sudo apt-get upgrade
then chk the hard ware manager no drivers there 
then i tried for wicd using 
sudo -apt get install wicd i got wicd but still didnt work with wireless

I un installed it and re installed the gnome network manager still no hope 
i have also tried some other options like back port and broadcam drivers for wireless
when i type lspci in the terminal for the network it shows only atheros driver 
so am going for a fresh install now . Will let you guys know if i get the solution.

---

### Post by melelim on 2010-03-12
Hi, I have the same problem. I had the previous version of Ubuntu installed, and everything was working fine, then I upgraded to 9.10 and restarted, and boom, wireless is gone. Wasn't able to even ENABLE it.

After doing some searches, I've come across a "solution" that works. It's not a permanent fix, but it does indicate that the problem might lie with Ubuntu 9.10 rather than hardware setup. So this is how it goes:

1. Shutdown your computer (hopefully a laptop)
2. Turn off the wireless switch on the laptop
3. Reboot into Ubuntu 9.10
4. After the OS is loaded, only then turn on the wireless switch on the laptop.

I know it's not the best of solutions, but it's working for me.

---

### Post by Sleepallnight on 2010-04-26
Hi, I also have the same problem. However I don't know why after I changed my icons, the problem is gone. 

I also experience slowness if I boot 9.10 with my wireless on. Now its gone, before I have to switch it off first and then turn it on. 

Cheers,

PS: My current Icon theme is "Oxygen"

Edit 27th of Apr, 2010

Its not working again, its not the icons sorry...Probably it has something to do with where our laptop is located. Thanks

---

### Post by rquinter1324 on 2010-06-07
i need help i have a dell studio 1737 laptop pc i set it so it dual boots unbuntu or vista
and under unbuntu the finger print scanner wont work which for the work i do is a big deal and i cant find drivers for the internet i can only getinternet by way of ethernet cabl:confused:

---

