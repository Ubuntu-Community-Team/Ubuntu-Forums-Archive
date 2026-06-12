---
title: "cannot play wmv file(s)"
date: 2014-06-11
forum: Multimedia Software
---

### Post by jgw on 2014-06-11
I am running with 14.04  I use xbmc as a player of downloads.  I have noticed that I cannot play wmv files and, sometimes, the program would freeze up.  I then tried to let ubuntu play a wmv file with the built in player.  It responds with an error "cannot determine type of stream".  I am wondering if these files are corrupt or there is another problem but I currently have no way of testing the file.  I either have corrupt files, or am lacking a codec, etc.  In either case I am kinda screwed until I can figure out an answer.  Any thoughts on this one would be appreciated.

Thank you................

---

### Post by tgalati4 on 2014-06-11
Install *vlc* and run it with the vlc message console open.  Under "Tools" you can get media information, codec info, and error messages.

---

### Post by jgw on 2014-06-11
Thanks for the reply - I will do that right now!!

---

### Post by Yellow Pasque on 2014-06-11
If you have gstreamer1.0-libav installed, totem (default player) should be able to play wmv.

---

### Post by jgw on 2014-06-11
Thanks for the reply  my problem is that I don't think its a wmv problem but a file problem but want to make sure.  I suspect I should be able to do that with vlc but can't figure out the commands.  I have, however, entered a request for help on the vlc forum.

---

### Post by mc4man on 2014-06-11
The only 'logging' you'll get by default is what's shown in a terminal when opening vlc, typically with a verbosity level set
(vlc -vv or vlc -vvv
That can be a bit of a pita to read thru.
logging can be enabled but you don't need for this. 
Try - 
open vlc
go ctrl+m to open a Messages window. In that window set Verbosity to 2 (debug
Leaving the Messages window open return to vlc > Media >  File > open your problem file.

After vlc fails then leave vlc open, return to &  read thru the output in the Messages window or click on "Save as" button & save to vlc.log 
Then you can read thru with a text editor (by default will be saved in home folder

---

### Post by jgw on 2014-06-12
thank you for the replies.  I forgot to add that I downloaded and installed the restricted codecs.  I did as suggested and have a vlc.log and I have no idea what I am looking for.  This can be seen at: [http://pastebin.com/ubHqQtnB](http://pastebin.com/ubHqQtnB)

---

### Post by Yellow Pasque on 2014-06-12
```
main debug: looking for demux module matching "asf": 63 candidates
mod debug: MOD validation failed (ext=wmv)
ts debug: TS module discarded (lost sync)
avformat debug: trying url: xxxxxxxxxxxxxx.wmv
avformat debug: couldn't guess format
...
ps warning: this does not look like an MPEG PS stream, continuing anyway
```

---

### Post by andrew.46 on 2014-06-13
Try uploading the file:

[http://www.datafilehost.com/](http://www.datafilehost.com/)

It would be interesting to see it first hand....

---

### Post by mc4man on 2014-06-13
Looks like you may have a garbage file. In addition to above could install avconv & or mediainfo
```
sudo apt-get install libav-tools
```
Then
```
    avconv -i /path/problem.wmv 
```
If using mediainfo gui then html view to read , text view to copy

---

### Post by jgw on 2014-06-15
Thank you for the replies.
I cannot upload as the smallest file I have is over 800mb

I did try the suggesting avconv and got:
greg@greg-N61PB-M2S:~$ avconv -i /media/greg/10D44B63D44B4A64/Movies/AmazingSpiderMan2/TheAmazingSpiderMan2.wmv
avconv version 9.13-6:9.13-0ubuntu0.14.04.1, Copyright (c) 2000-2014 the Libav developers
  built on May  9 2014 13:34:03 with gcc 4.8 (Ubuntu 4.8.2-19ubuntu1)
/media/greg/10D44B63D44B4A64/Movies/AmazingSpiderMan2/TheAmazingSpiderMan2.wmv: Invalid data found when processing input
greg@greg-N61PB-M2S:~$ 

I think its safe to say that it was a bad file?  I am going to mark this one as solved in that the solving proved, I think, that I somehow downloaded crap.

Thanks again!!

---

