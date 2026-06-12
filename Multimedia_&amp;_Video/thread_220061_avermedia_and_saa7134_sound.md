---
title: "avermedia and saa7134 sound?"
date: 2006-07-20
forum: Multimedia &amp; Video
---

### Post by sc30317 on 2006-07-20
Hey All,

I have an avermedia tv pc cardbus (E501r).  I have gotten the video from this card to work perfectly with these sets of code (done in this order):

sudo rmmod saa7134_alsa
sudo rmmod saa7134
sudo modprobe tda9887 debug=2
sudo modprobe saa7134 card=46 tuner=66

The video for this card works perfectly.  However, the sound does not work at all in any tv viewer (tvtime, mythtv ive tried).  Any help?

---

### Post by sc30317 on 2006-07-21
please help, im so close and i have been trying to get this to work for >6 months

---

### Post by LeonHeart on 2006-08-09
check the volume control and see if the line-in in "capture" is enabled....

---

### Post by mike.thorton on 2006-08-10
Hello, I've asked for similar problem in the forum a few hours ago..
([http://www.ubuntuforums.org/showthread.php?t=232871](http://www.ubuntuforums.org/showthread.php?t=232871))

Please, can you make for us simple howto? It would make us happy..

Where did you get Ubuntu drivers?

Thanks

---

### Post by Padre on 2006-09-12
sound work with saa7134_oss driver.
use sox command:
[COLOR="Blue"]sox -c 2 -s -w -r 32000 -t ossdsp /dev/dsp1 -t ossdsp -w -r 32000 /dev/dsp[/COLOR]
where dsp1 is device created by saa7134_oss

---

