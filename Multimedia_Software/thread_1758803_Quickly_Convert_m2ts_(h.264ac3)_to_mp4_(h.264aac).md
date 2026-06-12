---
title: "Quickly Convert m2ts (h.264/ac3) to mp4 (h.264/aac)"
date: 2011-05-15
forum: Multimedia Software
---

### Post by djdvant on 2011-05-15
Hi All,

I convert all my mkv files to m2ts for the Playstation 3, all the files are h.264 with ac3.

Now I also have a Asus Transformer (Android 3.1) I need these same files in MP4 format.

I have taken the mkv2m2ts.sh script (found elsewhere on the internet) and changed it to do m2ts to mp4.

The script is basic, but I thought that I would share it with you all. Requires: tsMuxeR, ffmpeg, libfaac, MP4Box (gpac)

I've updated the script to include frames per second and a 50ms interleaving MP4 (which seems to improve the video stuttering).

Please feel free to modify the script in any way.

Use the script at your own peril, do not blame me if anything untoward happens!

---

