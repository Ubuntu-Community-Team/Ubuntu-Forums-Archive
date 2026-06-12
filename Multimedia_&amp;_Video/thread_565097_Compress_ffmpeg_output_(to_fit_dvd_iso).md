---
title: "Compress ffmpeg output (to fit dvd iso)?"
date: 2007-10-01
forum: Multimedia &amp; Video
---

### Post by tefflox on 2007-10-01
Hello, which options (simply) can I use to make a rather smaller mpeg/dvd-iso image?  Currently, the following commands produce ~5.4G (for a 900M avi) where I need it at around 4.2G

As now ---
```
ffmpeg -i movie.avi -aspect 16:9 -target ntsc-dvd movie.mpg

dvdauthor -o dvd -t movie.mpg
dvdauthor -o dvd -T

mkisofs -dvd-video -o movie.iso dvd/
```Are there options to do this?  (Please be patient, I am only providing this iso creation service for my roomies.  I got Rails, prob's, too :-\

---

