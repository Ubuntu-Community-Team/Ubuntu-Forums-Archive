---
title: "K9Copy removes Mplayer during instalation ?"
date: 2008-03-03
forum: Multimedia &amp; Video
---

### Post by PiggiePaul on 2008-03-03
Is this normal?

K9 copy software removes mplayer and SMPlayer software from your system?

I tried to play a video tonight with Mplayer, but it did not play.

So I downloaded Mplayer again, it said it was clashing with Mencoder.

So I went to remove Mencoder, and it said K9copy will also go, if I remove Mencoder...

WTF !!!!

Ok, so got rid of that.

then got Mplayer back, and then SMplayer back (fresh installs)

Then got K9copy again, and putting K9 copy on, has again wiped out Mplayer and SMplayer (the front end)

Arghhhhhhhhhhhhh!

---

### Post by PiggiePaul on 2008-03-03
Just to add, this is strange, as I originally installed K9 a good week ago and I'm sure I 've had mplayer working as well since then................

Only other thing I've installed is Audacity (audio) but can't see that having any relevance.

Did have some graphics driver issues, (now put right) so not sure if that's had any effect.

But as I said, NOW, if I install KP copy it removed Mplayer and ifI install mplayer it removes K9 copy.

=========== EDIT =============

It's the Mencoder that seemed to be the problem
I Tried to uninstall Mencoder but that took K9 copy with it.

But, an update.

I seem to have got it working.

K9 installed (that again, took out Mplayer and SMplayer from my installed apps list!

I just ignored downloading mplayer again, and instead just installed SMplayer again, and during SMPlayers install it said "configuring Mplayer"

Now it all seems to work again.

Odd........... ?

---

### Post by mc4man on 2008-03-03
I had the same thing happen once on a test box - that install is long gone so I can't check. My memory is not what it once was but I think it came from having an mplayer that installed to /usr/local and then a k9 to /usr  
it was something like that

Edit: I think it was actually a compiled version of mplayer installed to /usr that also installed as part of the package, mencoder to /usr.  Synaptic though would not show mencoder as installed, so when trying to install k9 it would fail unless mencoder/mplayer were removed. I just used a built k9 instead of repo version instead.

---

