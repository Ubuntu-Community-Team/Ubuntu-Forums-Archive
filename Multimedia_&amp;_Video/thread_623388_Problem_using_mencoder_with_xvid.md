---
title: "Problem using mencoder with xvid"
date: 2007-11-25
forum: Multimedia &amp; Video
---

### Post by Rayn on 2007-11-25
I'm trying to setup a user job to encode my recorded programs to xvid using mencoder (Too many problems with ffmpeg, even after a recompile from svn)

It has been working nicely, but the file size of the output files is completely random and unpredictable.  Sometimes and hour show is about 350 MB (well, 44 minutes minus the commercials) and sometimes it's 900 MB ... all using the same settings.  It seems like the variable bit rate function is wildly unpredictable.  I tried to set it up using a constant bit rate, but the command line it generates for mencoder is wrong (it adds the bitrate to the lameopts paramater instead of the xvidopts or whatever it is so the job crashes out) ..

Looking at the output of two files created by the job right now in windows explorer here's file one:
Duration: 00:48:51
Data Rate 302kbps
File size: 867 MB

and here's another encoded a few hours before:

Duration: 00:41:33
Data Rate: 116kbps
File Size: 283 MB

I'm happy with the quality of the second file, and there's no way I can archive 1 GB for a 45 minute video, that's just ridiculous.  Is this due to the achieved bit rate fluctuating heavily for VBR?  Is there a way I can fix it to make it closer to what I request (I'm looking for 1296).  If not, is there a way to see where nuvexport-xvid is using to generate it's parameters and make it work with CBR?  (I looked through the code but it seems to be using external perl packages .. I cant' find the specific source though ... not sure where to look)

I read the how-to guide on this forum, but encoding XViD at 4000 bit rate is a bit high for my available storage.  This is my xvid nuvexportrc set up:
```
<XviD>

    vbr          = yes   # Enable vbr to get the multipass/quantisation options
                         # (enabling multipass or quantisation automatically enables vbr)
    multipass    = yes   # You get either multipass or quantisation; multipass will override
    quantisation = 4   # 4 through 6 is probably right...  1..31 are allowed (lower is better quality)

    a_bitrate    = 144   # Audio bitrate of 256 kbps
    v_bitrate    = 1296   # Remember, quantisation overrides video bitrate

    width        = 512   # Height adjusts automatically to width, according to aspect ratio
    height       = auto

</XviD>
```Can anyone spare some advice or perhaps point me towards some recommended reading?  I am missing something. Thank you.

---

