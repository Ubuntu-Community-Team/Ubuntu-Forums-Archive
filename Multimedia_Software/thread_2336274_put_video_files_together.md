---
title: "put video files together"
date: 2016-09-06
forum: Multimedia Software
---

### Post by jgw on 2016-09-06
I have a dvd with all the files on it.  What I am trying to do is to take 4 of the .vob files and create a new iso file which will play those 4 vob files as 1. I also have the bup and ifo files.  The reason is that I only want to play the 4 files and not any of the others.  This is an old movie (1959) and the original file contains a whole bunch of trailers, advertisements, etc. which I don't want to see.

Thank you..................

---

### Post by TheFu on 2016-09-07
I use **vobcopy** to get only the tracks desired off the media, then use mkvmerge to shovel them into an MKV container (still all the same contents), then you can use whatever DVD authoring software you like. Might be able to leave off the mkvmerge part.  Perhaps K3b? I dunno.

No transcoding should be involved with any of these methods.  

I don't use any dvd authoring software myself - stopped using video disks about 15 yrs ago. Data disks with H.264/DTS 5.1 inside an MKV container are pretty great.  If you need to support cheap media players, then H.264/AAC inside an MKV container works too.

---

### Post by SeijiSensei on 2016-09-07
[Handbrake]("https://launchpad.net/~stebbins/+archive/ubuntu/handbrake-releases") lets you select tracks as well.

---

### Post by TheFu on 2016-09-07
> **SeijiSensei said:**
> [Handbrake]("https://launchpad.net/~stebbins/+archive/ubuntu/handbrake-releases") lets you select tracks as well.

Handbrake is a GREAT tool!  I use it daily to transcode recorded TV into the h.264/ac3/mkv files - saving about 80% of the original size after cutting commercials (and 22min for every hour).  But if the goal is to create a DVD with DVD-Video, that transcoding is to be avoided.

Or does handbrake have a way to create DVD-video ISOs?  That would be fantastic for the OP!

---

### Post by jgw on 2016-09-07
Thanks for all the replies.  I will give this stuff a shot and post the results.

Thanks again!

---

### Post by SeijiSensei on 2016-09-07
> **TheFu said:**
> Or does handbrake have a way to create DVD-video ISOs?  That would be fantastic for the OP!
I don't know to be honest.  On the other hand, an H.264 encoding of a 1959 film on DVD probably won't lose much in translation.

I haven't used DeVeDe to author DVDs for quite some time, and it has undergone a major rewrite since I last used it.  Using Handbrake to extract the tracks to Matroska files, then using them to create the new ISO image with DeVeDe, might be one possible method.

---

### Post by jgw on 2016-09-07
thanks again for the replies.

Here is where I am at.  I downloaded a 1959 film called The Mouse That Roared.  I then copied the VIDEO_TS folder onto a thumb drive.  I then started taking a look at what I had.  The download included a bunch of trailers and advertisements for other movies.  I found the actual movie in 4 vob files.  I can play those files in any number of ways with no problem at all.  I then used winff to convert the vob files to mpeg-4 files.  I did this 2 ways, the first was to simply convert the vob files to mpeg files.  I think this is where my mistake was.  The vob files were named; VTS_01_1, VTS_01_2, VTS_01_3, VTS_01_4.  What was wrong is that I ignored the 30kb files called VTS_02_0, VTS_03_0, and VTS_04_0.  These were, I think, fillers.  So, I am now creating new mpeg files which also contain these files and see if its better.  My problem was that when I put them all together, with DeVeDe the files seemed to have missed a pile of the video.  Now I will use the newer mpeg files to do the same thing and, hopefully, things will work out.  There is also the hadnbrake program which I will also try.  I also tried the vobcopy thing but it did not work with a thumb drive (couldn't find anything)

---

### Post by goofprog on 2016-09-07
personally I use ffmpeg and concat them together.  I find it better because sometimes VOB files do not always have the same language on the same audio track.

---

### Post by TheFu on 2016-09-07
vobcopy is best used to clone a full DVD off the optical media.  The manpage explains all the options. It is an amazing tool.  The source input needs to be the top level directory of the DVD.

VOB files aren't 1-for-1 video files. There are indexes into various parts and often multiple "titles" are included in each vob file.  Really need to use something like **vobcopy** to get the "title" you want. Use **VLC** to see all the titles and pick the correct one.  Some DVDs will do strange copy-protection things and have 50-99 titles with 39 of them appearing to be about the size of the primary movie. Only 1 is actually the correct title, in the correct order. This is to confuse programs that copy the copyrighted content. 

If the DVD had copy protection and that was part of the physical media, then your copy of the vob files isn't complete.

---

### Post by jgw on 2016-09-09
DeVeDe			use to create dvd
MKVToolNix GUI	mkvmerge mkvinfo mkvextract mkvpropedit 
HandBrake		this will convert from and to almost everything
WinFF			this too will do conver

OK, I think I have worked it out.  I used WinFF to convert from vob to mpeg-4, then I used MKVToolNix GUI to run mkvmerge to merge the files.  It took me a while to run that one right.  The trick is not to simply add multiple files to merge but to add 1 new and then hit the little down arrow on the add new button and append the rest.  If you don't do that then they are not merged but simple converted to mkv files.  After the merge I used DeVeDe to create the dvd files.  This one too is slightly tricky.  When DeVeDe first comes up you are give a bunch of options.  If you are dealing with a dvd you choose the FIRST one as all the rest deal with CD's or other stuff.  The trick on all these things are to READ YOUR SCREEN!  (I have been preaching this for years and then forget it applies to me too! <g>)  One you have created the dvd files you can burn your dvd from this screen.  If, like me, you see its done and get out you will have to use something else to write your dvd (I used brasero).

Anyway, I thank everybody for their help and I will now mark this one as solved. (thanks again!)

---

### Post by nothingspecial on 2016-09-09
I always used to extract the vob files then

```
cat *.vob > movie.vob; avconv -i movie.vob -acodec aac -strict experimental -ac 2 -ar 48000 -ab 256k -vcodec libx264 -crf 20 -threads 0
```

(should work with ffmpeg now though not sure about the strict experimental option)

worked with my Harold Lloyd DVDs that are pre 1959 :P

Not bought a DVD in years though

---

### Post by TheFu on 2016-09-09
> **nothingspecial said:**
> 
Not bought a DVD in years though

That won't work for most modern DVDs. Those were the good 'ole days.

---

### Post by Remson_Felipa on 2016-09-12
I had try Handbrake, it should work

---

### Post by ltrtiger2 on 2016-09-17
Another vote for Handbrake. Fantastic app.

---

