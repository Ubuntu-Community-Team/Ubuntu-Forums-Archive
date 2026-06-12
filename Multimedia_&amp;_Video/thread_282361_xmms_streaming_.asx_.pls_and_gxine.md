---
title: "xmms streaming .asx .pls and gxine"
date: 2006-10-22
forum: Multimedia &amp; Video
---

### Post by xigen on 2006-10-22
HEllo.

my goal:  play kexp.org on xmms.

the issue:  when I get the url...
[http://kexp-mp3-128k.cac.washington.edu:8000/listen.pls](http://kexp-mp3-128k.cac.washington.edu:8000/listen.pls)
.. and ask xmms to play it.. nothing happens.

After quite a bit of experimenation I can play kexp via gxine and the link:
kexp-uncomp.asx

I have installed the win32codecs.

My question:  what would you recomend I do to get kexp to play under xmms. ([http://kexp.org/home.asp?noflash=true](http://kexp.org/home.asp?noflash=true))

dapper-drake, maudio-sound card, Alsa, AMD2200, 512ram, xmms and plf files instaled. 

thanks in advance.

---

### Post by H.E. Pennypacker on 2006-10-22
I am pretty sure you can't do .pls, and .asx on XMMS just as you wouldn't be able to do Real Media.  It's just one of those things.  It is possible that someone was nice enough to create a plug-in for XMMS.  You would have to check out XMMS' official website, and then the plug-ins section.  There's a list of plug-ins there.

I realize there's a plug-in for Real Media, but the download link is dead.

---

### Post by xigen on 2006-10-29
[http://www.kexp.org/audio/kexp-uncomp.asx](http://www.kexp.org/audio/kexp-uncomp.asx) 
This url works under Firefox 2.0 / Edgy  with win32codecs installed.

[http://kexp-mp3-128k.cac.washington.edu:8000/listen.pls](http://kexp-mp3-128k.cac.washington.edu:8000/listen.pls)
Works with streamtuner (streamtuner --> search --> kexp --> select kexp)
... it then uses xmms

So - xmms will play .pls
firefox 2.0 will play .asx

cheers,
mw

---

### Post by xeero on 2006-10-30
fyi, i can play .pls audio with xmms.  using xubuntu 6.10.  i installed the "multimedia codecs" (minus w32codecs) as instructed at:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

not sure if that was what it takes or not.

---

