---
title: "unable to play audio cd's..."
date: 2006-07-16
forum: Multimedia &amp; Video
---

### Post by joncamp on 2006-07-16
Ubunto 6.06, au8220 sound card, liteon cd drive, can hear logon and logoff sound clips, (card is listed in "sounds" app) read date cd's no problem, after inserting audio cd,Sound Juicer opens, select track to play, error message:"Reason: could not get/settings from/on resource" and "Internal data flow error" Am novice; easy fix?

---

### Post by ddonky on 2006-07-16
(cut and pasted from a similar thread yesterday)

I get the error you described when I try to play audio cds or cdrs, and when I try to open them with Totem, I get this error:

'error accessing 'cdda:///dev/hdc': Invalid URI'

DVDs and DVDRs play fine in this drive.

tail | dmesg returns a bunch of lines of this:

cdrom: This disc doesn't have any tracks I recognize!

---

### Post by ddonky on 2006-07-24
bump

---

### Post by stereosteve on 2006-08-13
I just encountered these same problems after a fresh install of 6.06 and applying updates through 08/13/2006.

I tried other CD music players with similar results.

StereoSteve

---

### Post by louieb on 2006-08-19
Your not alone. I am having the same problem. I did a fresh install of dapper and now get the same Reason: Could not get/set settings from/on resource. message.

I did some searching in the linuxquestions forum also and found a couple of other guys with the same problem. It appears to a problem with the Totem player. When I went to remove TOTEM I found out that the Ubuntu-desktop would be removed also. :confused: ain't gona do that. So out of curiosity I installed the KDE (kubuntu-desktop) and low and behold I can play audio Cd's in KDE. I guess I'll just have to wait for the next release of Ubuntu to see if the thing gets fixed.  
The funny thing is I have a old e-machine that I just installed Dapper on and it plays audio Cd's just fine. Just like breezy did on this machine.

---

### Post by groovestix on 2006-08-30
Yeah, this is really annoying. I wonder if the developers know of this.
I agree the problem might be revolving around Totem, but to make the situation even more weird, I can listen to my CDs with "CD Player".

I can't browse anything; in Nautilus when I click on the little arrow next to "Audio Disk" it crashes it (Nautilus) for some odd reason.

---

### Post by ddonky on 2006-09-27
bump

---

### Post by dumpster25 on 2006-10-14
Have you seen this? :-k 

