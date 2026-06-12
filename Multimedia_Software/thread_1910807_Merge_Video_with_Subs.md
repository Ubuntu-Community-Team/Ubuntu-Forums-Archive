---
title: "Merge Video with Subs"
date: 2012-01-17
forum: Multimedia Software
---

### Post by jorpoveda on 2012-01-17
Hello, is there an app to merge the video with the subs? I remember I once saw something like that as a Terminal program that merge video and subs.

Thank you.

---

### Post by SeijiSensei on 2012-01-17
I'm guessing you have a video and a subtitles file in .srt or .sub format?

You have a couple of options depending on the type of output you wish to create.  If you want a file that will play nearly anywhere, you should consider using [mencoder]("http://www.google.com/search?q=mencoder+subtitles+avi+xvid") to re-encode the file into XviD in the AVI container with hard subs.  ("Hard" subs are written directly into the video image.)

If you're creating a file that you intend to play with a media player that supports Matroska (.mkv) formats, you can use the utilities in the [mkvtoolnix]("http://packages.ubuntu.com/lucid/mkvtoolnix") package.  The Matroska container supports soft subtitles as a "stream" alongside the audio and video.

---

### Post by jorpoveda on 2012-01-17
Thanks mencoder worked really good.

---

### Post by rubylaser on 2012-01-18
mkvtoolnix is the way to go with this.  It's just
```
sudo apt-get install mkvtoolnix
```

```
mkvmerge -o output_movie_name.mkv original_movie.avi subtitles.srt
```

This will combine them without the need to lose quality through a re-encode.

---

### Post by SeijiSensei on 2012-01-19
> **rubylaser said:**
> This will combine them without the need to lose quality through a re-encode.

That works fine if the device he intends to play the video on supports Matroska and soft subtitles.  If he wants to create a file that can be played on a much wider range of devices, re-encoding with hard subs into XviD/mp3/AVI is a better choice. Even relatively modern devices like PS3's won't play Matroska files, and slightly older devices like my COWON portable video player won't either (new COWONs do, though).  Most DVD players support DivX, so XviD in AVI is a good bet for them as well.

---

### Post by jorpoveda on 2012-01-19
Yes I think I am going to go for the solution proposed by SeijiSensei. although I do appreciate your help rubylaser. I have another option on how to this for the future. Thanks.

---

