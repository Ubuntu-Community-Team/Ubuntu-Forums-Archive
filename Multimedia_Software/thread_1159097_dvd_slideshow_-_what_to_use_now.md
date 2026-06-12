---
title: "dvd slideshow - what to use now?"
date: 2009-05-14
forum: Multimedia Software
---

### Post by timcredible on 2009-05-14
with 9.04 jaunty, digikam no longer does mpg slideshows for dvds.  it seems to have a lot of other formats, but they've dropped the mpg format.  So, what should i use now?  some searches uncovered jdvdslideshow, image2mpeg, and mandvd.  what do you use?  Thanks.

---

### Post by timcredible on 2009-05-15
so, i tried mandvd, and it looks very promising, except that i get an error when trying to create a slideshow.  i did some searches, and they didn't help (most of them said to add a 'K' at the end of all audio_bitrate=192 lines).  does anyone have this working on their machines?

---

### Post by xc3RnbFO8P on 2009-05-15
> 
with 9.04 jaunty, digikam no longer does mpg slideshows for dvds. it seems to have a lot of other formats, but they've dropped the mpg format.
Can you try **Devede** to encode it to mpeg?

---

### Post by timcredible on 2009-05-15
> **Ringi said:**
> Can you try **Devede** to encode it to mpeg?

good idea.  however, i just checked again, and i was wrong about the exporting, digikam has several places it can export files to (flickr, picasa, etc.), but none of them are files that you can run on your computer (no .avi, or .mov, or anything).  also, it's weird that they want you to buy some commercial software to export a slideshow to flash.  this sure leaves a pretty big hole in the open source world wrt working with photos.  maybe the next version of digikam will put this option back....

---

### Post by timcredible on 2009-05-15
well, finally found out how to get past that error message:

ffmpeg -i "$tmpdir/audio1.wav" -y -vn -ab $audio_bitrate -acodec ac3 -ar $audio_sample_rate -ac 6 "$tmpdir/audio1.ac3" >> "$outdir/$logfile" 2>&1 ffmpeg-i "$ tmpdir/audio1.wav"-y-vn-ab $ audio_bitrate-acodec ac3-ar $ audio_sample_rate-ac 6 "$ tmpdir/audio1.ac3">> "$ OUTD / $ logfile" 2> & 1

debe de quedar must be

ffmpeg -i "$tmpdir/audio1.wav" -y -vn -ab $(audio_bitrate)k -acodec ac3 -ar $audio_sample_rate -ac 6 "$tmpdir/audio1.ac3" >> "$outdir/$logfile" 2>&1 ffmpeg-i "$ tmpdir/audio1.wav"-y-vn-ab $ (audio_bitrate) k-acodec ac3-ar $ audio_sample_rate-ac 6 "$ tmpdir/audio1.ac3">> "$ OUTD / $ logfile" 2 > & 1

however, after it says it created it, there's no file, you can't preview it, you can't put it in your dvd.  i guess i could keep on working on this, or just go back to 8.10...

---

### Post by cotcot on 2009-05-15
[[COLOR="Red"]Smile[/COLOR]]("http://linux.softpedia.com/get/Multimedia/Graphics/SMILE-38844.shtml") is the successor of mandvd.

---

### Post by timcredible on 2009-05-15
> **cotcot said:**
> [[COLOR="Red"]Smile[/COLOR]]("http://linux.softpedia.com/get/Multimedia/Graphics/SMILE-38844.shtml") is the successor of mandvd.

thanks.  i just tried it, it seems ok, kind of rough around the edges so far, but doesn't allow for adding a sound track to the slideshow, so i'm still looking.

---

### Post by timcredible on 2009-05-20
alright, so i finally figured this out - ignore the other thing i posted, and forget the 'adding a k to the end of the audio argument' stuff.  with jaunty, and dvd-slideshow 0.8.2, you need to do this:
```

sudo gedit /usr/bin/dvd-slideshow

```
and then do a replace all of "-compose src-over" with a space.  the problem turned out to be that dvd-slideshow was sending this parameter to the program "composite", which doesn't know what that parameter is.  ok, so now i can create dvd slideshows again.  good.  although i tried using the widescreen option, and it just added black bars to the left and right side, guess that's my next thing to look into....

---

