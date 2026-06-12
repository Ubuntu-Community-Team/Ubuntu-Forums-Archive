---
title: "windows speech decoder?"
date: 2011-09-21
forum: Multimedia Software
---

### Post by james2307 on 2011-09-21
i have changed to linux and trying to play videos from my windows os system.
Videos play but no audio, synaptic can't find a windows speech decoder for me to install.

can anyone pls help??:P

---

### Post by andrew.46 on 2011-09-21
Depends on which codec you are missing. There is a codec called Windows Media Audio 9 Speech which MPlayer will play with a windows codec:

```

andrew@skamandros~$ mplayer -ac help | grep -i windows
wma9dmo     dmo       working   Windows Media Audio 9 DMO  [wma9dmod.dll]
wmadmo      dmo       working   Windows Media Audio DMO  [wmadmod.dll]
**[COLOR="Red"]wma9spdmo   dmo       working   Windows Media Audio 9 Speech DMO  [wmspdmod.dll][/COLOR]**
wma9spdshow dshow     working   Windows Media Audio 9 Speech DShow  [wmavds32.ax]


```

But this codec is not all that common and perhaps there is something else you are missing. Could you post this file somewhere so I can have a look? If not perhaps try installing vlc:
```

sudo apt-get install vlc
```

which does not play Windows Media Audio 9 Speech files but will play most other things and perhaps this will play your files...

---

