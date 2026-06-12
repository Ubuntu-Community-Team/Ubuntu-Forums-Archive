---
title: "Gigabit ethernet Realtek RTL8169 too slow"
date: 2006-03-13
forum: Networking &amp; Wireless
---

### Post by al108 on 2006-03-13
Hi, 
I've got RTL 8169 network card installed in hopes to speed up my  server with Gigabit ethernet, but transfer speed still the same as with 100 Mbps ethernet.
The switch recognizes it as a 1000 Mbps. I tryed directly connect to my workstation but it was still the same. Realtek diagnostic utility for Win say the cable is OK, and the card works as expected in Win twice as fast without switching to jumbo frames. It's still not a 1000 Mbps but faster than 100 Mbps anyway. I've  tryed a Realtek driver r1000 and it did install, but I'm not sure if it actually loads.

I've did some searching and reading last couple of days, and some people made it work somehow (or not?) but they didn't provide any detailed explanations. Default r8169 driver  recognizes the card as a Gigabit card but still slow. Other posts suggested that there is a bottleneck in kernel...

Any ideas on how to fix this? Or at least what to try?

Thanks
Alex

---

### Post by Stormbringer on 2006-03-13
> ...but transfer speed still the same as with 100 Mbps ethernet.

Got the same problem with my onboard 8169 NIC ... transfers are en par or worse as with 100MBit. Couldn't find any solution so far ...

> I've tryed a Realtek driver r1000 and it did install, but I'm not sure if it actually loads.

To check if the r1000 module is loaded simply check with lsmod:

Open a terminal:

# lsmod | grep r1000

Output should look like this:
r1000                  16064  0

Now, let's find out if r8169 is loaded as well...

# lsmod | grep r8169

If it is loaded then there's the chance that r8169 has grabbed the NIC ... however, you can force r1000 to be used by a small "hack".

# sudo mv /lib/modules/`uname -r`/kernel/drivers/net/r8169.ko ~/
This will move the r8169 kernel module into your home directory.

# sudo depmod -a
Rebuild the kernel module dependencies.

# sudo mv /boot/initrd.img-`uname-r` /boot/initrd.img-`uname -r`.ubuntu
make a backup of the original initrd.

# sudo mkinitramfs -o /boot/initrd.img-`uname -r` `uname -r`
Create a new initrd WITHOUT the r8169 module

# sudo gedit /etc/modules

Add "r1000" (without the quotes) at the end of the file.

Save the file.

Upon reboot you are using r1000 for sure as there's no more r8169.

I'm sure the same goal may be accomplished by blacklisting r8169 somewhere in the config of hotplug --- haven't worked myself into this yet.

Now try and see if you see any improvements ...

[EDIT]
If you are curious you may find some output from the module in /var/log/dmesg - looks like this:

```

[   67.280895] eth0: Identified chip type is 'RTL8169S/8110S'.
[   67.280902] eth0: r10001.0, the Linux device driver for Realtek Ethernet Controllers at 0xd800, 00:0c:76:96:a5:64, IRQ 16
[   67.322309] eth0: Auto-negotiation Enabled.
[   73.642947] eth0: 1000Mbps Full-duplex operation.
[   73.642950] Realtek RTL8169/8110 Family Gigabit Ethernet Network Adapter
[   73.642952] Driver version:1.0
[   73.642953] Released date:2005/12/30
[   73.642955] Link Status:Linked
[   73.642957] Link Speed:1000Mbps
[   73.642959] Duplex mode:Full-Duplex
[   73.642960] I/O Base:0xD800(I/O port)
[   73.642962] IRQ:16

```

[/EDIT]


--- Undoing the changes:

# sudo gedit /etc/modules
Remove the "r1000" line and save the file

# sudo mv /boot/initrd.img-`uname -r`.ubuntu /boot/initrd.img-`uname -r`
Restore the original initrd

