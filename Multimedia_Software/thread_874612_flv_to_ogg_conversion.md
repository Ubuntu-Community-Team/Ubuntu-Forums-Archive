---
title: "flv to ogg conversion"
date: 2008-07-30
forum: Multimedia Software
---

### Post by Circus-Killer on 2008-07-30
alright, i know how to convert flv files to ogg files using ffmpeg2theora. my problem is that i want to know how do i convert the flv to ogg with minimal loss to the original quality. i would like to keep the ogg file almost the same quality as the flv file.

any suggestions?

---

### Post by Circus-Killer on 2008-07-30
the command i use now at the moment is like so:```
ffmpeg2theora -p pro --sync filename.flv
```

is there a way to get better quality oggs?

---

### Post by TenPlus1 on 2008-07-30
I use SoundConverter and simply drag the .flv file into the window, set the quality I require and let it do the work... quick & easy...

---

### Post by Rhubarb on 2008-07-30
There are plenty of options available to you for this.
Check out the manual page for it:
```
man ffmpeg2theora
```
With the right switches, you can increase the video and audio bitrate to much higher setting.

---

### Post by Circus-Killer on 2008-07-31
> **TenPlus1 said:**
> I use SoundConverter and simply drag the .flv file into the window, set the quality I require and let it do the work... quick & easy...

can soundconverter convert video files?!? :confused:

---

### Post by Rhubarb on 2008-07-31
For excellent audio and video quality, try this:
```
ffmpeg2theora -v 10 -S 0 -a 10 --sync filename.flv
```
This will create a large video file, but quality should be very much the same as from the original flv video.

---

