---
title: "Rebuffering Failure on Low Bandwith Connections"
date: 2008-07-29
forum: Multimedia Software
---

### Post by jadymitchell on 2008-07-29
I'm really, really pulling my hair out on this one and would appreciate any kind of suggestion.

I'm running Hardy.  To stream music, I use mt-dappd (firefly) connected through Soundbridges and Jinzora2 on an Apache server.

Everything was fine when I upgraded from Gutsy to Hardy and then I started to notice (say around March of this year) that mt-daapd would occasionally try to rebuffer  a track, fail, and then skip to the next track.  This would happen randomly, without any rhyme or reason.  Soon after, streaming Jinzora to a mobile device, I noticed there would be an attempt to rebuffer and then, again, a skip or just a total failure to stream.

I tried the Firefly and Jinzora forums, but no one else seemed to be having the problem.  There didn't appear to be many Ubuntu users either.

I wasn't sure if the problems were related.  After a lot of testing, it seems that it happens when Hardy is trying to stream to a weak network connection.  My Soundbridges usually have a relatively weak and inconsistent wi-fi connection and I stream jinzora2 over 3G.  The problem doesn't happen when the connection is fairly fast.  Note that steaming over the Soundbridges or 3G was never a problem until recently.

Forgive my ignorance, but is there one program/module that is common to mt-daapd and apache that might have been updated recently to cause this problem?  Put in a nutshell, the problem is that rebuffering no longer works for me.

Thanks.

---

### Post by jadymitchell on 2008-07-31
Bump.....

---

### Post by mattraines on 2008-08-03
I'm having exactly this same problem streaming MP3s from mt-daapd on Ubuntu to a Soundbridge Radio and a separate Soundbridge M1001. I've reinstalled mt-daapd from scratch (including deleting the configuration files) to no avail. I've tried it on both x86 and amd64 versions of Ubuntu.

Likewise it started happening when I upgraded from Gutsy to Hardy. My Soundbridges are also connected over wifi but I don't have any connection problems with laptops so I'm not convinced that's the issue. It's hardly "occasionally" though, it happens almost every 30 seconds or so. Not that it's regular, just frequent. My Soundbridges are currently sitting around idle as I can no longer listen to any music on them. :(

---

### Post by jadymitchell on 2008-08-03
Welcome to the club, Mattraines!  This problem just doesn't effect Soundbridges, but it seems any streaming media server.  I've put hours into this and have had no luck.

My most recent attempt was updating the kernel to the one in the proposed repositories, no luck.  Hopefully, someone who really understands streaming audio on linux will jump in here and help out.

---

