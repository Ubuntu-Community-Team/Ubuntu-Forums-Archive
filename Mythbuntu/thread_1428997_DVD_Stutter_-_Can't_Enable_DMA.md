---
title: "DVD Stutter - Can't Enable DMA?"
date: 2010-03-13
forum: Mythbuntu
---

### Post by tracyandskye on 2010-03-13
I'm running a dual core processor, good nvidia video card, a SATA hd, & IDE cdrom.

I have stuttering problems with some DVD's.  So are a lot of other people I guess.  It seems like a major issue if a a media center has DVD problems for so many people like this!  

I'll explain what I've done below but I don't mind buying different hardware if I could just get something that would work without such a time investment.

Trying to follow the instructions [here]("https://help.ubuntu.com/community/DMA") I try:

mount | egrep 'udf|iso9660'

Which is supposed to get me some output to find my drive but gives me nothing instead.  So I tried this :

dmesg | grep ata

Which is supposed to give me something like this:

ata2.00: simplex DMA is claimed by other device, disabling DMA

But gave me this instead:

[    2.908401] ata6.00: WARNING: ATAPI DMA disabled for reliablity issues.  It can be enabled

So I did this:

sudo gedit /etc/modprobe.d/aliases

And add the following lines to the bottom of the file:

## Turn on DMA for DVD ############################
alias ata_generic off
alias pata_atiixp on

And got this:

[    2.908401] ata6.00: WARNING: ATAPI DMA disabled for reliablity issues.  It can be enabled
[    2.908403] ata6.00: WARNING: via pata_ali.atapi_dma modparam or corresponding sysfs node.
[COLOR="Red"][    2.924324] ata6.00: configured for UDMA/66[/COLOR]
[    2.932490] Write protecting the kernel read-only data: 1840k
[    4.633858] EXT4-fs (sda1): mounted filesystem with ordered data mode
[   17.202837] EXT4-fs (sda3): mounted filesystem with ordered data mode
[   18.236141] ivtv0: Tried to open YUV output device but need to send data to mpeg decoder before it can be used
[   18.332458] ivtv0: Tried to open YUV output device but need to send data to mpeg decoder before it can be used

The red line looks like what I was supposed to get, but the DVD's still stutter.  And I'm not sure what the ivtv lines are about or if they have any impact on this.

---

### Post by utar on 2010-03-15
I have the same issue which IMHO has nothing to do with DMA.

Myth / Ubuntu seems to spin the drive too slowly and hence the data can't be transferred off the drive quick enough for smooth playback.  The various drive speed option in Myth don't work for me.

I can get smooth playback (for a while) if I fast forward until the DVD drive speeds up and then press play.

Given that I rip my DVDs and play them off the HDD this has never been a deal breaker for me and hence I haven't spent much time trying to fix it.  


Utar

---

### Post by Dewey_Oxberger on 2010-03-15
Find a dvd that doesn't work in mythdvd and try playing that DVD from VLC and see how it works.

If it works in VLC then I'd guess your hardware is okay.

As for DMA I know in my case it gets set automatically.  I was thinking that the wiki is out of date and no longer applies to current kernals (but I'm not sure, it might be that SATA doesn't have the DMA issue).

---

