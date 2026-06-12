---
title: "WMA plugin progress bar"
date: 2009-09-02
forum: Multimedia Software
---

### Post by Rainbowsix on 2009-09-02
Whenever I visit a page which has an embedded audio clip in a little player, the progress bar does not move at all. I already searched and could not find an answer to this. I've also tried the MPlayer plugin and the progress bar does not even appear. Is there a WMA audio plugin which actually works? I will give the page I tried if requested.

---

### Post by andrew.46 on 2009-09-03
Hi Rainbowsix,

> **Rainbowsix said:**
>  I will give the page I tried if requested.

That would be great, could you give the address? If the codec is WMA you might be interested to know that MPlayer +plugin will play many windows-based codecs under Ubuntu by using a set of external codecs which [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") packages as the w32codecs. So perhaps have a look at installing these...

Andrew

---

### Post by Rainbowsix on 2009-09-03
I'm actually using 64-bit. I already have the codec and the file plays, but the progress bar either doesn't work or isn't there at all.

here is the exact link:
[http://www.realmofdarkness.net/pranks/mays-woman.htm](http://www.realmofdarkness.net/pranks/mays-woman.htm)

---

### Post by andrew.46 on 2009-09-03
Hi Rainbowsix,

I successfully played this stream from the web page using the MPlayer plugin and the 32 bit svn MPlayer. Looks like it is an mp3 stream, I am not entirely sure why this does not work on your system...

Andrew

---

### Post by Rainbowsix on 2009-09-03
I solved my own problem by installing gecko-mediaplayer. It seems to work just fine.

---

### Post by andrew.46 on 2009-09-03
Hi Rainbowsix,

> **Rainbowsix said:**
> I solved my own problem by installing gecko-mediaplayer. It seems to work just fine.

Good to hear the issue is resolved :-).

Andrew

---

### Post by Rainbowsix on 2009-09-04
One thing which annoys me still is that media will automatically loop. I can't find how to disable this.

---

