---
title: "Is there an application which reads pdf with videos ?"
date: 2023-09-12
forum: Multimedia Software
---

### Post by musette2 on 2023-09-12
Hi !

Im looking for an application on Ubuntu which reads a pdf file with videos integrated.

On windows, adobe acrobat reader does play videos on my pdf file but on Ubuntu, instead of playing the video, I have a still picture.

Thank you.

Have a great day !

---

### Post by Holger_Gehrke on 2023-09-17
Never encountered a pdf with an embedded video in the wild, so I first tested whether I could create one in LibreOffice writer. Created an empty document and used 'Insert' -> 'Media' -> 'Audio/Video' to put a short video clip in there and exported to pdf. The resulting pdf was slightly bigger then the video file. Opened it in the default document viewer (evince) and clicked on the video and it played.

I think your problem is more related to the actual format of the video embedded in your pdf. You might need to install the right codec to play it. You might be able to find out what kind of video is in the pdf by using ffprobe from the package ffmpeg. For my self-made pdf it correctly identified the video stream as mpeg4/yuv420p/1024x576 although it did warn that it had low confidence in that detection ...

Holger

---

