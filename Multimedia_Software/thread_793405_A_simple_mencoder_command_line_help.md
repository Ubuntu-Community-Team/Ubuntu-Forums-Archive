---
title: "A simple mencoder command line help"
date: 2008-05-13
forum: Multimedia Software
---

### Post by orasetaina on 2008-05-13
ok ..ive tried to to do some encoding...but so far i havent got anyway...so was wondering if someone can help me out.

ok heres the scenario.

lets say I ripped a home video dvd and now its saved in a folder (A) on sdb5 as a vob file. There are several of these vob files totalling 4gb (lets just say). 

Ok now what i want is

join the files .... ( i can do that..a recently acquired skill, using comand line)
and encode to say avi. desired file size is 1gb.

so ill start off the command line ...

mencoder myhomevideo.vob.....

can someone give me a good line for conversion....considering all scaling and audio bitrates....
my target filesize would be about 1gb.
my video quality...well xvid or divx or avi is fine!

ive tried this 
[http://gentoo-wiki.com/HOWTO_Mencoder_Introduction_Guide](http://gentoo-wiki.com/HOWTO_Mencoder_Introduction_Guide)

but it just seems to complicated,

please help me finish this ......... :)

thanks in ...anticipation!!

---

### Post by cor2y on 2008-05-13
mecoder vob to avi well if you really want to learn how.
You will need to do a 2 pass encode or more either using xvid ,mpeg4 via lavc or x264 for video and libmp3lame for mp3 audio.
I can give you some examples for hq encodes
xvid
```

mencoder <filename> -oac mp3lame -lameopts cbr:br=128 -ovc xvid -xvidencopts pass=1 -o /dev/null
mencoder <filename> -oac mp3lame -lameopts cbr:br=128 -ovc xvid -xvidencopts pass=2:chroma_opt:vhq=4:bvhq=1:quant_type=mpeg:bitrate=900  -ofps 30000/1001 -o <filename.avi>

```
mpeg4
```

mencoder -o /dev/null -oac mp3lame -lameopts cbr:br=128 -ovc lavc -ffourcc DX50 -lavcopts vcodec=mpeg4:vbitrate=900:vhq:vpass=1 -ofps 30000/1001 <filename> ; mencoder -o <filename> -oac mp3lame -lameopts cbr:br=128 -ovc lavc -ffourcc DX50 -lavcopts vcodec=mpeg4:vbitrate=900:vhq:vpass=2 -ofps 30000/1001 <filename>
```
X264
```
mencoder <filename.avi> -ovc x264 -x264encopts pass=1:turbo=1:nr=500:psnr -oac mp3lame -lameopts cbr:br=128 -ofps 30000/1001 -o /dev/null

mencoder <filename.avi> -ovc x264 -x264encopts pass=2:nr=500:psnr:bitrate=900 -oac mp3lame -lameopts cbr:br=128 -ofps 30000/1001 -o <filename.avi>
```

The Easy way out is to use either a robust script like xvidenc/divxenc/h264enc or program with a gui frontend like say avidemux 

Encoding scripts
[http://xvidenc.sourceforge.net/](http://xvidenc.sourceforge.net/)
[http://divxenc.sourceforge.net/](http://divxenc.sourceforge.net/)
[http://h264enc.sourceforge.net/](http://h264enc.sourceforge.net/)

Avidemux
[http://avidemux.sourceforge.net/](http://avidemux.sourceforge.net/)
Avidemux Tutorials
[http://www.avidemux.org/admWiki/index.php?title=Main_Page#Tutorials_.26_guides](http://www.avidemux.org/admWiki/index.php?title=Main_Page#Tutorials_.26_guides)

There are other vob to avi tools that use mencoder just can't think of them now.
But others will have an idea.

---

### Post by orasetaina on 2008-05-14
why is a two pass required?
will just one not suffice?

---

### Post by orasetaina on 2008-05-14
i read somewhere that mencoder and mplayer are brother and sister...why cant mencoder be just amalgated into mplayer?

---

### Post by orasetaina on 2008-05-14
Anyone?

---

### Post by JH.Kael on 2009-08-29
> **cor2y said:**
> mecoder vob to avi well if you really want to learn how.
You will need to do a 2 pass encode or more either using xvid ,mpeg4 via lavc or x264 for video and libmp3lame for mp3 audio.
I can give you some examples for hq encodes
xvid
```

mencoder <filename> -oac mp3lame -lameopts cbr:br=128 -ovc xvid -xvidencopts pass=1 -o /dev/null
mencoder <filename> -oac mp3lame -lameopts cbr:br=128 -ovc xvid -xvidencopts pass=2:chroma_opt:vhq=4:bvhq=1:quant_type=mpeg:bitrate=900  -ofps 30000/1001 -o <filename.avi>

```
mpeg4
```

mencoder -o /dev/null -oac mp3lame -lameopts cbr:br=128 -ovc lavc -ffourcc DX50 -lavcopts vcodec=mpeg4:vbitrate=900:vhq:vpass=1 -ofps 30000/1001 <filename> ; mencoder -o <filename> -oac mp3lame -lameopts cbr:br=128 -ovc lavc -ffourcc DX50 -lavcopts vcodec=mpeg4:vbitrate=900:vhq:vpass=2 -ofps 30000/1001 <filename>
```
X264
```
mencoder <filename.avi> -ovc x264 -x264encopts pass=1:turbo=1:nr=500:psnr -oac mp3lame -lameopts cbr:br=128 -ofps 30000/1001 -o /dev/null

mencoder <filename.avi> -ovc x264 -x264encopts pass=2:nr=500:psnr:bitrate=900 -oac mp3lame -lameopts cbr:br=128 -ofps 30000/1001 -o <filename.avi>
```

The Easy way out is to use either a robust script like xvidenc/divxenc/h264enc or program with a gui frontend like say avidemux 

Encoding scripts
[http://xvidenc.sourceforge.net/](http://xvidenc.sourceforge.net/)
[http://divxenc.sourceforge.net/](http://divxenc.sourceforge.net/)
[http://h264enc.sourceforge.net/](http://h264enc.sourceforge.net/)

Avidemux
[http://avidemux.sourceforge.net/](http://avidemux.sourceforge.net/)
Avidemux Tutorials
[http://www.avidemux.org/admWiki/index.php?title=Main_Page#Tutorials_.26_guides](http://www.avidemux.org/admWiki/index.php?title=Main_Page#Tutorials_.26_guides)

There are other vob to avi tools that use mencoder just can't think of them now.
But others will have an idea.
I found this on google, the 2 pass encode worked great! Thanks!

---

