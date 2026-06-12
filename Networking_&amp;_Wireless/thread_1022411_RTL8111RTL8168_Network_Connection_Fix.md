---
title: "RTL8111/RTL8168 Network Connection Fix"
date: 2008-12-26
forum: Networking &amp; Wireless
---

### Post by nausicaavow on 2008-12-26
This is guidance for those with integrated Realtek RTL8111 series gigabit Ethernet, built in to motherboards such as the ASRock G41M-LE.

Ubuntu 8.10 (and may other versions) have been reporting problems with connectivity. Here is the solution in a walk-through format. You must be root (sudo su -).

1) Check to see if the r8169 module is loaded
[FONT="Lucida Console"]**-> lsmod | grep r816**[/FONT]
[SIZE="1"][COLOR="Red"]r8168[/COLOR]                  41104  0 [/SIZE]
[FONT="Lucida Console"]**-> lspci -v**[/FONT]
[SIZE="1"]01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
	Subsystem: ASRock Incorporation Device 8168
	Kernel driver in use: [COLOR="Red"]r8169[/COLOR]
	Kernel modules: [COLOR="Red"]r8169[/COLOR][/SIZE]

2) Download the official Realtek driver
[Realtek RTL8111/RTL8168]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2")

3) Remove the r8169 module
[FONT="Lucida Console"][B]-> rmmod r8169
-> mv /lib/modules/`uname -r`/kernel/drivers/net/r8169.ko ~/r8169.ko.backup[/B][/FONT]
[SIZE="1"]( the ` is a backtick, it is not an apostrophe or single quote )[/SIZE]

4) Build the new r8168 module for the kernel
[FONT="Lucida Console"][B]-> bzip2 -d r8168-8.009.00.tar.bz2
-> tar -xf r8168-8.009.00.tar
-> cd r8168-8.009.00
-> make clean modules
-> make install[/B][/FONT]

5) Rebuild the kernel module dependencies
[FONT="Lucida Console"][B]-> depmod -a
-> insmod ./src/r8168.ko[/B][/FONT]

6) Remove the r8169 module from initrd
[FONT="Lucida Console"][B]-> mv /initrd.img ~/initrd.img.backup
-> mkinitramfs -o /boot/initrd.img-`uname -r` `uname -r`[/B][/FONT]

7) Add r8168 module to /etc/modules
[FONT="Lucida Console"]**-> echo "r8168" >> /etc/modules**[/FONT]

8) Reboot, You are done!

9) Examine that ONLY the r8168 module is loaded for the interface
[FONT="Lucida Console"]**-> lspci -v**[/FONT]
[SIZE="1"]01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
	Subsystem: ASRock Incorporation Device 8168
	Kernel driver in use: [COLOR="Red"]r8168[/COLOR]
	Kernel modules: [COLOR="Red"]r8168[/COLOR][/SIZE]

If you need to, configure your /etc/network/interfaces for dhcp or static address then `sudo ifup eth0`

---

### Post by eombah on 2008-12-28
Thanks a lot, this saved me from buying a new network card for my brand new Dell Vostro 420.

One typo though:
> 5) Rebuild the kernel module dependencies
-> depmod -a
-> insmod ./src/rr8168.ko


should be:
> 5) Rebuild the kernel module dependencies
-> depmod -a
-> insmod ./src/r8168.ko


I guess I have to redo this for every kernel update that gets released?

-Bart

---

### Post by nausicaavow on 2008-12-30
Yes, unfortunately this will have to be done for each kernel upgrade. Luckily, it takes only a few minutes.

Thanks I will update the post

---

### Post by Deflatarat on 2008-12-30
Thanks for your post.

I am having trouble compiling the realtek driver. The directory:
/lib/modules/2.6.24-22-server/build
is missing on my system. The Makefile is trying to switch to that directory.

I am assuming that the driver tarball is expecting something in the build directory, probably kernel module sources. I already installed the linux-source-`uname -r` package. What package do I need to install? 

I had to download individual .deb pkgs and transfer it to my linux box. Thank goodness for USB flash drives :D

---

### Post by Deflatarat on 2008-12-30
I should have searched some more before posting. But if you install the following two packages, the build directory will be there.

linux-headers-2.6.24-22-server_2.6.24-22.45_amd64.deb
linux-headers-2.6.24-22_2.6.24-22.45_all.deb

Or sudo apt-get install linux-headers-`uname -r`, but my network was down :)

Replace version number with your `uname -r`. Mine was 2.6.24-22-server.

---

### Post by cprofitt on 2009-01-02
Why is the default kernel not identifying the right driver?

---

### Post by Phiwum on 2009-01-08
I'm afraid these instructions didn't help me.

I have a new HP Pavilion Intel Core2 Quad machine with the following onboard Ethernet controller:

```
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
        Subsystem: Hewlett-Packard Company Device 2a6f
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 2298
        Region 0: I/O ports at e800 [size=256]
        Region 2: Memory at febff000 (64-bit, non-prefetchable) [size=4K]
        Region 4: Memory at f8ff0000 (64-bit, prefetchable) [size=64K]
        Expansion ROM at febc0000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: r8168
        Kernel modules: r8168
```

As you can see, I'm using the r8168 driver (the latest one available from the realtek site).  

The driver works for a while, but seems to crap out after a little while -- typically during a large download.  ifconfig shows that the card is still up, but no packets are received.  dmesg provides no information about the failure that I can see.  You can see here the output of dmesg when I've loaded the module.  There's nothing in dmesg about the card going down.
```

[67522.264022] eth0: no IPv6 routers present
[67988.801622] r8168 0000:02:00.0: PCI INT A disabled
[67988.817782] r8168 Gigabit Ethernet driver 8.010.00-NAPI loaded
[67988.817830] r8168 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[67988.817903] r8168 0000:02:00.0: setting latency timer to 64
[67988.819477] r8168: This product is covered by one or more of the following patents: US5,307,459, US5,434,872, US5,732,094, US6,570,884, US6,115,776, and US6,327,625.
[67988.819482] eth0: Identified chip type is 'RTL8168C/8111C'.
[67988.819485] eth0: RTL8168B/8111B at 0xffffc20000646000, 00:1e:8c:4d:00:a8, IRQ 2298
[67993.042746] r8168: eth0: link up
[67994.040261] r8168: eth0: link up
[68003.988006] eth0: no IPv6 routers present

```
If I rmmod and modprobe r8168, then the card works normally (for a while).  

I've also tried the r8169 driver (the one selected on a clean install of AMD64 Ubuntu 8.10), but the behavior is just the same.  It works for a while and then silently fails.

Here's the output of ifconfig while the card is working.

```
eth0      Link encap:Ethernet  HWaddr 00:1e:8c:4d:00:a8  
          inet addr:192.168.1.3  Bcast:192.168.1.255 Mask:255.255.254.0
          inet6 addr: fe80::21e:8cff:fe4d:a8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:116 errors:0 dropped:0 overruns:0 frame:0
          TX packets:128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14766 (14.7 KB)  TX bytes:72354 (72.3 KB)
          Interrupt:250 Base address:0x6000 
```

I'm bumfuzzled.  It's been a long time since I had any trouble getting an ethernet card to work on Linux, so I'm a bit disappointed with this problem.  Any help would be greatly appreciated.  

Thanks much.

---

### Post by Elemaoh on 2009-01-28
:( I seem to have the same problem. Ive tried every "Solution" on the forums, got no errors, still no access to online. Any other ideas?

---

### Post by dargaud on 2009-04-08
Thanks, your instructions worked great. How can I figure out when the issue will be fixed in the kernel ? By looking at the replacement of r8169 by r8168 at kernel.org or somesuch ? I'd like to avoid updating my kernel until this is fixed, so if anyone knows for sure, a note here would be appreciated.

---

### Post by CFJ0 on 2009-04-19
I think that this should be included in Ubuntu 9.04 Desktop AND Server editions.
I am trying to run a server on a MB with Realtek RTL8111DL (ASRock G41M-LE) and its a pain to do this fix every time.

---

### Post by BubuXP on 2009-04-21
> **CFJ0 said:**
> I think that this should be included in Ubuntu 9.04 Desktop AND Server editions.
I am trying to run a server on a MB with Realtek RTL8111DL (ASRock G41M-LE) and its a pain to do this fix every time.

Today I installed 9.04 RC.
The motherboard is an Asrock G31M-GS with the same RTL8111DL NIC.
As expected, I had to install the r8168 driver because the r8169 driver included didn't work.
After installing and connecting, I made a system update and an updated kernel was in the list.
And surprise: the r8169 driver included in the new kernel is working out of the box!
I removed every r8168 reference from the system just to be sure and the network was still ok.
:D

---

### Post by dargaud on 2009-04-22
This morning after a reboot and some hardware changes, I lost the ethernet. I could see both drivers in lspci -v: "*Kernel driver in use: r8168, r8169*"
One small thing to avoid the return of the bad driver, add the following line to /etc/modprobe.d/blacklist:
```
blacklist r8169
```

---

### Post by BubuXP on 2009-04-23
> **dargaud said:**
> This morning after a reboot and some hardware changes, I lost the ethernet. I could see both drivers in lspci -v: "*Kernel driver in use: r8168, r8169*"
One small thing to avoid the return of the bad driver, add the following line to /etc/modprobe.d/blacklist:
```
blacklist r8169
```

I don't know if you did a kernel upgrade and what version of ubuntu are you using, but the 9.04 version has a kernel with a working r8169 driver for my RTL8111DL network controller.
I'm writing right now from the Jaunty live cd released today and the network is ok with r8169 module.

---

### Post by bakechad on 2009-07-16
I am having problems with r8169 on 9.04.  I have tried to compile r8168, but I keep coming up with errors.  I must be missing a package.  I just can't figure out what I am missing.

> chad@chad-desktop:~/chadtemp/r8168-8.012.00$ sudo make clean modules
make -C src/ clean
make[1]: Entering directory `/home/chad/chadtemp/r8168-8.012.00/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers Module.markers *.order
make[1]: Leaving directory `/home/chad/chadtemp/r8168-8.012.00/src'
make -C src/ modules
make[1]: Entering directory `/home/chad/chadtemp/r8168-8.012.00/src'
make -C /lib/modules/2.6.28-13-generic/build SUBDIRS=/src modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.28-13-generic'
scripts/Makefile.build:41: /src/Makefile: No such file or directory
make[3]: *** No rule to make target `/src/Makefile'.  Stop.
make[2]: *** [_module_/src] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.28-13-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/chad/chadtemp/r8168-8.012.00/src'
make: *** [modules] Error 2
chad@chad-desktop:~/chadtemp/r8168-8.012.00$ 



Any help would be greatly appreciated.

Thanks

Chad

---

### Post by p0rnflake on 2009-07-23
The RTL8111 bug is still there in 9.04 (I'm on kernel 2.6.28-13-generic right now) - following the directions in post #1 seems to have fixed it for me - Just copied 10 gigs over a gigabit link with no problems.

I'm puzzled by why this haven't been fixed in the kernel by now...

---

### Post by Andy Burn on 2009-07-27
Success, works for me. Many Thanks :)

Bakechad, read back in this thread - you need to install linux-headers for your kernel.
:popcorn:

---

### Post by p0rnflake on 2009-07-29
Has anyone testet if it's fixed in the latest kernel which includes this fix:

[http://cve.mitre.org/cgi-bin/cvename.cgi?name=2009-1389](http://cve.mitre.org/cgi-bin/cvename.cgi?name=2009-1389)

---

### Post by Idefix82 on 2009-08-01
> **p0rnflake said:**
> Has anyone testet if it's fixed in the latest kernel which includes this fix:

[http://cve.mitre.org/cgi-bin/cvename.cgi?name=2009-1389](http://cve.mitre.org/cgi-bin/cvename.cgi?name=2009-1389)

I have just installed the 2.6.28-15 kernel and the r8169 isn't loaded at all.

---

### Post by p0rnflake on 2009-08-15
> **p0rnflake said:**
> Has anyone testet if it's fixed in the latest kernel which includes this fix:

[http://cve.mitre.org/cgi-bin/cvename.cgi?name=2009-1389](http://cve.mitre.org/cgi-bin/cvename.cgi?name=2009-1389)

It's still a problem in the newer kernels aswell :(

---

### Post by rdrifter on 2009-10-01
trying to follow the first post as Igot RTL8111 onboard LAN. But the make command won't work, look like the required pack for this wasn't got installed. No I don't have a network. How can I install the package containing the make command.

I used the netinstall cd and got the distro installed without any trouble.

Thanks

---

### Post by Max Spain on 2009-10-20
Hello to all, I recently purchased an Intel d945gclf2 which I was using as a ZFS samba server and to test Kubuntu.  Until recently, I was having the same problem as all of you.  In order to get everything working, I had to use "sudo su" to become root instead of just using sudo to make the module.  And to those of you who were saying the r8169 driver works, you are right, but when I try to do file transfers over my GigE network, the nic stops functioning.  With the r8168, it hasn't given me a problem yet.

Summary of what I had to do that is not listed on the first post:  Install additional packages from repos as listed [here]("https://help.ubuntu.com/community/Kernel/Compile"), and use "sudo su" to build the module.

---

### Post by Sylar_7 on 2009-10-24
> **Max Spain said:**
> In order to get everything working, I had to use "sudo su" to become root instead of just using sudo to make the module.  

THANK YOU MAX SPAIN!!!

I spent my entire afternoon trying to get this to work, and as soon as I ran the make commands under sudo su it worked flawlessly!

---

### Post by Max Spain on 2010-01-25
Ok, so Realtek finally got around to updating their driver so that it works with recent kernels =D>.  I have been waiting for this since 9.10 was released.  I also seem to have figured out a quicker way to get the r8168 module installed.  It seems that after the source has been extracted, you can just run the "autorun.sh" file in the r8168-* directory, followed by "dpkg-reconfigure linux-image-`uname -r`" where uname -r is the output of the command uname -r which tells you which kernel version you have installed.  The first script builds, inserts, and blacklists the appropriate module, although it doesn't blacklist in a .conf file, and the second script handles the initramfs business.

Summary: run the autorun.sh file in the source provided by Realtek, then do dpkg-reconfigure on your kernel and you should be all set.

---

### Post by KillaB7 on 2010-02-15
Is there any chance of getting the new driver integrated into 10.04?
It would be nice since it's an LTS release.

---

### Post by dillzz on 2010-03-30
Same question here.  Any hope for the 10.04 release?  I am seeing the same issues.

---

### Post by KillaB7 on 2010-03-30
> **dillzz said:**
> Same question here.  Any hope for the 10.04 release?  I am seeing the same issues.

Just for the record, I'm not seeing any issues with my D945GCLF2D. I simply wish to use the latest available OEM driver.

Looking at the changesets over at kernel.org, r8168 support was rolled into the r8169 driver at the kernel level, so I'm not sure Ubuntu will ever make a change here?

---

### Post by BMWolf on 2010-04-15
> **Max Spain said:**
> Ok, so Realtek finally got around to updating their driver so that it works with recent kernels =D>.  I have been waiting for this since 9.10 was released.  I also seem to have figured out a quicker way to get the r8168 module installed.  It seems that after the source has been extracted, you can just run the "autorun.sh" file in the r8168-* directory, followed by "dpkg-reconfigure linux-image-`uname -r`" where uname -r is the output of the command uname -r which tells you which kernel version you have installed.  The first script builds, inserts, and blacklists the appropriate module, although it doesn't blacklist in a .conf file, and the second script handles the initramfs business.

Summary: run the autorun.sh file in the source provided by Realtek, then do dpkg-reconfigure on your kernel and you should be all set.
Thanks, worked great. My Vista to samba share writes are twice as fast, but my reads are still excruciatingly slow. Probably a Vista problem, who knows.

---

### Post by David Stodolsky on 2010-05-01
I am seeing this issue with Lucid Desktop 64 bit on a Gigabyte P55A-UD5 dual LAN MB.

mii-tool says "Link OK", but I don't get an IP address using DHCP.

---

### Post by pbryanw on 2010-05-04
Also getting a Realtek 8111 related error with Ubuntu 10.04 x64 (Motherboard is Gigabyte GA-P55M-UD2). I keep on getting disconnected, and my onboard networking stops working in Windows 7 after exiting Ubuntu, then booting into Windows.

As an interim fix, I've switched to an Intel Network card, until a reliable solution can be found.

---

### Post by David Stodolsky on 2010-05-05
My problem was due to a bad DHCP server. May still be having slow xfers for a GigE adapter.

---

### Post by phaile on 2010-05-05
I tried the first suggestion - doing things manually. Didn't work. Tried the later suggestion to use the autorun.sh script. Didn't work :(

The machine's showing the correct kernel module now (r8168 ) but I'm still getting no network :(

---

### Post by phaile on 2010-05-05
Wow, not only does my NIC not work in Ubuntu - it doesn't work in Windows anymore. It was working during the Ubuntu installation, because I managed to get this site up from the link on the last page of the installer. Something between then and booting up Ubuntu has screwed my NIC :'(

---

### Post by pbryanw on 2010-05-05
Installed the 8168 driver using instructions from the first post. Will see if this cures my disconnection problems.

---

### Post by pbryanw on 2010-05-05
> **phaile said:**
> It was working during the Ubuntu installation, because I managed to get this site up from the link on the last page of the installer. Something between then and booting up Ubuntu has screwed my NIC :'(
Having the same problem with my Realtek onboard adaptor. After exiting Ubuntu, it stops working in Windows 7. I've now Installed the 8168 drivers to see if this fixes it. Should note that the instructions in the first post are slightly outdated. Only because the Realtek driver is now version 8.0.18 so:

[B]-> bzip2 -d r8168-8.009.00.tar.bz2
-> tar -xf r8168-8.009.00.tar
-> cd r8168-8.009.00[/B]
becomes
[B]-> bzip2 -d r8168-8.018.00.tar.bz2
-> tar -xf r8168-8.018.00.tar
-> cd r8168-8.018.00[/B]

After changing these lines, the install process worked for me.

EDIT: Also, try the steps outlined in this thread, especially post #12:
[http://ubuntuforums.org/showthread.php?t=1465703&page=2](http://ubuntuforums.org/showthread.php?t=1465703&page=2)

---

### Post by phaile on 2010-05-06
> **pbryanw said:**
> Having the same problem with my Realtek onboard adaptor. After exiting Ubuntu, it stops working in Windows 7. I've now Installed the 8168 drivers to see if this fixes it. Should note that the instructions in the first post are slightly outdated. Only because the Realtek driver is now version 8.0.18 so:

[B]-> bzip2 -d r8168-8.009.00.tar.bz2
-> tar -xf r8168-8.009.00.tar
-> cd r8168-8.009.00[/B]
becomes
[B]-> bzip2 -d r8168-8.018.00.tar.bz2
-> tar -xf r8168-8.018.00.tar
-> cd r8168-8.018.00[/B]

After changing these lines, the install process worked for me.

EDIT: Also, try the steps outlined in this thread, especially post #12:
[http://ubuntuforums.org/showthread.php?t=1465703&page=2](http://ubuntuforums.org/showthread.php?t=1465703&page=2)
Thanks very much, this looks promising. I'll try it out when I get home :)

---

### Post by Drittponken on 2010-05-06
I can tell you this. I used the guide with the newest drivers on a clean install of 10.04.

At first it didn't work. But then i found this code on the forums:

```
sudo mii-tool --force=100baseTx-FD eth0
```
i couldn't use the 1000baseTX :/

And suddenly it did work. But then, ****** it's so god damned slow**
I have a 100/10 Mbp/s connection and i downloaded updates in 78 Kbp/s. I usually get **8 MB/s** when downloading from the Ubuntu servers. Also browsing seems slower. 

Anyone have an idea?

---

### Post by denied on 2010-05-08
Im having even weirder experiences with my network. Lets say i download a file thats 650mb (no matter the location or speed) on my 10/10mbit line. After 7 seconds, yes you read right, 7 seconds, i cant see the transfer speed anymore, its getting "stuck" on the last speed it had 6.99 seconds before going to 7 second "stuckness". Now i notice that everything that moved (icons, clock u name it) also gets stuck.

When i move my mouse it all gets back to "normal" except the speed on the transfer, its down on some seriously issued speed like 1-14k/sec (from being 1110k/sec). IF im lucky the speed will take up, else i need to cancel the download and start it over again.

I've had this issue for SOOOOO long, and frankly i havent even bother about it in the past since if i would run some torrent client (say wine with utorrent) it would keep the network connection alive by downloading and/or seeding torrents. Now that doesnt help either.

And whats so weird is that this happens after 7 seconds! I dont know how to explain this. This is one of the weirdest linux problems i've had since i started with linux back in 98. 
But yeah im on this driver and i think some changes has been made, for the good and for the bad. I wish we could settle this once and for all.


EDiT: did a test now, when you reply there is a waving LOL smiley with a plank :lolflag: So how long does it take before it stops waving for you? For me its exactly 26 seconds after i leave the mouse and keyboard untouched. Its like ubuntu is entering some kind of suspended state but while not being used. I know this since while im typing (we are over 30 seconds now) the smiley is still waving. Anyone getting my issue ? =) This affects all my system, network, installation and so on....

---

### Post by dillzz on 2010-05-09
denied,

Installed 10.04 hoping for a fix.  Still having the exact same issue.  Network will be very sporadic.  Only fix that seems to work is to put this in /etc/rc.local.

/etc/init.d/networking stop && /etc/init.d/networking start

If I do not do this the network will be so slow, pings will stop responding etc.  This is ridiculous.

---

### Post by phaile on 2010-05-12
The power-cycling fix worked for me for a while. Was able to boot into Ubuntu, shutdown, and come back up a a couple of times.

The other night, I tried to hibernate the machine and it didn't shut down properly (so I hard cut the power). When I booted back up the network problem reappeared (note I did not boot into Windows between hibernating and restarting).

The problem looks slightly more serious this time though. Whereas before if I used the ifconfig command I would see eth0 and loopback, now I only see loopback - it looks like Ubuntu isn't recognising the NIC anymore.

I tried the Realtek 8168 drivers - no change. Are there any known issues with hibernation affecting network interfaces?

---

### Post by phaile on 2010-05-12
...And now it magically works again. I'm able to go between Windows and Ubuntu with no problems.

Frustrating.

---

### Post by lsutiger on 2010-05-13
Hi all! I have been looking for a solution to this problem for months, I just been looking in the wrong venue. I was told it was a samba bug. 

I will try this, as I have the problem NIC.
But one issue I have is this - If I somehow brick this system off of the net, whats my best solution?? This machine needs to be up and running.

---

### Post by lsutiger on 2010-05-13
Everything seemed to have worked, browsing does seem a bit faster, but I am still receiving the following:
```
[  740.313573]  CIFS VFS: Send error in read = -9
[  744.181001]  CIFS VFS: No response for cmd 50 mid 18652
[  837.799572]  CIFS VFS: No response for cmd 50 mid 24095
[  837.799586]  CIFS VFS: No response for cmd 50 mid 24096
[  863.271527]  CIFS VFS: No response for cmd 117 mid 24107

```

I will see overnight. I have network shares that are written to in the early morning hours and the past few weeks have been disconnected  when the scripts try to write.

Thanx for all the work done in this thread!

---

### Post by lsutiger on 2010-05-14
Reporting back.

Even though I have the 'problem'  chipset for my NIC, and my browsing seems faster, this still did not resolve my problem of network shares dying  randomly.

Still on the search for a solution.

---

### Post by gladroger on 2010-05-18
Since the download driver from Realtek didn't work for me either, how do I roll back to the driver that came with Ubuntu 10.04?

I am dying with this low speed and I dont want to reinstall the system works so good expect for the samba speeds.. :(

---

### Post by gladroger on 2010-05-24
Any news on this?

---

### Post by lsutiger on 2010-05-24
I am just going to buy an Intel PCI NIC and turn off the onboard one...to much of a headache to deal with any longer.

---

### Post by dillzz on 2010-05-25
Can one of you try this entry in your rc.local:
/etc/init.d/networking stop && /etc/init.d/networking start

This is the only fix I have for this right now.  This seems to clear up all network problems.  Either execute the script or reboot.  

I did a clean install of 10.04 and this is still occurring.

---

### Post by lsutiger on 2010-05-25
dillz, I am trying that now...while waiting for the NIC I decided to unmount/remount the drives hourly and that did help quite a bit.

Just rebooted and will see tomorrow what happens.

---

### Post by comadreha on 2010-05-26
> **phaile said:**
> The power-cycling fix worked for me for a while. Was able to boot into Ubuntu, shutdown, and come back up a a couple of times.

The other night, I tried to hibernate the machine and it didn't shut down properly (so I hard cut the power). When I booted back up the network problem reappeared (note I did not boot into Windows between hibernating and restarting).

The problem looks slightly more serious this time though. Whereas before if I used the ifconfig command I would see eth0 and loopback, now I only see loopback - it looks like Ubuntu isn't recognising the NIC anymore.

I tried the Realtek 8168 drivers - no change. Are there any known issues with hibernation affecting network interfaces?

Hi!

You can have a check in the following link 

[http://ubuntuforums.org/showthread.php?p=9362238](http://ubuntuforums.org/showthread.php?p=9362238)

I had exactly the same problem with you 

This solution worked fine for me !!!

Best

---

### Post by dillzz on 2010-05-26
I looked into this, however I remove all things related to network manager as I have no need for it.  Still searching....

---

### Post by lsutiger on 2010-05-28
Reporting back. The solution dillz posted did not work for me. As a part time solution, I have been unmounting  and remounting my network shares every hour. I just received my Intel card today and will install later.

---

### Post by gladroger on 2010-05-28
it didnt work for me either, i am installign an old 3com card i found..

---

### Post by lsutiger on 2010-05-28
Addition.....I added an Intel card, disabled the RTL connection in BIOS.

I am still getting the "CIFS VFS: No response for cmd 114 " error....


These pretzels are making me thirsty!!!!!!!!!!](*,)](*,)](*,)](*,)](*,)](*,)](*,)

---

### Post by lsutiger on 2010-06-01
> **lsutiger said:**
> Addition.....I added an Intel card, disabled the RTL connection in BIOS.

I am still getting the "CIFS VFS: No response for cmd 114 " error....


These pretzels are making me thirsty!!!!!!!!!!](*,)](*,)](*,)](*,)](*,)](*,)](*,)

Correction!

I learned later that right as I was booting up my machine, the admin had to restart the server. I have not had an error since replacing the NIC with the Intel!

---

### Post by HDave on 2010-07-12
Thank You!  This 1.5 year old how-to is still valid in Ubuntu 10.04 and it really saved my butt tonight!  Thanks!

---

### Post by drommels on 2010-07-15
I suspect problems with the 8169 drivers on my computer. Crashing after rsyncing big files for like 5 minutes. I now use the 8168 drivers but the one thing that I notice is that my speed is a lot lower. Using 8169 I got around 80MB/s rsyncing big files from the server now with 8168 it's around 48MB/s

Anyone else noticing this?

btw it did fix my crashing problem

---

### Post by lsutiger on 2010-07-17
OK - after installing the Intel card, I am still receiving the error and loosing conection to network shares, but not as much as before. So there is definitely a problem in samba also...

---

### Post by dark.gixxer on 2010-10-17
Thanks for this useful post !
It solved my problem, **dineshs** pointed me to this thread and it saved the day.
But i wanted to thank **nausicaavow** also for the original post, and reup it a bit, as it still helps people.

---

### Post by ryannathans on 2011-01-16
When I had 10.04 "LTS" I had huge problems.

Using Gigabyte GA-P55a-UD5 Motherboard.

It has 2x RTL8111 chips and ports.

I have no problems.

I install Ubuntu 10.04 Desktop.

Network never works in Linux properly.

One chip no longer works at all and the other only in 10/100 MegaBit (not GigaBit like I NEED)

Summary: Ubuntu 10.04 install breaks my networking chips (in windows too) forcing me to buy a new motherboard. I could not find a fix and was not covered by warrenty.

Now I have a new GA-P55a-UD5 motherboard and want Ubuntu and windows dual booting. IS IT SAFE?

---

### Post by sogood007 on 2011-01-29
Wow.  it works for me even I am on 10.10 and my symptoms is packet drop (even ping drop packet).  install the RTL8168 driver fix the issue :-)

---

### Post by wookienz on 2011-02-01
running 10.10 - upgraded to 2.6.35-25 from -24 and my manually built r8168 module disappeared.

Page one fix sorted it though! Thanks.

I am using Gigabyte board with a r8111 and r8168 eth controller. I found that all releases i hade to manually download the source and rebuild the module to play nicely with this board. Once again the first post sorted this,though the link to the software is broken..

This is where i got mine: [http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2](http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2)


Cheers ubuntu community!

---

### Post by leespa on 2011-02-22
Hi All,

I have this NIC built into my Asus P7H55-M.

The overall impression I get is that even when/if you do get this thing working it's still full of surprises. 

Mine works, but can't do Gigabit for instance; haven't done any big xfers on it yet but plan to use this for a HTPC streaming 1080p so will need to work well.

In short its a piece of crap...at least under Linux. Is that general consensus?

---

### Post by KillaB7 on 2011-02-22
> **leespa said:**
> In short its a piece of crap...at least under Linux. Is that general consensus?

Mine has been running great under Ubuntu 9.10 Server. No modifications necessary!
The only thing holding me back from upgrading are the comments here.

---

### Post by leespa on 2011-02-22
Ubuntu minimal 10.10 x86_64

---

### Post by ryannathans on 2011-02-22
> **leespa said:**
> Hi All,

I have this NIC built into my Asus P7H55-M.

The overall impression I get is that even when/if you do get this thing working it's still full of surprises. 

Mine works, but can't do Gigabit for instance; haven't done any big xfers on it yet but plan to use this for a HTPC streaming 1080p so will need to work well.

In short its a piece of crap...at least under Linux. Is that general consensus?

In short, this NIC is brilliant, I have 2 gigabit ports teamed on my motherboard. Linux is crap.

---

### Post by leespa on 2011-02-22
More info. This only affects the rev 06 version of this chipset...info we have so far anyways.

I have a rev 03 in a different PC and it works fine.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/699761?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/699761?comments=all)

---

### Post by ryannathans on 2011-02-23
I am in need of installing linux once again on my desktop, however I have the affected NIC. 

What should I do to make sure I don't have to purchase another motherboard again? Compile the new drivers and then blacklist the old?

I really don't want to buy another motherboard D:

---

### Post by leespa on 2011-02-23
> **ryannathans said:**
> I am in need of installing linux once again on my desktop, however I have the affected NIC. 

What should I do to make sure I don't have to purchase another motherboard again? Compile the new drivers and then blacklist the old?

I really don't want to buy another motherboard D:

Short answer is stay tuned.

I have one of these in the mail for the time being; Intel PRO/1000 CT Desktop Gigabit Ethernet Network Adapter PCI Express NIC OEM; for $27 CAD.

In short I don't trust the performance or stability given the current state this NIC is in. Meaning even with the new drivers + blacklisting old I still find it suspect.

---

### Post by ryannathans on 2011-02-23
> **leespa said:**
> Short answer is stay tuned.

I have one of these in the mail for the time being; Intel PRO/1000 CT Desktop Gigabit Ethernet Network Adapter PCI Express NIC OEM; for $27 CAD.

In short I don't trust the performance or stability given the current state this NIC is in. Meaning even with the new drivers + blacklisting old I still find it suspect.

Yeah, I am fine with waiting, the only problem is that I have been waiting almost 12 months since the bug was reported and still no result. I am a bit fed up with this whole issue. How much longer would you think it will be before it is considered 'safe'? The next ubuntu release?

---

### Post by leespa on 2011-02-23
I wouldn't hold your breath. You'd likely be better off using an add-on card for now like I am planning to.

I also wouldn't be surprised if there was a layout / hardware issue with this rev 06 of the chipset. That would explain why the RealTek drivers only allow for 100 Mbps and NO Gigabit. If the traces or something in the IC were slightly bunk it wouldn't support the higher frequency protocol.

Then again they may fix it, but your guess is as good mine when that'd be.

---

### Post by ryannathans on 2011-02-23
arghh! I just forked out for a raid controller and new hard drives... But if i used a add-on NIC wouldn't it still 'fry' the onboard NICs?

---

### Post by leespa on 2011-02-23
No. Disable onboard NIC, add in the new one.

---

### Post by leespa on 2011-02-23
UPDATE: don't waste your time on this dog. My Intel NIC arrived this evening and within 5 min I'm up and running with rock solid Gigabit.

Intel PRO/1000 CT Desktop Gigabit Ethernet Network Adapter PCI Express NIC OEM


DOWNLINK: server --> htpc 
iperf -c 192.168.x.z -p 5000 -t 300 -i 5
------------------------------------------------------------
Client connecting to 192.168.x.x, TCP port 5000
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[ 3] local 192.168.x.x port 39223 connected with 192.168.x.x port 5000
[ ID] Interval Transfer Bandwidth
[ 3] 0.0- 5.0 sec 562 MBytes 942 Mbits/sec
...
[ 3] 295.0-300.0 sec 561 MBytes 942 Mbits/sec
[ 3] 0.0-300.0 sec 32.9 GBytes 942 Mbits/sec

UPLINK: htpc --> server
iperf -c 192.168.x.z -p 5005 -t 300 -i 5
------------------------------------------------------------
Client connecting to 192.168.s.s, TCP port 5005
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[ 3] local 192.168.s.s port 41760 connected with 192.168.s.s port 5005
[ ID] Interval Transfer Bandwidth
[ 3] 0.0- 5.0 sec 558 MBytes 936 Mbits/sec
...
[ 3] 0.0-300.0 sec 32.2 GBytes 922 Mbits/sec


02:00.0 Ethernet controller: Intel Corporation 82574L Gigabit Network Connection
Subsystem: Intel Corporation Gigabit CT Desktop Adapter
Flags: bus master, fast devsel, latency 0, IRQ 19
Memory at f7fe0000 (32-bit, non-prefetchable) [size=128K]
Memory at f7f00000 (32-bit, non-prefetchable) [size=512K]
I/O ports at ec00 [size=32]
Memory at f7fdc000 (32-bit, non-prefetchable) [size=16K]
Expansion ROM at f7f80000 [disabled] [size=256K]
Capabilities: <access denied>
Kernel driver in use: e1000e
Kernel modules: e1000e


sudo mii-tool eth0
eth0: negotiated 1000baseT-FD flow-control, link ok

sudo ethtool -i eth0
driver: e1000e
version: 1.0.2-k4
firmware-version: 1.8-0
bus-info: 0000:02:00.0

---

### Post by ryannathans on 2011-02-24
> **leespa said:**
> UPDATE: don't waste your time on this dog. My Intel NIC arrived this evening and within 5 min I'm up and running with rock solid Gigabit.

Intel PRO/1000 CT Desktop Gigabit Ethernet Network Adapter PCI Express NIC OEM


DOWNLINK: server --> htpc 
iperf -c 192.168.x.z -p 5000 -t 300 -i 5
------------------------------------------------------------
Client connecting to 192.168.x.x, TCP port 5000
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[ 3] local 192.168.x.x port 39223 connected with 192.168.x.x port 5000
[ ID] Interval Transfer Bandwidth
[ 3] 0.0- 5.0 sec 562 MBytes 942 Mbits/sec
...
[ 3] 295.0-300.0 sec 561 MBytes 942 Mbits/sec
[ 3] 0.0-300.0 sec 32.9 GBytes 942 Mbits/sec

UPLINK: htpc --> server
iperf -c 192.168.x.z -p 5005 -t 300 -i 5
------------------------------------------------------------
Client connecting to 192.168.s.s, TCP port 5005
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[ 3] local 192.168.s.s port 41760 connected with 192.168.s.s port 5005
[ ID] Interval Transfer Bandwidth
[ 3] 0.0- 5.0 sec 558 MBytes 936 Mbits/sec
...
[ 3] 0.0-300.0 sec 32.2 GBytes 922 Mbits/sec


02:00.0 Ethernet controller: Intel Corporation 82574L Gigabit Network Connection
Subsystem: Intel Corporation Gigabit CT Desktop Adapter
Flags: bus master, fast devsel, latency 0, IRQ 19
Memory at f7fe0000 (32-bit, non-prefetchable) [size=128K]
Memory at f7f00000 (32-bit, non-prefetchable) [size=512K]
I/O ports at ec00 [size=32]
Memory at f7fdc000 (32-bit, non-prefetchable) [size=16K]
Expansion ROM at f7f80000 [disabled] [size=256K]
Capabilities: <access denied>
Kernel driver in use: e1000e
Kernel modules: e1000e


sudo mii-tool eth0
eth0: negotiated 1000baseT-FD flow-control, link ok

sudo ethtool -i eth0
driver: e1000e
version: 1.0.2-k4
firmware-version: 1.8-0
bus-info: 0000:02:00.0

I need teaming, what should I get?

---

### Post by pretendo on 2011-05-17
hey

so my RTL8111 slowly stoped working on windows(almost like it was dying or something, would work, wouldent work, etc. i eventually installed debian squeeze testing. and it works fine.

i found this:

[http://driveragent.com/b/archive/13300/2-0-5](http://driveragent.com/b/archive/13300/2-0-5)

Andy Liao stoped working on it back in 05 eventually a masterious Hau picked it up and they 
stopped. i noticed when install windows 7 the default card is 
called RTL8168/RTL8111 when i update to the latest driver its named something 
like realtek family PCE blah. 


rtldriver
[URL="http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false"]http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false
[/URL]
update:
installed Xp 32bit went to network properties and disabled wake on lan... works fine now. i think its the WOL feature

update#2: 
installed windows 7 64bit still cant get it to work.. this is so ridiculous

---

### Post by ib80 on 2011-07-16
Hi,

I just changed my whole PC keeping only the hard drives where Kubuntu 11.04 was installed and installed Windows 7 x64 on what used to be my Windows XP drive.

I got a brand-new motherboard from Gigabyte : GA-Z68X-UD4-B3
I am saddened to see that a subject that started in 08 is still causing problems today.

FYI, it is working OK under Windows 7 x64 but acting weird under Kubuntu 11.04 x64 (kernel 2.6.38-10-generic).

I'll try the fix. Hope it works ;)

Regards.

---

### Post by ib80 on 2011-07-16
Well, it works so much better with the right module ;)

About my previous post, I installed the Windows 7 network driver I found on the motherboard manufacturer's website.

---

### Post by lsutiger on 2011-07-16
Willing to share on how you did this?

---

### Post by TheCardist on 2011-07-19
I can't do anything past the second command in step 3... need assistance :(

---

### Post by MikeEx on 2011-09-09
Just tried this on my new m5a97 motherboard with xubuntu 11.04.
Worked like a charm. My connection was barely holding before doing this.

Now I have full speed again.

Thanks OP.

---

### Post by pony-tail on 2011-09-12
Brand new Gigabyte GA-990fx-ud3 motherboard - Realtek RTL8111 onboard nic . Still having the same (realtek 8111 nics have had this issue since 8.10 that I know of )issue with the nic just completely ceasing sending or recieving after 10 to 15 seconds .
This occurs on 10.04 , 11.04 , and now 11.10 .
The realtek tarball fixes it to some extent ( works for 30 to 45 minutes then stops )
I was wondering is this likely to be fixed anytime soon as ALL of the Motherboards I am looking at to upgrade my old AM2 machines (3 in total ) have this onboard network adaptor .

---

### Post by dsbig on 2011-09-12
I followed the fix and it worked. before the fix I could have a stable internet connection.


thankyou

---

### Post by dsbig123 on 2011-09-12
also mods should make this a sticky has it seems to be a fix for alot of people.

ubuntu network connection was slow and unstable and network connection show r8169, replaced it with r8168 and connection was fast and stable afterwards.

only problem is, update the kernel and have to redo the driver replacement

---

### Post by camera battery on 2011-09-13
I use Lenovo notebook, do not know what network card, to be repeated for each boot to access dial-up, how is this going?

---

### Post by jsheedy on 2011-10-04
I am so glad I found this forum post today.  This has been driving me crazy for months.  depending on the kernel upgrade it could be better or worse, now it just stays up.  Thanks for this post, my wife was getting ready to shoot me over this.

---

### Post by Yudley on 2011-10-15
guys I wanted to add one thing (the fix didn't work for me, gigabyte board rtl8111e device, oneiric/11.10 that has kernel 3.0 not 2.x, so I had to do a bit of debugging)

i tried [another fix]("http://ubuntuforums.org/showthread.php?t=1661489") ... it didn't work for me but I made some changes to that and it worked ... following are the changes for this other fix not the one on this thread (maybe I should've posted in the other thread) but some mix-n-match might make it work for this thread's fix too:

the realtek bz2 source file comes with an autorun.sh and src/Makefile (besides other things) ... I had to fix these two files

for autorun.sh I had to change the first line from:

```
#!/bin/sh
```

to:

```
#!/bin/bash
```

(sh on oneiric points to dash which doesn't understand the autorun.sh syntax)

in src/Makefile I changed line 36 from:

```
KEXT := $(shell echo $(KVER) | sed -ne 's/^2\.[567]\..*/k/p')o
```

to:

```
KEXT := $(shell echo $(KVER) | sed -ne 's/^[23]\.[0567]\..*/k/p')o
```

cz this line wasn't working for 3.0 (only for 2.5, 2.6, 2.7) ... there's a caveat here though ... the new line would even work for 2.0 and 3.5, 3.6, 3.7 ... the regex needs to be fixed further but for now it's good enough for my 3.0 kernel

---

### Post by father_ted on 2011-10-26
i just been fighting with this ghastly adapter. 

i found this note after hours of googling.

[http://en.opensuse.org/SDB:Realtek_8169_driver_problem](http://en.opensuse.org/SDB:Realtek_8169_driver_problem)

so ive enabled wake-on-lan and now the sunofabiatch works again. 

i bought an intel pcie nic to replace it as i cant work with my lan randomly disapearing everytime i reboot.

---

### Post by ladasky on 2011-10-31
> **pony-tail said:**
> Brand new Gigabyte GA-990fx-ud3 motherboard - Realtek RTL8111 onboard nic. 

Hi there,

And I'm chiming in with my Gigabyte GA-990FX-UD5 motherboard, which is nearly identical, and has the same onboard NIC.  My son's upgraded system.  It runs both Windows Vista (for which I apologize, but the kid has to have his games) and Linux 11.04, with a 2.6.x kernel.

Out of the box, Ethernet connections were seriously crippled.  They would work for a short while, and then time out, in both operating systems.  Downloads would generally continue to run if they managed to start, but uploads were typically 10X slower than the other computers in my house, and then would drop out altogether.

Gigabyte wanted me to try another NIC peripheral before doing an RMA.  I had to scrounge for one.  Who uses them any more?

I was ready to go through the agony of installing the card.  But then, a family friend who has spent part of his career in IT tipped me off to the fact that the network drivers that came with Gigabyte's motherboard were likely to be outdated and buggy.  Apparently this is a chronic problem with several network chip manufacturers these days.  Buggy drivers get released and we're all beta-testers, and woe to the person who does not have multiple computers at their disposal to help diagnose and fix the problem.

Over at the Realtek web site, I found drivers for both Windows and Linux.  The Windows driver upgrade worked like a charm!  

That emboldened me to try the Linux driver upgrade -- which failed.

You can get the Linux driver tarball **_[here]("http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false")_**, the name of the current revision is r8168-8.026.00.tar.bz2.

When I uncompressed the tarball to the Desktop and ran the autorun shell script, I got this:

```
john@GA-990FXA-UD5:~/Desktop/r8168-8.026.00$ sudo ./autorun.sh
[sudo] password for john: 

Check old driver and unload it.
rmmod r8169
Build the module and install
Backup r8169.ko
rename r8169.ko to r8169.bak
load module r8168
**FATAL: Module r8168 not found.**
Updating initramfs. Please wait.
update-initramfs: Generating /boot/initrd.img-2.6.38-11-generic-pae
Completed.
john@GA-990FXA-UD5:~/Desktop/r8168-8.026.00$ lsmod | grep r816
john@GA-990FXA-UD5:~/Desktop/r8168-8.026.00$ 
```

I'm not a shell script genius, but something's wrong.  Inside the r8168-8.026.00 directory is a directory named src, which contains files named r8168.h, r8168_asf.h, r8168asf.c, and r8168_n.c.  Presumably this is where the shell script would look for files?  Why isn't it finding them?

Anyway, the inappropriate 8169 driver has been removed (good), but the 8168 driver was NOT installed even though I SHOULD have it.  My son's Linux boot has gone from having slow and unreliable networking to straight out nyet-working.  :(

---

### Post by Bardobrave on 2011-11-08
Well... it seems we have a new problem with 11.10 ver and the new kernel 3.0

Before I try the solution from Yudley I'd like to read a bit more about this. Anyone can share any piece of info on the matter?

Thank you.

---

### Post by praseodym on 2011-11-08
Hi,

check this:

[http://forum.ubuntuusers.de/topic/lan-karte-funktioniert-nicht/#post-3005217](http://forum.ubuntuusers.de/topic/lan-karte-funktioniert-nicht/#post-3005217)

You may want to translate it before ;-)

Driver version 026 works with kernel 3.0

---

### Post by Bardobrave on 2011-11-09
It's good news, thank you. 

I will try them soon.

---

### Post by IOException on 2011-11-17
OS: Ubuntu 11.10 x86_64, kernel: 3.0.0-12-generic 
Motherboard:GA-Z68A-D3-B3
Driver version: r8168-8.026.00 

Before it, network worked but was terrifically unstable (from 5% up to 60% packet loss from time to time)

Solution works fine for me, Thanx a lot!

But it really strange that problem still exist after three years.

---

### Post by praseodym on 2011-11-17
Check the mtu-value of your ISP and add it to the network-manager applet instead of "Automatic"

---

### Post by ratcheer on 2011-11-17
> **IOException said:**
> 
But it really strange that problem still exist after three years.

It seems that the bug has finally been fixed in kernel 3.1.

Tim

---

### Post by praseodym on 2011-11-17
> **ratcheer said:**
> It seems that the bug has finally been fixed in kernel 3.1.

Tim

I hope so.

---

### Post by ratcheer on 2011-11-17
> **praseodym said:**
> I hope so.

All I can say for sure is that I am able to use r8169 in Arch with kernel 3.1.1-1. I had not been able to use it when Arch was still on a 3.0 kernel.

Tim

---

### Post by ahendriks on 2011-11-18
When will kernell 3.1 be released for ubuntu? I doubt if it will be released for 11.10... so fixing is the only option for now...

---

### Post by mat1983 on 2011-11-19
I got this same problem in 11.10


---------------------------------------------------------------

john@GA-990FXA-UD5:~/Desktop/r8168-8.026.00$ sudo ./autorun.sh
[sudo] password for john: 

Check old driver and unload it.
rmmod r8169
Build the module and install
Backup r8169.ko
rename r8169.ko to r8169.bak
load module r8168
FATAL: Module r8168 not found.
Updating initramfs. Please wait.
update-initramfs: Generating /boot/initrd.img-2.6.38-11-generic-pae
Completed.
john@GA-990FXA-UD5:~/Desktop/r8168-8.026.00$ lsmod | grep r816
john@GA-990FXA-UD5:~/Desktop/r8168-8.026.00$
-----------------------------------------

Any solutions?

many thanks

---

### Post by mat1983 on 2011-11-19
it always says:


FATAL: Module r8168 not found.


and now i dont have internet :(

please i need help

---

### Post by ratcheer on 2011-11-19
First, the current driver is r8168-8.026.00. 24 and 25 work, but 26 is probably the one you should use. With earlier versions, the Makefile needed a slight modification for kernels higher than 2.x. This latest version seems to have accounted for any kernel version.

1) sudo depmod -a

2) Add "blacklist r8169" to /etc/modprobe.d/blacklist.conf

3) Add "r8168" to /etc/initramfs-tools/modules

4) In the driver directory, run "sudo ./autorun.sh"

5) Run "sudo update-initramfs -v -u -k `uname -r`

Note that uname -r is enclosed in grave accent marks, not quotation marks.

Reboot. After you're back up, run "sudo lspci -v" to make sure that r8168 is the driver in use.

Tim

---

### Post by praseodym on 2011-11-20
Try it with:
```
sudo make
sudo cp src/r8168.ko /lib/modules/$(uname -r)/kernel/drivers/net/
sudo depmod -a
sudo modprobe -v r8168
```

---

### Post by Rille_lkp on 2011-11-25
Installed 3.1.2 kernel and connection is stable with 8169 driver. One problem does however remain using the 8169 driver, can't get gigabit working, only 100 mbps.

---

### Post by vulture99 on 2011-11-26
I'm trying to fix this 8169/8168 issue on my system, which was running fine until the 11.10 upgrade.  I followed ratcheer's post (thanks) from a few days ago and verified via lspci that r8168 is in use by the network interfaces after rebooting.

I use a static IP on eth0.  After rebooting, Ubuntu says eth0 has an established connection (and the info appears correct), but I cannot ping google.com, my gateway, or other machines on my network.

If I switch to DHCP I can then ping google.com, but still cannot ping local machines or my gateway.

Thanks for any help.  I rely on this machine for Samba shares and this is really becoming a problem.  I added a few bits of info below, let me know if you need something else.  Thanks.

/etc/resolv.conf:
```
# Generated by NetworkManager
nameserver 208.67.222.222
nameserver 208.67.220.220
```

/etc/network/interfaces:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.88
gateway 192.168.1.1
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
```


lspci output for network interfaces:
```
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
	Flags: bus master, fast devsel, latency 0, IRQ 45
	I/O ports at c000 [size=256]
	Memory at ea010000 (64-bit, prefetchable) [size=4K]
	Memory at ea000000 (64-bit, prefetchable) [size=64K]
	[virtual] Expansion ROM at ea020000 [disabled] [size=64K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] MSI: Enable+ Count=1/2 Maskable- 64bit+
	Capabilities: [70] Express Endpoint, MSI 01
	Capabilities: [b0] MSI-X: Enable- Count=2 Masked-
	Capabilities: [d0] Vital Product Data
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Virtual Channel
	Kernel driver in use: r8168
	Kernel modules: r8168

05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
	Flags: bus master, fast devsel, latency 0, IRQ 46
	I/O ports at d000 [size=256]
	Memory at ea210000 (64-bit, prefetchable) [size=4K]
	Memory at ea200000 (64-bit, prefetchable) [size=64K]
	[virtual] Expansion ROM at ea220000 [disabled] [size=64K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] MSI: Enable+ Count=1/2 Maskable- 64bit+
	Capabilities: [70] Express Endpoint, MSI 01
	Capabilities: [b0] MSI-X: Enable- Count=2 Masked-
	Capabilities: [d0] Vital Product Data
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Virtual Channel
	Kernel driver in use: r8168
	Kernel modules: r8168
```

---

### Post by garolou on 2011-11-26
Check out this thread for a script that takes care of the 'FATAL: Module r8168 not found' when trying to install the latest Realtec driver.
[http://ubuntuforums.org/showthread.php?t=1861865](http://ubuntuforums.org/showthread.php?t=1861865)

My laptop can now go to sleep and wake up without losing the network connection. :-)

---

### Post by ladasky on 2011-12-14
> **garolou said:**
> Check out this thread for a script that takes care of the 'FATAL: Module r8168 not found' when trying to install the latest Realtec driver.
[http://ubuntuforums.org/showthread.php?t=1861865](http://ubuntuforums.org/showthread.php?t=1861865)


That thread seems only to address people using the 3.x Debian kernel.  I got this problem on Ubuntu 11.04, which uses the 2.6.x kernel.  So even though I read through it in some detail, I came away doubting whether any of the information there would actually help me.

BUT I have good news!  For those of us still using the 2.4.x or 2.6.x kernels, _[Realtec just released a driver update.  Version 8.027.00]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false")_ installed successfully on my system, and I finally have a network connection again.

---

### Post by ratcheer on 2011-12-14
Thanks, ladasky.

The old r8168 has been working fine, for me. I wonder if I should gamble on the new one? I would hope that if the new one gave problems, I could just reinstall the older one, but you never know.

Tim

---

### Post by praseodym on 2011-12-14
Driver version 027 does also compile against kernel 3.0.x (Oneiric), but still not with kernel 3.2 (Precise)

---

### Post by ratcheer on 2011-12-14
> **ratcheer said:**
> Thanks, ladasky.

The old r8168 has been working fine, for me. I wonder if I should gamble on the new one? I would hope that if the new one gave problems, I could just reinstall the older one, but you never know.


The new module version works, too. Thanks, again.

Tim

---

### Post by ratcheer on 2011-12-14
> **praseodym said:**
> Driver version 027 does also compile against kernel 3.0.x (Oneiric), but still not with kernel 3.2 (Precise)

Actually, kernel 3.2 should work with the standard supplied driver, r8169. At least, it works for me on Arch Linux with the newer kernels.

Tim

---

### Post by RalphP on 2012-01-10
I find that the r8169 driver in the 3.2 kernel (Ubuntu 12.04 alpha 1+) works once the connection is established which can take anywhere from 10 seconds to 5 minutes to occur. A fast boot is somewhat meaningless if it takes several more minutes to connect.

---

### Post by ventech on 2012-01-10
By "working", do you guys mean you're getting gigabit?

---

### Post by jloveless on 2012-01-12
Here are instructions on how to install kernel 3.2 to Ubuntu 11.10 x32 and x64:
[http://www.unixmen.com/how-to-upgrade-to-kernel-3-2-in-ubuntu11-10-and-linuxmint12/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+unixmenhowtos+%28Unixmen+Howtos+%26+Tutorials%29](http://www.unixmen.com/how-to-upgrade-to-kernel-3-2-in-ubuntu11-10-and-linuxmint12/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+unixmenhowtos+%28Unixmen+Howtos+%26+Tutorials%29)

I am hopeful that this will hold the correct driver.

---

### Post by ventech on 2012-02-04
I think something happened in the latest kernel (2.6.38-13, im using natty) because I did this update some time ago and now suddenly gigabit works. It loads r8169 but it works perfect

---

### Post by praseodym on 2012-02-04
I made changes to the source-code-tarball, so the driver r8168 can now be build with "dkms" automatically if a kernel upgrade occurs:

[http://forum.ubuntuusers.de/topic/lan-karte-funktioniert-nicht/#post-3005217](http://forum.ubuntuusers.de/topic/lan-karte-funktioniert-nicht/#post-3005217)

---

### Post by ladasky on 2012-04-23
> **ratcheer said:**
> Actually, kernel 3.2 should work with the standard supplied driver, r8169. At least, it works for me on Arch Linux with the newer kernels.

Oh, I wish that SOMETHING about this driver bug was simple.  I had it fixed -- and after a system crash and upgrade, I got the problem back again.  Because of some peculiar circumstances, it took me a while to recognize and fix it.

I have two systems.  The older one has a Gigabyte GA-MA78-US2H motherboard, and the newer one has a GA-990FXA-UD5 motherboard, also from Gigabyte.  Both of these motherboards have Realtek NIC chips.  I upgraded the older system first, and watched Ubuntu automatically install the r8169 driver.  To my great surprise, it worked!  

Therefore, I figured, there would be no trouble with the newer board.  Initially, things looked fine.  But it turned out I had a subtle problem.  Instead of getting a short burst of network access followed by a long timeout, I got _[an alternating pattern of roughly two minutes up, followed by two minutes down]("http://ubuntuforums.org/showpost.php?p=11831398&postcount=1")_.  Initially, I didn't try using the network long enough to see the timeout.  The initial uptime was longer, I think, than it was with an older revision of Linux.  But eventually, the system would choke again.  When I rolled back the r8169 driver, blacklisted it, and installed the r8168 driver, a stable connection was regained.

Looking more closely at the motherboard manuals, I can see that my older motherboard has a Realtek 8111C NIC, while the NIC on the newer one is an 8111E.  I find it weird that the new, r8169-series driver has more trouble with a newer NIC than the older one, but that's the way it is.  Both systems are running Oneiric 64-bit, kernel 3.0.0.17.

Best of luck to you all as we keep slogging through this problem!

---

