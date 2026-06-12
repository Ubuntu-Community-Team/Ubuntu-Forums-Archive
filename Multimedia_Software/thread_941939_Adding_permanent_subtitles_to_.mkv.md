---
title: "Adding permanent subtitles to .mkv"
date: 2008-10-08
forum: Multimedia Software
---

### Post by Deep100 on 2008-10-08
hi i was wondering how to add type ssa subtitles to .mkv videos permanently. Is there any program that can do this and if there is can you please tell me. :confused:

---

### Post by lovinglinux on 2008-10-08
mkvtoolnix can do that. If you like gui you can install mkvtoolnix-gui (I guess they are in the repos).

Please notice that this tool will not embed the subtitles in the video, but insert them in the mkv container (which is much better). You can include as many subtitle files you want for each video, like you do for audio files and toggle between them while playing. If you like to edit or translate the subtitles, I would recommend keeping the original subtitle files, so you can append them to the mkv later.

---

### Post by Deep100 on 2008-10-09
is the programe called mkv files creator? and if it is how do you use it because i have the subtitles file and the mkv file but how do you permanently add them?

---

### Post by lovinglinux on 2008-10-09
> **Deep100 said:**
> is the programe called mkv files creator? and if it is how do you use it because i have the subtitles file and the mkv file but how do you permanently add them?

Yes, it is. Open the program and click the add button, next to the "Input files" field, select the mkv and the subtitle files and click Open. The files should be added to the list. Then you can select the subtitle track, in the "Tracks" field and configure the subtitle language and if it is the default track. Click "Browse" next to the "Output filename" field and select where you want to save (DON'T save in the same directory, unless you change the mkv filename). Hit "Start Muxing" and the new mkv file containing the subtitles will be created.

---

### Post by Deep100 on 2008-10-09
Thanks allot for your help:lolflag:

---

### Post by lovinglinux on 2008-10-09
> **Deep100 said:**
> Thanks allot for your help:lolflag:

You are welcome. There are other options/settings you can configure. I gave you the basic ones to get started.

---

