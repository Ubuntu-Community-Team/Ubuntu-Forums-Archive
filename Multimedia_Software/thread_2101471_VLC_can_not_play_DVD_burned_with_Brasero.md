---
title: "VLC can not play DVD burned with Brasero"
date: 2013-01-04
forum: Multimedia Software
---

### Post by rybnik on 2013-01-04
I copied a DVD with Brasero.

When I try to open the burned DVD in VLC, VLC just closes itself after about half a second.  It's /dev/sr0 and when I specifically point VLC to that path, it does the same.  VLC also just closes when I specifically point it to /media/movie-name-here/VIDEO_TS

However, I *am* able to open individual .VOB files within the /media/movie-name-here/VIDEO_TS directory

Also, I tried playing the burned DVD on a home DVD player.  After inserting the disc, the player does something, then stops.  After pushing play, it works just fine.  So I figure that if I can get it to play on a home DVD player perfectly, then why can't I get it to play on my computer?  Any ideas?  

Please and thank you.

---

### Post by mc4man on 2013-01-04
You could run vlc from a terminal, maybe something of interest will show.
Some alternate commands to just
 
vlc

no menus
```
vlc dvdsimple:///dev/sr0
```
or if you know the title number for movie, ex. [COLOR="Blue"]title 1[/COLOR]
```
vlc dvdsimple:///dev/sr0#[COLOR="Blue"]1[/COLOR]
```
or
```
vlc dvd:///dev/sr0#[COLOR="Blue"]1[/COLOR]
```

---

### Post by rybnik on 2013-01-04
Ah.  So I am able to play it without menus in VLC.  Do you have any suggestions for how I might be able to play it WITH menus in VLC?

(On my home DVD player, it was able to play WITH menus.)

---

### Post by mc4man on 2013-01-04
> **rybnik said:**
> Ah.  So I am able to play it without menus in VLC.  Do you have any suggestions for how I might be able to [COLOR="Blue"]play it [/COLOR]WITH menus in VLC?

(On my home DVD player, it was able to play WITH menus.)

With the current disc you could try the last command I posted, use for the blue the main movie title number (you can get that by playing without menus in vlc > Playback > Title

That should start on the main movie, then see if "Playback > Title > Dvd Menu" works.

It's possible the orig disc had some minor structure protection that brasero copied over or caused some dvd navigation issue.
(brasero has no means to deal with structure protection

---

### Post by rybnik on 2013-01-04
[quote=mc4]With the current disc you could try the last command I posted, use for  the blue the main movie title number (you can get that by playing  without menus in vlc > Playback > Title

That should start on the main movie[/quote]

That didn't work.

[quote=mc4]It's possible the orig disc had some minor structure protection that brasero copied over or caused some dvd navigation issue.
(brasero has no means to deal with structure protection[/quote]
I suppose that's it.  Do you know of any burning software that DOES have "structure protection" that I could use to re-burn the original?

Thanks for your help.

---

### Post by TOMBSTONEV2 on 2013-01-04
You can rip your discs with AcidRIP or k9copy. You can use k3b to burn, its better than Brasero.

```
sudo apt-get install k3b
```

These are what I use.

---

### Post by leclerc65 on 2013-01-04
+1 for k3b.
I don't trust Brasero at all, even with a RW dvd.:(

---

### Post by rybnik on 2013-01-05
Well, I burnt the original again, except with k3b this time, but the same issues arise.

I can play the original just fine in VLC.  Does this mean that the software isn't copying the disc exactly?

---

### Post by TOMBSTONEV2 on 2013-01-05
It would seem so, what dvd ripping software are you using?

---

### Post by mc4man on 2013-01-05
> **rybnik said:**
> Well, I burnt the original again, except with k3b this time, but the same issues arise.

I can play the original just fine in VLC.  Does this mean that the software isn't copying the disc exactly?
By software if you mean braseo anything is possible.

If there is no structure protection (or any large amount of intentional unreadable sectors), then you should have good results with vobcopy.
(k9copy was probably the best linux app for intentionally messed up dvd's though it could only handle some protections & I believe currently is no longer maintained.

To try vobcopy install it
Put dvd in drive, close any pop up
In terminal - 
```
vobcopy -v -m -F 16
```
If all goes well the you'll find a folder in home named from the volume label, inside will be a VIDEO_TS containing the complete dvd disk, use k3b or whatever to create an .iso, then burn

* if vobcopy starts re-reading **a lot** of sectors then stop it & post the output

---

### Post by rybnik on 2013-01-06
IN CONCLUSION:

disc burned with Brasero disc-copy feature:
--can be played in home DVD player
--can only be played in VLC if menus disabled

disc burned with k3b disc-copy feature:
--can be played in home DVD player
--can only be played in VLC if menus disabled

disc burned with mc4man's method in post #10:
--can be played in home DVD player, but before movie playback starts, a .VOB file that says "Thank you for not pirating this DVD" plays, but after it plays that file it advances to the DVD menu and can play the contents just fine
--in VLC, when specifically pointed to /media/discName it can play just fine (with menus and all), but it does not play automatically

I suppose that's </thread>.  Thanks for all the help, mc4man and others.

---

