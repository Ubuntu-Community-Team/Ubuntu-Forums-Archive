---
title: "Mini-ITX client with no HDD - advice req'd"
date: 2008-10-01
forum: Mythbuntu
---

### Post by alexeix on 2008-10-01
Hi,

So, after some initial problems, I've got Mythbuntu working and although I have some issues to work out, I'm really impressed so far.
Really good results from recorded TV and no stuttering or lost frames.

Now, I'm thinking of setting up a small, quiet client to connect to the backend machine and I understand that it's possible to configure a machine with no HDD.

Can anyone advise on how to go about this and what is required?

I'm looking at getting one of the starter packages on mini-itx.com, but with no HDD, I'm assuming I'll need some flash memory (???); if that's right, how should it be connected?

OR does will it only use RAM?

Thanks in advance for any advice!

---

### Post by ian dobson on 2008-10-02
Hi,

On my frontend I'm using a small MATX motherboard, Core2, Passive cooled NVidia card and the system boots from a 2GB IDE Flash drive that I picked up on ebay for 10Euro.

Although 2Gb isn't much it's more that enough for a Mythbuntu frontend (I'm using about 1.5Gb in total at the moment).

The system also seems to boot up much quicker than with the 2 1/2 inch drive that I used to use.

The only problem I have is that MythArchive (DVD burning) needs more free space to work but I've got it working using a share on my network which is slower than a local drive but it's good enough.

Regards
Ian Dobson

---

### Post by Archmage on 2008-10-02
> **alexeix said:**
> I'm looking at getting one of the starter packages on mini-itx.com, but with no HDD, I'm assuming I'll need some flash memory (???); if that's right, how should it be connected?

OR does will it only use RAM?

Both is possibile. A diskless will need less energy, but is hard to install. Personal I think a small Flash IDE-drive is a good idea.

---

### Post by SiHa on 2008-10-02
My only advice would be, don't try MiniMyth unless you are a Linux expert. Admittedly, I only tried for an evening, but the errors it gives aren't great and there's not nearly as much on-line support as there is with a mainstream distro like Myth/Ubuntu.

If you've never even heard of MiniMyth then please take the blue pill, and forget the last ten seconds of your life.

---

### Post by Eric Boring on 2008-10-02
This guy has an interesting article about this topic:
[http://www.mythpvr.com/mythtv/frontend/set-top/silent/howto.html](http://www.mythpvr.com/mythtv/frontend/set-top/silent/howto.html)
It's a great site for general myth info. Also has some stuff on LIRC and the CommandIR blasters.

I love mini itx. I have a file/print server on a mini itx machine. I did find it a little harder to work with than my old HP, but it's totally worth it for the small, quiet, cool form factor. And you can build these boxes fairly cheaply.


-Josh

---

### Post by anonymousdog on 2008-10-02
> **Archmage said:**
> A diskless will need less energy, but is hard to install.
I'd have to strongly disagree.  With diskless client support built in to Mythbuntu and the MCC, creating a working PXE/netboot system is just a few clicks away.  I've even run it very successfully over 802.11g (using a wireless bridge at the client end for simplicity).  Your only issues would likely be with video driver setup for whatever mini-itx system you choose, and, possibly remote control support.  The rest is cake.

Diskless clients have many advantages.  A diskless system not only uses less power but generates a bit less heat and is quieter than systems with spinning disks.  In addition, nearly all of your diskless FE maintenance (no matter how many you have) is performed on the server, one time per change on a single file system (i.e., reduced maintenance chores).  I'd at least give it a shot; if you fail utterly, you can always buy a disk or CF card and boot the FE locally.

The tradeoff is lack of local file system; so, user jobs, dvd rips, mythvideo, and mytharchive require a bit of additional setup and may run slower than if you had local disk space.  Diskless clients also require more RAM than the same machine would with local disks available (due to the diskless having no swap space available).

---

### Post by xykevinr on 2008-10-02
My experience

I have a mini-itx board (intel atom d945gclf) which I use as a frontend, I run 8.04.1 and it all worked direct from the install disk. I boot from a 2G usb flash pendrive thing and have 2G of RAM - no HDD installed. I tried the diskless stuff once but couldnt get it to work - this was on an older version of mythbuntu and I meant to go try again but never have.

Built-in graphics work fine, although it doesn't work for HD content - too stuttery. I dont do any processing on this frontend, just watch videos, TV, listen to music etc.

The amusing part for me is that I paid about £45(UK) for the motherboard (with processor and on board graphics), £20 for the RAM. The mini-itx case (Noah something) cost about £70 ! ie the box cost more than the stuff inside. 

Maybe one day the flashdrive thing will fall over as its been written to too many times - its been running about 4 months so far. To be honest I'd probably just buy another one if it broke - maybe I'd have a go at diskless again as well.

Hope this helps.... Kev

---

### Post by C.S.Cameron on 2008-10-06
I also have an Intel D945GCLF mITX.
It works just fine booting from Flash Drive.
I install Ubuntu to flash same as to any other hard drive.
I understand that a persistent may make the flash last longer.

---

### Post by alexeix on 2008-10-06
> **C.S.Cameron said:**
> I also have an Intel D945GCLF mITX.
It works just fine booting from Flash Drive.
I install Ubuntu to flash same as to any other hard drive.
I understand that a persistent may make the flash last longer.

I don't understand what you mean - a persistent *what* may make the flash last longer?

I gather that a flash drive won't last that long then?  Is there any point in using a higher capacity flash drive (8 GB)or is that just going to be a waste?

Does the drive just sit one of the external USB slots?

Thanks for all the helpful comments! :)

---

### Post by alexeix on 2008-10-06
> **xykevinr said:**
> My experience

I have a mini-itx board (intel atom d945gclf) which I use as a frontend ...
Built-in graphics work fine, although it doesn't work for HD content - too stuttery. I dont do any processing on this frontend, just watch videos, TV, listen to music etc.



How quiet is this box?  This is the kind of starter kit (from mini-itx.com) that I was thinking of getting, but I want it as a Mythbuntu client and I don't want to hear any fans.

---

### Post by Baka no Kami on 2008-10-06
> **alexeix said:**
> I don't understand what you mean - a persistent *what* may make the flash last longer?

I gather that a flash drive won't last that long then?  Is there any point in using a higher capacity flash drive (8 GB)or is that just going to be a waste?

Does the drive just sit one of the external USB slots?

Thanks for all the helpful comments! :)

