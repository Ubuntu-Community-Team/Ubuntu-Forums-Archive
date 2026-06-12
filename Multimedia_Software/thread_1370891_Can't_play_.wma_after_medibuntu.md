---
title: "Can't play .wma after medibuntu"
date: 2010-01-02
forum: Multimedia Software
---

### Post by b1lancer on 2010-01-02
Hello,

I followed instructions on the medibuntu site for installing the codecs to play .wma files. I checked to make sure the repositories where properly added and they are. I even tried usin VLC player. Any ideas?

Thanks!


Happy new year all!

---

### Post by ron999 on 2010-01-02
Are you saying that VLC media player won't play those .wma files?

---

### Post by mc4man on 2010-01-02
If you're on a 32 bit install and haven't installed already,  than run this in a terminal. If you're on a 64 bit install don't bother, only wma2 is possible and for that you don't need anything more than should you already have. ( libavcodecXX, and the  3 basic gstreamer plugins - bad, ugly, ffmpeg
```

sudo apt-get install w32codecs 
```

Basic state of wma in 9.04 -> 10.04 with standard repo, ppa players

wma2 - all players, 32 and 64 bit (- if you can't get playback of wma2 w/ those gstreamer plug-ins on karmic then try a restart.

wma3 (pro, 9.1, 10 ) - only mplayer and xine based players w/ w32codecs installed
   - *technically* gstreamer should decode wma3 (pro, 9.1) thru w32codecs and the gstreamer plug-in - pitfdll
  
wmal (lossless) - only mplayer and xine based players w/ w32codecs

If the ubuntu dev's would bump their ffmpeg (libavcodecXX) version up a bit then wma3 decoding would be available to vlc, mplayer and with possibly some work also gstreamer in both 32 and 64 bit.

So far they haven't, what happens in 10.04 is atm not clear.

(( vlc can also use some of the w32codecs if built with dmo enabled, It worked flawlessly in 0.9.X, not so well in 1.0.X though wma3 and wmal are still possible in a limited playback fashion.

---

### Post by b1lancer on 2010-01-04
Ok. I see that the file I am trying to open is in fact .wmal and that is why vls wasnt opening it. I believe I had already installed all the win32 codecs because I followed the instruction shown on medibuntu. Is there a way I can verify I have the codecs installed??


Thanks a whole lot **mc4man **for your excellent explanation! i was able to play the file using Xine.

---

### Post by andrew.46 on 2010-01-05
> **mc4man said:**
> 

(( vlc can also use some of the w32codecs if built with dmo enabled, It worked flawlessly in 0.9.X, not so well in 1.0.X though wma3 and wmal are still possible in a limited playback fashion.

wmal playback seems a little better with the latest vlc:

```

andrew@skamandros~$ cvlc --version
VLC media player 1.1.0-git The Luggage
VLC version 1.1.0-git The Luggage (fe9974b)
Compiled by root@skamandros.andrews-corner.org

```

Finally [my favourite wmal clip]("http://samples.mplayerhq.hu/A-codecs/lossless/luckynight.wma") plays perfectly:

```

[0x8114414] main decoder debug: looking for decoder module: 32 candidates
**[COLOR="Red"][0x8114414] dmo decoder debug: DMO codec for WMAL may work with dll=wma9dmod.dll[/COLOR]**
[0x8114414] dmo decoder debug: DMO input type set
[0x8114414] dmo decoder debug: DMO output type set
[0x8114414] dmo decoder debug: GetOutputSizeInfo(): bytes 16384, align 1
[0x8114414] main decoder debug: using decoder module "dmo"
[0x8114414] main decoder debug: TIMER module_need() : 48.925 ms - Total 48.925 ms / 1 intvls (Avg 48.925 ms)
[0x8114414] main decoder debug: thread (decoder) created at priority 5 (input/decoder.c:302)
[0x8114414] main decoder debug: thread started
[COLOR="Red"]**[0x810f34c] main input debug: `file:///home/andrew/samples/luckynight.wma' successfully opened**[/COLOR]

```

All the best,

Andrew

---

