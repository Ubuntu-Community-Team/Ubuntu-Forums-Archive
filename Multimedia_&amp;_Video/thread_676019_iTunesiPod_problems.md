---
title: "iTunes/iPod problems"
date: 2008-01-23
forum: Multimedia &amp; Video
---

### Post by Canew on 2008-01-23
Hi:

So I got an iPod Shuffle for Xmas, and I've decided to take the plunge into iPod/iTunes land. I love my Shuffle, and Rythmbox, until last night, has been a great manager for my songs and playlist (it's a Shuffle, so I only get one at a time on it).

Originally, I set up iTunes, registered my Shuffle, etc. on my gf's Windoze XP computer (which I don't always have access to). Took the Shuffle home, and after a few minor hangups, have managed to get it working well under Rythmbox.

The problem: I bought a song at my gf's place using iTunes, put it on my otherwise blank Shuffle (@^&# autosync wiped it out), and took it home.

So I go to transfer the song to my (Gutsy Gibbon, for those who care) computer, I find it's "encrypted," and can't be played or used in any way. I can't add it to my playlist. Whatever. I just take my playlist (100+ songs) and add it to the iPod. Then I try to manually add the iTunes song I bought. All heck breaks loose. Now, not only did that NOT work, but now, even when I wipe out everything on it and RELOAD it, the songs all appear in Rythmbox, and I can even play stuff from the Shuffle through the computer, but when I go to use the headphones, I get that green-amber-green-amber message indicating nothing's on it.

My questions:

1) Can I use Floola to "repair" the Shuffle, or am I gonna have to wait till the weekend, hook it up to iTunes, and reformat it to "Factory settings?"

2) Would burning the song I bought (which is still in iTunes on the XP computer) onto a CD, then ripping it onto my computer allow the song to show up normally?

---

### Post by tgalati4 on 2008-01-23
(choose the foreign accent of choice)

. . . You have experienced the benefits of Digital Rights Management (DRM).  Your device is acting normal.  To avoid further problems, only use iTunes with the Shuffle and only purchase your music from iTunes music store. . . .

. . . Try reinstalling Windows . . .

Seriously,

If you want to use your shuffle with both iTunes and Linux, you will have to reset it first under iTunes.  You can certainly reset it with other programs, or create a new database with gtkpod or floola, but then iTunes will fart and wipe it.

Yes, you can always burn a CD and rerip it.  There are perhaps better ways to do it but we can't advocate circumventing DRM in the forums.  Afterall you paid for the priviledge of having DRM, so you should enjoy all of its advantages.

---

### Post by Canew on 2008-01-23
Thanks for the reply. If floola really does work, then I'll use it from now on, but first you're saying I have to hook the shuffle up to iTunes to fix it? Grr! Whatta pain! That'll wipe everything on it, which means I have to take it BACK home to my Linux box to re-load it! :cry:

Yeah, DRM is a pain, but I am NOT asking for ways to circumvent it. I'm not a music/software pirtate. I don't even use filesharing software. I'm not looking to become a bootleg bandit here. I just want the $&#^@ song to work! *sigh*

---

### Post by Canew on 2008-01-24
ARGH! I can't use Floola because I don't have write permission on the iPod! I'm trying to change it in terminal with sudo chmod, but the iPod isn't responding. 

This is what I get for the iPod when I do ls -al in the media directory:

```
dr-x------  3 gonzo root 8192 1969-12-31 19:00 SEAN'S IPOD

```

So I do this:

```
gonzo@gonzo-desktop:/media$ sudo chmod a+w SEAN'S IPOD

```

and all I get is this: 

```
> 

```

with a blinking cursor next to it. That's it. I'm stuck. I have to close out of the terminal the hard way. No response to commands, and the permissions still don't change. WTF?

---

### Post by Canew on 2008-01-24
Anybody? This is making me nuts. It seems sometimes I can access it, and sometimes I can't.

---

