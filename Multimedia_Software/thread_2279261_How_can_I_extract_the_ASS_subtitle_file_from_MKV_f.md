---
title: "How can I extract the ASS subtitle file from MKV file using mkvmerge?"
date: 2015-05-22
forum: Multimedia Software
---

### Post by remmas-sido on 2015-05-22
Hello guys  I want to learn both ways which means the graphical user interface way,  and the command line (terminal) way. I'm planning to install it on  Ubuntu. 
Thanks

---

### Post by SeijiSensei on 2015-05-22
Install the **mkvtoolnix** package.  I never use GUIs for this type of task because you can do everything you want in a couple of lines at the command prompt. To see the structure of the file use "mkvmerge -i file.mkv" like this:
```

mkvmerge -i file.mkv

Track ID 0: video (MPEG-4p10/AVC/h.264)
Track ID 1: audio (AAC)
Track ID 2: subtitles (SubStationAlpha)
Attachment ID 1: type 'application/x-truetype-font', size 47864 bytes, file name 'baars.ttf'
[etc.]

```
Usually the subtitles are stored in the third track, which is numbered 2 since like all things Unix, it starts counting from zero.  Once you know which track has the subtitles, use
```
mkvextract tracks file.mkv 2:subfilename.txt
```
to create a text file containing the subtitles.

There's also a GUI if you install **mkvtoolnix-gui** as well, but I've never used it.

---

### Post by remmas-sido on 2015-05-22
> **SeijiSensei said:**
> Install the **mkvtoolnix** package.  I never use GUIs for this type of task because you can do everything you want in a couple of lines at the command prompt. To see the structure of the file use "mkvmerge -i file.mkv" like this:
```

mkvmerge -i file.mkv

Track ID 0: video (MPEG-4p10/AVC/h.264)
Track ID 1: audio (AAC)
Track ID 2: subtitles (SubStationAlpha)
Attachment ID 1: type 'application/x-truetype-font', size 47864 bytes, file name 'baars.ttf'
[etc.]

```
Usually the subtitles are stored in the third track, which is numbered 2 since like all things Unix, it starts counting from zero.  Once you know which track has the subtitles, use
```
mkvextract tracks file.mkv 2:subfilename.txt
```
to create a text file containing the subtitles.

There's also a GUI if you install **mkvtoolnix-gui** as well, but I've never used it.

Thanks. You are always the first one who answer my threads. I really appreciate it.

---

### Post by andrew.46 on 2015-05-22
> **SeijiSensei said:**
> There's also a GUI if you install **mkvtoolnix-gui** as well, but I've never used it.

Looks like the latest version ships by default with a QT5 gui which might be interesting to have a look at...

---