# sudo mv /lib/modules/`uname -r`/kernel/drivers/net/r1000.ko ~/
Move the r1000 module to your home directory

# sudo mv ~/r8169.ko /lib/modules/`uname -r`/kernel/drivers/net/
Move the r8169 module back to where it belongs.

# sudo depmod -a
Rebuild the module dependencies.

Reboot.

---

### Post by jwd45244 on 2006-03-13
Using Gibabit NICs requires changes to the Frame size to take best advantage of this new potential bandwidth.  Also, if this is an old machine, the system bus can easily be outrun by gigabit NICs.

You did not describe the other equipment involved, switches, cabling, other computers.  There are plenty of places where these could easily be the bottleneck that would prevent fuller usage of the new bandwidth.  

You also did not say how you measured the bandwidth.

---

### Post by dpickle on 2006-03-13
hi dont know if this helps but at ubuntu startup it says something like rltek 8169 drivers loaded...error in confiutation use 8139 drivers instead...all this info goes by really quickly so i didnt catch it or remember it until i read this thread ....het it rhymes::P Anyway try that.....dont have any idea how to load the 8139 drivers but ill bet that is your problem.:-D

---

### Post by al108 on 2006-03-13
Thanks for all the info. That sounds like what I was  looking for.
Unfortunately I won't be able to try it till tomorrow, I have to be at work overnight.

This is not a very fast machine, but should be able to handle a little more bandwidth. I have a CeleronD 2.66GHz CPU with some cheap VIA motherboard Ubuntu 5.10 AMD64 generic kernel, 5 HDDs - one IDE for a system drive, and four SATA in RAID5 setup using mdadm. the NIC is a Hawkin brand. Cables are Cat 5e with the longest of 50'. Switch is a linksys EG008W. On the other side is a AMD64x2 4400 with Abit NF4 Ultra Ubuntu, Gigabit card  onboard, Ubuntu i386-smp kernel. I have other computers at 100Mbps and a network printer hooked up to a linksys WRT54G router and a couple of wirless connections. 

For the most part I had a 4GB file copied to and from the server and it takes about 7.5 min over a 100Mbps network. While in Win it takes about 3.5 min with 1500 mtu. Almost same results with computers connected directly without switch. Same file transferred from an external USB drive takes about 1.5 min. Haven't tryed jumbo frames yet as I'm not sure of mixing different frames on the same network.

Yep, I figured out that r8169.ko should be removed from /lib/modules/`uname -r`/kernel/drivers/net but didn't know about making new initrd.

I hope this works.
Thanks

---

### Post by al108 on 2006-03-14
Well the elimination of r8169 in initrd went pretty easy. Copying from workstation to server is under 3min for a 4GB file, copying from server to workstation still slow... switched to a different cable and now it works both ways. Even though the cable was "good" (all conections are present) but swithching to a different cabel proved otherwise. I wasn't able to switch r1000 to any differnt mtu other than 1500, so I'll probably be looking at getting a D-link or MarvelYukon based card which reportedly can support mtu upto 9000.

You learn something everyday.

---

### Post by Stormbringer on 2006-03-15
Hi al108, glad you got it to work.

Support for Jumbo-frames seems to be commented out in the source of r1000.c ... so you may really be better off with a different NIC.

However, keep in mind that you cannot talk to 10 or 100mbps devices anymore when you enable jumbo frames.

I would love to do so, but my printer is attached to the network and because it has a 100Mbps network card built in that's no option.

@dpickle:
r8139: this is the driver for the Realtek RTL8139 series (100Mbps NIC).
r8169: this is the driver for the Realtek RTL8169(S)/8110(S) series (**1000Mbps NIC**)

In no way one can use r8139 to operate a RTL8169(S)/8110(S) or the other way around.

Storm.

---

