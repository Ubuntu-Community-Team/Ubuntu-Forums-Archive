---
title: "Some DVDs crashing for me"
date: 2008-12-13
forum: Multimedia Software
---

### Post by abelundercity on 2008-12-13
Sometimes I just want to kick back and watch a movie, y'know? :popcorn:

Since the upgrade to Intrepid that's become a bit of hit-or-miss.  Some work fine, and others, well, I get past the DVD menu and VLC crashes out after a few seconds into the movie.

I'm running Intrepid with a Celeron 1.7 processor and a 128 MB Nvidia GeForce 6200 and 2 gigs of RAM.

A check of log messages turns up this for me:
> Dec 13 20:56:03 Metropolis kernel: [  300.252475] UDF-fs INFO UDF: Mounting volume 'SUPERMAN_RETURNS', timestamp 2006/09/29 12:59 (1ed4)
Dec 13 20:56:27 Metropolis kernel: [  324.942152] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Dec 13 20:56:27 Metropolis kernel: [  324.942175] sr 0:0:1:0: [sr0] Sense Key : Hardware Error [current] 
Dec 13 20:56:27 Metropolis kernel: [  324.942184] sr 0:0:1:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)

I'm no expert, but I seem to recall DMA having something to do with sound.  Am I way off?

Thanks in advance!

---

### Post by mc4man on 2008-12-13
You may be running into some of the inconsistencies of intrepid and the new version of vlc.(they both have issues
Have you tried with another player? (anything but totem-gstreamer.

That dma error is sometimes associated with having a 40 wire ide cable with an umda4 capable drive. (sometimes also with udma2 drives

If your dma is set at udma2 or higher I wouldn't worry.

While hdparm isn't of much value you can still ck. your drive settings. (adjust red to match drive, * shows current setting
```

hdparm -i /dev/scd[COLOR="Red"]0[/COLOR]
```

You could also grep your logs for 'DMA' to see if your being reset to **pio** mode (bad), for instance

```
grep 'DMA' /var/log/syslog
```


If you saw something like this it's safe to ignore if you know you have an 80 wire. (I have 80 wire cables but some Udma4 cable drives on 80 wire cables will only run at Udma2 on linux, no real harm

Dec 13 21:06:43 doug-desktop kernel: [   19.175758] ata1.00: ATAPI: ATAPI   DVD A  DH20A4P, 9P59, max UDMA/66
Dec 13 21:06:43 doug-desktop kernel: [   19.175773] ata1.00: limited to UDMA/33 due to 40-wire cable

---

### Post by abelundercity on 2008-12-13
totem-xine says that it's encrypted.  I have libdvdcss already installed, so that has me wondering if it's either something else or they've gotten better at encrypting.

hdparm puts me at udma4.  Checking the log for the dvd I used that *did* work, the error doesn't show up.

Yep, there it is:

> Dec 13 20:52:59 Metropolis kernel: [    8.079123] ata1.00: limiting speed to UDMA/44:PIO4


OK, so how do I fix that?

---

### Post by mc4man on 2008-12-14
> limiting speed to UDMA/44: PIO4 

I don't think that's anything to worry about yet. 

> totem-xine says that it's encrypted

that's a generic error, Did you install or ck. for libxine1-ffmpeg?

As far as vlc, maybe go into the settings (tools -> preferences and click on the video icon. Switch your 'output'  off of 'default', Xvideo  is preferred but you may need to use X11.

You may also want to do the same for sound, move off of 'default', try pulse and try alsa.

You need to click 'save' for setting changes to take effect.

System wide video output settings (totem) are in system -> preferences -> 'multimedia system  selectors'

---

### Post by abelundercity on 2008-12-14
libxine1-ffmpeg is definitely in place.

None of the changes to video or audio in VLC seemed to have significant impact.

And I don't seem to have that selection in my preferences menu.

---

### Post by mc4man on 2008-12-14
> Some work fine, and others.....

If you want to mention a title or two that don't maybe I have one of them and I'll test on my "never used too much" 8.10 install.

I think 8.04 is a great release in terms of multimedia and while I haven't had too much trouble with 8.10 I think it's as I mentioned , inconsistent. 

See what happens if you reboot (in terms of totem-xine

While the output will be large and full of irrelevant stuff you could open vlc from a terminal with 

vlc -vvv

Maybe something will stand out.


Edit : it never hurts to go into home folder (edit _ show hidden files0 and delete the .dvdcss folder, sometimes you get 'bad keys'

---

### Post by abelundercity on 2008-12-14
At the risk of inspiring cries of "DUH, STUPID!" being hurled at me from many a workstation across the world, you mean to remove and reinstall libdvdcss, right? :redface:

OK, the home video library isn't extensive, as I usually get most of my movies from the public library, here's what works and what doesn't:

Superman Returns-  Doesn't
Justice League: The New Frontier- Does
The Nightmare Before Christmas (special edition)- Doesn't (not even as far as the menu coming up)
Superman: The Movie - Doesn't
Criss Angel: Mindfreak Season Two - Doesn't
The Call of Cthulhu - Doesn't
50 Horror Classics - Does

With the exception of "Nightmare", smaller features on the discs will play, like scene selections and those little "making of" documentaries, for the most part.  Opening credits fail uniformly ("..and he couldn't find this out sooner because...?").

A check of the logs shows the same error to do with Ultra-DMA as I noted above for all of the discs that failed.

---

### Post by abelundercity on 2008-12-17
OK, so I Googled "crc error Ubuntu 8.10" and got [this page]("http://www.computechgroup.com/?p=593").  Following the advice therein I opened up the CPU and switched some cables around.  Now DVD playback works perfectly.

Thanks for taking the time to help, though mc4man!  Your advice got me pointed in the right direction!

---

