---
title: "VLC - capture and transcode mms stream from commandline"
date: 2008-03-28
forum: Multimedia &amp; Video
---

### Post by YoG%*@ on 2008-03-28
hi, 

i'm trying to capture (and transcode) an mms stream using vlc. there's a new episode available every day on the site that hosts the streams (actually, it's a newscast) and i want to automate the process of downloading it and making it available on my ipod. 

i know that it can easily be done through the gui but i don't want to do it by hand every day, therefore i'd like to write a script/something similar and set up a cron job or something like that. 

so far, i've come up with 
```

vlc mms://address.stream/file.wmv --sout "#transcode{vcodec=mp4v,vb=1024,scale=1,acodec=mpga,ab=192,channels=2}:duplicate{dst=std{access=file,mux=mp4,dst="filename.mp4"}}" -vvv -I dummy

```after googling and reading some of [http://wiki.videolan.org/Documentation:Streaming_HowTo](http://wiki.videolan.org/Documentation:Streaming_HowTo)

i used the '-I dummy' for not launching the gui, never mind the transcoding options, i'm still tinkering around with that.

the problem is that vlc keeps running after it has finished transcoding the file so i have to manually shut it down, which prevents me from using this in a script. is there a way around this?

are there any other tools to achieve this (i know mplayer can capture a stream)? i like the vlc approach because i can do everything (capture/transcode) in one step/command.

thanks in advance for any help!
mux

---

### Post by andrew.46 on 2008-03-29
Hi,

 I have set something similar with mplayer and a radio stream:

[http://www.andrews-corner.org/ftgws.html](http://www.andrews-corner.org/ftgws.html)

         Andrew

---

### Post by YoG%*@ on 2008-03-29
thank you for the tip, i'll definitely look into it and try it that way!

i'm still interested if it could be done using vlc. does anyone else maybe have an idea?

---

