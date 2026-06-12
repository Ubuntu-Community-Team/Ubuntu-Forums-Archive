---
title: "How do I record sounds from my sound card?"
date: 2006-12-25
forum: Multimedia &amp; Video
---

### Post by mjolinr on 2006-12-25
ok, so i have all these .ram files that only play in real player.  they are like a radio broadcast or something and I would like to put them on my ipod.  I tried **alsamixer** and i made the captur level 70 then **arecord -f cd -t raw | lame -x outputname.mp3** and then i play the file in real player.  when the file finishes i use control c to kill the arecord but when i go to play the new .mp3 file in movie player or whatever, it is blank.  what am I doing wrong?

---

### Post by logos34 on 2006-12-25
try  '... out.mp3'

here are the commands I use::

ARECORD - record audio from soundcard to compressed format (--> output = ~/out.<file extension>)

$ arecord -f cd -t raw | lame -x - out.mp3 (default - 44100Hz, joint stereo, 128kbps cbr)

$ arecord -f cd -t raw | lame -x -b bitrate out.mp3 (custom bitrate)

$ arecord -f cd -t raw | oggenc - -r -o out.ogg

$ arecord -f cd -d numberofseconds -t raw | lame -x - out.mp3

---

### Post by mjolinr on 2006-12-28
ok so i tried the 
> arecord -f cd -t raw | lame -x - out.mp3
because i dont need it in ogg since i want to put it on my iPod and custom bitrates arent necessary either.  i am only confused about how to stop the recording. is there a special thing to do or do you just hit control c? thats what i do.

---

### Post by logos34 on 2006-12-28
yep, ctrl + c or just set the recording duration (numberofseconds) so it stops automatically.  

So for a 1 hour program:

arecord -f cd -d 3600 -t raw | lame -x - out.mp3

---

### Post by natgwil on 2007-02-03
When I try the above I get the message:

Recording raw data 'stdout' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo

But nothing happens. Any ideas?

It turns out Audacity was causing some kind of problem. I had been trying to use it earlier to do some recording. After starting it and closing it again I tried the suggestions here and it started working.

---

### Post by natgwil on 2007-02-03
It turns out I still do have a problem. The recordings are distorted. I tried using alsamixer to set the capture setting as low as possible but there is still distortion. Any ideas what I'm doing wrong?

---

### Post by pseudonym on 2007-02-03
> **mjolinr said:**
> ok, so i have all these .ram files that only play in real player.  they are like a radio broadcast or something and I would like to put them on my ipod.  I tried **alsamixer** and i made the captur level 70 then **arecord -f cd -t raw | lame -x outputname.mp3** and then i play the file in real player.  when the file finishes i use control c to kill the arecord but when i go to play the new .mp3 file in movie player or whatever, it is blank.  what am I doing wrong?
Instead of recording, why don't you convert the files to mp3 using [ffmpeg]("http://ffmpeg.mplayerhq.hu/ffmpeg-doc.html#SEC25") or [mencoder]("http://www.mplayerhq.hu/DOCS/HTML/en/mencoder.html")? Both tools handle Real Audio well, I believe.

---

### Post by juah on 2007-02-05
> **mjolinr said:**
> ok, so i have all these .ram files that only play in real player.  they are like a radio broadcast or something and I would like to put them on my ipod.  I tried **alsamixer** and i made the captur level 70 then **arecord -f cd -t raw | lame -x outputname.mp3** and then i play the file in real player.  when the file finishes i use control c to kill the arecord but when i go to play the new .mp3 file in movie player or whatever, it is blank.  what am I doing wrong?

Don't use ctl+c to kill your arecord piped to lame. It kills the lame as well and the mp3 gets corrupted (not finished).  Open up another terminal window, use 'top' to kill arecord only or, use 'killall arecord'.  This is of course necessary only if you cannot predeterminate the length of recording.

---

### Post by mjolinr on 2007-03-15
just for the reference, i found a website that converts a bunch of different media,

[http://media-convert.com/](http://media-convert.com/)

---

