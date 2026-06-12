---
title: "genisoimage -dvd-video making incorrect image"
date: 2013-03-26
forum: Multimedia Software
---

### Post by Elbiot on 2013-03-26
Hi all,

I followed [http://ubuntuforums.org/showthread.php?t=120186](http://ubuntuforums.org/showthread.php?t=120186)

The author specifies that VIDEO_TS must be in an lower sector than AUDIO_TS when viewed with isoinfo.  He also specifies that AUDIO_TS must be present for a dvd to play in all commercial players. 

I have VIDEO_TS and AUDIO_TS in a directory called dvd_dir.  (This dvd has no menu,btw).

I run mkisofs -dvd-video -o ./dvd.img ./dvd_dir/

but, 

```

~/dvdtest$ isoinfo -i dvd.img -l

Directory listing of /
d---------   0    0    0            2048 Mar 25 2013 [    276 02]  . 
d---------   0    0    0            2048 Mar 26 2013 [    276 02]  .. 
d---------   0    0    0            2048 Mar 25 2013 [    277 02]  AUDIO_TS 
d---------   0    0    0            2048 Mar 25 2013 [    278 02]  VIDEO_TS 


Directory listing of /AUDIO_TS/
d---------   0    0    0            2048 Mar 25 2013 [    277 02]  . 
d---------   0    0    0            2048 Mar 25 2013 [    276 02]  .. 


Directory listing of /VIDEO_TS/
d---------   0    0    0            2048 Mar 25 2013 [    278 02]  . 
d---------   0    0    0            2048 Mar 25 2013 [    276 02]  .. 
----------   0    0    0            6144 Mar 25 2013 [    282 00]  VIDEO_TS.BUP;1 
----------   0    0    0            6144 Mar 25 2013 [    279 00]  VIDEO_TS.IFO;1 
----------   0    0    0           75776 Mar 25 2013 [1470553 00]  VTS_01_0.BUP;1 
----------   0    0    0           75776 Mar 25 2013 [    285 00]  VTS_01_0.IFO;1 
----------   0    0    0      1073709056 Mar 25 2013 [    322 00]  VTS_01_1.VOB;1 
----------   0    0    0      1073709056 Mar 25 2013 [ 524594 00]  VTS_01_2.VOB;1 
----------   0    0    0       863614976 Mar 25 2013 [1048866 00]  VTS_01_3.VOB;1 



```

As you can see, VIDEO_TS is at sector 278, and AUDIO_TS is at 277.  I can open the image using Movie Player and it works as expected, but when I go to burn it as an image with Brasero, it complains that this isn't a valid dvd image.

genisoimage is version 1.1.10 and I am running ubuntu 10.04

Is Brasero choking because of what isoinfo reveals?  Or is there something else wrong?

---

### Post by matt_symes on 2013-03-27
Hi

Did you author the dvd before creating the ISO ?

I don't know if this will be the issue or not but...

... my steps in the past have been to 

1. Transcode using ffmpeg (if required).
2. Use dvd-author to author the DVD.
3. Use mkisofs to create the ISO image.
4. Use growisofs to burn to a DVD. 

This has always worked for me.

Kind regards

---

### Post by Elbiot on 2013-03-27
Yes I authored the DVD.  That's how AUDIO_TS and VIDEO_TS were created!  I used dvdauthor with an xml file that looked like this:

```

<dvdauthor dest="./dvd_dir">
 <vmgm/>
 <titleset>
  <titles>
   <pgc>
    <vob file="./dvd.vob" chapters="0:0:0, 0:2:41, 0:17:55, 0:22:55, 0:26:6, 0:40:42, 0:45:28," pause="3"/>
    <post> call vmgm menu entry title ; </post>
   </pgc>
  </titles>
 </titleset>
</dvdauthor>
```

and the command dvdauthor -x dvd.xml -o test (but the -o doesn't seems to make any difference, i guess the xml file overrides it)
I created the vob with ffmpeg using the "-target ntsc-dvd" switch

At all stages prior to burning, the file, directory, and then image all play in Movie Player as a DVD.  

growisofs is currently burning the image.  It hasn't thrown any errors, so I'll report back about the resulting dvd.

Thanks

---

### Post by Elbiot on 2013-03-27
growisofs burned the DVD and it played in an old DVD player, so it must have been an issue with Brasero.

Thanks!

---

### Post by matt_symes on 2013-03-27
Hi

> **Elbiot said:**
> growisofs burned the DVD and it played in an old DVD player, so it must have been an issue with Brasero.

Thanks!

Excellent. I'm glad it worked for you.

I have had bad copies in the past when i have authored the DVD incorrectly and that is why i mentioned it.

It's very easy to script the entire transcoding, authoring and burning process using these command line tools.

You may want to consider doing something similar. Just a though.

Kind regards

---

