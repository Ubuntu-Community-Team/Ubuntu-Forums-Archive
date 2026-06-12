---
title: "Avidemux 2.4 for PSP"
date: 2007-10-29
forum: Multimedia Production
---

### Post by ukripper on 2007-10-29
Has anyone tried Avidemux 2.4 to convert videos or dvd to PSP format?
[http://news.softpedia.com/news/Convert-Movies-with-subtitles-for-your-PSP-on-Ubuntu-67806.shtml](http://news.softpedia.com/news/Convert-Movies-with-subtitles-for-your-PSP-on-Ubuntu-67806.shtml)

---

### Post by ukripper on 2007-11-04
bump

---

### Post by netyire on 2007-11-05
I haven't tried converting a video for the PSP with avidemux. But I wrote a python program to convert videos/vcd/dvd to media files playable on the pocket pc, palm, psp and ipod. It should play on a PSP even if it does not have upgraded firmware.

I've attached the script, just right click it in nautilus and select open with other application and type python in the box. Make sure you've installed mencoder first though, type sudo apt-get install mencoder in the terminal. The script makes use of mencoder and hence is able to convert any file playable in mplayer.

The script does not modify your system in any way and is completely safe -UNLESS- you run it in root mode, if you do so, the script will automatically set its process piority to -20. This is meant to speed up encoding time but it could slow down your computer during the conversion process. Just run it normally to be safe.

If you want better bitrates/quality, open up the script with a text editor and scroll till you see "# Video Quality", and "# Audio Quality", you can then change the bitrate. Its recommended not to increase audio bitrate to more than 192 nor video bitrate to more than 800. This is because doing so will result in huge files.

If your PSP's firmware is above 2.02, you can try settting the scale=320:240 to scale=480:272, this will allow you to encode fullscreen video for your psp without upscalling.

If you don't want to change any settings thats fine too, the default is wonderfully powerful and creates ~80mb file for ~40mins of video and audio.

Should you want to convert a DVD, simply enter dvd:// in the input box. Ensure that you enter the correct title if the DVD has more than one title. For example dvd://2 if that is the main title on the DVD.

---

### Post by ukripper on 2007-11-05
looks great I will use your script for my mobile phones..

I have been using Avidemux 2.4 now and AVC format works great and encoding is bloody quick even on full res supported by PSP using 1000 average bitrate. Avidemux is a must have tool for PSP in my opinion. 

i have tried PSPVC which is so slow when compared to Avedemux no where near it. Also tried IMTOO on windows machine at work same file encoding took 15 mins extra on that compared to avidemux

---

### Post by .Ix on 2007-12-22
i don't seem to be able to get avidemux to work for me.

i installed it through synaptic, and i open the video, click Auto -> PSP, leave everything on default, then Save the file and give it a random name, then stick it into ms0:\video. the psp always says it's not supported. PSPVC works, but it's uselessly slow for me. 21 hours for a 50 minute vid? no, thanks.

---

### Post by Creative2 on 2007-12-23
i have done this :

[http://ubuntuforums.org/showthread.php?t=567016](http://ubuntuforums.org/showthread.php?t=567016)

mencoder has chanded so... but i think you can use this :

mencoder INPUT -oac lavc -ovc lavc -of lavf -lavcopts aglobal=1:vglobal=1:vcodec=mpeg4:vbitrate=500:acodec=libfaac -af lavcresample=24000 -vf scale=368:208,harddup -lavfopts format=psp  -ofps 30000/1001 -o OUTPUT

or 

ffmpeg -i INPUT -acodec libfaac -ab 128kb -vcodec h264 -b 1200kb -ar 48000 -mbd 2 -coder 1 -cmp 2 -subcmp 2 -s 368x192 -r 30000/1001 -title TITLE -f psp -flags loop -trellis 2 -partitions parti4x4+parti8x8+partp4x4+partp8x8+partb8x8 OUTPUT

---

### Post by wickwire on 2008-01-03
> **.Ix said:**
> i don't seem to be able to get avidemux to work for me.

i installed it through synaptic, and i open the video, click Auto -> PSP, leave everything on default, then Save the file and give it a random name, then stick it into ms0:\video. the psp always says it's not supported. PSPVC works, but it's uselessly slow for me. 21 hours for a 50 minute vid? no, thanks.

Same problem here, solved it using this "recipe", hope it works for you:

```
Avidemux 2.4:

1- Load input file with "Open"
2- Select "Auto" -> "PSP (h.264)"
	2.1 - Select "PSP" instead of "PSP fullrep" leaving ratio as is
3- Video section (on the left) choose MPEG-4 ASP (lavc)
4- Save file with <may_be_original_filename>.MP4
5- Once finished, copy the MP4 file to the "VIDEO" directory in the mem stick
```

PSP 3.71-M33 update 2

This seems to be the only working combination of parameters for me.

---

### Post by Mize on 2008-01-31
> **netyire said:**
> I haven't tried converting a video for the PSP with avidemux. But I wrote a python program to convert videos/vcd/dvd to media files playable on the pocket pc, palm, psp and ipod. 

Running this now and it's about 5x faster than pspvc and a bit faster than Handbrake on my c2d mac...of course I haven't seen the output yet :) Interestingly Avidemux output was stuttery and pspvc was slower with more threads.

---

### Post by rootkit on 2008-02-01
I have a script for PSP too: [http://ubuntuforums.org/showthread.php?t=684571](http://ubuntuforums.org/showthread.php?t=684571)

---

### Post by Mize on 2008-02-01
This one (from top of this thread) is really fast, but the video I got on trial one was a bit jerky. I notice is uses the mpeg4 codec. Can it use h264? I'm getting great results with Handbrake on Mac, but it's not my computer (my kids) and my Q6600 should be faster !

---

### Post by rootkit on 2008-02-01
> **Mize said:**
> This one (from top of this thread) is really fast, but the video I got on trial one was a bit jerky. I notice is uses the mpeg4 codec. Can it use h264? I'm getting great results with Handbrake on Mac, but it's not my computer (my kids) and my Q6600 should be faster !

try my script. It supports multiple cpu

---

### Post by fanoodlehey on 2008-03-02
Thanks for the instructions wickwire. This is the only way that I have been able to get videos converted to my psp.

---

### Post by krychek on 2008-06-28
I still can't play any videos on my PSP that I've converted with avidemux.. Mp4tools works but it's slow and it doesn't show any progress bar. It can't burn subtitles either. Do the developers of avidemux know that it doesn't really work?

---

### Post by bardic on 2008-06-29
Hey all,
I have several mp4 videos but I have no idea how to actually get them onto my PSP. What directory should I copy them to? 

I have looked around for a while but have found anything....


Thanks,
bardic

---

