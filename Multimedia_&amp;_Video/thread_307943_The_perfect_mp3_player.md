---
title: "The perfect mp3 player??"
date: 2006-11-27
forum: Multimedia &amp; Video
---

### Post by hellmet on 2006-11-27
One thing that I've been waiting and wanting on Ubuntu is a player..
that could all these things for me..with no fuss

1)Play Mp3Pro(Most of my mp3 collection is in mp3pro
2)Double Clicking should enqueue the song into the playlist

its as simple as that.. but the search has been gng on....

XMMS plays mp3pro..but not thru ALSA for some strange reason.:???:
It can't enqueue files..double clicking plays the new song..](*,)

---

### Post by richardward101 on 2006-11-27
amarok queues up with a double click, and I'm pretty sure it plays mp3pro. Its a great player in general, if slightly bloated.
You may need w32codecs to do mp3pro in general, not sure, but bear in mind its illegal in America and some other places to use w32codecs.

---

### Post by hellmet on 2006-11-27
me in India.. so no prob.. btw.. can someone clarify if Amarok can
play mp3pro?..maybe with some extra plugin or something

---

### Post by Mike'sHardLinux on 2006-11-27
I just googled for mp3pro and downloaded some clips that claim to be mp3pro. Amarok plays them fine, without any plugins. I cannot verfiy if these really are mp3pro, though. They sure are encoded at low bitrates: [http://www.deepskydivers.com/new%20age%20music/dsd_free_downloads.htm]("http://www.deepskydivers.com/new%20age%20music/dsd_free_downloads.htm")

I second the motion for Amarok. It is my absolute favorite player. It can be a media manager similar to iTunes, but you can also use it in player mode that's more like XMMS or Winamp.

Also, in case the question comes up, you ***can*** use Amarok in Gnome. I do.

---

### Post by hellmet on 2006-11-28
nope.. for me it din play..mp3pro
neither does it enqueue when double clicking songs..

---

### Post by hellmet on 2006-11-28
amarok is really nice..
but.. as I said.. I'd want those features in it..

---

### Post by richardward101 on 2006-11-28
Strange, As I'm using Amarok now, and items definitely queue up when you double click them in the players collection, or do you mean that they need to queue up when you double click on them in the file browser? Because if thats the case then you can do that with most players, let me know if thats the case and say which player and I'll tell you how.

As for mp3pro, is the music from the site quoted above proper mp3pro (check if you can play it in amarok), as it works for me, so it may just be a codec thing thats easily fixed.

---

### Post by hellmet on 2006-11-30
yea. I was talking of double cliks in the file browser..
and mp3pro doesn't play.. 
I checked the file from the site u mentioned too..
It plays but.. it doesn't have the mp3pro codec..
so the file loses its high freq. notes..
Its plays fine in XMMS with the mp3pro plugin..
but I've had problems trying to enqueue files in XMMS too..

---

### Post by richardward101 on 2006-11-30
OK then, bring up a terminal and type:

sudo nano /bin/xmmsqueue

then type:

#!/bin/bash
xmms -e $@


Now press CTRL+O (not zreo) to save, and CTRL+X to exit

now:

sudo chmod +x /bin/xmmsqueue

now right click an mp3 in the file browser and click properties, go to the 'open with' tab and click add, use a cuton command, and type in:

xmmsenqueue

make sure its selected as the default in the 'opens with' tab, and now when you double click files they should enqueue in xmms.

Hope that works.

---

### Post by Mike-97470 on 2006-12-28
This thread's discussion seems to be missing the fact that mp3pro is backwards compatible.  ie: mp3 players can play mp3pro files and mp3pro players can play mp3 and mp3pro files, but only mp3pro players can play mp3pro with inhanced mp3pro fidelity.

What that means is that Amorak and XMMS, etc. can being playing a mp3pro stream and you may not know it.

Check it out mp3pro here:
[http://www.all4mp3.com/info/mp3pro_about.html](http://www.all4mp3.com/info/mp3pro_about.html)

---

### Post by Dillinger-1969 on 2007-02-19
I also have the same complaint about mp3pro playback as hellmet......
yes they play but at same quality as low bitrate mp3
the way I understand it is that amarok lacks the necessary codecs for mp3pros to be played as mp3pros. So the question is Is there a way to get Amarok to use a codecs that will recognize mp3pros as such. If not then I guess I will have to switch to XMMS.

---

### Post by hellmet on 2007-06-04
I've converted most of my collection back to mp3 !!

---

### Post by drietow on 2007-06-04
This web page says it has an MP3PRO plug in for XMMS.
[http://wholewheatradio.org/wiki/index.php/XMMS](http://wholewheatradio.org/wiki/index.php/XMMS)

---

### Post by hellmet on 2007-07-05
Ok.. I've most of my collection now in mp3, so mp3pro ruled out.
The amaroK on Feisty enqueues files on double click while playing, and plays files when there ain't nothing in the playlist. Perfect. This thread should be [SOLVED] :D

---

