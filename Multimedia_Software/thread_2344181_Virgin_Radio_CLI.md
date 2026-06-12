---
title: "Virgin Radio CLI"
date: 2016-11-23
forum: Multimedia Software
---

### Post by WDYSUN on 2016-11-23
Ciao a tutti

qualcuno sa come posso ascoltare la diretta di Virgin Radio dalla shell? Ho trovato diverse soluzioni in rete ma nessuna di queste mi funziona. La più suggerita in diversi post (di qualche anno fa ormai) è questa:

```

 rtmpdump -v -r "rtmp://fms.105.net:1935/live" -y "VirginRadio" | vlc -

```

ma nisba!

P

---

### Post by cariboo on 2016-11-25
You may be better off going [here]("http://forum.ubuntu-it.org/") if English isn't your first language, as this is an English only Forum.

---

### Post by WDYSUN on 2016-11-25
> **cariboo said:**
> You may be better off going [here]("http://forum.ubuntu-it.org/") if English isn't your first language, as this is an English only Forum.

I'm really sorry, for some reason I was convinced to write on [http://forum.ubuntu-it.org/](http://forum.ubuntu-it.org/)

I'll close this!

Regards
P

---

### Post by shantiq on 2016-11-26
Just to listen   
solo per ascoltare


> cvlc  [http://radio.virginradio.co.uk/stream]("http://radio.virginradio.co.uk/stream?awparams")

+++++

If you want to record:
Se si desidera registrare:


> cvlc --run-time=1800 [http://radio.virginradio.co.uk/stream]("http://radio.virginradio.co.uk/stream?awparams") --sout "#duplicate{dst=std{access=file,mux=raw,dst=/home/[COLOR=#ff0000]yourname[/COLOR]/Desktop/Virgin Live &#9834;&#9834; -$(date "+%a %F [%T]").mp3}" vlc://quit

Just change the duration to suit your needs; 1800 is half an hour
Basta cambiare la durata in base alle proprie esigenze; 1800 è mezz'ora
And change [COLOR=#ff0000]yourname[/COLOR] for your name of course
E cambiare [COLOR=#ff0000]yourname[/COLOR] per il nome ovviamente

---

