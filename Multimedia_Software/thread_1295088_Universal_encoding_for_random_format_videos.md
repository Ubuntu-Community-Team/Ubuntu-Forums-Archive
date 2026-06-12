---
title: "Universal encoding for random format videos ??"
date: 2009-10-19
forum: Multimedia Software
---

### Post by rahul23 on 2009-10-19
Hello ubunties
      I am using ffmpeg on  my ubuntu server . Is there a vedio and audio encoder which is by means truly universal , Since for e.g sometimes some encoders like libx264 gives error "this type of resolution not supported"
"this tpye of frame rate not supported"
"Audo resampling rate not supported"

Since I am dealing with multimedia files in wild which wd be uploaded by random people and they are not going to give ffmpeg commands hence which settings should i use which always works independent of the input multimedia files properties such as frame rate , resolution,audio resampling rate etc.

Thanks in Advance.:guitar:

---

### Post by vinutux on 2009-10-19
Try Mencoder ...... or Handbreake cli

---

### Post by rahul23 on 2009-10-19
well i am looking for the universal encoder not a diff program , mpeg encoding is greate but it sucks when input file frame rate falls to 15 ?

---

### Post by vinutux on 2009-10-20
There is video encoding engine linux version [http://www.sothinkmedia.com/flash-video-encoder-linux/index.htm]("http://www.sothinkmedia.com/flash-video-encoder-linux/index.htm")

---

### Post by rahul23 on 2009-10-23
> **vinutux said:**
> There is video encoding engine linux version [http://www.sothinkmedia.com/flash-video-encoder-linux/index.htm]("http://www.sothinkmedia.com/flash-video-encoder-linux/index.htm")

600$ = Rs 30,000 r u kidding me :P!!

---

### Post by vinutux on 2009-10-23
Check [Firefogg]("http://firefogg.org/sites/index.html") 

**[http://firefogg.org/dev/index.html]("http://firefogg.org/dev/index.html")**

---

### Post by FakeOutdoorsman on 2009-10-23
> **rahul23 said:**
> Hello ubunties
      I am using ffmpeg on  my ubuntu server . Is there a vedio and audio encoder which is by means truly universal , Since for e.g sometimes some encoders like libx264 gives error "this type of resolution not supported"
"this tpye of frame rate not supported"
"Audo resampling rate not supported"

FFmpeg is probably the best tool for this.  Give an example where you are getting these errors.  Show your FFmpeg command and the complete FFmpeg output.

---

