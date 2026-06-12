---
title: "k9copy makes ISOs that ae too big"
date: 2007-12-04
forum: Multimedia Production
---

### Post by Phosphoric on 2007-12-04
Tried k9copy to copy a DL DVD to a single layer.  It produces an ISO file of about 5400 Mb which is too big......as k3b delights in telling me.


Any ideas folks?

---

### Post by nalmeth on 2007-12-04
Settings -> Configure k9copy -> DVD -> DVD size

I've never copied dual-layer DVDs, but I don't see why this wouldn't work

---

### Post by Phosphoric on 2007-12-05
Thanks for the reply, but that setting is already at 4400Mb

It's reducing it down from 7600 to 5600 but that's obviously too large.  Some of that reduction is me taking out the subtitles.

I must be missing something else. :confused:

---

### Post by nalmeth on 2007-12-05
Then try taking that number even lower, and there are reductions you can make, like the menu I believe, and other languages.

Regardless that is odd behavior, and maybe reducing the size even more will chop it down to your liking

---

### Post by Phosphoric on 2007-12-06
Right, I cut out everything but the main movie and I managed to get an ISO of 4400Mb.

The finished result is of good quality and has undefined chapters, but of course lacks the menu, subtitles, extras etc.

So, I have a watchable movie but not so easy to navigate.  ( It's actually 10 episodes of a TV programme)

I shall continue to look for a better version of k9copy which should be able to shrink the whole DL DVD.

Thanks. :)

---

### Post by orange2k on 2007-12-06
It works fine here. I never bothered to change any default settings and it works perfectly. Most of the times, I use k9copy to copy movies completely with all menus and comercials and I never had a single problem - size of the .iso is exactly such to fit on a single-layer 4.7 G DVD...:confused:

---

### Post by ryanVickers on 2007-12-06
They're not "too big", they are double layer DVD's, and so you can just use them.  If they are too expensive however (I can relate, don't feel bad :p), then just do what's been already recommended here - reduce the video quality or take out some of the special features.

---

### Post by orange2k on 2007-12-06
> **ryanVickers said:**
> They're not "too big", they are double layer DVD's, and so you can just use them.  If they are too expensive however (I can relate, don't feel bad :p), then just do what's been already recommended here - reduce the video quality or take out some of the special features.

But k9copy does that by default. Just the other day I made a backup of a double layer DVD to a single layer one. No additional quality settings tweaking was necessary. It compressed the whole movie with menus from 7,5 GB to 4,7 GB with no serious quality loss.

The whole point in using programs like DVD Shrink or k9copy is to use single layer DVD target media instead of the dual layer...

---

### Post by ryanVickers on 2007-12-06
If it was me though, I would not let it just do whatever it does to shrink it, I would want to try and see if removing unnecessary languages or extra sound modes would help, and if it's STILL not enough, then I would just do the whole thing on double layer! :p  But that's just me.... Also, anyone else who didn't know this - you can save a decent amount of pace by getting rid of languages that you don't speak lol

---

### Post by orange2k on 2007-12-06
> **ryanVickers said:**
> If it was me though, I would not let it just do whatever it does to shrink it, I would want to try and see if removing unnecessary languages or extra sound modes would help, and if it's STILL not enough, then I would just do the whole thing on double layer! :p  But that's just me.... Also, anyone else who didn't know this - you can save a decent amount of pace by getting rid of languages that you don't speak lol

There is a problem with that approach - Ive tried that strategy. The problem is that if you want to keep the menus and remove something, the menus won`t work anymore (in most cases).
My experience is that keeping everything from the original DVD works best. Quality loss resulting from the shrinkage is almost unnoticable.

On the other hand if I want to rip the movie only, without additional content, then I prefer to rip it to XVID to fit on 2 CD-s. But thats just me...

---

### Post by Phosphoric on 2007-12-06
> **orange2k said:**
> But k9copy does that by default. Just the other day I made a backup of a double layer DVD to a single layer one. No additional quality settings tweaking was necessary. It compressed the whole movie with menus from 7,5 GB to 4,7 GB with no serious quality loss.

The whole point in using programs like DVD Shrink or k9copy is to use single layer DVD target media instead of the dual layer...

That really was the point of my post...it should work.

Orange2k, what version of k9copy are you using and what version of Ubuntu are you using?

Thanks. :)

---

### Post by orange2k on 2007-12-06
> **Phosphoric said:**
> That really was the point of my post...it should work.

Orange2k, what version of k9copy are you using and what version of Ubuntu are you using?

Thanks. :)

I`m using version 1.1.3 on Gutsy 64-bit...

and I`m using k9copy only for image creation - for burning I use k3b

---

### Post by Phosphoric on 2007-12-06
OK, I'm using version 1.1.0 on Feisty 7.04 32 bit.  That's the latest version in the repos.

Maybe I should have a go at downloading an updated version   I guess from Source forge.  Perhaps I'll give it a go.

Last time I tried to compile my own deb I got in to dependancy hell and stuffed up my whole installation. :(
That's noobs for you.

Thanks for responding, maybe I'll have a go at the weekend when I've got some time.

Cheers :KS

---

### Post by orange2k on 2007-12-06
Maybe you changed the default settings by mistake.
Check the properties in k9copy and see if the DVD size is set to proper value (default is 4400 MB...)

---

### Post by Phosphoric on 2007-12-06
Thanks mate, but I've done all of that.  I've been through every tab to see if there is an option that might help.
DVD size definitely set at 4400Mb.

Anybody know if there is a changelog for this software, that might give me a clue at which version to try for?

---

