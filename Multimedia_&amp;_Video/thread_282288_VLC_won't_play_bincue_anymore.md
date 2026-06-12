---
title: "VLC won't play bin/cue anymore"
date: 2006-10-22
forum: Multimedia &amp; Video
---

### Post by d3v1ant_0n3 on 2006-10-22
Basically, the thread title says it all. 

I used to be able to open bin/cue type videos (vcds that hadn't been burned onto cd yet). And now I can't. I'm not sure when this started happening- I've only noticed it today since we ran out of blank cds.

And since I last used vlc, I've upgraded to edgy, put Beryl on, upgraded the kernel, uninstalled and reinstalled codecs, etc, etc, etc, so I don't really know how to troubleshoot this problem...I've tried just plain purging vlc and reinstalling, but no joy.

Any suggestions for a solution, or another program that will happily play bin/cues?

---

### Post by dorme1 on 2006-10-27
I'm having a similar problem with Banshee, it will no longer play aac files. It says I don't have the right decoder installed. I've uninstalled it, re-installed it and all the plugins. The last thing I changed was installing beryl so I'm guessing that's somehow the culprit. I ran edgy off the livecd and installed banshee and all the needed plugins and it worked. Maybe I just won't have a fancy dancy desktop...damn it was so cool too.

---

### Post by newlinux on 2006-11-02
I have the same problem wiht VLc since going to edgy (and installing Beryl) Anyone with ideas?

---

### Post by taurus on 2006-11-02
Have you tried using mplayer to play your bin?

```
gmplayer <filename>.bin
```

---

### Post by newlinux on 2006-11-02
yes mplayer works, but I prefer vlc, as I use it for other things. Just wondering why it doesn't play .bin files anymore.

---

### Post by dr.drake on 2006-11-05
same here: no cue/bin playback anymore since my new install of edgy.

not even with mplayer...

---

### Post by newlinux on 2006-11-05
> **dr.drake said:**
> same here: no cue/bin playback anymore since my new install of edgy.

not even with mplayer...

Just curious, have you installed Beryl?

---

### Post by dr.drake on 2006-11-06
> **newlinux said:**
> Just curious, have you installed Beryl?

no, why? 
I had compiz installed in dapper, but did a clean install, so all is gone..

---

### Post by newlinux on 2006-11-06
The original person who posted also had installed Beryl, so I was just seeing if that was a common package added among those who are having problems with VLC. When I installed compiz in dapper it did mess up some playback of totem and other players, but I was able to fix it...

---

### Post by dr.drake on 2006-11-06
yeah, some playback problems, like the diagonal breakline..

in this case it just won't play at all.. 
so it is not a case of shakey playback, just a no go area..

and I know that the files aren't corrupted, because I can play them in VLC on my mac..

---

### Post by newlinux on 2006-11-06
hopefully someone will notice come with a fix because I really like using VLC. I know the files work as well because they work with other players and OSs. I just liked using VLC for everything (viewing, streaming, etc.) and having it on my other OSs and never having to worry about it recognizing a file type. not anymore...

---

### Post by dr.drake on 2006-11-07
> **newlinux said:**
> I know the files work as well because they work with other players and OSs.

what other players do they work in?
I can't find ANY player in edgy that works for me..
now I'm stuck with my mac 13" screen to watch them :(

---

### Post by newlinux on 2006-11-07
mplayer works for me on .bin/cue files (gmplayer). I saw that it doesn't work for you.

---

### Post by randomi on 2006-11-17
Anyone figured out what is causing this yet? I've had the same issue for a while and would like to be able to use vlc player again.

---

### Post by pgatrick on 2006-11-17
Yet another with the same issues.. Diagonal line in video playback, and inability to play bin and cue in vlc now.

---

### Post by dr.drake on 2006-11-18
> **pgatrick said:**
> Yet another with the same issues.. Diagonal line in video playback, and inability to play bin and cue in vlc now.

the diagonal line is connected to compiz somehow, I reckon you are using that or beryl??? no workaround yet.

the bin/cue issue seems to be edgy related: still waiting for a solution.

---

### Post by Hemmer on 2006-11-23
> **dr.drake said:**
> the diagonal line is connected to compiz somehow, I reckon you are using that or beryl??? no workaround yet.

the bin/cue issue seems to be edgy related: still waiting for a solution.

yeah it must be an edgy problem because i just tested it on the Vista version of VLC and it could play .bin/.cue files fine...

---

### Post by daveyiv on 2006-11-23
I know it's not a spectacular solution, but renaming the files from <filename>.bin to <filename>.mpg worked for me. I also had the issue where nothing would play them with a .bin extension, but simply changing it to .mpg solved it for most of my movies with .bin extensions, there is still 1 that refuses to work, however it gives a different error. It says something about hte media being scrambled and encrypted. Oh well though, most of them work again.

---

### Post by pgatrick on 2006-11-24
All of mine worked fine in vlc after editing the .cue file to delete all but the last track.. No idea why, I've never had to do that before, and they worked fine before I changed it when burned to a cd.

---

### Post by trash on 2006-12-02
yup renaming the .bin to .mpg works for me too... (EDIT) errr no sound though!

Somebody mentioned playing them in mplayer which I tried but I get a playback of 3"x4" and I can't adjust it at all... very annoying to watch anything that small lol, anybody got a fix for that?

---

### Post by dr.drake on 2006-12-05
> **trash said:**
> yup renaming the .bin to .mpg works for me too... (EDIT) errr no sound though!

YEAH!!! \\:D/ renaming it to .mpg worked for me too.. and at first also no sound, BUT..

in the VLC tabs goto: **audio > audio track**  and select the other track, probably track2.

voila :biggrin:

---

### Post by newlinux on 2006-12-06
I still don't understand why we have to rename the files... Is VLC a new version in Edgy - perhaps with this bug? It obviously can play these files, but doesn't recognize that it can unless you make it an mpg

---

### Post by ron999 on 2006-12-08
Hi trash
Change the .bin to .mpg as you have done.
Open the file in vlc player.
Then change the audio track to track 2 :-
Audio > Audio Track > Track 2
:cool:

That's what worked for me.

---