[https://launchpad.net/distros/ubuntu/+ticket/2046](https://launchpad.net/distros/ubuntu/+ticket/2046)

Did it solve your problems.

---

### Post by dumpster25 on 2006-10-14
Have you seen/tried this? :-k 

[https://launchpad.net/distros/ubuntu/+ticket/2046](https://launchpad.net/distros/ubuntu/+ticket/2046)

Did it solve the problem?

---

### Post by JaceMan on 2006-10-14
Xubuntu 6.06.

I cannot play audio CD's either.  If I insert an audio CD and launch xfmedia and press play, xfmedia seems to 'hang'.  It does not ever detect a playlist, and I cannot close xfmedia by any other means that issuing a 'kill' command.

I thought, 'Perhaps xfmedia is screwy (after all I'm an XFCE virgin),' so I used apt to grab myself amarok.  It will not play my CD either.  In fact, 

**_A_ctions**
**Play _A_udio CD** is grayed out.

So, I got to thinking... perhaps the device isn't mounted (although I thought Ubuntu derivatives auto mounted internal optical drives... do they not?) so with that I used the terminal to attempt to mount my drive and am met with some dialog I don't particularly like, because I cannot understand it:

sudo mount /media/cdrom0
mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


Any help would be appreciated.  This is an older (not ancient) laptop that I would rather keep Windows off of and I think XFCE can really make it fly if I can get the use out of it that I need.

Thanks in advance for any and all suggestions.

-Jace

---

### Post by JaceMan on 2006-10-15
Bueller?  Bueller?  -- Anyone?  Anyone?

Anyway...

I have been searching and reading the forum like crazy in a vain attempt at solving this.  It looks like I might be able to get help a little quicker with the contents of fstab... so to anyone who understands this stuff and knows how to interpret it, here are the contents of mine:


```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```


Do you see any reason there why I am getting the dialog error I'm getting when I try to mount the drive, why it doesn't auto-mount, or why I cannot rock my audio CD's?

---

### Post by JaceMan on 2006-10-15
Well, we're getting closer.

Since fstab informed me that my cd-rom drive was /dev/hdc and not /dev/cdrom or wherever xfmedia was previously pointing... I changed the preferences of xfmedia for cd and dvd to point to /dev/hdc.

Next, I ejected and reinserted my Queen's Greatest Hits disc and bringing a smile to my face the playlist populated for me.  My smile was relatively short-lived though...

When I pressed play I was greeted by 2 seconds of "We Will Rock You" and then silence (save for a spinning cd rom drive) for about 15 to 20 seconds.  After that time, the song counter resumed but with no audio... moving the slider back to the beginning of the song brought the tunes back.  Then when the playlist hit song 2, "We Are the Champions" I was met with the same.  Yep, 2 seconds of audio, long delay, program shows song is playing after a while, but the lack of sound causes me to drag the slider back to the beginning to actually hear the tune.

*sigh*

I hypothesize that this has something to do with the drive probably being in PIO mode.  Does that sound right?  How can I check/verify that?  What about changing it?

Also, my wife and younger brother who live with us also use this computer so I want this process to be easy and seamless for them when I'm done.  With that in mind, will I have to point xfmedia to /dev/hdc under their profiles as well or will their profiles just use my settings?

Lastly, where do I go in amarok to show it where to find my drive like I did with xfmedia?  Better yet, is there a command I can issue so that all programs will look in /dev/hdc for optical media first without me having to direct them there?

I'm getting close, but I could use a little help down the home stretch.  Thanks!

---edit---

It doesn't look like my original hypothesis about PIO was correct.  With more searching I learned about a command known as hdparm... here's what it has to say.

```
:~$ hdparm -i /dev/hdc

/dev/hdc:

 Model=DVD/CDRW UJDA770, FwRev=1.50, SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=yes, tPIO={min:180,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  sdma0 sdma1 sdma2 mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 *udma2
 AdvancedPM=no
 Drive conforms to: ATA/ATAPI-5 T13 1321D revision 3:  ATA/ATAPI-1 ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5

 * signifies the current active mode
```

Looks like it is using DMA already.  As you guys can plainly see I am trying to fix this on my own, but I'm really getting discouraged.

---

### Post by confusimo on 2006-10-16
I can't paly any audio cds either.  I did an update and installed Xubuntu .  Gnome or Xubuntu will not paly audio cds either.  But strangely there is no error.  CD player Or juicer see the drive and all the songs but there si no volume.  It is up all the way and onboard sound is detected.  But nothing Plays.   It did once by fluke.  But after I ejectecd the CD and put it back in it stopped playing.  I hit play and the tracks play.  But no audio.  Weird.

Thanks,
Confusimo

---

### Post by confusimo on 2006-10-16
It works now.  I installed goobox.  It closes when I hit play.  It won't play.  I ran update and two things goobox and 1 other g something file updated.  I forgrt which one.  But now it works.  

Goobox doesn't work.  BVut oddly enough every other application now owrks.  CD player, juicer, etc.

Weird why goob would do that.  I've restarted before and no change.  Only after installing goobox.  Weird.

Thanks,
Confusimo

---

### Post by H.E. Pennypacker on 2006-11-23
I am getting a similar error message with no solution:

The folder contents could not be displayed

error accessing 'cdda:///dev/hdb': Invalid URI

This message is from Totem.  The same CD works just fine in Windows and in a CD player.  XMMS comes closest to playing it.  XMMMS plays it, but with no audio.

---

