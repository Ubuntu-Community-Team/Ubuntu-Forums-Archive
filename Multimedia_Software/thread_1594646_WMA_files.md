---
title: "WMA files"
date: 2010-10-12
forum: Multimedia Software
---

### Post by Janeleaper on 2010-10-12
Ubuntu 10.04 Lucid

Whenever I download a WMA file from Beebotron I'm unable to play it.  I get the message *GstDecodeBin2: This appears to be a text file*.  Does anyone know how I can stop this happening?

---

### Post by andrew.46 on 2010-10-12
Hi Jane,

When I had a look at this site I could only find dead links and empty pages. Do you have a link to a working wma file on the site?

Andrew

---

### Post by Janeleaper on 2010-10-12
[http://beebotron.org/public3/radio4fm.html](http://beebotron.org/public3/radio4fm.html)

The above link will get you to the Beebotron page for BBC Radio 4 programmes.

---

### Post by ron999 on 2010-10-12
Hi
The BBC have recently changed the way the 'listen again' service works.
Previously they used RealAudio streams.
Now they're using WMA streams instead.
With the WMA streams they are downloaded in 'real time'.
So a half-hour show takes half an hour to download.:mad::mad::mad:

To download a show, right-click on one of the Beebotron links and 'Copy link location'.
For example the link for Bells on Sunday when copied to clipboard is:-
```
http://wm.bbc.co.uk/wms/radio4fmcoyopa/radio_4_fm_-_monday_0045.wma
```

You can download the show using mPlayer.
It is a 3 minute show, so it takes 3 minutes to download.
Use this command:-
```
mplayer -dumpstream -dumpfile Bells_On_Sunday.wma http://wm.bbc.co.uk/wms/radio4fmcoyopa/radio_4_fm_-_monday_0045.wma
```

After 3 minutes when the download is complete there is a message from mplayer says something like this:-

> Cache size set to 90 KBytes
Stream not seekable!
Ahhhh, stream_chunck size is too small: 4
Error while parsing chunk header
Core dumped ;)

Exiting... (End of file)

---

### Post by Janeleaper on 2010-10-12
Thank-you.  I've managed to get a bbc file to play.  I right clicked on the Beebotron link, copied address, and pasted into MPlayer.  It was a 15 minute programme, but did not actually take 15 mins to download -- more like 3, and it played!  I'll try with a longer programme now and see what happens.

---

### Post by andrew.46 on 2010-10-12
Works nicely here Ron, and I love that 'Bells' radio broadcast, it sounds the way I picture England!! 

Andrew

---

### Post by ron999 on 2010-10-13
> **Janeleaper said:**
> ... I've managed to get a bbc file to play.  I right clicked on the Beebotron link, copied address, and pasted into MPlayer...

Yes, that method is OK to use if you only want to **listen** to the programme without **downloading** it.

---

