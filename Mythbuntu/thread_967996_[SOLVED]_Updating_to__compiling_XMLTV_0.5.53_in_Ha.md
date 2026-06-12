---
title: "[SOLVED] Updating to / compiling XMLTV 0.5.53 in Hardy"
date: 2008-11-02
forum: Mythbuntu
---

### Post by EasyRiderOnTheStorm on 2008-11-02
Hi all, I've got a bit of a problem with my new Mythbuntu box; it's mostly working (you'll see me asking other questions around here), but the XMLTV grabber won't work. The reason seems to be a changed webpage layout (I'd be using tv_grab_huro), which may or may not have been fixed since - there is a note regarding fixing layout changes for tv_grab_huro in the 0.5.53 changelog. Which brings us to my problem:

- The latest available XMLTV update for Hardy is 0.5.51. I know its grabber is broken, for the URL it tries to crawl is clearly no longer accessible on the source.

- The XMLTV site mentions an available Debian package cared for by Chris Butler, which is also stuck at 0.5.51 for about three months now.

- The new Ibex seems to have the up-to-date 0.5.53 version of XMLTV, but it's not a LTS version, Hardy works mostly fine, and considering that grabbers can break anytime being able to compile the latest version seems like a better idea then hoping Ibex will keep me up-to-date seeing how Hardy doesn't.

My only EPG source is XMLTV, and unfortunately MythTv without a guide seems as practical as a fish on a bicycle.

I have built all my PC's myself starting with a 386, on windows; under Linux I'm a n00b - can use gedit, have seen vi, have no idea how to search for a file, let alone hop around repositories. I'm rather stubborn, though. Do you think there is a fairly detailed guide somewhere about compiling XMLTV (or the offending grabber) for Ubuntu/Debian, or some other way to get 0.5.53 to work? Am I making any sense here or is this like building the pyramids myself? Again, I'm a n00b here, please don't bother with "get the tarball and type make" sort of thing - if I could do that I wouldn't be here asking this. Any ideas...?

---

### Post by EasyRiderOnTheStorm on 2008-11-02
I'm a fool, as B.A. Baracus would put it, that's what I am. I looked up how to search for a file since the previous post by the way, and it's already working wonders: coming from the Windows world it never occured to me that the tv_grab_huro might not be a binary compiled file - which it's not. It's simply a Perl script marked as executable. Which is just as well, because noticing that allowed me to just fetch the new tv_grab_huro from the current 0.5.53 XMLTV package and replace my 0.5.51 version with it. This is of course not actually the real 0.5.53 XMLTV package that I have now, only it's grabber, but the point is that it works, it solved my problem, and now I have EPG data. Yaaaay...! :cool:

---

