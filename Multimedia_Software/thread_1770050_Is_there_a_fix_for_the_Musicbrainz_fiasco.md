---
title: "Is there a fix for the Musicbrainz fiasco?"
date: 2011-05-28
forum: Multimedia Software
---

### Post by stchman on 2011-05-28
Has anyone found a fix for it?

---

### Post by karrank% on 2011-05-31
I just discovered this too.

[http://ubuntuforums.org/showthread.php?t=1763064](http://ubuntuforums.org/showthread.php?t=1763064)

Bug reports filed via Launchpad.

[https://bugs.launchpad.net/ubuntu/+source/sound-juicer/+bug/788921](https://bugs.launchpad.net/ubuntu/+source/sound-juicer/+bug/788921)

 and here.

[http://tickets.musicbrainz.org/browse/MBS-2249](http://tickets.musicbrainz.org/browse/MBS-2249)

---

### Post by stchman on 2011-06-01
I have read that many are aware of the problem, yes.

Here's a what if, what of Musicbrainz goes away?  Are all Ubuntu users that use Rhythmbox, SoundJuicer, and Banshee SOL?

I would like to see a way to input another online database.

---

### Post by stchman on 2011-06-01
I tried using Banshee (the latest version using the Banshee PPA) and it suffers from this as well.

---

### Post by karrank% on 2011-06-02
> **stchman said:**
> I tried using Banshee (the latest version using the Banshee PPA) and it suffers from this as well.

Rats, that's the next thing I was gonna do. Is Musicbainz the only cd database?

I mean, are there other rippers around that use a different cd-lookup system?

---

### Post by stchman on 2011-06-03
> **karrank% said:**
> Rats, that's the next thing I was gonna do. Is Musicbainz the only cd database?

I mean, are there other rippers around that use a different cd-lookup system?

There is RipperX, which you can specify a different server.

I get not so good sounding .mp3 files when I use RipperX.

If anyone can suggest optimum settings for RipperX then please do.

My thing about having only Musicbrainz is what if Musicbrainz goes belly-up?  Since there is no way to specify a CD database in Rhythmbox, Sound Juicer, or Banshee, what would happen?

---

### Post by karrank% on 2011-06-03
> **stchman said:**
> There is RipperX, which you can specify a different server.

I get not so good sounding .mp3 files when I use RipperX.

If anyone can suggest optimum settings for RipperX then please do.

My thing about having only Musicbrainz is what if Musicbrainz goes belly-up?  Since there is no way to specify a CD database in Rhythmbox, Sound Juicer, or Banshee, what would happen?

I think we're seeing what would happen.

And....

time to go install RipperX and see what happens....

---

### Post by mc4man on 2011-06-03
> Here's a what if, what of Musicbrainz goes away? 
Then you'll need to do what you're doing now, wait for upstream to fix or use a different ripper
(use abcde ansd or RubyRipper here, both are more useful rippers and don't need/use MB

As far as banshee the issue was a bit different and has been seemingly fixed
[http://git.gnome.org/browse/banshee/commit/?id=ee467bdc](http://git.gnome.org/browse/banshee/commit/?id=ee467bdc)
Applied the commit here and banshee is fine, hopefully you'll see in a banshee ppa soon if not already
> Bertrand Lorentz [banshee developer] 2011-05-28 14:49:29 UTC

This problem has been fixed in our software repository. The fix will go into
the next software release. 

---

### Post by karrank% on 2011-06-07
> **karrank% said:**
> I just discovered this too.

[http://ubuntuforums.org/showthread.php?t=1763064](http://ubuntuforums.org/showthread.php?t=1763064)

Bug reports filed via Launchpad.

[https://bugs.launchpad.net/ubuntu/+source/sound-juicer/+bug/788921](https://bugs.launchpad.net/ubuntu/+source/sound-juicer/+bug/788921)

 and here.

[http://tickets.musicbrainz.org/browse/MBS-2249](http://tickets.musicbrainz.org/browse/MBS-2249)

I've experimented briefly with  the "fix" in post # 5 of launchpad bug #455461 (#788921 was just a dup) [https://bugs.launchpad.net/ubuntu/+source/sound-juicer/+bug/455461]("https://bugs.launchpad.net/ubuntu/+source/sound-juicer/+bug/455461") and so far, working just fine --until Canonical, Ubuntu, or Musicbrainz resolve this, I imagine this is a good temp. fix. Try it and let me know if you agree.

---

