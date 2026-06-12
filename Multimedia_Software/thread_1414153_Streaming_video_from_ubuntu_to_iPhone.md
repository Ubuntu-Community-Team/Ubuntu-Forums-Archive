---
title: "Streaming video from ubuntu to iPhone?"
date: 2010-02-23
forum: Multimedia Software
---

### Post by aebrett on 2010-02-23
I've got a large collection of movies and TV shows on my linux box at home, and I'd love to be able to watch them on my iPhone whilst travelling. I could obviously transcode and copy them to my iPhone whilst at home, but frankly, I'm not that organised. What I'm really looking for is a webapp that can give me a view onto my media collection, and then allow me to select a file which will be transcoded on-the-fly to an iPhone-friendly format (preferably at a configurable bitrate) and streamed to my iPhone.

I've hunted around, and whilst there are a plethora of applications which will do something similar for music (ampache/kplaylist etc), I can't find anything for video files. Does anyone know of something like this?

Thanks.

---

### Post by tgui on 2010-03-08
I stream videos to my iPhone

- Transcode collection of desired videos with handbrake. I wrote some scripts to do this.

- Install apache web server

- Link IphoneVideos folder to Apache /var/www

- Setup .htaccess to password protect files

- Use iphone safari to browse folders and files.

- Click link on iphone and the video player launches!

Easy peasey.

When you find an all in one solution, let me know ;)

---

### Post by rotox on 2010-04-17
Hi,

Take a look at this thread. I think that it is just what you need.

J

[http://ubuntuforums.org/showthread.php?t=1456417](http://ubuntuforums.org/showthread.php?t=1456417)

---

### Post by mike_tyrell on 2011-10-14
and if that doesnt work for you use instead of air-video use "videostreama" or "video stream" and if that also doesnt work for you if u have a shared folder on ur network u can stream it using "o Player lite" or "O player" and if that also not working for you u can install mythbuntu on ur system and use a DLNA app on ur iphone to brows ur media servers and play videos. I my self use Video Stream with wine. its good to have more then one option to see what suits you :)

---

