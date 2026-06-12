---
title: "can't play FLAC files on XMMS on GUTSY"
date: 2007-10-20
forum: Multimedia &amp; Video
---

### Post by whorush on 2007-10-20
hi, anyone get FLAC files working on XMMS on GUTSY?

i have libflac8 installed which supposedly has an xmms flac plugin... thats what it says at least in the description in synaptic.  but if there is an xmms plugin, XMMS doesnt know about it.

i think there used to be an XMMS FLAC package that you can instal with synaptic in fiesty? 

not sure if this is a bug?  i figure it is.

---

### Post by JoshuaJamZ on 2007-10-20
Bump...

Having the same issue. I noticed that when upgrading, it removed xmms-flac as being an obsolete package. Searching synaptic for FLAC related plugins seems to indicate I have everything installed, but XMMS won't load them... bummer... anyone know an answer to this?

---

### Post by JoshuaJamZ on 2007-10-20
Well, Audacious plays FLAC just fine. I'm still stubborn though and like XMMS... if you figure it out or if anyone else knows how to get FLAC working again with XMMS in Gutsy, please post!

---

### Post by disturbedite on 2007-10-21
i was gonna recommend moving to audacious...

---

### Post by NeoLithium on 2007-10-21
```
sudo aptitude install xmms-flac
```

---

### Post by FredB on 2007-10-21
> **NeoLithium said:**
> ```
sudo aptitude install xmms-flac
```

:lolflag:

As simple as this ? ;)

---

### Post by NeoLithium on 2007-10-21
Oh, hehehe. For gutsy it probably is xmms2-plugin-flac  My bad.

---

### Post by whorush on 2007-10-21
xmms-flac doesnt exist.

xmms2-plugin-flac is only for xmms2.  it doesnt work for the plain jane xmms.

any more ideas?

---

### Post by JoshuaJamZ on 2007-10-21
Looks like XMMS is just being weeded out, so it's almost as if it's a forced move to Audacious. Kinda irritates me, as I have used XMMS for some time and it's worked very well and then to have it working fine, playing FLAC just the other day with Feisty and suddenly now the plugin is gone. I'm now using Audacious.. seems nice, but one thing odd is when I go to add music, I don't see a add Dir selection, so instead I have to shift select all the files.. navigating to the directory with the music and selecting add all works too, but it also tries to add any non music files within the directory, so will give an error if a .txt or .jpg is there.. still loads everything in the playlist, though.

I don't have a definite answer to the XMMS flac plugin... but as I said, looks like it's being eliminated.. can anyone confirm this?

Just a quick note also that all in all, I think the Gutsy upgrade is very nice... only other issue is my second display (SVIDEO) on my NVIDIA isn't loading the desktop (had it separate desktops before.. Xinerama will work, but not what I want)... but another matter for another thread I guess.

---

### Post by whorush on 2007-10-21
i really dont think they're phasing out xmms.  i think someone just missed something.

that would be a damn shame!  its so good and its so fast!  i have 9000 something mp3s.  when i load them all into audacious, rythmbox and xmms....

xmms needs 3.6 megs of ram.
rythmbox needs like 38 megs
audacious needs 32 megs.

thats 10 times more ram!  and not surrpsingly they're way less responsive, etc.

---

### Post by JoshuaJamZ on 2007-10-21
Ok, well, I just installed the xmms-flac package again and FLAC plays again in XMMS.. it's not in the Gutsy repos, we know.. as to why it was removed in the first place...??? Anyway, got it here:

