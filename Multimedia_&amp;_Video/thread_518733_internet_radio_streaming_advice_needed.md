---
title: "internet radio streaming advice needed"
date: 2007-08-06
forum: Multimedia &amp; Video
---

### Post by raevsky.andrei on 2007-08-06
Hi,

Is it possible to listen (with Feisty Fawn) to internet radio stations streaming in Windows Media Player format?  I tried Rythmox, XMMS and Streamtuner but none of them could do that?

What about the BBC which streams in Real Audio (ram) format?

Thanks,

Andrei

---

### Post by Chappy7777 on 2007-08-07
> **raevsky.andrei said:**
> Hi,

Is it possible to listen (with Feisty Fawn) to internet radio stations streaming in Windows Media Player format?  I tried Rythmox, XMMS and Streamtuner but none of them could do that?

What about the BBC which streams in Real Audio (ram) format?

Thanks,

Andrei
=========================
Same question here. Streamtuner does a great job of bringing down some great stuff to listen to thru XMMS. However, I would like to know how to play the stuff I used to listen to using Real Audio and WMP "listen here" links. They open up .ra and .rm files and what do I do to hear these?

---

### Post by Chappy7777 on 2007-08-07
bump

---

### Post by raevsky.andrei on 2007-08-08
bump?

---

### Post by Chappy7777 on 2007-08-08
Bump    is used to get the post back to the head of the forum.

---

### Post by Obor on 2007-08-08
Have you got all the restricted formats installed? [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

That should let you play just about everything (including the BBC streams)

---

### Post by raevsky.andrei on 2007-08-08
@chappy7777 - ok. thanks for the bumping :-)
@obor - yes, I added the mediubuntu repo and installed all the stuff.  I also instelled Real Audio 10 but here is what I get when I tried to listen to the BBC:

> Connection to server has been lost. You may be experiencing network problems. (rtsp://rmlive.bbc.co.uk/bbc-rbs/rmlive/ev7/live24/worldservice/livenews_v8.ra?BBC-UID=44163b596fa5e3b8361e98cd8030c04f5999fc11600030534b7a40bace32f58d_n&SSO2-UID=)

and when I try to watch [Democracy now]("http://www.democracynow.org/streampage.pl") I get a Totem message saying "location not found".  (By the way, I would like Epiphany to use VLC as a video plugin, not Totem, how can I do that?)

why do I get a location problem?

thanks in advance

---

### Post by Obor on 2007-08-09
When I go to democracy it opens the video with the mplayer plugin for mozilla, you could try that one, it should be in repos.

If you want to use vlc I believe its the "mozilla-vlc-plugin" which should work with any gecko based browser.

I watch the BBC streams using the realplayer stream which works with both realplayer and mplayer plugin. 

Try few different plugins from the repos, one of them should work for you :)

---

### Post by cimex on 2007-08-09
The firefox MediaPlayerConnectivity Add-on lets you run the stream in an external player (you can define any player, I prefer VLC).  One of the advantages is that you very easy can save the playlist, and thus get the addresses for the stream.

[https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)

---

### Post by andrew.46 on 2007-09-10
Hi,

 Saw apost about streaming radio:

> **raevsky.andrei said:**
> Hi,

Is it possible to listen (with Feisty Fawn) to internet radio stations streaming in Windows Media Player format?  I tried Rythmox, XMMS and Streamtuner but none of them could do that?

What about the BBC which streams in Real Audio (ram) format?

mplayer will do that and will also save the files for offline listening if you wish. Some details here:

[http://people.aapt.net.au/~adjlstrong/ubuntu_cli.html#real](http://people.aapt.net.au/~adjlstrong/ubuntu_cli.html#real)

I am not sure of the repository version of mplayer has all the codecs that are available if you compile your own:

[http://www.mplayerhq.hu/MPlayer/releases/codecs/all-20061022.tar.bz2](http://www.mplayerhq.hu/MPlayer/releases/codecs/all-20061022.tar.bz2)

but it probably does not as real play etc are not open formats.

                  Andrew

---