### Post by al108 on 2006-03-15
Yeah, I thought I did, but it was not the cable. I went and bought  another cable and it did work just like the old one - for some strange reason it transfers at a 100 Mbps one way and 200 Mbps the  other way. Rebooted to Win on  the server side and it does 200 Mbps both ways(ranges from 100 to 250 with average of about 200 judging by Realtek utility). So it's not the cable. I did order new cables though and 2 D-link cards. I could connect the server and my computer at 1000Mbps with jumbo frames directly, and running a second cable from the server at 100 Mbps to the router for everybody else. This way also I won't need a switch which has a very noisy and annoying fan.

If I have time I'll try a 32 bit kernel on the server and see if that makes any difference with Realtek.

Storm or anybody do you know why is it slow one way and fast the other way?

Thanks for help, though I may need it again with D-link.

---

### Post by Stormbringer on 2006-03-15
In this case you are at the same point as I am ... I'm stuck having no more ideas what still could be done to improve transfers. The only difference from my situation is that you're getting faster transfers from the server to the client.

> If I have time I'll try a 32 bit kernel on the server and see if that makes any difference with Realtek.

Good idea, but I doubt that you're going to see any improvements because...

Server (CentOS 32-Bit, Kernel 2.6.15-cks, r1000) -> Windows Workstation (WXP, Netgear GA-302T) ... max. 12-17MB/s
Windows Workstation -> Server ... max. 7-12MB/s

AMD64 Workstation (Breezy, r1000) -> Server ... max. 4-9MB/s
Server -> AMD64 Workstation ... max. 4-7MB/s

AMD64 Workstation -> Windows Workstation ... max. 4-7MB/s

The transfer speeds aren't stable, they go up and down as they feel like it.

I tested the throughput by copying Breezy's DVD ISO-Image via SSH (SCP) several times between the systems. I even doen't look any better by using CIFS, SMBFS, NFS or whatever.

And I already did the same steps as you did...

- changing cables (PatchSee cables - they got tested with a Fluke Cabletester to ensure they are fine and meet CAT6)
- replacing the switch
- using a x-over cable
- running a live-cd instead of installed system
- tweaked around in /proc

The only thing I haven't tried so far is to...

- install Windoze on my AMD64 rig
- create a customized BartPE Boot CD to boot my AMD64 rig from

Oh well ... I guess I'll try to create a BartPE CD with Realtek drivers included to see if it operates faster.

Storm.

---

### Post by al108 on 2006-03-15
That looks to me like a bug  in r1000 or some sort of incompatibility with current kernel. My D-link cards should be here on Friday night. I couldn't get the stuff in town. I'll let you know then if there is any improvement. I might e-mail Realtek to see if they have something to say about it.

Alex

---

### Post by al108 on 2006-03-19
Ok. Installed a D-link DGE-530T (Marvell Yukon 88e8003-LKJ) card and spend a lot of time figuring it out. It was DOA. Installed another one and it worked. I already had sk98lin drivers installed, but it was picked up by SKGE.
dmesg showd that it was initialized at 1000 Mbps, but transfer speed was slower than 100Mbps card. Used same trick as for realtek, removed SKGE driver, recompiled and sk98lin gives me transfer speed around 30MBps both ways without a problem. Jumbo framse didn't work with my switch, so I had to test it with direct connection between computers. Speed increase was about 10% wtih 9000 mtu, cpu load was significantly less on the server (40% with 9000 and 70 with 1500) not that bad on the workstation (11% with 9000 and 20% with 1500)

Thaks for the help
Alex

---

### Post by al108 on 2006-03-21
One more thing. I've tryed Dapper today from a daily build CD of 19-mar-06 and D-Link card works right out of the box, and it's fast too with SKGE driver. Realtek card on the other hand got worse, but maybe also because it's not initialized properly - dmesg shows it eth0, but ifconfig finds it on eth1?. But I'm not worried about it. The D-link is working great.

---

### Post by Stormbringer on 2006-03-22
Just to add an oddity...

