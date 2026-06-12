---
title: "recommended cd ripper/encoder"
date: 2007-08-12
forum: Multimedia &amp; Video
---

### Post by ayu on 2007-08-12
Hello! Hope I don't start a flame war here :wink:.  I'm new to linux and was wondering what cd rippers and encoders you recommend.  Is Sound Juicer 2.16.3 (default on Feisty) "good enough" if I change the ogg setting to .8 instead of the default of .5?  For reference of what I consider "good enough", on Windows I used EAC to rip the CDs, and then compressed with lame to mp3s of VBR 256 kbps.  However, as the cd's are all free from defects, I came to realize EAC isn't really necessary to rip cds.  I've seen other recommendations of Grip or cdparanoia, but like I stated early, is it really necessary to install another program; is there a substantial difference in encoding quality?  Thanks!

---

### Post by moore.bryan on 2007-08-12
*i might be a minimalist/cli fan, but i think [abcde]("http://lly.org/~rcw/abcde/page/") is incredibly powerful...*

---

### Post by ayu on 2007-08-14
Are there any other suggestions? And remember, the most important question is "Is there any real difference in the compression quality?"  Thanks!

---

### Post by jctosu on 2007-08-15
Sound Juicer is a good program, if you set your quality settings to CD quality lossy and set quality to 'quality=.8' you will get very good quality rips, at least as good as 256KBps MP3 VBR, that should be a good setting to go with for just about anybody.

---

### Post by jmate24 on 2007-08-15
Gnome Baker?

---

### Post by andrew.46 on 2007-08-24
Hi,

 I suspect that you are asking the wrong question:

> **ayu said:**
> Are there any other suggestions? And remember, the most important question is "Is there any real difference in the compression quality?"  Thanks!

 ogg and mp3 are lossy formats so quality *will* vary with 'compression', although this will not easily be apparent to most listeners.  If you want *no* loss of quality you would use flac.

                       Andrew

---

### Post by ayu on 2007-08-25
> **andrew.46 said:**
> Hi,
 I suspect that you are asking the wrong question:
 ogg and mp3 are lossy formats so quality *will* vary with 'compression', although this will not easily be apparent to most listeners.  If you want *no* loss of quality you would use flac.

                       Andrew

Yes, ideally Program A and Program B will result in the same identical file given the same compression settings.  However, in the mp3 world, it is generally accepted LAME is the best encoder out there.  (Although I'm no audio expert myself so I'm not sure why).  I'm asking whether the encoder used by SoundJuicer, whatever that is, is considered "good enough," when compared to other ogg encoders out there.  
Also, in the case for damaged CDs, reading the same bit twice will sometimes give different results.  This is usually okay for audio CDs because it is rarely noticeable during playback, but for those audio aficionados out there, they will want to rip the CD with EAC.  Again, I'm asking whether the built in ripper is comparable to EAC, or should I really get a dedicated ripping program?  And would it really make a difference for nondamaged CDs (I'm guessing no)?
Lastly, I've stated that 256kbps vbr mp3's were good enough for me.  I am not looking for lossless as I honestly can't hear the difference with my speakers.  Thanks!

---

### Post by andrew.46 on 2007-08-26
Hi again!

 Can I suggest that might try the encoding tools directly rather than through a GUI? It is the way I encode my own mp3s / ogg files and it really eliminates all question of which GUI program is better.

 I have written a brief walkthough at:

[http://people.aapt.net.au/~adjlstrong/ubuntu_cli.html#mp3](http://people.aapt.net.au/~adjlstrong/ubuntu_cli.html#mp3)

 And I would love to hear your thoughts on this approach to encoding. To manipulate the quality of the mp3 encoding you would normally choose *one* of the following:

```
LAMEOPTS='--preset standard'
LAMEOPTS='--preset extreme'
LAMEOPTS='--preset insane'
```

   All the best,

       Andrew

---

### Post by ayu on 2007-08-26
Hello,
Yes exactly!  I was wondering which ogg encoder was considered the best, if there are more than one.  After digging through some manuals, I realize SoundJuicer uses Gstreamer plugins which uses "vorbisenc."  On your site, I see for ogg you tell abcde to use "oggenc."  Are these the same or different?  Which one will produce better results given the same settings?
Thanks!

---

### Post by andrew.46 on 2007-08-26
Hi,

 You have raised some interesting points:

> **ayu said:**
> Hello,
Yes exactly!  I was wondering which ogg encoder was considered the best, if there are more than one.  After digging through some manuals, I realize SoundJuicer uses Gstreamer plugins which uses "vorbisenc."  On your site, I see for ogg you tell abcde to use "oggenc."  Are these the same or different?  Which one will produce better results given the same settings?
Thanks!

 The reason I use oggenc is simply that it is part of the vorbis-tools package that can be downloaded from the Ubuntu Repositories. It contains:

> vorbis-tools contains oggenc (an encoder), ogg123 (a playback tool), ogginfo (displays ogg information), oggdec (decodes ogg files), vcut (ogg file splitter), and vorbiscomment (ogg comment editor).

and is a pretty standard ogg package. As to what soundjuicer uses I would only be guessing and I notice that the documentation for Soundjuicer gives nothing away. Can anybody help out here?

In oggenc sound quality is adjusted differently to Sound Juicer:

>        -q n, --quality=n
              Sets encoding quality to n, between -1 (very low) and  10  (very
              high).  This  is  the  default mode of operation, with a default
              quality level of 3. Fractional quality levels such  as  2.5  are
              permitted.  Using  this  option  allows the encoder to select an
              appropriate bitrate based on your desired quality level.


Hopfully there is a SooundJuicer expert among us?

            Andrew

---

