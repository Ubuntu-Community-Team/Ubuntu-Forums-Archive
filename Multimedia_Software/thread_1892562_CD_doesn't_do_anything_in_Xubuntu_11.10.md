---
title: "CD doesn't do anything in Xubuntu 11.10"
date: 2011-12-08
forum: Multimedia Software
---

### Post by M_Mynaardt on 2011-12-08
Hi!

I've got a new install of Xubuntu 11.10 on my computer.  I can't seem to get anything to happen when I pop in a music CD to play.  It's a new CD and it works just fine in a CD player, but when I pop it into my computer, I just get a message to the effect that it's unmountable.

I'm not having trouble accessing my sound files, so it seems a bit odd that the CD is unresponsive.

Would there be a setting I'm overlooking?

Thanks in advance!

---

### Post by BC59 on 2011-12-08
Silly question but did you install the restricted extras?

---

### Post by editheraven on 2011-12-08
Post the output of  wodim --devices and wodim -scanbus.

Then try  mplayer -ao alsa cdda:// .

---

### Post by M_Mynaardt on 2011-12-08
> **BC59 said:**
> Silly question but did you install the restricted extras?

Yes I did, actually; both Xubuntu and Ubuntu restricted extras.  That was to get Parole to play some Videos earlier on.

---

### Post by M_Mynaardt on 2011-12-08
> **editheraven said:**
> Post the output of  wodim --devices and wodim -scanbus.

Then try  mplayer -ao alsa cdda:// . Change cdda with the output name of the device from  wodim --devices.

Right!  First thing I had to do was install wodim
```
~$ sudo apt-get wodim
```

Then I got the following output:
```
desktop:~$ wodim --devices
wodim: Overview of accessible drives (2 found) :
-------------------------------------------------------------------------
 0  dev='/dev/sg2'	rwrw-- : 'TSSTcorp' 'CD/DVDW SH-S162A'
 1  dev='/dev/sg3'	rwrw-- : 'LITE-ON' 'DVD SHD-16P1S'
-------------------------------------------------------------------------
desktop:~$ wodim -scanbus
scsibus3:
	3,0,0	300) 'TSSTcorp' 'CD/DVDW SH-S162A' 'TS02' Removable CD-ROM
	3,1,0	301) 'LITE-ON ' 'DVD SHD-16P1S   ' 'GS02' Removable CD-ROM
	3,2,0	302) *
	3,3,0	303) *
	3,4,0	304) *
	3,5,0	305) *
	3,6,0	306) *
	3,7,0	307) *
desktop:~$ 

```

Would there be something else I'm missing?

Thanks!

---

### Post by editheraven on 2011-12-08
If you insert an audio cd and try
```
mplayer -ao alsa cdda://
```

what happens?

---

### Post by M_Mynaardt on 2011-12-09
> **editheraven said:**
> If you insert an audio cd and try
```
mplayer -ao alsa cdda://
```

what happens?

Nothing happened (I had to install mplayer too) as far as playing tunes goes

The result was:
```
-desktop:~$ mplayer -ao alsa cdda://
mplayer: Symbol `ff_codec_bmp_tags' has different size in shared object, consider re-linking
Creating config file: /home/user/.mplayer/config
MPlayer SVN-r33713-4.6.1 (C) 2000-2011 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing cdda://.
Can't open disc.
Failed to open cdda://.


Exiting... (End of file)

```

---

