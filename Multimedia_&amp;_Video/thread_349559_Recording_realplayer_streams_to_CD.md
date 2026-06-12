---
title: "Recording realplayer streams to CD"
date: 2007-01-30
forum: Multimedia &amp; Video
---

### Post by Zill on 2007-01-30
The BBC supplies radio programs in realplayer ra format.  Suggestions please on:
1)  The best app(s) to record these ra streams
2)  The best format to save these streams in so that they can be played by a "normal" domestic CD or DVD player.
Any help on this gratefully appreciated - multimedia is not my strong point :-(

---

### Post by HenrikAn on 2007-01-31
I doubt it's the best way, but it works for me... Command line style...
First I rip the stream (I use the [World News Bulletin]("http://www.bbc.co.uk/radio/") as an example)
```
mplayer -dumpstream -dumpfile summary5min.ra rtsp://rmv8.bbc.net.uk/worldservice/summary5min.ra
```  
Then I convert the Real Audio file to wav:
```
mplayer -quiet -vo null -vc dummy -ao pcm:waveheader:file="sumary5min.wav" summary5min.ra
``` 
If you want to archive this as an audio CD you can now go ahead and burn it from the wav file, or you could convert it to mp3:
```
lame -m s sumary5min.wav-o sumary5min.mp3
```

---

### Post by Zill on 2007-02-04
Thanks for that HenrikAn.  Your code works very well.
The command line is wonderful when you understand it :-)
Thanks again.

---

