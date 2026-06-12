---
title: "Recommended CD ripper/encoder?"
date: 2009-12-05
forum: Multimedia Software
---

### Post by The Bright Side on 2009-12-05
Hey guys!

I switched to 9.10 this weekend (it's amazing), and I found that I can no longer install Grip, so I'm looking for a new CD ripper and encoder to use. There seem to be a couple out there, but I didn't find a single one that I could install through Synaptic or at least download as a deb, they're all only available as source codes, and I tried coding from source in the past, I f*cked up every single time...

Anybody have an idea where I can find a good CD ripper and encoder?

Thanks!

EDIT: it would have to be one with a GUI...

---

### Post by ikacer on 2009-12-05
There are several to choose from, though it all depends on what you want from your CD ripper. If you want extremely high quality encodes, I would suggest Rubyripper. It is not available in deb format, but it is very easy to compile. Instructions to do so can be found here:
[http://wiki.hydrogenaudio.org/index.php?title=Rubyripper]("http://wiki.hydrogenaudio.org/index.php?title=Rubyripper")
If you choose this I would recommend using 'checkinstall' instead of 'make install'.

If you aren't obsessed with a near perfect quality rip, then there are many others that are available as deb files. 'ripperx' seems to be a popular choice, though I haven't tried it myself, and it is available via Symantic.

---

### Post by The Bright Side on 2009-12-06
Thanks! I actually found a rubyripper .deb, but I wonder one thing about this program: how do I get it to actually fetch my CD's data from freedb? I set it up in the Preferences, but when I insert a CD, it doesn't find the info for some CDs, and for other CDs, it finds "CDDB info", so that sounds to me like it's not looking on freedb.

Also, do you know about the parameters for vorbis? The usual value is "-q 4", but what's better and what's worse, what's the range for the -q parameter and is this VBR?

---

### Post by Uncle Spellbinder on 2009-12-06
There is a PPA  repo someone set up for Rubyripper -

[https://launchpad.net/~aheck/+archive/ppa](https://launchpad.net/~aheck/+archive/ppa)

---

### Post by andrew.46 on 2009-12-07
Hi The Bright Side,

You might be interested to read the following:

CDRipping - Ubuntu Community Documentation
[https://help.ubuntu.com/community/CDRipping](https://help.ubuntu.com/community/CDRipping)

My only reservation with this page is that it downplays my own personal ripper/encoder which is abcde :).

All the best,

Andrew

---

### Post by cascade9 on 2009-12-07
> **The Bright Side said:**
> Thanks! I actually found a rubyripper .deb, but I wonder one thing about this program: how do I get it to actually fetch my CD's data from freedb? I set it up in the Preferences, but when I insert a CD, it doesn't find the info for some CDs, and for other CDs, it finds "CDDB info", so that sounds to me like it's not looking on freedb.

Also, do you know about the parameters for vorbis? The usual value is "-q 4", but what's better and what's worse, what's the range for the -q parameter and is this VBR?

AFAIK, freeDB was bought by Magix a few years ago. No idea how that happened, but its explains why there are limited numbers of programs that use freeDB under linux these days.

MusicBrainz might be better than freeDB these days, if you want to avoid CDDB. Sound Juicer works with it, and like most of the linux rippers, Sound Juicer is just a front-end for CDparanioa. It should be avaible from synaptic, as it is ubuntus default ripper. 

Vorbis goes from -q0 (64k/sec) to -q10 (500k/sec). IMO, as far as is worth going with vorbis is -q8 (256k) and -q9 (320k). If your even thinking about -q10, you might as well use .flac lossless. Unles there is soem reason for using 500k lossy files like your portable media player only supports .ogg (which is very rare now, .flac support is probably more common than .ogg support) 

There is also -q- 1 and -q- 2, but at 48 and 32k/sec, all that would be good for is speech, and speex would be better for that. Vorbis is VBR, unless you use some encoder setting that forces CBR.

---

### Post by mc4man on 2009-12-07
If you used that repo's .debs (he split up the cli and gui versions), or similary built,  there would of been a 'recommend' of cd-discid  that you might or it might not of installed.
to ck.
```
sudo apt-get install cd-discid
```

> Also, do you know about the parameters for vorbis?


```
man oggenc
```

> -q n, --quality=n
              Sets encoding quality to n, between -1 (very low) and  10  (very
              high). 


---

### Post by The Bright Side on 2009-12-07
Yeah that page in the Community Ubuntu Documentation confused the heck outta me because it says that Sound Juicer is installed by default. Where? I can't find it.
I tried Rubyripper, it works well on my laptop, but on my desktop PC, when I click on "Rip CD now!", nothing happens. Nothing at all. :-(


EDIT: I installed RipOff from the Repos and it's actually pretty cool!

---

### Post by dnairb on 2009-12-07
I've recently started using Rubyripper, with great success. I like the fact that one can encode to different formats at the same time, and that it rips the CDs a number of times to check that the ripping is consistent.

Another surprising point is that as Rubyripper isn't confined by the "tracks" on a CD, it finds hidden tracks that you wouldn't hear through a conventional CD player, or by using Sound Juicer (such as at the start of Kylie's "Light Years" CD or The Music's "The Music" CD)

---

### Post by cascade9 on 2009-12-07
Rubyripper is what I use on linux. IMO its not quite as good at dealing with damaged CDs as EAC is, but its pretty close, and its the best of all the linux rippers I've used.

---

### Post by 1083 on 2009-12-07
[http://www.translation.pk/check-republic-czech-tra](http://www.translation.pk/check-republic-czech-tra)
Regards,
Muhammad Riaz-5032

---

