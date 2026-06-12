---
title: "Lossless mp4 converter? Does one exist?"
date: 2008-06-05
forum: Multimedia Software
---

### Post by Cody Jordan on 2008-06-05
Im looking for either a terminal command or gui program for linux
that will losslessly convert my avi vids to mp4 and will work on ipod
i dont wana change the size or quality and i want the audio to sync flawlessly!

---

### Post by eye208 on 2008-06-05
Lossless conversion from AVI to MP4 will only work if the AVI file already contains streams in a format suitable for the iPod. This is very unlikely. As far as I know, the iPod supports the H.264 baseline profile. Even if the AVI contains an H.264 video stream, it will most likely be optimized for size and therefore use advanced H.264 features that even Quicktime doesn't support (more than 2 B-frames, 8x8 DCT, etc.).

---

### Post by Cody Jordan on 2008-06-05
i know it will work its just the program im using is sliping the audio

---

### Post by eye208 on 2008-06-05
Install the package "gpac" from the repository. It comes with a command line tool "MP4Box". This can be used to extract streams from AVI files and put them into a MP4 file. Nothing will be transcoded, so the conversion will be lossless. Make sure to specify the frame rate of the video stream when building the MP4. Test A/V sync in a media player prior to uploading the file to the iPod. If it works in the media player but not on the iPod, there is a problem with the stream format. In that case transcoding is your only option.

---

