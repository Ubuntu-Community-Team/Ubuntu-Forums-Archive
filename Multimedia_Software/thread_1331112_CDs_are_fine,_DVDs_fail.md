---
title: "CDs are fine, DVDs fail"
date: 2009-11-19
forum: Multimedia Software
---

### Post by GMann7 on 2009-11-19
I've got a head scratcher that's driving me crazy.  My cd/dvd drive plays cds perfectly fine but doesn't recognize dvds at all.  Doesn't matter if the dvd is store bought, home-made or blank.  Nothing I've tried has worked so I'm asking for help.  My machine is an old IBM Thinkpad T40 with a Matshita UJDA745 DVD/CDRW combo drive. I did a clean install of Ubuntu 9.10, and there's no other OS on the system.  Everything else works fine. Below are the steps I've already taken.

First I followed the instructions [here]("https://help.ubuntu.com/community/Medibuntu") to no avail.

Then I tried wodim -checkdrive since that appeared to have magically fixed this issue for some people, but not for me.
> wodim -checkdrive
Device was not specified. Trying to find an appropriate drive...
Detected CD-R drive: /dev/cdrw
Using /dev/cdrom of unknown capabilities
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'MATSHITA'
Identification : 'UJDA745 DVD/CDRW'
Revision       : '1.02'
Device seems to be: Generic mmc2 DVD-ROM.
wodim: Cannot load media with this drive!
wodim: Try to load media by hand.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R96RSo, I tried manually installing libdvdread4 as suggested to another person having this issue.
> sudo apt-get install libdvdread4
sudo /usr/share/doc/libdvdread4/install-css.shWhen that failed I manually installed libdvdcss2, but that didn't help.
> sudo apt-get install libdvdcss2Next I tried manually mounting the drive, but that was a non-starter.
> sudo mount -t iso9660 /dev/scd0 /media/cdrom
mount: no medium found on /dev/sr0
sudo mount /media/cdrom0/ -o unhide
mount: no medium found on /dev/sr0Lastly, just for beer and giggles, I tried setting my DVD region code but that didn't help either.
> sudo regionsetSo I'm stumped.  Does anyone have a clue as to what I can do to get my dvd drive up and running?

---

### Post by GMann7 on 2009-11-19
I've tried a few more things, uninstalling vlc, uninstalling and reinstalling medibuntu, etc. but nothing has helped.  Am now thinking of trashing and reinstalling Ubuntu to see if that helps, but before I do I thought I'd ask again if anyone has any other suggestions.

---

### Post by ilil on 2009-11-19
As far as I see you have problems not with playing DVD but mounting it.
Can you see the contents of a DVD?

---

### Post by GMann7 on 2009-11-19
Sorry for the delayed response, been out all morning.  To answer your question, no I can't see DVDs at all.  They simply don't mount.  With a DVD in the drive I can even force mount.  CDs mount and work perfectly.

---

### Post by ilil on 2009-11-19
Try to see output tail of 'dmesg' program (in terminal) right after you insert DVD.
Maybe you'll see errors related to DVD there.
```

dmesg | tail

```

---

### Post by GMann7 on 2009-11-19
I'm still out right now but I'll try that as soon as I get home in a couple of hours and post my results.

---

### Post by GMann7 on 2009-11-19
Again, sorry for the delay.  Here's what happens when I run the dmesg | tail command.  I got the same results whether the DVD was just inserted into the drive, spinning in the drive, or had just stopped spinning.  I also get the same results if there's no disc in the drive at all.
> dmesg | tail
[   26.480583] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
[   26.480625] pci 0000:01:00.0: putting AGP V2 device into 4x mode
[   26.896591] [drm] Setting GART location based on new memory map
[   26.896603] [drm] Loading R100 Microcode
[   26.896661] [drm] writeback test succeeded in 2 usecs
[   33.044027] eth0: no IPv6 routers present
[   67.954749] lib80211_crypt: registered algorithm 'WEP'
[   68.840092] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   79.148027] eth1: no IPv6 routers present
[   86.648031] Clocksource tsc unstable (delta = -75237867 ns)

---

### Post by 4Orbs on 2009-11-19
Here is something I discovered by accident. DVD's will properly mount more often if I have the file manager (Thunar or Nautilus) open on the desktop when the disk is inserted. Don't know why. Can't imagine how the open file manager could possibly influence the mounting of a DVD, but it does so on my system. Crazy, crazy Ubuntu.

---

