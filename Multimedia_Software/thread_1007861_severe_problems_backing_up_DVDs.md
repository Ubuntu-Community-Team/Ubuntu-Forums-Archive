---
title: "severe problems backing up DVDs"
date: 2008-12-10
forum: Multimedia Software
---

### Post by mailbox on 2008-12-10
So I have The Empire Strikes Back here on DVD, and I'm trying to back it up to disc in case I scratch it beyond repair (which generally happens within two months of me getting a disc of any kind). The problem is, though... I can't. Nothing seems to be working.

PLEASE NOTE: I do not want to transcode the DVD! I don't want a divx movie! I want the entire DVD, on my harddrive, as a single vob, with all audio tracks intact.

I first tried with *vobcopy -i /media/dvd -l*, but that died with:```
[Info] Outputting to /media/sdb1/r3/starwars5/EMPIRE_STRIKES_BACK1.vob
2749MB of 7107MB written (39 %)
[Error] Write() error
[Error] It's possible that you try to write files
[Error] greater than 2GB to filesystem which
[Error] doesn't support it? (try without -l)
[Error] Error: Bad address
```
I later learned that vobcopy can't deal with multiple angles, and that's exactly what the Star Wars DVDs use to switch between text languages for the opening scroll, so I guess I won't be using vobcopy for this, even though it's what I've always used.

Next, I tried using mplayer: *mplayer -dvd-device /dev/sr0 dvd://1 -dvdangle 1 -chapter 1-51 -dumpstream -dumpfile dump.vob* That one never actually died, but just slowed to a halt when the file reached 2.5gb. I tried leaving my machine on overnight, but it was at the exact same place where I left it when I woke up.

Then I tried VLC with *dvdsimple:///dev/scd0@1:2* under the "open" menu, and then *:sout=#duplicate{dst=std{access=file,mux=ts,dst="/media/sdb1/r3/starwars5/title.vlc.vob"}}* as the "Stream Output MRL." Again, no luck:```
** (.:14162): CRITICAL **: gtk_pizza_set_size: assertion `pizza != NULL' failed
[00000308] dvdread demuxer error: read failed for 3/4 blocks at 0x1578bd
[00000289] main playlist: nothing to play
```

I'm really not sure what's going on here. I've wiped the disc off several times. and I was able to rip both of the other two Star Wars films with almost no problems. Anyone have any ideas?

---

### Post by wolfen69 on 2008-12-10
k9copy does not work?

---

### Post by mailbox on 2008-12-10
Uhh...
k9copy outputs a 30 second video saying "this disc will not play due to the current parental settings of the player. Please eject the disc."
Never even heard of that before.

Edit: regionset-ing cleared this. Ripping now, Ill let you know how it goes.

---

### Post by mailbox on 2008-12-10
Nope. k9copy is now also stuck at either 38% or 43% - both bars are there, and I don't know which is which. Either way, it's stuck there and doesn't look like its moving.

---

### Post by Dynamo_Joe on 2008-12-11
Use DDrescue to create an ISO

```
ddrescue -n -b 2048 /dev/scd0 MyMovie.iso
```

Change "scd0" to the DVD Rom drive that you are using. 

The ISO file is normally placed in your home directory. 

VLC will play the ISO file using the "Open File" option in the menu. 

This will NOT rip the disk or REMOVE any protections that are on the original disk.

---

### Post by mc4man on 2008-12-11
Have you tried using vobcopy with the -m switch like 

