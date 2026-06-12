---
title: "Totem and VLC"
date: 2006-12-01
forum: Multimedia &amp; Video
---

### Post by hardeep27 on 2006-12-01
Hi Guys, 

When i instert a DVD Totem fires up, problem is i get the 'Totem could not play 'dvd///media/dvdrecorder'. No URL handler implemented or 'dvd'.

This is a problem in itself but i would prefer to use VLC player to play all my media files. I have installed it but cant figure out how to make it my default player so any media file (music or video) i run opens and plays in VLC.

If anyone could helpe me out on that i would appreciate it.

thanks

hardeep

---

### Post by drphilngood on 2006-12-01
IIRC, you can right-click on the DVD icon on your desktop, select Properties, click the ¨Open With¨ tab and select VLC media player.

This will also work on other media.  For instance, clicking on an ogg/MP3 music file and following the above steps will set VLC as the default player for ogg/MP3.

Hope this helps.

---

### Post by dlehman on 2006-12-01
DVD's open up in totem for me too I have not got around to figuring that out but I do know for music or movies file whatever the file really right click goto properties and then the open with tab and select the program you would like it to open with

---

### Post by dlehman on 2006-12-01
also look at 

system>preferences>removable drives then multimedia tab

---

### Post by lori.ann on 2006-12-08
> **dlehman said:**
> also look at 

system>preferences>removable drives then multimedia tab

Once I get there, how do I find where VLC is?

---

### Post by artships on 2006-12-09
In an Xterm, type "which vlc".  Though, judging by the default in my installation, what you want is:

wxvlc dvd:///dev/dvd

---

### Post by ubu-for on 2007-02-19
> **artships said:**
> In an Xterm, type "which vlc".  Though, judging by the default in my installation, what you want is:

wxvlc dvd:///dev/dvd

... or ...

wxvlc dvdsimple:///dev/dvd

... starts the movie immediately.

---

### Post by hogar_mn on 2007-06-06
There is a simpler way, for us GUI huggers ;-)

Go to menu System -> Preferences -> Removable drives and media, then to Multimedia tab and under DVD section (middle one) type vlc %m instead of totem %m. 

That's it!

The same goes for other media/disc types.

Plaese have in mind that:

1. it only works when DVD is freshly inserted (i.e. in autoplay) and
2. it works in Feisty Fawn, dunno about the other versions.

Enjoy.

Greetings from Montenegro
Hogar

---

### Post by jnorthr on 2007-09-02
Ok, good idea. So i did that and now when i insert a BBC dvd of Dr.Who. It does start vlc, but never plays anything. Where can i look to see why it won't play ? I looked in dmesg and found these error messages: 
>  5254.328000] ide: failed opcode was: unknown
[ 5254.328000] hdc: error code: 0x70  sense_key: 0x05  asc: 0x6f  ascq: 0x03
[ 5254.328000] end_request: I/O error, dev hdc, sector 565448
[ 5254.328000] Buffer I/O error on device hdc, logical block 141362
[ 5254.368000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[ 5254.368000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[ 5254.368000] ide: failed opcode was: unknown
[ 5254.368000] hdc: error code: 0x70  sense_key: 0x05  asc: 0x6f  ascq: 0x03
[ 5254.368000] end_request: I/O error, dev hdc, sector 565452
[ 5254.368000] Buffer I/O error on device hdc, logical block 141363
[ 5254.368000] Buffer I/O error on device hdc, logical block 141364
[ 5254.368000] Buffer I/O error on device hdc, logical block 141365
[ 5254.368000] Buffer I/O error on device hdc, logical block 141366
[ 5254.368000] Buffer I/O error on device hdc, logical block 141367
[ 5254.440000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[ 5254.440000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[ 5254.440000] ide: failed opcode was: unknown
[ 5254.440000] hdc: error code: 0x70  sense_key: 0x05  asc: 0x6f  ascq: 0x03
[ 5254.440000] end_request: I/O error, dev hdc, sector 565628
[ 5254.440000] Buffer I/O error on device hdc, logical block 141407
[ 5254.440000] Buffer I/O error on device hdc, logical block 141408
[ 5254.440000] Buffer I/O error on device hdc, logical block 141409
[ 5254.440000] Buffer I/O error on device hdc, logical block 141410
[ 5339.620000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[ 5339.620000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[ 5339.620000] ide: failed opcode was: unknown
[ 5339.620000] hdc: error code: 0x70  sense_key: 0x05  asc: 0x6f  ascq: 0x03
[ 5339.620000] end_request: I/O error, dev hdc, sector 565464
[ 5339.620000] printk: 47 messages suppressed.
[ 5339.620000] Buffer I/O error on device hdc, logical block 141366
[ 5339.620000] Buffer I/O error on device hdc, logical block 141367


---

### Post by jnorthr on 2007-09-08
Gentlemen:
As per your other posts, i've tried to play a BBC video of Dr.Who using a command like:
wxvlc dvdsimple:///dev/dvd
giving:
jim@Tiny:~$ wxvlc dvdsimple:///dev/dvd
VLC media player 0.8.6 Janus
[00000291] dvdread demuxer error: read failed for block 0
[00000280] main playlist: nothing to play

[3]+  Stopped                 wxvlc dvdsimple:///dev/dvd

but no joy. In fact, my VLC will not play any DVD's.. unless i use w98se on the same machine. Am i missing a codec ? The dvd packaging  says 
Region 2+4 PAL UK
DVD9 16:9
Dolby Stereo

---

### Post by Sbarton on 2007-09-22
Thanks hogar_mn, this works fine for me.
regards

---

### Post by chrismine on 2007-10-02
> **hogar_mn said:**
> There is a simpler way, for us GUI huggers ;-)

Go to menu System -> Preferences -> Removable drives and media, then to Multimedia tab and under DVD section (middle one) type vlc %m instead of totem %m. 

That's it!

The same goes for other media/disc types.

Plaese have in mind that:

1. it only works when DVD is freshly inserted (i.e. in autoplay) and
2. it works in Feisty Fawn, dunno about the other versions.

Enjoy.

Greetings from Montenegro
Hogar

Can somebody please tell what the %m means?

---

### Post by vijaym on 2007-11-07
thanks for this info. 
What about other files which are already on the pc or come as email attachments. when i click on those totem opens. how can i default to VLC

Vijay

---

### Post by Sbarton on 2007-11-07
You could try right clicking and choosing 'Open with other application' to see if you can open your files.
regards

---

