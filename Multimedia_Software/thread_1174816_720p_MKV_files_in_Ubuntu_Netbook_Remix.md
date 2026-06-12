---
title: "720p MKV files in Ubuntu Netbook Remix?"
date: 2009-05-31
forum: Multimedia Software
---

### Post by dangling participle on 2009-05-31
I have an Acer Aspire One with a dual boot WinXP / Ubuntu Netbook Remix.  I am trying to play 720p MKV files in Ubuntu, but they play terribly slow.

I've followed the Comprehensive Multimedia & Video howto here, and regular videos play fine, but 720p MKV's are still extremely choppy in both Totem Movie Player and VLC. I haven't been able to get Mplayer to work, and I think that it is a known bug with Netbook Remix, see bug 370246.

I'm wondering if anyone has had any luck with 720p MKV files in Ubuntu on an Acer Aspire one or similar netbook.  Am I doomed to use Windows for HD videos?

---

### Post by celtic_druid on 2009-06-16
The Atom isn't really powerfull enough for 720p AVC decoding. I would think that coreavc is still the fastest software decoder which is maybe why it works better under windows? mplayer would only help if it is built to use coreavc, in which case you probably need to compile a recent SVN checkout yourself (maybe also still requires an additional patch?). A regular mplayer build would use libavcodec for decoding; same as VLC and Totem.

---

### Post by najgeetsrev on 2009-12-09
> **dangling participle said:**
> I have an Acer Aspire One with a dual boot WinXP / Ubuntu Netbook Remix.  I am trying to play 720p MKV files in Ubuntu, but they play terribly slow.

I've followed the Comprehensive Multimedia & Video howto here, and regular videos play fine, but 720p MKV's are still extremely choppy in both Totem Movie Player and VLC. I haven't been able to get Mplayer to work, and I think that it is a known bug with Netbook Remix, see bug 370246.

I'm wondering if anyone has had any luck with 720p MKV files in Ubuntu on an Acer Aspire one or similar netbook.  Am I doomed to use Windows for HD videos?
Hey. I have had the same problem. [I solved it using VLC](http://www.ditdomeinisvanmij.nl/2009/12/01/720p-video-on-an-atom-netbook-with-ubuntu-9-10/). Most content play's pretty smooth, atleast when there isn't a lot of movement in the scene. The atom proc just isn't powerfull enough.

---

### Post by SomeoneSimple on 2010-01-06
> The Atom isn't really powerfull enough for 720p AVC decoding.
> The atom proc just isn't powerfull enough.

Utter nonsense, the Atom N270 1.6Ghz should handle 720p just fine.

I am able to playback any 720p h.264 file with MPC-HQ on my Aspire One, with bitrates up to 6-8Mbit with FFMpeg decoder (using the Overlay renderer) under WinXP, the only thing you have to do, is disable the loop filter (deblock) and magically all 720p content is playable without framedrop or desynced audio. 
Same machine, but running a Linux Distro (doesnt really matter which one, i tried several, atm Mandriva 2010) trying to open the same file with VLC with the loop filter disabled, i get massive framedrop, simply unwatchable.

Im not proving anything here, but i'm just saying that the Atom N270 and up, playbacks 720p just fine on WinXP. But strangely enough, not with the same (?) FFMpeg decoder under Linux.

That said, i'll check out Corecodec under Linux, i don't have high hopes, but i am really missing the flawless playback of 720p back when i temporarily installed WinXP.

---