On the weekend my server broke and so I had to change my network setup a little. For now I'm connecting to the internet through an Netgear RP614v3 router - uplinked from my Netgear Gigabit switch.

In order to be able to access the files stored on my Breezy AMD64 rig I simply installed Samba ... and copied some files from/to my Windows rig.

Guess what - the speeds are, magically, up! Except for the router I haven't changed anything on the physical setup of my network - even the cable connecting the switch to the router is the same as before.

Now I'm able to transfer large files (200MB+) at ~32-38MB/sec ... that's a good starting point for 1000Mbps.

Breezy is still using Realtek's r1000.ko - so the problem cannot be related the kernel module. It's seems to be something else I'm not aware of.

Cheers,
Storm.

---

### Post by al108 on 2006-03-22
You know, just before I swithced from rtl8169 to D-link my speed "magically" was up both ways... I don't know why either. Maybe it's one of the updates we picked up from repositories?

---

### Post by Stormbringer on 2006-03-22
[QUOTE=al108]Maybe it's one of the updates we picked up from repositories?[/QUOTE]

Hmm ... the only "major" update within the last few days, that could somehow be related to the increased speeds, was the kernel update. I don't assume that any other "high-level" package has something to do with this issue.

At the time the update took place my server was still alive, and I don't recall that speeds got any better. Since Saturday, the day my server broke and got replaced with the router, I rebooted the system several times - and the speeds are still up ... let's see if they come down again at some point (maybe this will give some clue).

Oh, and I just discovered a bug in the r1000.ko:

While running Azureus (x86_64, v2.4.0.x) I fired up VMware Workstation (5.5, latest revision). This made Breezy to lock up hard.

Upon reboot I checked the logs and found out that the crash (Kernel oops) was caused by r1000.ko as the kernel drivers of VMware caused the NIC to switch into promiscous mode (setup of VMnet#).

For me this crash can be reproduced at any time ... guess I'll file a bug report to Realtek.

Storm.

---

### Post by barbz127 on 2006-09-13
So was this ever sorted or still an issue?

Cheers
Paul

---

### Post by ihatethetv on 2006-10-09
I'm running into problems with the Realtek8169 in Dapper, similar to those mentioned throughout this thread.  I am getting decent speeds towards my winxp box (~200-300Mbps) and terrible (100kbps) in the other direction.  I've tried changing cables and rearranging the port order on my Netgear GS605.  I too have a netgear 614 uplinked to the internet.  

I haven't figured out (don't understand yet) how to change the drivers...I'll work on that now.

-Glen

Hope someone is still reading this thread =)

---

