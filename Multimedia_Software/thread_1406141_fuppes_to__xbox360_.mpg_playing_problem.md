---
title: "fuppes to  xbox360 .mpg playing problem"
date: 2010-02-13
forum: Multimedia Software
---

### Post by neill64 on 2010-02-13
i know this has probably been covered in the forum somewhere but i have tried various things and still have a problem.
i am running ubuntu 9.10 and fuppes 661 and i have stacks of .mpg files that will play on my PS3 over the network but when i try to play on my xbox 360 it connects ok but just says no videos found. i have changed various bits of the .cfg file and done the db rebuild and virtual contaner rebuild a fair few times and still get the same problem.

can anyone offer an advice as i am running out of ideas ?

---

### Post by Shhnap on 2010-02-14
Lets try basic debugging first. Can you get any other media files to play?

Please try wmv files and avi files. If you can view those then it is a good sign what we can get the mpg files working. Thanks.

---

### Post by neill64 on 2010-02-15
tried avi and wmv and mp4 and none of them are recognised.

---

### Post by Shhnap on 2010-02-15
> **neill64 said:**
> tried avi and wmv and mp4 and none of them are recognised.

That means that you will not be able to see anything; though I'm not sure why. Have you have enabled the XBox device in the devices list and followed the basic setup guide here? [http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Microsoft_Xbox_360#Basic_Setup](http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Microsoft_Xbox_360#Basic_Setup)

---

### Post by neill64 on 2010-02-16
i have done the basic setup and am using the default vfolder.cfg and an amended fuppes.cfg (attached), PS3 works fine but the xbox is a different matter.

---

### Post by Shhnap on 2010-02-16
> **neill64 said:**
> i have done the basic setup and am using the default vfolder.cfg and an amended fuppes.cfg, PS3 works fine mut the xbox is a different matter.

That's very odd. Can you post your fuppes.cfg? And maybe the vfolder.cfg too?

---

### Post by neill64 on 2010-02-17
The file attached above is my fuppes.cfg file, I thought I had found the problem as my brooder had xbox=disabled as default but changed it a rebuilt the virtual container and still no luck. As another test I put a non drm mp3 file on my server and the xbox does not see that either

---

### Post by neill64 on 2010-02-17
latest update, i have done some more fiddling with my fuppes.cfg file and can now see mp3 files and wmv files but it still wont see my .mpg files. i am new to this stuff and have read that the xbox 360 does not recognise mpg as an extension, do i need to do something with mime or transcoding ?

and forgot to say thanks for the help

---

### Post by art2003 on 2010-04-01
I am with the same problem.

Xbox 360 can play the .avis perfectly fine (divx, xvid) files on my HTPC but it does not show .mpg or .ts

What is the most efficient (less cpu load) transcoding settings to transcode .mpg and .ts files to a format the xbox 360 will accept (avi, mp4, wmv)

This is my current setting in fuppes.cfg (the xbox 360 sees the mpg files this way but does not play them giving a network error, the avi files work fine (no transcoding there) )

```

  <file ext="mpg">
             <type>VIDEO_ITEM</type>
             <mime_type>video/mpeg</mime_type>
             <transcode enabled="true">         
               <transcoder>ffmpeg</transcoder>
               <ext>avi</ext>
               <mime_type>video/avi</mime_type>         
               <video_codec>xvid</video_codec>
               <audio_codec>lame</audio_codec>
               <video_bitrate>1800000</video_bitrate>
               <audio_bitrate>128000</audio_bitrate>
             </transcode>
           </file>

```

Any suggestions?

---

