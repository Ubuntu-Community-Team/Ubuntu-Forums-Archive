---
title: "Desastrous bad network transfers on Gigabit ethernet"
date: 2006-01-13
forum: Networking &amp; Wireless
---

### Post by Stormbringer on 2006-01-13
Hello!

I recently upgraded my home network from 100Mbps to Gigabit - and now I seem to have a problem with Breezy. No matter if I read or write a file from/to my server or Windows-Workstation (shares mounted via smbfs) it doesn't get any faster than ~3-6MB/s (read) and ~2.5MB/s (write).

A short hardware spec:

Breezy is running on my AMD64 rig in the 64-bit flavor - a MSI K8T Neo with a Athlon 64 3000+, 1.5GB RAM, OnBoard Realtek 8169S GbE NIC.

My server is running CentOS 4.2 (might get upgraded to Ubuntu Server when its out) - Tyan Trinity KT400, Athlon XP 1700+ (Palomino), 1GB RAM, SureCom EP-320GT-X GbE NIC (Realtek 8169S). The smb-share is a software RAID-5 (4x 160GB Hitachi 7K250 UDMA133, 8MB cache).

The Windows machine is running XP Home - MSI KT6V, Athlon XP 2500+ (Barton), 1GB RAM, Netgear GA302T GbE NIC (Tigon3).

The switch is a Netgear GS105 5-port GbE (works just fine) and the attached network cabling consist of Patchsee CAT6 cables.

As I said before ... if I read or write a file from either my server or Windows workstation the performance is desastrous. Example: Copying a ~2GB large ISO from my AMD64 box onto a share on my Windows box takes about 9 minutes ... same is true if I try to copy the file onto the server. No collisions (would be somewhat strange on a switched network), no dropped packets, no crc errors (not on Breezy and not on the server).

If I try to do the same on Windows it runs in super sonic speed (compared to the transfer rates on Breezy) ... copying the very same file from the server onto the Windows box results in a transfer speed of ~20MB/s (that's near the maximum of the target hard drives write performance).

No matter what I try - it remains slow as hell on Breezy ...

I even already swapped network cabling (the former cables were "noname" CAT6) - network transfers didn't get any better.

Does anyone have an idea how to resolve this problem?

Thanks for any useful help.

Cheers, Storm.

---

### Post by Mr_Grieves on 2006-01-13
Duplex issues? Do you run the same duplex mode on both computers?
You're best of not using autoneg. Define full duplex.

What happens if you connect a computer directly point-to-point with the Ubuntu box?

---

### Post by Stormbringer on 2006-01-13
Duplex Mode: if there would only be a module parameter to define - or force - duplex mode. modinfo shows no such parameter on r8169.ko

According to the LEDs on the switch, the connections are full-duplex. You know about a method to force a particular duplex mode (i.e. trying out half-duplex)?

Direct Connect: Luckily I found my X-over cable.

AMD64 from/to Linux server: Directly connected - same result. It's sloooooow.
AMD64 from/to Windows box: Same problem - transfers aren't getting better.

In the meanwhile I'll try the "Vanilla Kernel with CK patchset HOWTO" (oh well, seems as I'll have to go through the torture and compile the Nvidia kernel module) - maybe it's somehow an issue of the current Ubuntu kernel.

---

### Post by Stormbringer on 2006-01-14
Another question ...

- I downloaded the 8169 Series Linux driver from Realtek's website and compiled the module.
- I added "r1000" (name of the module) to /etc/modules

Now, how do I tell Breezy NOT to load the r8169 module on startup?
I want r1000.ko to be used as the driver for the NIC, not r8169.ko!

lsmod tells me that both modules are loaded, but eth0 has been initialized by the r8169 module instead of the r1000.

Is there some magic to achieve that goal (or will it be sufficient to move r8169.ko out of /lib/modules/kernel/drivers/net)?

Thanks, Storm.

---

### Post by starNIX on 2006-02-24
I just discovered something that kind of disappoints me.  

I store all my movies and such on a server on my LAN.  I have my multimedia folder mounted thru Gnome using the "Places >>  Connect to Server" dialog.  I have been unable to play DVD rips over the network because it would always have to stop and rebuffer.

When I tried mounting the drive with the "mount -t smbfs ......" command,  now it plays smooth as hell.  No rebuffering or anything.  I can even initiate other file transfers while playing them.  

Does gnome-vfs have that much of a performance issue or am I doing something wrong?


Maybe try mounting the share manually or thru fstab.  Gnome seems to slow things down alot.

---

### Post by Stormbringer on 2006-02-24
Hi, starNIX!

Well ... the smb-shares are mounted through fstab as I need to have access out of every application (mounting SMB via Gnome-VFS sucks bigtime as not every application is able to access the shares in this case).

Meanwhile I tried everything in and outside of the book (Gnome-VFS, crossover-cabling with and without jumbo frames, CIFS instead of SMBFS, tweaking around in /proc, and everything else you can think of).

Still a "no go" on my AMD64 Breezy - transfer speeds are no faster than ~6MB/s.

To be honest, I gave up on the issue ... my hopes are that it will get better in Dapper.

Anyway, thanks for your reply.

---

### Post by gnottage on 2006-03-01
I'm having a similar issue with my very recent upgrade to gigabit. I'm using a Netgear GS108, which supports jumbo frames acording to reports from users at the etailer I got it from. Not that I'm ready to try them as I have a couple of non gigabit clients for now. Thing is the Ubuntu box is my new server, taking over from a Gentoo one that's been pretty good. I find large transfers are stopping after a while, that my WinXP pro desktop (with Gigabit) stops being able to talk to the Ubuntu box, and that the Dovcot IMAP server has issues with it too. Could be the switch, or perhaps configuration...

My 2 gigbit PCs are:
Ubuntu Breezy Server with 3Com 3C2000 NIC
WinXP pro with built in 3Com 3C940

I have a couple of D-link DGE-528T's to try when I get a chance... (life is verrry busy ATM!)

---

### Post by gnottage on 2006-03-06
I had a chance to sort things out yesterday, but it's really wierd.

Looking closer I saw that although my IMAP, shares and web server weren't responding, there was my home folder that was responding still. Except it had a bunch of files missing. From the Ubuntu server it always had everything. Since I have a software RAID-5 array mounted at /home it looked that somehow that was not being read. Apache reads from /home/www, Dovecot reads out of my home directory, and samba shares from other stuff under /home. So that explained what could be happening, but no explanation as to why. I had had problems installing LDAP a while back, which along with Courier-IMPA seemed to screw up the system. I managed to use synaptic (sp?) to completly uninstall these things (I usually use apt-get on the command line). Along with reinstalling all the RAID stuff I was hopefull.

My dektop XP box still had problems, so I tried from another. That also seemed to suffer, but I though it worth turning off my XP desktop. Problems gone! Ahhh though, the internet is reached through the XP deksop which bridges my 802.11a with wired LAN. (I never got Linux to do that when I tried still keeping an IP address). So after a while of no problems, and running a CAT6 cable downstairs (can never be permenant!) I removed the Linksys WiFi card and booted my XP desktop again. All seems happy still, so now I wonder if I dare stick the card back in any box! Perhaps XP gets confused when bridging a connection...

The D-Link card is now in the Ubuntu box, fully supported and working fine. Great for under £10!

---

### Post by scifan on 2006-08-27
Gigabit handles speed/duplex alot better than 100mb... (actually, you wouldn't get a link if you'd fooled w/ settings on this...

Were you running the same interface on your 100mb network?  it might be worth trying to run a stacking cable between the two computers and rule out the switch?

---

