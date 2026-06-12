---
title: "rhythmbox autoconvert to ogg with a samsung YP-U5"
date: 2012-02-27
forum: Multimedia Software
---

### Post by sidell on 2012-02-27
Hello, 

A big part of my music is in flac format. In order to save space in my  samsung YP-U5, I would like to autoconvert these files in ogg when I  drag them to my player. I have my preferred format set to ogg 
in rhythmbox's preferences. 

My problem is that my samsung YP_U5 is able to read flac, so rhythmbox  doesn't convert my files. I tried to modify the file  /usr/share/media-player-info/samsung_u5.mpi: I removed "audio/flac" from  the OutputFormats line. It's not working. I also tried to create a  .is_audio_player in the root of my player with informations that I my  player supports ogg or mp3 files (but not flac). It's not working neither. 

So here is my question: how can I autoconvert my music from flac to ogg  with rhythmbox? 

P-S: I use ubuntu 11.10. 
P-S 2: /usr/share/media-player-info/samsung_u5.mpi corresponds to my  player (DeviceMatch=usb:04e8:5121 matchs with udevadm info)
P-S 3: udevadm info's file is attached

---

