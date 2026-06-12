---
title: "[Feisty] Multi-media CD won't play"
date: 2007-05-03
forum: Multimedia &amp; Video
---

### Post by robenroute on 2007-05-03
Hi there,

I've got a CD with 10 audio tracks and an 11th track which is a video file. In the booklet it says that the CD is playable in any CD-ROM player. However, Totem, VLC or other media players can't even open the CD. Neither can Nautilus. Grip, however, sees all 11 tracks. So does CD Player, but it cannot play the 11th track.

What to do?

P.S. I've got a full-SATA system (if that's important somehow)

---

### Post by robenroute on 2007-05-04
Not a single person around having similar problems with mixed-content CDs?

---

### Post by Nikusan on 2007-05-04
Similar problem here. I'm having trouble with a few "enhanced" CDs. Audio CD with a data track as well. In past versions of Ubuntu you get a dialog to the effect of "This CD contains both data and audio tracks" with options to ignore, mount as data, or play as audio cd.

The strange thing is my girlfriend's computer (also Feisty) presents the dialog I'm talking about when mine does nothing.


Here's some interesting lines from syslog when the CD in question is inserted:

```
May  4 19:20:52 starbuck kernel: [ 7335.196000] ata2.00: configured for UDMA/33
May  4 19:20:52 starbuck kernel: [ 7335.196000] ata2: EH complete
May  4 19:20:55 starbuck kernel: [ 7338.004000] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
May  4 19:20:55 starbuck kernel: [ 7338.004000] ata2.00: (BMDMA stat 0x25)
May  4 19:20:55 starbuck kernel: [ 7338.004000] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x28 data 69632 in
May  4 19:20:55 starbuck kernel: [ 7338.004000]          res 51/51:03:00:00:00/00:00:00:00:00/a0 Emask 0x1 (device error)
May  4 19:20:56 starbuck kernel: [ 7338.332000] ata2.00: configured for UDMA/33
May  4 19:20:56 starbuck kernel: [ 7338.332000] sr 1:0:0:0: SCSI error: return code = 0x08000002
May  4 19:20:56 starbuck kernel: [ 7338.332000] sr0: Current [descriptor]: sense key: Medium Error
May  4 19:20:56 starbuck kernel: [ 7338.332000]     Additional sense: Address mark not found for data field
May  4 19:20:56 starbuck kernel: [ 7338.332000] Descriptor sense data with sense descriptors (in hex):
May  4 19:20:56 starbuck kernel: [ 7338.332000]         72 03 13 00 00 00 00 0e 09 0c 00 51 00 03 00 00 
May  4 19:20:56 starbuck kernel: [ 7338.332000]         00 00 00 00 a0 51 
May  4 19:20:56 starbuck kernel: [ 7338.332000] end_request: I/O error, dev sr0, sector 0
May  4 19:20:56 starbuck kernel: [ 7338.332000] Buffer I/O error on device sr0, logical block 0
May  4 19:20:56 starbuck kernel: [ 7338.332000] Buffer I/O error on device sr0, logical block 1
May  4 19:20:56 starbuck kernel: [ 7338.332000] Buffer I/O error on device sr0, logical block 2
May  4 19:20:56 starbuck kernel: [ 7338.332000] Buffer I/O error on device sr0, logical block 3
May  4 19:20:56 starbuck kernel: [ 7338.332000] Buffer I/O error on device sr0, logical block 4
May  4 19:20:56 starbuck kernel: [ 7338.332000] Buffer I/O error on device sr0, logical block 5
May  4 19:20:56 starbuck kernel: [ 7338.332000] Buffer I/O error on device sr0, logical block 6
May  4 19:20:56 starbuck kernel: [ 7338.332000] Buffer I/O error on device sr0, logical block 7
May  4 19:20:56 starbuck kernel: [ 7338.332000] Buffer I/O error on device sr0, logical block 8
May  4 19:20:56 starbuck kernel: [ 7338.332000] Buffer I/O error on device sr0, logical block 9
May  4 19:20:56 starbuck kernel: [ 7338.332000] ata2: EH complete
```

Any ideas?

---

### Post by robenroute on 2007-05-05
I'm not sure what's going on with Feisty, but it just feels like Feisty isn't up to scratch. This mixed-content CD problem, problems with getting the correct monitor (wide-screen) resolution to work properly. I'm just testing this installation, as I'm still not convinced of it's quality. Same goes for Edgy, by the way. I find it difficult to put my finger on, but Dapper still feels the most solid and usable of the lot (the lot since Breezy, that is).

Anyone knows what pots with this mixed-content CD business? Thanks in advance.

---

### Post by robenroute on 2007-05-08
Not a single person around with a mixed-content CD? Go on then. Be a good lad/ladina and put one in and give it a whirl. Tell us wo 'append.

Ta

---

### Post by robenroute on 2007-05-09
Not a single person?

---

### Post by robenroute on 2007-05-11
Honestly? Or are you just too lazy to be bothered?

---

### Post by cfischer on 2007-06-05
Just tried - cannot access the data on the enhanced audio cd. Looks like a bug - see [this]("https://bugs.launchpad.net/ubuntu/+source/gnome-volume-manager/+bug/87663"). I got it to work once, but now I just get sound juicer when I click browse. Dang ... when's the next update?

---

### Post by Stang Ulysses on 2008-03-29
I'm running 7.10 and the system will not even read an audio CD.  I *can*, however, play 
dvd's on my Optiarc DVD device.  The CDrom is loaded in /media/cdrom0.  When I put an audio CD in, it shows on the desktop as CD-ROM Disk.  If I go to open it, I get the CD creator.  This happens no matter what audio CD I put it.

HELP!!  :)

---