### Post by GMann7 on 2009-11-19
> **4Orbs said:**
> Here is something I discovered by accident. DVD's will properly mount more often if I have the file manager (Thunar or Nautilus) open on the desktop when the disk is inserted. Don't know why. Can't imagine how the open file manager could possibly influence the mounting of a DVD, but it does so on my system. Crazy, crazy Ubuntu.
Thanks for the attempt.  I tried this just now and it didn't help me at all.  I'm thisclose to borking the system and reinstalling to see if that helps.  This is totally frustrating!

---

### Post by mc4man on 2009-11-19
You should take into consideration that it is the drive itself, it's not uncommon for drives that are beginning to  fail to read cd's but not dvd's or read dvd's and not cd's.

Cd's and dvd's are 'read' differently, though there are different ways to do so they remain sepearate so to speak
> ......
The common solution is for the DVD player or drive to use two lasers at different wavelengths: one for reading DVDs and the other for reading CDs and CD-Rs. Variations on the theme include Sony's "dual discrete optical pickup" with switchable pickup assemblies with separate optics, dual-wavelength lasers (initially deployed on Sony's Playstation 2), Samsung's "annular masked objective lens" with a shared optical path, Toshiba's similar shared optical path using an objective lens masked with a coating that's transparent only to 650-nm light, Hitachi's switchable objective lens assembly, and Matsushita's holographic dual-focus lens.....

---

### Post by GMann7 on 2009-11-19
> **mc4man said:**
> You should take into consideration that it is the drive itself, it's not uncommon for drives that are beginning to  fail to read cd's but not dvd's or read dvd's and not cd's.

Cd's and dvd's are 'read' differently, though there are different ways to do so they remain sepearate so to speak
I thought of that, also and did a test by taking the cd/dvd drive out of the linux laptop and putting it into another t40 that was running Windows.  Worked perfectly in WinXP, read CDs and DVDs the way it's supposed to.  Then I took the WinXP laptops cd/dvd drive and installed it in the linux t40 and the linux t40 wouldn't even register that there was a cd/dvd device attached, even after a reboot.  I then reinstalled the original cd/dvd drive and it once again reads CDs perfectly but fails to even mount DVDs.

I'm really at a complete loss here.  This makes no sense to me whatsover.  It's as if Linux can only "see" the CD portion of the combo CD/DVD drive and the DVD part just doesn't exist. Anyone have any ideas at all on where to go from here other than a complete re-installation?

---

### Post by ilil on 2009-11-20
Show the output of this command please:
```

cat /proc/sys/dev/cdrom/info

```

Then try to execute dvd+rw-mediainfo from dvd+rw-tools package (need to install it first):
```

dvd+rw-mediainfo /dev/scd0

```
(replace /dev/scd0 with your device name)

---

### Post by ilil on 2009-11-20
> **GMann7 said:**
> I thought of that, also and did a test by taking the cd/dvd drive out of the linux laptop and putting it into another t40 that was running Windows.  Worked perfectly in WinXP, read CDs and DVDs the way it's supposed to.  Then I took the WinXP laptops cd/dvd drive and installed it in the linux t40 and the linux t40 wouldn't even register that there was a cd/dvd device attached, even after a reboot.  I then reinstalled the original cd/dvd drive and it once again reads CDs perfectly but fails to even mount DVDs.

More straight test is to install Windows on linux t40 and check DVD work there.
Also, try other DVD disks to insert (scratches on media?)

---

### Post by GMann7 on 2009-11-20
Thanks for all your help guys, I really appreciate it!
> **ilil said:**
> Show the output of this command please:
```

cat /proc/sys/dev/cdrom/info

```Then try to execute dvd+rw-mediainfo from dvd+rw-tools package (need to install it first):
```

dvd+rw-mediainfo /dev/scd0

```(replace /dev/scd0 with your device name)
Here's the output I get from cat /proc/sys/dev/cdrom/info
> cat /proc/sys/dev/cdrom/info
CD-ROM information, Id: cdrom.c 3.20 2003/12/17

drive name:        sr0
drive speed:        24
drive # of slots:    1
Can close tray:        1
Can open tray:        1
Can lock tray:        1
Can change speed:    1
Can select disk:    0
Can read multisession:    1
Can read MCN:        1
Reports media changed:    1
Can play audio:        1
Can write CD-R:        1
Can write CD-RW:    1
Can read DVD:        1
Can write DVD-R:    0
Can write DVD-RAM:    0
Can read MRW:        1
Can write MRW:        1
Can write RAM:        1
I don't think dvd+rw-mediainfo /dev/scd0 will help me at all since this drive is only a DVD player, not a writer.  It can only write CDs.
As for the following suggestions:> More straight test is to install Windows on linux t40 and check DVD work there.
Also, try other DVD disks to insert (scratches on media?) 	
This laptop was originally Windows XP and the CD/DVD drive worked perfectly in Windows.  I don't have a Windows installation CD so I can't install Windows on this machine but as noted in my last post I do have another identical machine with Windows still on it and when I install this drive into that computer the drive works.  I also tried over a dozen different DVDs (Purchased movies, burned movies and burned data) with no luck.

