---
title: "where is play, the console wav player?"
date: 2006-11-05
forum: Multimedia &amp; Video
---

### Post by asipi on 2006-11-05
hi all,

in dapper I used the console command play to listening for wav files but I do not find it in Edgy.
Is it possible that it has been removed from ubuntu?
It was in dapper, but I do not remember the package name :(

Any idea or suggestion?

PS: as an alternative solution I am using now the alsaplayer command line interface but I would prefer the simple play.

---

### Post by catlett on 2006-11-05
Very interesting. I am using play right now to play an mp3 file. Could it be a codec issue and not a play issue?
Can you play an mp3 or do you get the error "play...command not found"

P.S. I have a play binary in /usr/bin but I don't have a package called play in synaptic, for what it's worth.

---

### Post by asipi on 2006-11-05
command not found...
could you tell me wich package consists it?

---

### Post by catlett on 2006-11-05
I have tried searching but I cannot find it.  But get this, I found 2 similar command line players. splay and madplay,  figure that one out? I have the play binary but there isn't a lib folder for play. The package it is part of isn't labeled play. While searching I found "splay" and "madplay". Madplay appears almost exactly the same. Splay doesn't print out details of the track, it just plays.

---

### Post by asipi on 2006-11-06
thanks, splay is not working for me directly, i suppose more options need to call it (eg. sound device or something). I will check out madplay also, but as I mentioned right now I am usin the alsaplayer CLI. It is working, it is fine, but I would prefer the simple play.

As I remember there is a command somewhere wich can tell about a file what package it belongs to, but I did not remember.
I checked man of apt-cache but I could not find it, maybe not apt-cache is the right command for this.

---

### Post by catlett on 2006-11-06
[http://s7.quicksharing.com/v/7771925/play.html](http://s7.quicksharing.com/v/7771925/play.html)
For what it is worth, here is the binary for Play. Try putting it in /usr/bin and see what happens. You may have to make it executable, I don't know what happens when it goes to you. It is executable on my system.
Sorry about the file sharing site but it is the only way I could get it uploaded to share it with you. The page is mostly adds but just click on the "Download File" phrase and the binary will download. (firefox's download manager will open.

---

### Post by taurus on 2006-11-06
How about mpg321?

---

### Post by asipi on 2006-11-06
thanks, it helped!!!
when I tried to use it it said sox needed, after installed the sox package I found the play in /usr/bin
:)
so play belongs to package sox

---

### Post by asipi on 2006-11-06
> **taurus said:**
> How about mpg321?

thanks taurus, it did not played wav files corretly for me, I heard only noise, I think there is no bitrate control for wav audiodata in mpg321

---

### Post by catlett on 2006-11-06
> **asipi said:**
> thanks, it helped!!!
when I tried to use it it said sox needed, after installed the sox package I found the play in /usr/bin
:)
so play belongs to package sox

Well sox it is! Glad the binary helped, it was the only thing I could think of trying.

---

### Post by srt4play on 2006-11-07
> **asipi said:**
> As I remember there is a command somewhere wich can tell about a file what package it belongs to, but I did not remember.

That command would have been:

dpkg -S /usr/bin/play

which would return output:

sox: /usr/bin/play

---

### Post by catlett on 2006-11-07
> **srt4play said:**
> That command would have been:

dpkg -S /usr/bin/play

which would return output:

sox: /usr/bin/play

Thanks for taking the time to post that command. I'm saving it right now just to make sure I don't forget it in the future. 
> catlett@ubuntu:~$ dpkg -S /usr/bin/play
sox: /usr/bin/play
catlett@ubuntu:~$ Now that would have been easy. :D

---