### Post by Stormbringer on 2006-10-10
Changing the "driver" is quite simple ... r8169 (OpenSource 8169 driver) and r1000 (Realtek's driver) should be included as a kernel-module - at least that's the case with my amd64-k8 kernel.

Inside of Gnome press ALT + F2 and type:

gksudo gedit /etc/modprobe.d/blacklist-network

Now create ONE of the following lines

# Prevent r8169.ko from loading and allow r1000.ko to load
blacklist r8169

# Prevent r1000.ko from loading and allow r8169.ko to load
blacklist r1000

Save the file and reboot ...

I blacklisted r8169 so that r1000 will load --- the speed isn't as good as in Windows, but I'm tranferring large files with ~26-34MB/s.

Network setup is somewhat similar to yours ... the Linux box has the 8169S onboard, the Windows box has a 8169S add-in card, the Switch is a Netgear GS105, the "uplink" to the internet is a Symantec VPN/100 hardware firewalling roouter.

---

### Post by silverado on 2007-01-21
I have been beeting my head against the wall trying to get a GA311 to work with a GS605 connected to a router.  I finally gave up and bought a new switch (Linksys EG008W) which connected at gigabit instantaneously.  Hope this helps.  For your reference before I did that I tried disabling IPv6, using ndiswrapper to use a windows driver, blacklisting the 8169 driver to use the r1000 driver, and forcing the adapter to the proper mode.  Definitely just buy the new switch and save yourself the headache.

---

### Post by bosjee on 2007-03-01
> **Stormbringer said:**
> Changing the "driver" is quite simple ... r8169 (OpenSource 8169 driver) and r1000 (Realtek's driver) should be included as a kernel-module - at least that's the case with my amd64-k8 kernel.

Inside of Gnome press ALT + F2 and type:

gksudo gedit /etc/modprobe.d/blacklist-network

Now create ONE of the following lines

# Prevent r8169.ko from loading and allow r1000.ko to load
blacklist r8169

# Prevent r1000.ko from loading and allow r8169.ko to load
blacklist r1000

Save the file and reboot ...

I blacklisted r8169 so that r1000 will load --- the speed isn't as good as in Windows, but I'm tranferring large files with ~26-34MB/s.

Network setup is somewhat similar to yours ... the Linux box has the 8169S onboard, the Windows box has a 8169S add-in card, the Switch is a Netgear GS105, the "uplink" to the internet is a Symantec VPN/100 hardware firewalling roouter.


Tried this. My speed went from maxing out at 8% of 1Gigabit to 16~20% of 1Gigabit (as report on Windows Task Manager network performance bar). This looks like a good start. Thanks Stormbringer. Maybe I'm expecting too much but I think a more reasonable number is to be in the 40MB/s range for a Gigabit link. Has anybody reached this speed? What nic/switch/router are you using to achieve this? Thanks.

BTW, here is my setup:
(Realtek 8169 Nic in Ubuntu Edgy) -> Netgear GS105 -> D-Link DGL-4300 -> (Intel Onboard GBit Nic in Windows XP)

---

### Post by DoomedTX on 2007-07-29
Is it possible to disable the 8169 module if it's compiled into the kernel? I wanted to try out the r1000 (already loaded on my system) just to see if it would help, but got an error when I tried moving r8169.ko. I tried 'locate 8169' and got this result:

```
/sys/bus/pci/drivers/r8169
/sys/bus/pci/drivers/r8169/0000:00:09.0
/sys/bus/pci/drivers/r8169/bind
/sys/bus/pci/drivers/r8169/new_id
/sys/bus/pci/drivers/r8169/unbind
/usr/src/linux-headers-2.6.18-chw-13/include/config/r8169
/usr/src/linux-headers-2.6.18-chw-13/include/config/r8169.h
/usr/src/linux-headers-2.6.18-chw-13/include/config/r8169/vlan.h
```

That makes it look like the module is in the kernel and cannot be disabled by the previously stated method. Is there an easy way to temporarily disable 8169 to try out the r1000?

---

### Post by al108 on 2007-08-28
Did you try following readme from Realtek driver?

It's funny how I came back to experince this problem again and I'm reading the same post again. This time though instead of trying new r1000 driver I've installed D-link adapter that I already had and it worked outofthebox with SKGE driver supplied with Fiesty.

Alex

---

### Post by cmcginty on 2007-08-29
I'm still having this issue with the RTL8168 driver. I have a NFS transfer test that runs about 30KB/s at 100% CPU. There is something seriously wrong with this driver.

Is R1000 still a valid solution? Looking for anyone that got this working?

My chipset is the RTL8111B.

---

### Post by al108 on 2007-08-29
It didn't really work for me last time I tried, but realtek probably has a new version of r1000 now. It was just so much faster to replace the network card for me. Besides even if r1000 driver works you would have to recompile the moudules every tiime you upgrade kernel. 

If you have patience go ahead and try it. I think that between the instructions from readme supplied with driver and explanations from Stormbringer it should be pretty easy to do.

Let us know what you had to do and how it worked.

---

### Post by cmcginty on 2007-09-01
Well I solved my problems by upgrading from the 8.002.00 drivers to 8.003.00.

[Here is a link the driver page.]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false")

---

### Post by al108 on 2007-09-03
> **cmcginty said:**
> Well I solved my problems by upgrading from the 8.002.00 drivers to 8.003.00.

[Here is a link the driver page.]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false")


It's good to hear that new drivers work... I'll go pull out my realtek card out of the garbage bin.:)

---

### Post by ramstell on 2007-09-11
I have downloaded the latest driver and followed instructions in the readme file, but my compile is failing when I execute the following:

sudo make clean modules

Directory '/lib/modules/2.6.22-10-server/build' does not exist!

I have tried creating this directory, but then I get the following:

*** No rule to make target 'modules'. Stop.

Does anyone know how to compile the driver? I am running Ubuntu server 7.10 (gutsy).

---

### Post by jedcred on 2007-09-26
Just had this problem. The build folder is sometimes not linked properly to the headers for the kernel you are running.  

To fix this, do the following.

sudo apt-get install build-essential 

This will make sure you have most of the build tools, though ubuntu provides these already (usually).  This is mostly useful for debian users who installed with the basic packages and not the programming ones. Naturally debian users will not need the sudo as debian encourages the use of the root account as opposed to sudo.

sudo apt-get install linux-headers-`uname - r`

This will installed the latest headers for your kernel.  Note the backquotes around uname: this is the quote on the same key as the tilde ~.  

sudo ln -s /usr/src/linux-headers-`uname - r` /lib/modules/`uname -r`/build

This will link the headers to the build folder in the proper place.  This should get you compiling! 

By the by, the `uname -r` just pops in the current kernel version number into the path, to make these instructions as generic as possible.  Enjoy!

The next steps are to blacklist the old driver (the r8169) and make sure the r8168 is loaded on startup, the instructions for which you can find here on the forums.  For debian users, the blacklisting didn't seem to work for me, but the instructions near the start of this thread do.

---

### Post by someonestolecc on 2007-10-14
I just wanted to say thank you to everyone who contributed to this thread.

I have a P5LD2-SE motherboard which has the RTL8111B/8168B chipset doing the network thing.

It was fine till we changed to a gigabit switch recently (LinkSys SD2008 ) and all of a sudden my pc could no longer stream to our xbox or copy across samba shares easily (to another ubuntu pc).

Through everyone reporting back to this thread and the generous step by step steps provided by stormmaster and someone providing the RTL drivers link I was able to disable the 8169 driver that is loaded with the kernel by default, which worked up till now and replaced it with the 8168 driver which worked great... a few reboots and BAMmMM.

So thank you everyone - the problems I've been having with my pc over the last few months are a nightmare so it's great that after what seems an eternity to have something come together - I hope it lasts and I hope my info helped someone out! :)