---

### Post by ilil on 2009-11-20
GMann7,

Then try manually mount a DVD (as you did before) and look 'dmesg' output after it:
```

sudo mount /dev/sr0 /media/cdrom

```
And try different options, -t udf or -t iso9660

---

### Post by GMann7 on 2009-11-20
> **ilil said:**
> Then try manually mount a DVD (as you did before) and look 'dmesg' output after it:
```

sudo mount /dev/sr0 /media/cdrom

```And try different options, -t udf or -t iso9660
Here's what I got:> sudo mount /dev/sr0 /media/cdrom
mount: /dev/sr0: unknown device

dmesg | tail
[  286.454198] VFS: busy inodes on changed media or resized disk sr0
[  288.908196] VFS: busy inodes on changed media or resized disk sr0
[  289.385962] VFS: busy inodes on changed media or resized disk sr0
[  290.341758] VFS: busy inodes on changed media or resized disk sr0
[  290.955283] VFS: busy inodes on changed media or resized disk sr0
[  290.961462] VFS: busy inodes on changed media or resized disk sr0
[  290.980667] VFS: busy inodes on changed media or resized disk sr0
[  292.437581] VFS: busy inodes on changed media or resized disk sr0
[  292.443832] VFS: busy inodes on changed media or resized disk sr0
[  292.455518] VFS: busy inodes on changed media or resized disk sr0

Next I did a standard dmesg and after poring through the entire thing I found the following seemingly relevent lines:> [    1.032875] ata2.00: ATAPI: UJDA745 DVD/CDRW, 1.02, max UDMA/33
[    1.048639] ata2.00: configured for UDMA/33
[    1.052428] scsi 1:0:0:0: CD-ROM            MATSHITA UJDA745 DVD/CDRW 1.02 PQ: 0 ANSI: 5
[    1.053064]  sda1 sda2 <sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    1.059343] Uniform CD-ROM driver Revision: 3.20
[    1.059463] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.059520] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.083292]  sda5 >
[    1.083620] sd 0:0:0:0: [sda] Attached SCSI disk
This is leading me to believe that Ubuntu is only loading CDRW drivers and not DVD drivers.  Could that be the problem?  And if so, is there any way to find and install the proper drivers necessary for this DVD drive?

---

### Post by ilil on 2009-11-20
Yeah, you are not alone with this bug! :)
I found this bug in Karmic by googling 'busy inodes on changed media or resized disk':
[https://bugs.launchpad.net/linux/+bug/464134](https://bugs.launchpad.net/linux/+bug/464134)

Also, look at this too:
[https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/405544](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/405544)

P.S. 1. Add your comments at launchpad about this problem - more people screaming should resovles problems quicker :)
2. Install Ubuntu Jaunty, not Karmic. I think you could read DVD perfectly there.

---

### Post by GMann7 on 2009-11-20
> **ilil said:**
> Yeah, you are not alone with this bug! :)
I found this bug in Karmic by googling 'busy inodes on changed media or resized disk':
[https://bugs.launchpad.net/linux/+bug/464134](https://bugs.launchpad.net/linux/+bug/464134)

Also, look at this too:
[https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/405544](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/405544)

P.S. 1. Add your comments at launchpad about this problem - more people screaming should resovles problems quicker :)
2. Install Ubuntu Jaunty, not Karmic. I think you could read DVD perfectly there.
Thanks a bunch ilil!
I'll add my voice to that thread on launchpad, in the meantime I'm going to download 9.04 and see if that helps me.  Whether it works or not I'll post here.  If it doesn't work then I'm just going to reinstall 9.10 and live without my DVDs until some future release fixes the issue... I hope.

---

### Post by GMann7 on 2009-11-20
Well, installing 9.04 failed to fix the problem so I'm in the process of reinstalling 9.10 since I was able to get everything else to work with it other than the DVD.  I'll just have to use my other computers for all my DVD viewing and ripping tasks.  Thanks to everyone for their help, if I or anyone else, ever finds a solution (or if the bug is fixed in a future release) post it here so others can find it.

---

