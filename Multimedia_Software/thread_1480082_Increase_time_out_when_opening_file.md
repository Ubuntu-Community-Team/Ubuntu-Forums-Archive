---
title: "Increase time out when opening file"
date: 2010-05-11
forum: Multimedia Software
---

### Post by K.J. on 2010-05-11
Well, here's the background information.  My media PC is modestly powered, enough for high-def video but not enough for full screen flash (really need a beast for that one).  It's currently running Ubuntu 10.04.  I have a Windows machine running PlayOn software to serve up Netflix, Hulu, and the like via UPNP.  I've been using XBMC/Boxee to open the UPNP stream, but it's quite annoying.  Because PlayOn takes a little bit to get the stream up, it times out. You then have to re-attempt to open the stream several times before it works and you quite often miss the first few seconds of the tv show/movie.

However, as far as I can tell (and Google), XBMC (and Boxee by proxy) have no user definable way of increasing the time-out.  Therefore, I have installed djmount to try and stream the videos. However, the videos also time-out using this method, with Nautilus, I believe, as the culprit.  For example, if I use Filezilla to ssh into the machine (either local or remote) and disable time-out, the files stream/transfer perfectly fine.

What I want to know, is there a way to increase the "native" time-out on opening files. Either straight from nautilus, or in XBMC, VLC, etc.

Thanks!


EDIT:

In case anyone is curious, while not elegant, I have been able to solve my problems. You can use upnp-inspector to browse the PlayOn share and find the address to the HTTP stream for the movie file (or the m3u which contains the http stream). You can then watch it with pretty much any movie player, although the default seems to work better than vlc.  You can also use wget to download it as a .mpg and watch it later.

---

