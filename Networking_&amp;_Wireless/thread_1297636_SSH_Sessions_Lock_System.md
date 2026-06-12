---
title: "SSH Sessions Lock System"
date: 2009-10-22
forum: Networking &amp; Wireless
---

### Post by georgelenzer on 2009-10-22
UPDATE 020091027:

I spent a good deal of time obtaining the following facts about this problem, but never really solved it:

1. Any network transfers to or from the system using ssh, rsync, nfs or other methods cause the system to become completely unresponsive.
2. While the system appears to be completely frozen and does not respond to pings, the kernel is alive (accidentally discovered when opening the DVD drive while at the console)
3. Kernel says that there is a soft lock on CPU #0 and there are many SATA errors for the system disk.  However, I've determined using other OSes (Linux and Windows) that there is no problem with the hardware.
4. If any of the copies are performed locally using the 127.0.0.1 loopback address, the transfer works.  But it fails if a self reference is made to the IP assigned to eth0.  (NIC module issue?)
5. The kernel is 2.6.28-3-rt.  When I installed and booted with 2.6.2-11-generic, the transfer problem went away.  However, due to a bug noted in Launchpad that could cause massive data corruption I chose to avoid this kernel

What I did yesterday is install Karmic Koala RC since it can be updated to the actual released version of Karmic when it comes out Thursday.  There are no network data transfer issues, and even more of my HP laptop hardware is working with this release.  I expect there will be other issues, but the data transfer one was enough of a hinderance that this route is preferable.

Thanks to all who helped.


UPDATE: It's not just SSH.  Happens with rsync and NFS too.

I have two laptops on which I've installed Ubuntu Studio 9.04.  The first laptop (Acer) has a Centrino 32-bit Intel CPU in it and the second (HP) has a 64-bit dual core Intel CPU.  I'm running the 32-bit version of Ubuntu Studio on the Acer and the 64-bit version on the HP.  While testing the installation on the Acer in August, I noticed that after about 100 or so bytes of session data being transmitted (an 'ls' command, an scp session, etc...) the Acer would completely lock up.  I created the session using gnome-terminal.

When I say "lock up" I mean a complete system failure.  At first I thought it was Xorg freezing.  Ctrl-Alt-F1 through F6 would not get me to a VT.  Pinging the box returned nothing at this point.  The only recourse is to press the power button until the system shuts off and then reboot.  The system is fine as long as I don't do any SSH sessions which makes it kind of hard to use...  Since this laptop was an Acer, I chalked it up to some instability in the system.  Maybe a CPU overheat or bad RAM.  It was a $279 refurb after all.

But I recently got a brand new HP HDX16t which is a really nice bit of hardware.  To my surprise, SSH sessions do the same exact thing.  So I just tested a little more.  It has nothing to do with how long I remain connected.  I let it sit for about five minutes an pings continued to work while I was logged in via SSH.  I also checked the interface on the remote machine (the one I'm connected to the HP from) and watched to verify the amount of data transmitted (roughly) until the system stops responding to pings.  It's still about 100 or so bytes and then the system is not responsive.  Identical behavior to the Acer.

The chances of me having two laptops that both have dodgy hardware are pretty slim.  I've swapped network cables, and switches (Netgeat and Linksys) and the same problem occurs, so it doesn't appear to be network hardware.  It also happens in the reverse if I connect from the HP to another system on my network with SSH.  I am going to test with NFS for file transfers next to see if this might be a NIC driver issue.  Sadly, since the system locks up, there's no real way I can think of logging the cause of the problem.  It' likely that the system is already too far gone before it can log anything.

I did search around the net for OpenSSH lock ups but found very very little.  Let me know if more info is needed and I will do my best to provide it.

---

### Post by georgelenzer on 2009-10-22
UPDATE:

1. The problem only happens when the HP or Acer laptops are the "source" of the data transfer.  If they are the "destination" the transfers complete successfully.  I was incorrect in saying that the problem existed in both directions in my original post.


2. It's not just SSH and rsync (using ssh as it's agent), but NFS exhibits the same problem too.

