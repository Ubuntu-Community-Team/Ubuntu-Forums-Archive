---
title: "Problem with DVD drive and Sound"
date: 2009-01-03
forum: Multimedia Software
---

### Post by yhertz on 2009-01-03
Hey,
I just installed ubuntu 8.10 .
1. I've got 2 dvd drives on my computer, one of them works properly and reads all of my discs, but the other one doesn't... it only reads the ubuntu installation cd and some cd's with mp3 files and nothing else.
It used to read everything fine when I was working with windows before.

> [ 15.236248] ata9.00: ATAPI: LITE-ON DVDRW LH-20A1P, KL0A, max UDMA/66
[ 15.236264] ata9.01: ATAPI: SONY DVD-ROM DDU1615, FYS1, max UDMA/33
[ 15.656102] scsi 10:0:0:0: CD-ROM LITE-ON DVDRW LH-20A1P KL0A PQ: 0 ANSI: 5
[ 15.657063] scsi 10:0:1:0: CD-ROM SONY DVD-ROM DDU1615 FYS1 PQ: 0 ANSI: 5
[ 16.296361] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray

2. I couldn't talk through skype, I got a notification that said there is some sound problem. I've tried the skype test call and got this message "Problem with audio play back" . I posted a Q on another ubuntu forum and followed the suggestions in their reply:

> 
killall pulseaudio
sudo apt-get remove pulseaudio
sudo apt-get install esound
sudo rm /etc/X11/Xsession.d/70pulseaudio

which didn't work. 
and then this one: 

> sudo apt-get -f install

Now it looks like the test call works okay but...NOW I DONT HAVE SOUND AT ALL ON MY COMPUTER!!


Suggestions anyone ? Would appreciate all help I can get... 
I'm desperate... :(

---

