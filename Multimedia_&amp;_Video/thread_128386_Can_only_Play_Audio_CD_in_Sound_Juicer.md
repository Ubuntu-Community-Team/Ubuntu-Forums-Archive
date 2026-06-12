---
title: "Can only Play Audio CD in Sound Juicer"
date: 2006-02-11
forum: Multimedia &amp; Video
---

### Post by malacandra on 2006-02-11
When I use Sound Juicer, I can play an Audio CD just fine.

When I use KsCD, or Gnome's CD Player, of Grip, I cannot hear the CD at all (though the clock advances, indicating the program is playing it). I can't seem to hear an audio CD in any other application except Sound Juicer.

(I would prefer Grip because I like to use that for ripping & encoding).

(I also tried in VLC and it will play the CD, but the drive stutters and so does the music).

Any help is appreciated.

PS - If you can show me how to use Lame in Sound Juicer to encode MP3s, then that would be nice, too. (I want to be able to use the same program to listen and rip/encode.)

Thanks.
Mark

---

### Post by malacandra on 2006-02-11
Well, I didn't get Grip to play the CD so I could hear, but I got Sound Juicer to encode into mp3.

To do that, followed this link: [http://www.emcken.dk/weblog/archives/99-MP3-encoding-with-Sound-Juicer.html](http://www.emcken.dk/weblog/archives/99-MP3-encoding-with-Sound-Juicer.html)

You can do this from within SJ by editing or adding a new Profile. Restart SJ so it   will be available to select.

So, just gonna use SJ to play CDs and rip to mp3.

---

### Post by FarEast on 2006-02-12
Hi,

Regarding gnome CD player, it seems to use the device file /dev/dsp .
Check if the file exists in the following way.
$ ls -l | /dev | grep dsp

If /dev/dsp does not exist, loading the module 'snd-pcm-oss' may help.
$ sudo modprobe snd-pcm-oss

---