I'm going to check and see if I export a flash drive if I can transfer without problems to rule out the possibility of a disk I/O driver issue with the SATA controller next...

---

### Post by georgelenzer on 2009-10-22
Same thing with a flash drive exported via NFS. So it's probably not a disk I/O issue. That leads me to believe that the NIC driver might be problematic. The NIC is listed in lspci as "Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Giabit Ethernet controller (rev02) I'm pretty sure that's a fairly stable driver. Anything else I should check?

---

### Post by Lars Noodén on 2009-10-22
What happens when you try transferring locally?  

e.g.

rsync -avv -e ssh /testdir/ me@127.0.0.1:/tmp/

---

### Post by georgelenzer on 2009-10-22
Good thought!  That does work.  I synced about 160 megs of data from my home dir to a flash drive with no problem.  The same dir could also be synced to /tmp with no problem.  So it definitely looks like it has something to do with transferring over the network.  The NIC is a a Realtec RTL8111/8168B according to lspci.  The loaded kernel module is r8169.

> **Lars Noodén said:**
> What happens when you try transferring locally?  

e.g.

rsync -avv -e ssh /testdir/ me@127.0.0.1:/tmp/

---

### Post by Lars Noodén on 2009-10-22
Ok.  That narrows it down a bit.  How about testing the external ip for that machine the same way to see if that causes any problems:

rsync -avv -e ssh /testdir/ [email]me@*xx.yy.zz.aa[/email]*:/tmp/

---

### Post by georgelenzer on 2009-10-22
OK.  I tried that and it works.  The locally DHCP assigned IP address for the HP laptop is 10.0.3.167, so I ran:

```
rsync -avv -e ssh /home/lenzer/Testdir/ lenzer@10.0.3.167:/tmp/Test/
```

Everything copied with no issue.  But when I tried copying to my workstation (10.0.3.146):

```
rsync -avv -e ssh /home/lenzer/Testdir/ lenzer@10.0.3.146:/tmp/Test/
```

The HP laptop locked up.

Some new and interesting info...  I left the laptop on for quite a while last night and it just never came back.  Today, I also left it on, but I opened the CD-ROM tray to get ready to boot another OS without shutting the system down.  I got kernel messages...
```

ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x6 frozen
ata1.00: cmd 60/08:00:37:08:a9/00:00:10:00:00/40 tag 0 ncq 4096 in
res 40/00:fe:00:00:00/00:00:00:00:00/40 Emask 0x4 (timeout)
ata1.00: status: { DRDY }
ata1.00: failed to set xfermode (err_mask=0x4)
ata1.00: failed to set xfermode (err_mask=0x4)
ata1.00: failed to set xfermode (err_mask=0x4)
end_request: I/O error, dev sda, sector 279513143
end_request: I/O error, dev sda, sector 279513143
end_request: I/O error, dev sda, sector 279513143
sd 0:0:0:0: [sda] Asking for cache data failed
sd 0:0:0:0: [sda] Assuming drive cache: write through
BUG: soft lockup - CPU#0 stuck for 61s! [ata_aux:46]
BUG: soft lockup - CPU#0 stuck for 61s! [ata_aux:46]
BUG: soft lockup - CPU#0 stuck for 61s! [ata_aux:46]
BUG: soft lockup - CPU#0 stuck for 61s! [ata_aux:46]
BUG: soft lockup - CPU#0 stuck for 61s! [ata_aux:46]
BUG: soft lockup - CPU#0 stuck for 61s! [ata_aux:46]
```

I wonder if the SATA driver is an issue.  This might also explain the lockups with Adobe Flash in Firefox which I planned on attacking after solving this problem.  Even though the kernel seems to still be somewhat alive, I can't switch VTs and the KB does nothing.

Additional info based on the above errors:

The CPU in the system is an Intel Core 2 Duo 7550 running a 2.26 GHz.
The SATA controller is an Intel Corporation ICH9M/M-E SATA AHCI Controller
There are six SATA ports detected (in dmesg) ata1 through ata6
The system drive is ata1.00 which is a Western Digital WD3200BEKT-60F3T1
The kernel is using libata version 3.0

