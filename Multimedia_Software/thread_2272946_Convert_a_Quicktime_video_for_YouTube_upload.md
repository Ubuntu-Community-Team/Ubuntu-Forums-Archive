---
title: "Convert a Quicktime video for YouTube upload"
date: 2015-04-09
forum: Multimedia Software
---

### Post by coldraven on 2015-04-09
I used an Android app called Framelapse to video the recent Solar eclipse. It created a 180MB Quicktime mp4 file, 1280x720, H264, 30fps, 10020kbps of 2min 23sec duration with no sound.
 I must state that it is not a work of art, merely one of my first attempts at time-lapse photography. I set up my phone in a hurry and used the free version of the app which did not have exposure lock. For some reason the free version saves videos upside down, I used VLC to rotate it by 180 degrees.

Being a video codec ignoramus I was wondering if I could convert it so that it's upload time was shorter. (my upload speed is abysmally slow)
I read recently that Google uses VP9. Can I convert it locally before uploading?

---

### Post by Vladlenin5000 on 2015-04-09
The usual softwares can convert between many video formats. Handrake has some presets for web content. It's now available at the Ubuntu repositories.

---

### Post by ajgreeny on 2015-04-09
I agree that handbrake is probably the way to go; it is very easy to use, and has the preset output types available at the click of a dropdown box.  It can also easily encode just a small part of a long video, if that is your wish, by clicking on the Chapter, Seconds or Frames selector in the Source dialogue.

---

### Post by coldraven on 2015-04-11
Thanks, I  gave Handbrake a go and it created a MKV that is a lot smaller, only 33MB, but is a little bit jittery.
I used the default settings, maybe I'll try adjusting something for a smoother result.

---

### Post by FakeOutdoorsman on 2015-04-11
> **coldraven said:**
> For some reason the free version saves videos upside down, I used VLC to rotate it by 180 degrees.
That program may be setting stream rotation metadata. Some players ignore it. The ffmpeg console output will mention if there is any rotation metadata:
```
$ ffmpeg -i input
...
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'output.mp4':
  Metadata:
    major_brand     : isom
    minor_version   : 512
    compatible_brands: isomiso2avc1mp41
    encoder         : Lavf56.15.101
  Duration: 00:00:04.71, start: 0.021333, bitrate: 245 kb/s
    Stream #0:0(und): Video: h264 (High) (avc1 / 0x31637661), yuv420p, 640:480 [SAR 1:1 DAR 4:3], 165 kb/s, 24 fps, 24 tbr, 12288 tbn, 48 tbc (default)
    Metadata:
      rotate          : 180

```

If it is just being dumb and recording upsidedown you can rotate it 180° with a variety of filters in ffmpeg:
```
-vf "hflip,vflip"
```
or
```
-vf "transpose=2,transpose=2"
```
or
```
-vf "rotate=PI:bilinear=0"
```

If there is metadata, and you want to physically rotate it so all players show it the same, then use one of the rotate filters shown above and then clear the metadata with:
```
-metadata:s:v rotate=""
```

> Being a video codec ignoramus I was wondering if I could convert it so that it's upload time was shorter. (my upload speed is abysmally slow)
I read recently that Google uses VP9. Can I convert it locally before uploading?
VP9 encoding is slow, and Google will re-encode whatever you give it. I recommend H.264. Your example may look like this:
```
ffmpeg -i input -vf "hflip,vflip" -c:v libx264 -crf 18 -preset veryslow -metadata:s:v rotate="" output.mp4
```
[list]
[*]A crf value of 18 will look more or less like the original. Since YouTube will re-encode it anyway this will output a high quality to help minimize the additional YouTube induced quality loss.
[*]Use the slowest preset you have patience for. Since it's a relatively short video you can probably just use "veryslow".  See [FFmpeg Wiki: H.264 Encoding Guide](https://trac.ffmpeg.org/wiki/Encode/H.264).
[*]Ubuntu doesn't provide ffmpeg yet, and development is very active anyway, so you can [compile](https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu), use a [static build](http://johnvansickle.com/ffmpeg/), or a [PPA](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media).
[/list]

---

### Post by coldraven on 2015-04-12
> That program may be setting stream rotation metadata. Some players  ignore it. The ffmpeg console output will mention if there is any  rotation metadata:
Well that problem is solved, I paid for the "Pro" version which saves in the correct orientation. It also has exposure lock and some other goodies.
I just found this WebM guide for compiling ffmpeg with libvpx support. I will give it a try later today maybe..
I can hardly see my screen because the Sun is streaming in and I don't have curtains for that window. This is the disadvantage of early rising :)

[https://sites.google.com/a/webmproject.org/wiki/ffmpeg/building-with-libvpx](https://sites.google.com/a/webmproject.org/wiki/ffmpeg/building-with-libvpx)

---

### Post by FakeOutdoorsman on 2015-04-12
I wouldn't follow that guide: it performs a "make install" that will install to the system without using the package management system. Kind of messy and a pain to uninstall properly if you get rid of the directories that you ran "make install" in.

The compile guide I linked to "installs" to your home directory, so it won't mess with anything. Alternatively, the static build supports libvpx, and so does the PPA. Both of those options are easy.

---

### Post by coldraven on 2015-04-13
> **FakeOutdoorsman said:**
> I wouldn't follow that guide: it performs a "make install" that will install to the system without using the package management system. Kind of messy and a pain to uninstall properly if you get rid of the directories that you ran "make install" in.

The compile guide I linked to "installs" to your home directory, so it won't mess with anything. Alternatively, the static build supports libvpx, and so does the PPA. Both of those options are easy.
Aha! Thanks for that, I should have read your post more thoroughly. (Sun in eyes!) I will try the PPA later. I have vehicle problems to sort out today, are you any good at suspension faults :)

---

### Post by FakeOutdoorsman on 2015-04-14
> **coldraven said:**
> I have vehicle problems to sort out today, are you any good at suspension faults :)

I recently replaced the CV axles on my crappy, old Protege, but then the passenger side replacement (remanufactured) was defective, so now I have to replace that one too. Just bought an air impact wrench. That will make it easier to deal with.

Got a new coil and strut rolling around in the trunk. I did the drivers side, but I may never get to that. Coils are too dangerous. Too bad it doesn't take "quick struts".

At least it gets ~29 mpg.

---

