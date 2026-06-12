---
title: "aplication for video editing"
date: 2008-09-27
forum: Multimedia Software
---

### Post by mattkmponk on 2008-09-27
Hi.. guys! :) wh4t's d' b3st pro9r4m for vid3o 3ditin9 in Ubuntu. 'n how to inst4ll it? th4nks.

---

### Post by hansdown on 2008-09-27
Hi mattkmponk.

You can try libmjpegtools0csa, or mjpegtools.

They're both in the synaptic package manager.

---

### Post by ad_267 on 2008-09-27
Try kino with ffmpeg or avidemux. This tells you how to install anything in Ubuntu: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

And this is an English speaking forum.

---

### Post by rsambuca on 2008-09-27
From the Ubuntu Forums Code of Conduct:

> Please refrain from using "leet" speak or slang.

---

### Post by perlluver on 2008-09-27
Also there is a list of programs at: [http://www.linuxmovies.org/software.html](http://www.linuxmovies.org/software.html), look under the free list.

---

### Post by binbash on 2008-09-28
avidemux by far in my opinion.You can get from the repos or you can get the deb at getdeb.net

---

### Post by bconover on 2008-09-28
> **mattkmponk said:**
> Hi.. guys! :) wh4t's d' b3st pro9r4m for vid3o 3ditin9 in Ubuntu. 'n how to inst4ll it? th4nks.

Id s4y d' b3st pro9r4m for vid3o 3ditin9 iz Op3n Movi3 3ditr!!1

Ahem.

I'd say the best program for video editing is Open Movie Editor. I believe it is in the repos (repositories). I use it all the time. Very simple and clean. Don't forget to visit their site to download the extra effects pack and to learn about custom titles. 

For more advanced work, try Cinelerra. If you're importing from a DV camera, Kino is good for simple capturing and editing.

EDIT:

You can install Open Movie Editor by going to Applications -> Add/Remove and searching for "open movie editor", or browse the Sound&Video section.

---

### Post by bconover on 2008-09-28
> **perlluver said:**
> Also there is a list of programs at: [http://www.linuxmovies.org/software.html](http://www.linuxmovies.org/software.html), look under the free list.

They misspelled "VLC" as "VPC"...

---

### Post by Cresho on 2008-09-29
im currently using cinelerra for High definition video editing from xacti hd1000.  I am also using blender but blender is not that well supporting HD 59.94fps.  I am able to successfully edit high definition video content.  I am also mastering it pretty nicely and creating a new gui (just the buttons) to make it more enjoyable.

this is the one I use!

it uses mp4 files just fine.  I can only export to mov for my use on winff or avidemux to convert to other formats.  Video editing is very powerfull in linux as long as you know what your doing.

cinelerra-4-ubuntu-i686.tar.bz2

extract and launch
 ./cinelerra

---

### Post by eye208 on 2008-09-29
> **Cresho said:**
> I am also using blender but blender is not that well supporting HD 59.94fps.
Why not?

---

### Post by Cresho on 2008-09-29
When I add a video, My videos are 720p@ 59.94 frames per second.  If I drop in a solid video in blender, After setting the properties at 60fps or 59 fps, My one hour video has minutes between the end of an audio.  I cannot set 59.94 frames per second in blender.  Audio is not sync able!  If i did, i still have a big gap because of lost frames especially on a 1 hour long video.  my videos become out of sync automatically.

---

### Post by eye208 on 2008-09-29
> **Cresho said:**
> I cannot set 59.94 frames per second in blender.
Blender supports fractional framerates. I guess you are using an old version.

---

### Post by Cresho on 2008-09-29
247 version.  ill check again.  i saw something like 1/100 or something but couldnt make heads or tails from it.

its called frames per second and frames per second base.

---

### Post by eye208 on 2008-09-29
That's exactly what you are looking for. Set the first field to 60 and the second to 1.001. This representation (60 / 1.001) is actually the most accurate one. 59.94 is only an approximation. See [here](http://en.wikipedia.org/wiki/Frame_rate#Frame_rates_in_film_and_television).

---

### Post by Cresho on 2008-09-29
you get a gold star for this.  I guess I was on the right track but couldnt figure out how.  The link helps! :KS

---

### Post by Cresho on 2008-09-29
thanks!  it works.  Now my videos loads correctly...now to see if I can get a blender with ffmpeg.  The one I am using I just noticed I have no ffmpeg support.  I'll look at the source.

You know how long I been looking at the frames per second base?  about 6 hours before I threw in the towel and wasn't gonna try again for a good while.  Couldn't fine nothing on fps base.

The xvid with mp3 audio loads but mp4 mpeg4 video and audio does not work.  Definetly an ffmpeg issue.

---

### Post by renepotvin on 2008-10-15
I am also looking for a movie editor. I am now using gimp exclusively for my photo editing (this surprised the hell out of me) so I figure I'll see what linux can offer for movies.

My main needs are** white balance correction and color balancing.** Stuff that's pretty basic and use profusely on adobe premiere. 

Any software that can do this as well as other basic editing tasks?

---

