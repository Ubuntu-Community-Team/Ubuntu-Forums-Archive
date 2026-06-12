---
title: "DVDs trouble - DVD Movie Protect and others"
date: 2010-03-14
forum: Multimedia Software
---

### Post by needhelpplease on 2010-03-14
Hello Ubuntuans,

I've been using MPLayer, which comes with libdvdcss and so on, for quite a while.  I get it from the Medibuntu repos.  It's very easy to set up and use.  I'm currently using Ubuntu 9.10.

Anyway, MPlayer has been quite good at playing DVDs for a long time, but recently I'm hitting more DVDs which don't play.  Just recently I was trying to play 2012 and I get:

```
libdvdnav: demux error! 00 00 00 (should be 0x000001) ?% ??,?% 854 0        
DVDNAV stream read error!
```

and it doesn't play.

I looked that up on line and found some references which indicate it's DVD Movie Protect, which I think is the same as [x-protect]("http://www.x-protect.com/").

I found a reference to [a patch]("http://archives.free.net.ph/message/20100214.192558.90b2b1e6.en.html") which is supposed to fix it.  I tried that patch, but I couldn't get mplayer to be stable with it compiled in.  Probably I was compiling it wrong.

Anyway, is there a solution to this?  I spent several hours today trying to get mplayer to compile and work with that patch, but no success.  Maybe someone will put together a repos for patched mplayers that are more aggressive in dealing with things like dvd-movie-protect?

It's really annoying and stupid because if I can't play this disk, which I legitimately rented, then I have the option of just downloading the whole thing from a torrent, but I would like to be able to play the "DVD" in my computer.

Someone should sue them for even marketing these things as DVDs.  They aren't DVDs.  They look like DVDs but they violate the DVD format specifications so they should not be allowed to be marketed as DVDs.

---

### Post by mc4man on 2010-03-14
A few things - 
that patch is quite old and no longer needed or viable, at least for any player using libdvdread4 (libdvdnav4

(I used to use it quite a bit in gutsy (7.10

Also if you're using 9.10 then mplayer isn't in medibuntu and wouldn't have libdvdcss internally, you'd need to have it installed (which you probably do.

As far as the title you mentioned - 2012, that's a sony release and when sony does use structure protection it uses it's own  - ARccOS, which generally doesn't cause players trouble. 
(there are some current protections that can be a bit problematic, particularity for some  mplayer builds.

You didn't mention what region you're from, ocassionally sony will treat R 2, 4 a little differently.

Anyway this title does have ARccOS protection (looking at a R 1 disk), though I see no playback issues with either vlc. totem-xine and a recently built mplayer (on karmic

The main movie is title 1, which mplayer should default to. ARccOS discs do tend to have a mis-encoded false start to the movie - maybe that's tripping up your mplayer, doesn't here.
Try from terminal and see what shows up
```
mplayer dvd://1
```

Vlc should have no problems playing this title, maybe try it.

(sometimes it's good to first go into your home folder (view -> show hidden files), find the .dvdcss folder and delete it in case you have incomplete or corrupted keys for the title in question.

---

### Post by needhelpplease on 2010-03-14
Thanks for the info.  It may be a bad disk or a problem with the reader.  I'll try it out.

I did try

mplayer dvd://1

And that works but it only shows the menu screen over and over without going into the movie.  When I try to play 

mplayer dvdnav://1

that hits the problem.

Any ideas on that?

---

### Post by mc4man on 2010-03-14
> Any ideas on that? 
Post your region, in R 1 title 1 is the movie so if you're R 1 this shouldn't happen...
> mplayer dvd://1

And that works but it only shows the menu screen over and over without going into the movie. When I try to play 

Or figure out the title for the movie and use that

As far as dvdnav, it works here, better to just use dvdnav://  and then if desired use the keyboard to call the main menu if it doesn't start on it (- unless you know the movie title number
( on mt laptop ESC call the menu, on my desktop numpad 5 - personally I find mplayer dvdnav to be skechy at best, particularly on a 5.1 audio system - it does not handle menu to movie or back audio very well

Try smplayer ( and check mplayer log in smplayer if needed

Use another player like vlc

Post a terminal output from mplayer, if there are 'too many video mplayer packets in the buffer' errors - don't need to see them - before and after more useful

---