The minimal web searches I've done don't really reveal much.  A few people noted power cable issues but I don't think that could be the case here since this is a laptop and packed pretty tightly.  The other thing is that the system runs stable doing many other disk intensive things (audio and video editing).  Only transferring data out of the laptop over the network cause the lockups.  Occasionally while watching something on Hulu with Flash will the laptop freeze but only in fullscreen so I'm still thinking it might be a different issue and I'm leaving that out of consideration for now.

> **Lars Noodén said:**
> Ok.  That narrows it down a bit.  How about testing the external ip for that machine the same way to see if that causes any problems:

rsync -avv -e ssh /testdir/ [email]me@*xx.yy.zz.aa[/email]*:/tmp/

---

### Post by georgelenzer on 2009-10-22
I should also note that I am having a lot of trouble booting some of the liveCDs I have.  This is likely owing to the fact that the DVD drive is a SATA drive and the liveCDs are probably expecting IDE, so they can't find the CD-ROM for squashfs after the kernel hands off to whatever init process comes next.  Some work, some don't.

---

### Post by georgelenzer on 2009-10-22
Still more info...  I booted up with the Ubuntu Studio 63-bit installer CD and went into  "rescue mode".  I then mounted my system's root FS on /mnt/temp and chrooted into it.  So other than the loaded kernel, I'm basically running the same system, same software as a regular boot.  The rsync over the network, worked with no problems.

The kernel on the installer CD reports as:

Linux ubuntu 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux

The kernel when I boot normally is:

Linux hdx16t 2.6.28-3-rt #12-Ubuntu SMP PREEMPT RT Fri Apr 17 10:09:12 UTC 2009 x86_64 GNU/Linux

Is there any way I can try a different kernel (I'm new to Ubuntu) to see if something about this kernel is the problem without hosing my system?

---

### Post by georgelenzer on 2009-10-22
I've installed the 2.6.28-11-generic kernel and headers.  (I don't know if this will work out in the long run since it doesn't have RT and SMP which I need for the audio and video work)  The file transfer worked.  So something about the 2.6.28-3-rt kernel seems to be the problem.  Where should I go from here?  Do I need to collect more information before I can file a bug report?  Is there a place to file a bug report?  I'm new to Ubuntu, so I don't know the proper approaches to this sort of thing yet.

---

### Post by georgelenzer on 2009-10-23
I found this bug that relates to massive data corruption on 64-bit installations where the ICH8/9 chipset is in use for SATA devices.  Unfortunately, it seems that this bug has not been solved and applies to the 2.6.28-11-generic kernel that I just installed to resolve my data transfer problem.  So using this particular kernel might not be the best move for me since I'm on 64-bit Ubuntu and the HP laptop has an ICH9M/M-E chipset.

Considering that I also want RT and SMP functionality in the kernel, is there a way to go back to an older 2.6.?-?-rt kernel for Ubuntu Studio?  Or move forward to something newer than the 2.6.28 series?  A few people in the bug report mentioned that they upgraded to 2.6.29 or even 2.6.30 (still seemed to be Ubuntu kernels though).  How does one do that?

Also, I'm not opposed to building my own kernel from sources.  Does anyone have any guidance on that under Ubuntu?  Are there any guides or "best practices" for doing that?

Here is  link to the bug report:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691)

---

### Post by georgelenzer on 2009-10-23
I'm going to wipe the disk and install Ubuntu Studio 8 (Hardy) since it uses an older rt kernel and test to see if the problem still exists there.  There don't seem to be any newer rt kernels for Jaunty.  Hopefully Hardy's installation DVD will boot for me since the HP DVD drive is on SATA and a lot of install/liveCDs don't seem to like that.  They all break after the kernel loads and they try to go to init.

---

### Post by georgelenzer on 2009-10-26
Have not tried Hardy.  I'm actually thinking of going straight to Karmic instead.  My main problem being the data transfer over the network... if it's solved in Karmic RT kernel, I'll be happy.

---

