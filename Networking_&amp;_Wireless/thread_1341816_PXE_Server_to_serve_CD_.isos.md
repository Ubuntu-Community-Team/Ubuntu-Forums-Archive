---
title: "PXE Server to serve CD .isos"
date: 2009-11-30
forum: Networking &amp; Wireless
---

### Post by joelwhitehouse on 2009-11-30
I setup a PXE server.  It serves pxelinux, which in turn pulls memtest86+.  Now I want to be able to serve bootable CD-ROM .iso files.  

I've seen tutorials on netbooting the Ubuntu Installer by mounting the .iso and copying a part of it the (the iso-linux kernel -- either for the livecd or the installer) into the PXE server's tftp directory.

But what if I want to copy the whole CD - not just the livecd or the installer?  What if I want to netboot a windows installer cd, norton ghost cd, acronis cd, etc?  How can I transport the entire .iso image and run it?

-Joel

---

### Post by sedawk on 2009-11-30
Hello!

I think it doesn't work this way.

Here is what you normally do:
When booting PXE you download a binary file that is executed.
This binary takes care to download more files, e.g.
a linux kernel and some data (initrd) and then starts
the linux kernel (which is triggering a network installation).

So there are two solutions possible:
1) a binary that downloads and activates the iso.
2) a modified kernel that downloads and mounts the iso.

I think 2. doesn't work because you are only mounting the 
bootable iso, you are not booting it.
Solution 1. might work if there would be such a 
binary (or loader or boostrap tool or whatever it is called).
But this solution might depend on your BIOS or even the
iso image (e.g. somehow your iso needs to be working
as a "virtual" cd drive so that the BIOS and you bootable
iso are happy with it).
But on the other hand we use server hardware here that
I can configure to believe that a CD (or iso?) that is
inserted into my local PC is located in the server - magic !
(This is nothing your normal desktop PC can do - so
 I doubt there is a binary/loader/boostrap for that one).


There is one alternive: You can use "normal" PXE to install
a mini linux and then install something like VMware server (free)
or VirtualBox (free) and then after downloading the iso
and a preconfigured virtual PC you can start that 
preconfigured virtual PC which will boot the iso (!) and
do the installation. Small problem: Where to store that
mini linux (RAM (>8 GB)?, or small partition, or second disk?).

If this is only about backup and restore of an install
operating system you might use partition images
(similar to ghost) and a mini linux to restore a partition
image. The tool you might want to check is "partimage".

---

### Post by joelwhitehouse on 2009-11-30
> **sedawk said:**
> 
When booting PXE you download a binary file that is executed.

Agreed.


> **sedawk said:**
> 
So there are two solutions possible:
1) a binary that downloads and activates the iso.
2) a modified kernel that downloads and mounts the iso.

I think 2. doesn't work because you are only mounting the 
bootable iso, you are not booting it.
Solution 1. might work if there would be such a 
binary (or loader or boostrap tool or whatever it is called).


I've explored the option of simply sending the .ISO file over PXE.  This doesn't work because an ISO is not an executable file, but contains the El Torito header, etc.  When you strip the El Torito header out and send just the executable file, it cannot find the rest of the files it's trying to access as it uses INT13 to try to get to the rest of the files -- that are still on the network.

It appears that memdisk can load an iso now, but it doesn't map everything directly, so there are still problems between bootable .iso files.  Plus you have to store all 680 megabytes in client ram.

[QUOTE=sedawk;8413139]
There is one alternive: You can use "normal" PXE to install
a mini linux and then install something like VMware server... 


This is a potentially destructive solution.  I understand that it could work, but working with a virtual machine makes the whole process difficult to automate.

---

### Post by joelwhitehouse on 2009-12-02
The solution appears to be memdisk... though it involves transferring an entire .iso image to the client's RAM before booting can begin.

I am joining the SYSLINUX mailng list to see if I can assist with developing memdisk's functionality further.

-Joel

---

