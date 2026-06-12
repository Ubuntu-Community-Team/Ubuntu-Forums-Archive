---
title: "Convert MOD to Lightworks compatible format"
date: 2014-01-01
forum: Multimedia Software
---

### Post by Ifaistos on 2014-01-01
Hello everyone :-)

I just downloaded and installed Lightworks.
I have a video file which is in .MOD format which I want to edit in Lightworks.

Unfortunately Lightworks, does not support importing .MOD files.

I guess my best option is to convert the .MOD file into mp4 or anything else that is compatible with the codecs it is able to import.

Does anyone know if there is a tool available in Ubuntu that can do the job?

If this can be done through a GUI, that would be awesome !!

Thanks !!

edit :  This are the details of the file.

---

### Post by Ifaistos on 2014-01-01
I couldn't attach a picture to the previous message...
So here it is :

---

### Post by FakeOutdoorsman on 2014-01-02
Surely it can handle mpeg-2 video and AC-3? Maybe it doesn't like the container.
[B]
1. Download ffmpeg[/B]
The stuff in the repository is buggy.
```
wget http://ffmpeg.gusari.org/static/32bit/ffmpeg.static.32bit.$(date +"%F").tar.gz
tar xzvf ffmpeg.static.32bit.$(date +"%F").tar.gz
```

**2. Re-mux**
Try re-muxing it using stream copy mode in ffmpeg. This will simply "copy and paste" the video and audio into another container (notice the **./** before ffmpeg):
```
./ffmpeg -i input.mod -codec copy output.mpg
```

---

