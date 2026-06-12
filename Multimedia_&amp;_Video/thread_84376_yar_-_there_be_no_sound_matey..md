---
title: "yar - there be no sound matey."
date: 2005-10-30
forum: Multimedia &amp; Video
---

### Post by teeler on 2005-10-30
Sooo i've got mpd ([http://www.mpd.org](http://www.mpd.org)) running on a box, and suddenly it drives itself into an insanely horrid sounding loop. 

Stunned, i spill my soup all overmyself and rush up to turn the volume down because my client (gmpc) has proven unresponsive to the task.

Upon further inspection and a restart of mpd, i find that I hear nothing. Not only do I hear nothing, but the behavior is quite suspicious as well:

> 
.....
9622"Oct 30 20:03 : problems opening audio device while playing "http://205.188.215.229:8018"


Naturally I investigate further,

> 
tyler@m0tivator:~/music/Doves$ mpg321 Doves\ -\ 01\ -\ Some\ Cities.mp3
High Performance MPEG 1.0/2.0/2.5 Audio Player for Layer 1, 2, and 3.
Version 0.59q (2002/03/23). Written and copyrights by Joe Drew.
Uses code from various people. See 'README' for more!
THIS SOFTWARE COMES WITH ABSOLUTELY NO WARRANTY! USE AT YOUR OWN RISK!
Title  : Some Cities                     Artist: Doves
Album  : Some Cities                     Year  :
Comment:  00001426 00001659 00003475 00  Genre :

Playing MPEG stream from Doves - 01 - Some Cities.mp3 ...
MPEG 1.0 layer III, 128 kbit/s, 44100 Hz joint-stereo
Can't find a suitable libao driver. (Is device in use?)


Now i'm stumped. 
Even more curious,

> 
root@m0tivator:~/music/Doves# fuser /dev/*
/dev/apm_bios:        6902
/dev/console:         6744
/dev/fd:              7579
/dev/initctl:            1
/dev/log:             6643
/dev/mem:             6793m
/dev/null:            3377  6660  6675  6688  6695  6697  6701  6743  6744  6853  6855  6934  6938  6944  6965  7001  7002  7003  7142  7158  7159  7259  7273 7286  7357  7370  7401  7459  7460  7461  7462  7463  7466  7468
/dev/ptmx:            7466  7468
/dev/pts:
/dev/shm:
/dev/stderr:          7469  7562  7579
/dev/stdin:           7469  7562  7579
/dev/stdout:          7469  7562  7579
/dev/tty1:            7433
/dev/tty2:            7434
/dev/tty3:            7435
/dev/tty4:            7436
/dev/tty5:            7437
/dev/tty6:            7438
/dev/tty7:            6793
/dev/xconsole:        6643

Which turned up nothing familiar in the way of sound. 

I checked lsmod, and I do indeed have my sound card modules loaded, and alsamixer reports a valid sound card as well as valid levels and all that.

SOoooooooooo what happened? Pleeeeeeeeease heeelp me...i'm stereo-less without this!!! ;)

---

