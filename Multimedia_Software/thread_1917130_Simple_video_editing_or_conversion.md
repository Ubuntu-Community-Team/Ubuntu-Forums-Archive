---
title: "Simple video editing or conversion"
date: 2012-01-29
forum: Multimedia Software
---

### Post by Odense on 2012-01-29
I am using Ubuntu 11.4 on my Samsung laptop.

I am sometimes using my cheap Blue Tinnum harddisk recorder to record movies from the cable TV. It 
works well and they can be played back nicely with the Blue Tinnum recorder.

I would however like to be able to play them back on anything (as well as store them in a format with a better name and in a single fil.

The video is stored in 2 GB files with names like data0001.dat and data0002.dat and so on. I don't know what the true format is - but these files play with no problems in VLC.

Can someone tell me (preferably for dummies) how to transfor these 2-3 dat-files into one avi or mp4 file ?

---

### Post by tersogar on 2012-01-29
I´m not sure but Handbrake may help you.

---

### Post by JohnAStebbins on 2012-01-29
> **Odense said:**
> I am using Ubuntu 11.4 on my Samsung laptop.

I am sometimes using my cheap Blue Tinnum harddisk recorder to record movies from the cable TV. It 
works well and they can be played back nicely with the Blue Tinnum recorder.

I would however like to be able to play them back on anything (as well as store them in a format with a better name and in a single fil.

The video is stored in 2 GB files with names like data0001.dat and data0002.dat and so on. I don't know what the true format is - but these files play with no problems in VLC.

Can someone tell me (preferably for dummies) how to transfor these 2-3 dat-files into one avi or mp4 file ?
It's likely that these ".dat" files are just regular transport streams.  If so, you can just concatenate them together into a single file and feed the merged file into your transcoder of choice.  I prefer HandBrake,  but I'm biased since I wrote the Linux GUI for HandBrake.  VLC ought to be able to play the merged file as well.

e.g.
```

cat data0001.dat data0002.dat > video.ts
HandBrakeCLI -i video.ts --preset "High Profile" -o video.mkv

```

---

### Post by Odense on 2012-02-09
Thank you - I copied the two files into a library on the harddisk and I managed to make the -ts file.
However - when I tried to use the handbrake command I got these error messages:

mnj@Samsung-RV510-S3510-E3510:~/Videos$ cat data0001.dat data0002.dat > video.tsmnj@Samsung-RV510-S3510-E3510:~/Videos$ HandBrakeCLI -i video.ts --preset "High Profile" -o Stenhuggeren.mkv
HandBrakeCLI: command not found

What should I do to make the command available in the library ?
Would the cat command also work on 5 dat files (each is about 2 gb) ?
The dat files are on a usb harddisk - how do I open a terminal window and use the commands directly there ?

---

