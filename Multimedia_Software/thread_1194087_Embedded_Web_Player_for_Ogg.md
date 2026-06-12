---
title: "Embedded Web Player for Ogg?"
date: 2009-06-22
forum: Multimedia Software
---

### Post by BennieBlount on 2009-06-22
Does anyone know of Ogg player that can be embedded in a web page? A Google and Sourceforge.com search comes up really nothing. Need a player to play ogg files that are located on the server.

Thanks,

Bennie

---

### Post by chuyh on 2009-06-22
In this case the playback of your videos will rely on clients -viewers web browsers- and plugins available.

---

### Post by BennieBlount on 2009-06-22
To clarify my question:

No video, audio only. Is there Linux version of an ogg webplayer that can be embedded in a webpage?

---

### Post by mcduck on 2009-06-22
You should be able to embed your ogg files to the page with the object-tag.

Of course HTML5 also has the audio-tag, but until that gains some support in browsers I'd recommend sticking with the object-tag instead.

---

### Post by Seq on 2009-06-22
I'm not quite clear on your issue.

[LIST]
[*]If you want to play back ogg content on a site, there is a totem plugin for mozilla (probably a VLC and mplayer one as well).

[*]If you want to support media playback on your own site, you could use an applet like [cortado]("http://www.flumotion.net/cortado/") from flumotion. This is a java applet you could embed in your site to allow client-side playback of ogg formats.

[*]Along with the applet, you could start getting ready for HTML5. Firefox 3.5 will support vorbis and theora on it's own with the <video> tag.
[/LIST]

---

### Post by chuyh on 2009-06-22
I meant "audio" Bennie. I didn't know about Cortado, but it seems to be a good solution for your needs. Thx Seq.

---

### Post by BennieBlount on 2009-06-22
Yes, Cortado seems to be what I am looking for. Now to figure out how to get it working :)

Thanks,

Bennie

---

