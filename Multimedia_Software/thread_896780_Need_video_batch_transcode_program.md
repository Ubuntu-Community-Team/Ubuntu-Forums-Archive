---
title: "Need video batch transcode program"
date: 2008-08-21
forum: Multimedia Software
---

### Post by sumpm1 on 2008-08-21
I am new to linux and used to use MediaCoder on windows. I will convert my downloaded movies (avi mpeg4 usually) to a lower bitrate and or resolution so that I can store more movies on a DVD after watching them in full quality. I have heard that ffmpeg is the way to go, and I have been looking for a gui that will help with that, but found very little.

Since I have a standalone Divx player, the videos get transcoded to avi with xvid and mp3 to comply with my player. And the only things I will change is the audio bitrate, the resolution (sometimes) and a fixed quantizer 1 pass. When I feel lazy, I simply leave the resolution alone.

Is there any program or gui for ffmpeg that will let me do these things easily to a FOLDER of avi files all at once? If not, I am glad to learn more advanced functions that will allow me to do EXACTLY these things (I don't need to learn how to rip DVD's or VOB's).

Thanks

---

### Post by sumpm1 on 2008-08-22
help me out here guys

---

### Post by FakeOutdoorsman on 2008-08-22
WinFF is the most often recommended GUI for ffmpeg.  I beleive it can do batch conversions, but I don't use it so I may be wrong.  The version of ffmpeg from the Ubuntu repository does not support restricted formats such as mp3.  You can use ffmpeg from the Medibuntu repository.  It has better support for restricted formats.

---

### Post by sumpm1 on 2008-08-23
Thanks for the reply fake. I have tried WinFF and there is NO customization for Xvid setting and the whole interface is very minimalistic. I am looking for some more advanced features that will at least let me select a quality (fixed quantizer) mode in in Xvid rather than a flat bitrate (which will have too low of quality for some scenes.)

---

### Post by FakeOutdoorsman on 2008-08-23
You can edit each preset or add additional ffmpeg parameters in WinFF.  If you want total control, then I recommend using ffmpeg or mencoder without a GUI:
```
find ~/path/ -iname "*avi" -exec ffmpeg -i {} -pass 1 -b 512k -acodec copy -vcodec mpeg4 -vtag xvid -s 320x240 -flags +trell -f avi /dev/null && ffmpeg -i {} -pass 2 -b 512k -acodec copy -vcodec mpeg4 -vtag xvid -s 320x240 -flags +trell -f avi ~/newpath/{}.avi \;
```
I didn't test the above code.  You will need to change ~/path/ to whatever directory you want to encode from, and ~/newpath/ to the destination directory.  I don't use xvid, so you may have to change -vcodec to xvid and possibly omit -vtag xvid.

---

