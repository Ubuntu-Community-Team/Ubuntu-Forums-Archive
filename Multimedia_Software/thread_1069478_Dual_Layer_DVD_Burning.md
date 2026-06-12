---
title: "Dual Layer DVD Burning"
date: 2009-02-14
forum: Multimedia Software
---

### Post by JustANewb on 2009-02-14
Ok, I have been all over the Internet, tried all sorts of different things (including using k3b, nerolinux (which, since I paid for it, I am pretty disappointed it didn't work), cli commands, and the built in CD/DVD creator) but I cannot get this to work for the life of me.

I, for some reason, cannot get dual layer DVDs to burn at all.  I am using Memorex DVD+R DL DVDs and I have a Lite-On DVD drive (I think...it's whatever came with my hp computer when my parents bought it 4 years ago...) that is capable of burning DL DVDs.  

All I want to do is backup some of my DVDs at 100% quality.  I don't want just the main title or anything like that...the WHOLE thing (so comments about just ripping the title will be ignored).  

And here's what is happening:
I use k3b to create the ISO of the DVD I want to burn.  Then I choose (and I have a lot to choose from now) the program I want to burn it with and start the burning process...
And here's when it gets tricky...
Depending on what program I am using, I either get (a) an Input/Output error (or something along those lines) and the burn fails (luckily not coastering a not-so-cheap DVD) or (b) the DVD drive spins up then stops, never making any progress in any kind of buffer or anything.  :confused:

If anyone can help me from what I have said, great!  Many thanks in advance.  If you need output from code or anything, just let me know.  I can get anything you want.  

I really appreciate any help that I get on this...it is really bugging me that I have 50 DVDs just laying around that I can't do anything with...

---

### Post by JustANewb on 2009-02-14
And another thing...  I don't think that it is a bad ISO or anything, because I am able to mount it with Gmount-iso and watch it in any video player (VLC is player of choice) as a disc...

---

### Post by hansdown on 2009-02-14
Hi JustANewb.

Could you look at this and see if it helps?

---

### Post by Melcar on 2009-02-14
I can't burn duals either.  Haven't tried K3B yet, but neither Brasero or the DVD Creator thing in Nautilus can do it.  Even worse, Brasero causes my drive to "die" when I try this particular operation, and I have to manually unplug-replug the drive to the mobo for the BIOS to pick it up again.  I know the drive works and can burn duals just fine under Windows with Nero.  I've seen bug reports on the issue and supposedly it was fixed for Intrepid (when it comes to Brasero), but still no luck for me.

---

### Post by JustANewb on 2009-02-14
> **hansdown said:**
> Hi JustANewb.

Could you look at this and see if it helps?

I looked at that and have seen that before.  Mine does show that it supports dual layer and here is a screenie of that which they are talking about...

And I am using DVD+R DLs...  I know it doesn't support DVD-R DLs.

---

### Post by khelben1979 on 2009-02-14
It looks like you need to burn on discs which has another brand. Look at [this thread]("http://ubuntuforums.org/showpost.php?p=5920783&postcount=26") from last year.

Verbatim discs should work according to Matt26.

---

### Post by JustANewb on 2009-02-14
> **khelben1979 said:**
> It looks like you need to burn on discs which has another brand. Look at [this thread]("http://ubuntuforums.org/showpost.php?p=5920783&postcount=26") from last year.

Verbatim discs should work according to Matt26.

Thanks.  I read through that thread and I think I'm going to try to get a hold of something other than memorex to try.  I'll let you know if it works.  

In the mean time, has anyone had luck with these disks?


Edit:  One more thing, is it just Memorex discs that aren't working or are other types not working as well?  Just thought I would ask before I dropped more money on something that won't work...

---

### Post by JustANewb on 2009-02-14
Also, I find it kinda funny that my Memorex DVD+Rs will burn just fine...  its only the DVD+R DLs that don't work...

---

### Post by Melcar on 2009-02-14
All I have are Memorex disks (cheap) and I can burn anything from CD-R's to DVD-RWs (and all the +'s in between).  What's so different between Memorex's dual disks to other brands?  Seems kind of silly if you ask me.

---

### Post by JustANewb on 2009-02-14
> **Melcar said:**
> All I have are Memorex disks (cheap) and I can burn anything from CD-R's to DVD-RWs (and all the +'s in between).  What's so different between Memorex's dual disks to other brands?  Seems kind of silly if you ask me.

I know.  But for some reason, I only have problems with the DL Memorex DVD+R discs.  I have Memorex DVD+R and they work just fine...

Maybe it has something to do with the way they are formatted or something...  I dunno...

On another note, does anyone know of a distribution that will burn on these disks?  I really love Ubuntu, and I don't want to see it go...but for a $40 loss, I think I'm going to have to do something different...  Or is this quirk built into the Linux kernel and shared among all distros?

---

### Post by mc4man on 2009-02-15
While i wouldn't use anything but verbatium for dl, you should be able to get some use out of those disks.

There may factors other than the disk quality at play here. One  possibility is the firmware of your drive. 
> 
parents bought it 4 years ago.
If you go this we can ck. how outdated it may be 

```
sudo lshw -C disk
```

When it was manufactured I'm pretty sure memerox wasn't making dl's. (verbatium was -Disc ID: MKM-001-00

the good thing is liteon is very good about updating it's firmware (if needed

As your drive stands now the most compatable dl disks would be the above mentioned verbatiums **2.4x** (the box or pack would say "up to 6x with compatible high speed drives"

The newer "up to 8x" discs may be a problem.

If anything can burn those disks it would be Imgburn (running in wine

It is vastly superior in all regards, particularly so on dual layer video burns 

Let me know, takes a few minutes to set up , a little more to learn

---

### Post by JustANewb on 2009-02-15
```
description: ATA Disk
       product: ST3200822AS
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/sda
       version: 3.02
       serial: 3LJ2N8PW
       size: 186GiB (200GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0af20af2

```

I don't think what you told me to run was right.  That pulled up info about my harddrive

---

### Post by khelben1979 on 2009-02-15
Run dmesg instead.

```
sudo dmesg
```

---

### Post by mc4man on 2009-02-15
> I don't think what you told me to run was right. That pulled up info about my harddrive

When you run that command you should have also had a listing starting with 
cdrom

your drive model would be listed and the firmware is on the line
version

post the whole output if you don't see it


Ex.
> doug@doug-desktop:~$ sudo lshw -C disk
password for doug: 
  *-cdrom:0               
       description: DVD-RAM writer
       product: DVD A  DH20A4P  [COLOR="Red"]<- model[/COLOR]
       vendor: ATAPI
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/cdrom0
       version: 9P59  [COLOR="Red"]<- firmware[/COLOR]
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,utf8 state=mounted status=ready
.....................................clipped


---

### Post by JustANewb on 2009-02-15
Ok...that's weird.  I did exactly what you said before and that is what I got.  Now when I ran it, I got this...

```

...
 *-cdrom
       description: DVD reader
       product: DVD+RW SOHW-822S
       vendor: LITE-ON
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrw1
       logical name: /dev/dvd1
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: VPPE
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 status=nodisc

```

Does this help at all?  I'm going to check if that is the latest firmware now...

EDIT:  I looked for the updated firmware and this appears to be the latest.  I came with my HP computer and the HP site is the only one with the updated firmware.  The latest version is the VPPE that mine has...

---

### Post by JustANewb on 2009-02-15
Would buying a new burner be a possible solution to the problem?

---

### Post by Melcar on 2009-02-15
If the drive is capable of burning dual layer disks and if it's not faulty, buying another one won't solve anything.  I got the same problem and as I said, my drive works fine and can burn under Windows with no issue.  I think it's a Linux specific thing, most likely the associated libraries for burning media.

---

### Post by JustANewb on 2009-02-16
Ok.  I give up on these disks.  I rebooted into windows and even still they didn't burn like they were supposed to.  I don't know what the deal is.  I'm just going to buy some verbatims and call it a day.

---

### Post by driven1 on 2009-03-05
Did the Verbatim disks work? I just ran into this problem last night as I tried to burn my first DL DVD, and no joy. My Lite On burner supports DL and is only a few months old. I don't have a Windows option, so I really need to find a way to make this work. Thanks.

---

### Post by JustANewb on 2009-03-05
I don't know.  When I went to look at buying some, I was turned off by how expensive they were...  I decided just to compress my dvds to fit on a single layer dvd instead of getting uncompressed quality.  It's a pain for me to try to watch them ( ;) ) but you gotta do what you gotta do.  From my understanding of it, though, Verbatim disks are supposed to work no problem.

---

