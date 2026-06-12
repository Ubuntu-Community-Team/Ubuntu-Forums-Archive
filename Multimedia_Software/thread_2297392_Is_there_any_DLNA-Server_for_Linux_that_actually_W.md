---
title: "Is there any DLNA-Server for Linux that actually WORKS?"
date: 2015-10-03
forum: Multimedia Software
---

### Post by b00nish on 2015-10-03
Hi

I'm a bit frustrated because I failed the task to find a working DLNA Server even if I tought such a thing would be the easiest thing in the world. But let me explain.

I have some kind of file server (running kubuntu 14.04) with music and movies on it. And i have a quite modern Sony TV (running Android) and a Yamaha Network Media Player.

To the TV I'd like to stream my movies (mostly x264/MKV) and to the Yamaha I'd like to stream my MP3s. Since navigation in my MP3 collection is a bit of a problem, I need a DLNA-Server that can parse M3U (or PLS) Playlists.

Since Mediatomb (which I used years ago for other purposes) isn't able to parse playlists, I switched, after quite some searching, to "PS3 Media Server". This worked fine for some weeks (well, playlist-parsing isn't as good as you'd wish but at least it works partially) and movie-streaming woprked great.

Now, all of a sudden, movie streaming ceased service completely. I didn't change anything. My TV didn't change anything. It just stopped working. So after hours of tinkering without result if found the information that "Universal Media Server" would be a great fork of PS3 Media Server - a fork that actually is still maintained. Unfortunately Universal Media Server also refuses to stream any video to my TV.

So is there any way to have DLNA Streaming with Linux?

---

### Post by SeijiSensei on 2015-10-03
I use **minidlna**.  It don't use it often, but it seems pretty reliable.

---

### Post by b00nish on 2015-10-03
I remember that I tried minidlna aka ReadyMedia and gave up on it. Don't remember the reason, tough. Does it parse playlists?

---

### Post by SeijiSensei on 2015-10-03
[Apparently yes](https://www.google.com/search?q=minidlna+playlist).

---

### Post by coldraven on 2015-10-04
Kodi supports m3u playlists
[http://kodi.wiki/view/Basic_playlists](http://kodi.wiki/view/Basic_playlists)

---

### Post by b00nish on 2015-10-04
Hi

Thank you for your replies:

I tried MiniDLNA aka ReadyMedia yesterday again (in my desparation). Unfortunately it doesn't work the way I nedd it at all.

But Kodi was a good hint - but not as server, as a client. I read about it in another board where they suggested to use Kodi as a client instead of the built in of the TV (since it's an Andorid TV I can just install other clients form the PlayStore). And look at it - it works perfectly. So apparently it's not just that the server OR the client have to work properly, they also have to works properly togehter. This doesn't seem the case with the built in Andorid Client and "PS3 Media Server" (aka Universal Media Server), but it works with the latter and Kodi. Since Kodi is such a feature rich client, I actually have no interest in gettin back to the standard one anyway.

---

### Post by coldraven on 2015-10-05
FYI with the Yatse (non-free) remote control app running on my Android phone I can stream music/video directly to my Raspberry Pi2 Kodi server. The free Kodi created remote control app Kore works just fine as a remote, no streaming.

---