vobcopy -v -m -F 16  (reads from /media/cdrom0, outputs to home dir.

vobcopy -v -m -o /media/XXX -F 16  (output to /media/whatever

vobcopy -v -m -o /media/XXX -F 16 /media/cdrom1  (reads from /media/cdrom1

Unless you've got some specific reason to only want a single .VOB with no menus, navigation ect.

---

### Post by mailbox on 2008-12-11
Alright, Joe, it's running.
If it doesn't remove CSS, am I to assume that it's essentially just cdparanoia for DVDs?

As for mister wolfen, k9copy is actually not stuck; it has now moved to a whopping 44%. We might be getting somewhere.

mc4man: no, I have not. I'll look into -m right now, thanks.

Also, it seems the Ubuntu forums are finally knowledegable with subjects other than "where's my start menu" and "how do i beryl?"  Thanks, all!

---

### Post by mc4man on 2008-12-11
Here's a few things for you may or may not be interested in

Auto rip with vobcopy
[http://ubuntuforums.org/showthread.php?p=5883353#post5883353](http://ubuntuforums.org/showthread.php?p=5883353#post5883353)

some general and screen of dvdisaster (gui similar to ddrescue

[http://ubuntuforums.org/showthread.php?p=6139837#post6139837](http://ubuntuforums.org/showthread.php?p=6139837#post6139837)

---

### Post by mailbox on 2008-12-11
> **mc4man said:**
> Here's a few things for you may or may not be interested in

Auto rip with vobcopy
[http://ubuntuforums.org/showthread.php?p=5883353#post5883353](http://ubuntuforums.org/showthread.php?p=5883353#post5883353)

some general and screen of dvdisaster (gui similar to ddrescue

[http://ubuntuforums.org/showthread.php?p=6139837#post6139837](http://ubuntuforums.org/showthread.php?p=6139837#post6139837)Vobcopy is what I generally use, but will not work in this specific instance because of the DVD's use of angles.
I'm reading into that other thread right now, and... damn. I thought I understood most of this. I guess not.

---

### Post by mailbox on 2008-12-11
52% with k9copy - only four hours remaining.

---

### Post by mc4man on 2008-12-11
```
but will not work in this specific instance because of the DVD's use of angles
```

Out of curiosity have you tried with one of the above commands?

In the -m mode your just mirroring the disk by sectors (F 16 means read in blocks of 16 sectors, useful for various reasons.

I can't see any reason why it wouldn't copy, let me know if you try.

(if there's no sp. it shouldn't take more than 10 - 15 min.

---

### Post by zeronothing on 2008-12-11
what i do to completely backup my dvd is install wine. then download and install dvdfab. it works perfectly in wine. dvdfab has a free version of  dvdfab available. hope this helps...

---

### Post by zeronothing on 2008-12-11
to better help you, open up synaptic and search for wine. after installing wine from synaptic go to this link and download [[COLOR="Blue"]dvdfab[/COLOR]]("http://www.dvdfab.com/download.htm"). you should be able to double click on the dvdfab execute file and install dvdfab just like any windows program.

---

### Post by mailbox on 2008-12-11
> **mc4man said:**
> ```
but will not work in this specific instance because of the DVD's use of angles
```

Out of curiosity have you tried with one of the above commands?

In the -m mode your just mirroring the disk by sectors (F 16 means read in blocks of 16 sectors, useful for various reasons.

I can't see any reason why it wouldn't copy, let me know if you try.

(if there's no sp. it shouldn't take more than 10 - 15 min.
Trying *vobcopy -v -m -F 16* right now.
Now, are these going to be decrypted?

---

### Post by pietjanjaap on 2008-12-11
Dvdfab is very good.

VLC I read on a website, that if you use a old version, it will copy, but i forget the website.

---

### Post by mailbox on 2008-12-11
Well, looks like k9copy did the job... after 27 hours. The quality is really, really degraded, though (think VCD), but I guess I have to live with it: I really don't care enough to go through all this crap again.

Thanks to everyone who helped.

---

### Post by andrew.46 on 2008-12-24
Hi mailbox,

> **mailbox said:**
> Next, I tried using mplayer: *mplayer -dvd-device /dev/sr0 dvd://1 -dvdangle 1 -chapter 1-51 -dumpstream -dumpfile dump.vob* That one never actually died, but just slowed to a halt when the file reached 2.5gb. I tried leaving my machine on overnight, but it was at the exact same place where I left it when I woke up.

I sense that you have almost had enough :-). But I wonder if you have tried with [a modern copy of MPlayer]("http://ubuntuforums.org/showthread.php?t=558538")? I do not have access to that particular dvd but I suspect if you simply want the entire dvd as a single vob a less complex syntax with the svn Mplayer should work:

```
mplayer dvd://1 -dumpstream -dumpfile dump.vob
```

But you may have had enough of this effort by now :-).

Andrew

---

### Post by Sweet Spot on 2008-12-24
OMG.. forget almost everything suggested, with no offense to those who tried to help. I say this because every piece of software written for Linux has been far from good for archiving my DVD's. The one good suggestion was DVDfab. But even before DVDfab, I'd use WINE for DVD Shrink. 

It's easy to set up in WINE and only ever fails if your DVD drive doesn't read the disc because of scratches or if there's some encryption that it can't break, which in that case, DVDfab to the rescue. That has been my case, and I've only had to use DVDfab perhaps twice in the YEARS that I've been using DVD Shrink. 

PM me if you want me to send you DVD Shrink via email, since it can be kind of tricky to find because it is no longer supported. Google will yield results though.. 

Doug

---