The flash drive will last long enough.  In addition you can always clone the drive once you've got it set up like you want.  Then you tape the clone to the inside of the case and you have it ready if the drive ever fails.

I don't know about the mini-ITX boards but normally motherboards have extra headers to add USB ports.  I used one of those and just didn't hook it up the case exterior.

---

### Post by alexeix on 2008-10-06
This may sound daft, but how do you go about cloning it?

Can you point me to any posts which deal with this?  Do you just mean make a backup and restore it to the second USB key?

Sorry; I'm still new to this.

---

### Post by Baka no Kami on 2008-10-06
Actually I'm new to this myself.  I only thought of cloning the drive yesterday after I spent a few hours setting up my system and don't want to have to do it again.

I found [this]("http://www.arsgeek.com/2008/01/22/how-to-clone-your-bootable-ubuntu-install-to-another-drive/") while looking.  It's for HDD instead of flash drives, but it should work OK.

---

### Post by anonymousdog on 2008-10-06
I'm still at a loss as to why you'd not want to try a diskless client on this setup.  The MCC makes it a cake walk, and, since your video chipset will happily use drivers already in the kernel, there's virtually no setup to do on the frontend.  Periodically, you do maintenance on the single disk image maintained on the server...cake.

Or, you could (go the full local file system client and) do the installation on the frontend local media (USB flash, SS disk, spinning disk, CF flash, whatever), setup the frontend, and still have to perform regular maintenance on each frontend you create, and have no central control, and produce more noise, and have unique frontend systems to diagnose when something goes wrong (not to mention change control or file backup [if anyone uses the underlying OS or saves stuff to the local file system]).

---

### Post by C.S.Cameron on 2008-10-06
You can install to Flash Drive as to a HDD using the Live CD.
You end up with a full operating system that can be customized.

Or you can install per pendrivelinux, or using tools like usb-creator, unetbootin or live-usb

These copy the Live CD image to the usb, they are compact but not customizable, the flash is not written to. these can be made persistent so some settings can be saved.

Cloning,this worked for me, I have 4 partitions, Fat32, Home, Root and Swap.
Booted computer using primary pendrive, (sdb).
(can also boot from HDD or Live CD).
Inserted pendrive to clone o/s from, (sdc).
Inserted pendrive to clone o/s to, (sdd).
In terminal ran:
sudo dd if=/dev/sdc of=/dev/sdd
After operation completed, rebooted with sdd.
So far everything looks identical to sdc.
Although identical make and model sdd has a few more megs than sdc thus a bit of unallocated space at the end.

---

