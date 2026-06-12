---
title: "I am attempting using last.fm for Ubuntu"
date: 2007-02-12
forum: Multimedia &amp; Video
---

### Post by justinrotnluk on 2007-02-12
[http://www.last.fm/tools/downloads/](http://www.last.fm/tools/downloads/)
the one on the right when linux is highlighted in the scroll bar, it says it's for debian/ubuntu [http://static.last.fm/client/Linux/lastfm_1.1.3.0-0edgy1_i386.deb](http://static.last.fm/client/Linux/lastfm_1.1.3.0-0edgy1_i386.deb)
I have Ubuntu Dapper
and when i opened the package manager it says:
Error: Dependency is not satisiable: libasound2
I am very very new to the whole linux experience, and was just about to give up until I found this forum.

---

### Post by frafu on 2007-02-13
> **justinrotnluk said:**
> 
Oh dear, I put this in the wrong forum... X_X

No Problem, I am moving it to the Multimedia and Video Forum. 

Have a nice day. 

Francesco

---

### Post by drezha on 2007-02-15
Last.fm is in the repository. At least in one of them. Universe propably.

Goto Synaptic Package manager and download it in that and it'll download all the requirements as well.

If you just want it to send in what you've listened to, use Rythmbox. It has support built in for last.fm already. Open it, goto edit then plugins to put your username and password in.

Hope that helps.

---

### Post by bsmith1051 on 2007-02-16
> **drezha said:**
> Last.fm is in the repository. At least in one of them. Universe propably.
All I see in the Universe repository is an old old version.

Thanks for the tip re Rhythmbox.  I don't particularly like it as a music app but the built-in Last.fm support is eeeasy.

---

### Post by bsmith1051 on 2007-02-16
> **justinrotnluk said:**
> it's for debian/ubuntu [http://static.last.fm/client/Linux/lastfm_1.1.3.0-0edgy1_i386.deb](http://static.last.fm/client/Linux/lastfm_1.1.3.0-0edgy1_i386.deb)
I have Ubuntu Dapper
and when i opened the package manager it says:
Error: Dependency is not satisiable: libasound2
I get the same thing.  And it's in error -- I have libasound2 installed already.  I even added the optional libasound2-plugins (using Synaptic) and it still reports "libasound2 not found"

There's also a generic Linux installer (an older 1.0.0.b version?) but that requires command-line 'make' etc which I don't want to have to do.

---

