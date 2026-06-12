---
title: "Radio Station: don't know which plugin/codec is needed."
date: 2011-07-19
forum: Multimedia Software
---

### Post by Lepard on 2011-07-19
I'm having trouble getting audio from this particular radio station and have tried the gstreamer plugins, totem, VLC, win32codecs amongst others.  Using Ubuntu 11.04 and Firefox 5.0

Radio Station:
[http://z101digital.com/app/emisora.aspx](http://z101digital.com/app/emisora.aspx)

It works fine on my Windows 7 PC and my Macbook Pro.

Thank you for your assistance.

---

### Post by ron999 on 2011-07-19
Hi
The station plays in Firefox browser with **gecko-mediaplayer** plugin.

```
sudo apt-get install gecko-mediaplayer
```

---

### Post by Lepard on 2011-07-19
> **ron999 said:**
> Hi
The station plays in Firefox browser with **gecko-mediaplayer** plugin.

```
sudo apt-get install gecko-mediaplayer
```

Would I have to disable the other media plugins from within Firefox? Or can I leave those enabled?

---

### Post by andrew.46 on 2011-07-20
Try playing the stream directly from MPlayer as follows:

```
mplayer -cache 2048 'mms://67.159.60.125/zeta101'
```

Plays nicely in vlc as well, I attach a gratuitous screenshot of the radio station playing along with goom :). Now if only I understood Spanish......

---

### Post by ron999 on 2011-07-20
> **Lepard said:**
> Would I have to disable the other media plugins...

Yes, un-install totem-mozilla plugin and re-start Firefox.
Use this method:-
```
sudo apt-get remove totem-mozilla
```

---

### Post by Lepard on 2011-07-22
Thank you everyone for all of your assistance.  The tips worked great!

---