Just tested smb to smb copy =  5.81 MB/s top as reported by ethstatus <shrug> I wonder if the cat6 was really necessary...

---

### Post by Deshi! on 2007-10-16
I've been having the same problem with slow download speeds yet fast upload speeds from windows to linux,  (on both NFS and Samba) and believe it to also be the fault of the r8169 driver.  (I have the RL8111b chipset according to Biostar's website)  I've tried everything listed here and in other forums,  to try ang get rid of the R8169 driver and install the r8168 one,  but every time I reboot R8169 magically reapears in the list generated by ```
lsmod | grep 816
``` command and also claims the eth0 port.  R8168 also loads but won't claim the eth0 port. 

I've tried manually removing the r8169 mod by the command

```
rmmod -f R8169
```

followed by

```
depmod -a
```

and everything seems to work properly,  R8169 is gone and R8168 remains,  however

```
dmesg | grep 816
```

still shows R8169: eth0: link up  

indicating it still claims Eth0 even though it is not loaded, yet  trying to access the internet or network also doesn't work at this stage,  indicating it is in fact unloaded.  

Of course all commands run as root using sudo. 

But when I reboot,  everything reverts back as if I did nothing.  ](*,)

I've been trying to work this out on my own the past 4 or 5 days and i'm starting to get beyond frustrated with this >.>

Might endup just buying a linksys or something if this doesn't get resolved.  I'm hoping its just something simple I am overlooking that a fresh pair of eyes might point out to me.  Thanks!

System specs in sig, Running Ubuntu Feisty fawn 7.04-64 bit, all packages upgraded to latest versions.

Edit:  I should also state that trying to use the Blacklist as mentioned in a previous post also did nothing to stop it from loading.

---

### Post by Nephi on 2007-10-17
I have the same problem.  Have you rebuilt a new initrd?  I'm going to try that myself on my system when I get home tonight.

---

### Post by Deshi! on 2007-10-17
Solved it by building a custom kernel using the 2.6.20.30 source and Kernel-package,   with the r8169 module disabled in the kernel config.  Loaded R8168 driver and alls well so far,  Send and receive speeds now match,   though probably still needs some tweaking to get optimal Gigabit speeds.   :)

I did not try rebuilding init.rd since I tried the above message before seeing this post,  so I dunno if that may have worked also.

---

### Post by Mcavity on 2007-11-13
I'm in the same boat..
Im running the 8169 drivers from real tech. I'm getting about 9megs when pushing to xp file share over natualus. but less then 1 when i try and pull a file back. 
I tried going to the r1000 but that didn't work [killed the card]
ETHtool doesn't seem to do much. 

any ideas on the uneven speeds?

---

### Post by Mcavity on 2007-11-15
well I finally gave up. I went and picked up a dlink gigabyte nic. It used a different chip set.  Now things are working much better. 
I think theres something that seriously needs a fix.

---

### Post by narsaw on 2007-12-12
Where can the r1000 drivers be downloaded for Ubuntu 7.10? I cannot find it on the Realtek website and I tried searching Google. 

On the Realtek website I can find the "r8168-8.004.00" driver. But I am looking for r1000.

Info:

 dmesg | grep 8169
[   36.259178] r8169 Gigabit Ethernet driver 2.2LK loaded
[   36.260099] eth0: RTL8169s at 0xf883c000, 00:08:54:b3:84:ae, XID 00800000 IRQ 5
[   49.161766] r8169: eth0: link up

more: 

lspci | grep 8169
01:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)

I am only getting 100MB performance from this card. The actual card I bought is:
[ E**_NCORE ENLGA-1320 10/ 100/ 1000Mbps PCI Ethernet Card 1 x RJ45_**]("http://www.newegg.com/Product/Product.asp?Item=N82E16833180026")

Will the r1000 drive for this this card?
Thanks

---

### Post by al108 on 2007-12-12
> **narsaw said:**
> Where can the r1000 drivers be downloaded for Ubuntu 7.10? I cannot find it on the Realtek website and I tried searching Google. 

On the Realtek website I can find the "r8168-8.004.00" driver. But I am looking for r1000.

In


It looks like Realtek has posted a new driver with a name change. I'm not sure if it is different, but now RTL 8169 and RTL 8168 get different drivers, they are named respectively.

If you are getting 100Mbps speeds it's not bad, usually you'll get double of that on Gigabit without any tweaks.

---

### Post by MachineBucket on 2007-12-14
I recently installed a gigabit card with the RTL8169 chip on it in my 6.06 server box. I installed the most recent driver from RealTek's website, but it still transfers files dog slow. A 4 GB file took about 15 minutes to transfer. I'm going to test the card in a Win XP machine and see if it performs any better. If it does, I'm thinking about giving NDISwrapper a try. Has anyone else tried it yet?

---

### Post by cjsoftuk on 2007-12-22
You say 4GB in 15 mins.

That averages at 4.5MB a second.  That is about typical if you have a 100mbps switch/hub etc in there.

I haven't tried the realtek drivers yet, but after moving to a via-rhine 100mbps card, I get better speeds than the realtek r8169 card.

Will go and try to compile the r8169 drivers from realtek now.

---

