---
title: "Make tga How To?"
date: 2008-03-12
forum: Multimedia &amp; Video
---

### Post by ipburbank on 2008-03-12
Hello guys, I have a new application that I am using to do match moving for a project of mine. I have a video that I want to use for testing, but the App needs TGA format to work. I am working in ubuntu studio, and it seems as though none of the apps here export to TGA. Does anyone know of the program I am looking for? :confused:

---

### Post by Jimmey on 2008-03-12
The GIMP can.

What type of application do you need?

---

### Post by ipburbank on 2008-03-12
Just to clarify, I am looking for a video TGA converter. so I have a '.avi' video that I need to convert to a '.tga' video. So what i am looking for is an app that will do this for me.

---

### Post by Jimmey on 2008-03-13
I reckon FFMPEG will probably be capable, but you'll have to read the documentation. To install :
```
sudo apt-get install ffmpeg
```

---

### Post by eye208 on 2008-03-13
Try

ffmpeg -i yourvideo.avi frame%04d.tga

The "%04d" is a placeholder for the frame number (4 digits, leading zeros). If your AVI has more than 9999 frames, use e.g. "%05d" instead.

---

### Post by ipburbank on 2008-03-13
Thanks guys!

---

