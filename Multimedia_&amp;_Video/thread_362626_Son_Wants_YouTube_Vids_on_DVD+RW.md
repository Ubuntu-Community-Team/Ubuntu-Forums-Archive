---
title: "Son Wants YouTube Vids on DVD+RW"
date: 2007-02-15
forum: Multimedia &amp; Video
---

### Post by SuperMike on 2007-02-15
My son is skateboard crazy. Every sentence he speaks has "skateboard" in it. Anyway, he says he wants me to download YouTube skateboard videos onto DVD+RW so that he can watch them downstairs on our widescreen TV and DVD player.

I think I can do the FLV download, at least...

[FONT="Courier New"]bu="http://youtube.com/get_video.php?";mkdir -p ~/mp3;cd ~/mp3;read -p "YouTube url? " ur;read - p "Name? " nv
echo;echo;
wget ${ur} -O /tmp/y1;uf=${bu}`grep player2.swf /tmp/y1 | cut -d? -f2 | cut -d\" -f1`;wget "${uf }" -O /tmp/out.flv[/FONT]

...and then I'm ***guessing*** the following might be the MPEG translation:

[FONT="Courier New"]ffmpeg -i /tmp/out.flv -f mpegvideo /tmp/out.mpg[/FONT]

...although these are the formats that might work instead of mpegvideo:

mpeg1video
mpeg2video
mpeg4
msmpeg4
msmpeg4v1
msmpeg4v2
dvbsub
dvdsub
dvvideo

...and then once I have this MPEG, how do I get it on the DVD?

(BTW, I look at pp. 137-142 of O'Reilly's Ubuntu Hacks book on how to create a video DVD using tovid, makexml, dvdauthor, mplayer, mkisofs, and dvdrecord, so I might be able to figure it out -- but the example it gives is with an AVI file instead of an MPEG.)

---

### Post by RomeReactor on 2007-02-15
Hi. If you already have the mpeg files, then i suggest using [AviDemux]("http://fixounet.free.fr/avidemux/") as it gives you the option to encode to DVD (though most DVD players i've seen already play mpeg's); anyway, its [Wikipedia]("http://en.wikipedia.org/wiki/Avidemux") entry has a lot of information. Look for it in Synaptic.

---

### Post by SuperMike on 2007-02-15
Okay, so the technique with...

ffmpeg -i /tmp/out.flv -f mpegvideo /tmp/out.mpg

...worked, but there was no sound. I know that it could see the sound in the FLV file, however. I've also been able to extract the MP3 out of it on its own. It's the combining of sound and video that's tough. So, if anyone feels eager to jump on figuring that one out, let me know.

Also, RomeReactor, you make a good point I didn't think about. I could just put it on CDRs or DVDRW's as data and it would probably play just fine on my DVD player without all the hub-bub of encoding it as a true VCD. I'll have to see.

---

### Post by daveisadork on 2007-02-15
Try this:

```
ffmpeg -i input_file.avi -target ntsc-dvd -aspect 4:3 movie.mpg
```

---

### Post by SuperMike on 2007-02-15
Seems I was thinking to hard:

ffmpeg -i /tmp/out.flv /tmp/out.mpg

...and ffmpeg just figures it out.

Now I'm working on putting it on a CDR and I hope that works. I discovered in my new PC that I don't have a DVDRW recorder, but do have a CDR/CDRW recorder and do have a DVDROM playback. (I know -- laugh it up -- I just inherited this PC from my office and hadn't had time to check all its features out yet.)

---

### Post by SuperMike on 2007-02-15
Darn. I stick in a CDR and a window pops open and says Burn Audio CD, Burn Photo CD, or Burn Data CD. I choose Burn Data CD. It then presents a window that says CDROM. I copy the file to the CDR and then click the Write Contents To Disc button. It then says CDRW and Maximum Possible. I click OK and it then says "Insert blank disc in recorder." I had already done so, therefore I clicked OK again. It then repeats this question again, over and over, until I hit cancel.

So for some reason, now I can't burn a CDR. Bummer.

---

### Post by RomeReactor on 2007-02-16
Are you trying to burn a **new** rewritable cd? if it's a used one, maybe you need to erase it first. I don't remember if GnomeBaker can erase rewritables, but it wouldn't hurt to install it (though i prefer K3B); both are in Synaptic

---

### Post by RomeReactor on 2007-02-16
Or, if you *are* using a CDR, make sure you don't cram too much data on the disc (690 MB or less would be ideal, i think).

---

