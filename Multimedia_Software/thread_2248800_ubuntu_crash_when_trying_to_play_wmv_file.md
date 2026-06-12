---
title: "ubuntu crash when trying to play wmv file"
date: 2014-10-17
forum: Multimedia Software
---

### Post by oren tal on 2014-10-17
Hi,

Every time I try to play WMV file in my Ubuntu, the player crash.

I believe the problem in Ubuntu and not in the player, because it happend in VLC and in other players as well.

It is also happening only in the case of WMV file, other file are played just fine.

---

### Post by Vladlenin5000 on 2014-10-18
Do you remember installing some additional codecs? I mean, something besides (or instead of) the usual *ubuntu-restricted-extras *package?
It's a weird problem indeed but you aren't alone... I recently heard of a similar problem in a friend's Ubuntu -and- she has a vague recollection of installing some additional codec "recommended" in one of those pages of "10 things to do after installing Ubuntu XX.XX". She was following instructions without really knowing what those things meant.
Anyway, the problem was solved by a fresh installation plus restricted extras. Every media file plays fine now in every program so she's happy :p
The downside is I never had the chance to get to the bottom of it. Let's hope some multimedia&codecs expert post here some troubleshooting suggestion.

---

### Post by coffeecat on 2014-10-18
*Thread moved to **Multimedia**.*

---

### Post by Rob Sayer on 2014-10-18
Do you mean just *one* .wmv file or *any* .wmv files?  If it's just one it may be corrupt or have been made with some wonky non standard codec.

It is possible that installing some 3rd party codec messed up another library, though it's rare in linux, not common as in windows.  In linux if that happens you should get a message that installing it will remove something else.

Whether you have ubuntu-restricted-extras or not shouldn't affect vlc or smplayer.  They come with their own codec libraries.  But it's possible, as mentioned.  This is why noobs shouldn't use external ppa's.

I'd try installing smplayer and seeing if that works first.  It actually has a better codec library than VLC, which is not quite the "play anything" program people seem to think it is.

You should also install mediainfo-gui and open a/the file you're having problems with.  Then post the results in text mode.  Use code tags.  It may have some wonky codec/format.  Especially if it's a downloaded file. In media circles encoding to .wmv at all is considered a good sign of incompetence.  It's a crap format by a company that is strangely unable to make decent media software.

---

### Post by Vladlenin5000 on 2014-10-18
I can only speak about my friend's case, the only one I knew until I stumbled upon this thread: All .wmv files triggered the crash in all players tested; the some files played perfectly in other Ubuntu computers and all worked fine before in the same computer (and work now as well after reinstalling Ubuntu) therefore I suspect it's something codec related.

Do you know the exact name of the codec that deals with .wmv? And how to check its version and/or other details?

---

### Post by Vladlenin5000 on 2014-10-19
Bump (for your issue and my scientific curiosity).

---

### Post by Rob Sayer on 2014-10-20
I'm kind of curious too.  Need mediainfo data.  If there's any program you should have if you do a lot of multimedia stuff it's that one.

Some .wmv files use a very old Microsoft VC-1 format that's proprietary and very poorly supported.  And not just in linux.

---

### Post by Vladlenin5000 on 2014-10-21
> **Rob Sayer said:**
> Some .wmv files use a very old Microsoft VC-1 format that's proprietary and very poorly supported.  And not just in linux.

I'm aware of that. However, all of her videos play fine now after reinstalling whereas before they didn't and all the players, including VLC, crashed. I can ask her about the mediainfo -perhaps this week if she isn't busy - but I suspect there were something else going on before.

---

### Post by wilson0028 on 2014-11-06
I had this exact problem, all wmv files would crash in totem and vlc.  I also had ffmpeg installed via jon-severinsson/ffmpeg.  purging this and then updating to the official packages fixed the problem for me.

---