[http://packages.ubuntu.com/edgy/sound/xmms-flac](http://packages.ubuntu.com/edgy/sound/xmms-flac)

If anyone knows a good reason to not install it, please enlighten me.. but it seems to be working fine...

---

### Post by disturbedite on 2007-10-21
if it worked fine for me, then i'd just use it...regardless.

---

### Post by docshawnc on 2007-10-31
Thank you!!!!  Lack of this one thing made me rip Gutsy out and put Fiesty back on my machine.  I really like the old-school look, feel and workings of xmms.  It integrates with gyachi my IM client and I have it running when ever I'm at my machine.

---

### Post by lapsey on 2007-12-14
Nothing works on gutsy. old libflac7 & xmms-flac installs but nothing happens in xmms.

Looks like someone dropped the ball on the xmms-flac package when libflac went from 7 to 8.



**solution:** I found this at [https://bugs.launchpad.net/ubuntu/+source/xmms/+bug/139754](https://bugs.launchpad.net/ubuntu/+source/xmms/+bug/139754)

I compiled libxmms for gutsy on AMD64 from source and it gave me the flac for xmms plugin! The instructions are easy enough to follow.

To save you trouble I attach the plugin file (inside a tar.gz). This may only work on AMD64 but it is worth a try! It goes in ~/.xmms/Plugins/

I guess this is all that the xmms-flac package contains..

( edit: oh, I've missed you, Beatles :) )

---

### Post by Codeman05 on 2007-12-20
Thank you Lapsey! 

You have saved me much headache

---

### Post by fifafrazer on 2007-12-22
Ty so much.. XMMS is the only decent player for X, when you got more than 100 files in a playlist... I really dont hope they will phase it out. But I've heard somewhere, that they've stopped developing it, because of Audacios.

---

### Post by brum103 on 2007-12-31
First you need to get 
[http://packages.debian.org/sarge-backports/libflac7](http://packages.debian.org/sarge-backports/libflac7)
and then
[http://packages.debian.org/etch/xmms-flac](http://packages.debian.org/etch/xmms-flac)

and you're done!

---

### Post by phillywize on 2008-01-31
> **lapsey said:**
> 

**solution:** I found this at [https://bugs.launchpad.net/ubuntu/+source/xmms/+bug/139754](https://bugs.launchpad.net/ubuntu/+source/xmms/+bug/139754)

I compiled libxmms for gutsy on AMD64 from source and it gave me the flac for xmms plugin! The instructions are easy enough to follow.

To save you trouble I attach the plugin file (inside a tar.gz). This may only work on AMD64 but it is worth a try! It goes in ~/.xmms/Plugins/



I don't know whether the AMD64 issue makes a difference, but for those unwilling to tempt fate, here's the file compiled under a generic x86 kernel.  In any event, the fix at the launchpad link above worked for me, and the file that did the trick is attached.

---

### Post by marscay on 2008-02-14
> **phillywize said:**
> I don't know whether the AMD64 issue makes a difference, but for those unwilling to tempt fate, here's the file compiled under a generic x86 kernel.  In any event, the fix at the launchpad link above worked for me, and the file that did the trick is attached.

thanks boss :KS

---

### Post by quirau on 2008-03-17
thanks, works for me. i used xmms-flac and libflac7 from feisty :)

see yah

---

### Post by prvngrnd on 2008-03-26
> **brum103 said:**
> First you need to get 
[http://packages.debian.org/sarge-backports/libflac7](http://packages.debian.org/sarge-backports/libflac7)
and then
[http://packages.debian.org/etch/xmms-flac](http://packages.debian.org/etch/xmms-flac)

and you're done!

tada! 

Worked like a charm.

Thanks

---

### Post by JoshuaJamZ on 2008-05-28
I had previously posted instructions for installing xmms and xmms-flac here, since upgrading to Hardy... these were links to .debs... it worked, however, these packages depended on libglib1.2 and has been replaced by libglib1.2ldbl... so the update manager kept wanting to remove these. So, not a good method.

This post: [http://ubuntuforums.org/showpost.php?p=4831431&postcount=20](http://ubuntuforums.org/showpost.php?p=4831431&postcount=20) directed to a site with good instructions for compiling from source...

Thanks to this, I have xmms and xmms-flac running perfect on Hardy and also question why I had such problems with it before... but we live and learn... hopefully :lolflag: ;)

---

