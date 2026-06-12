---
title: "BluRay (and DVD) still not working."
date: 2012-07-17
forum: Multimedia Software
---

### Post by StardustLuna on 2012-07-17
I have spent the last couple of hours trying to get VLC, or anything, to play Blu-Rays. 

I have downloaded VLC, and MakeMKV. I streamed the disc from Make to VLC, but VLC doesn't do anything after I enter in the stream address. 

I also followed the steps from [this]("http://vlc-bluray.whoknowsmy.name/") page and now VLC doesn't respond when I try to open anything. I'll go to Media>Open Disk/Network/etc and no new window pops up to let me choose which file. 

I'm not sure if it's the disk itself, I've heard that BluRays encrypted with bd+ currently have no solution with Ubuntu. I'm currently trying to play one of the Harry Potter's from a box set I got last Christmas if that helps. 

Specs:
HP Pavilion dv7
Ubuntu 12.04

UPDATE: I now can open up the Disk and Network stream and such. But I've tried instead a Matrix DVD and while it is 'playing' there is no video except sporadic pixelated clusters and very sporadic, broken audio.

---

### Post by BicyclerBoy on 2012-07-17
I recall playing the last Potter movie directly off a BD using mythtv0.24 & libaacs.

I compiled libaacs from source.
The libaacs method requires the right key entries in the keyDB file.
You require udf2.5 filesystem support.

Never bothered trying to get VLC to play from the optical drive, it has no problem playing unencrypted m2ts files.
Built but never used makeMKV.

The makeMKV method is an alternative self-contained soln, it doesn't need libaacs etc. The streamed output is playable by anything (AFAIK).

Usable DVD playback requires a media player built with updated libraries of libdvdnav/read.

Slimline optical drives in laptops are problematic.

---

### Post by StardustLuna on 2012-07-18
So then, why won't VLC play my streams? Is there a codec or something of the sort that I'm missing?

As for myth, I don't know much about it, and so I'd prefer to use something a little bit more familiar. 

~Stardust:KS

---

### Post by BicyclerBoy on 2012-07-18
I was not recommending MythTV to you..just that the mentioned BD title does play directly from optical drive using libaacs & keyDB file.

A weak PC may need h/w accelerated video decode to play m2ts.
A core2duo seems okay with CPU decode playing VC1 1080p24.
VLC supports VAAPI.

BD Method 1 VLC native:
Do you have:
- a VLC version that supports dynamic loading of libaacs
- libaacs installed so it is loadable
- keyDB file & mediakeys files in correct folder.
- udf2.5 filesys support

BD Method 2 makeMKV:
Do you have:
- latest makeMKV source & have compiled/installed it.

BD Method 3 dumpHD:
- see doom9

BD Method 4 AnyDVD in windows VM:
- see mythtv mailing list archive thread

The ancient VLC in lucid 10.04 should play the makeMKV stream.
Method 1 works for mythtv.
Method 1 should work for VLC, XBMC & mplayer.
Methods 1 & 3 require keyDB.cfg &/or a method to get them..
Method 3 can help obtain the keys..

Does the BD auto mount & pretty icon appear on desktop?
Can you navigate the BD filesystem?

---

### Post by StardustLuna on 2012-07-19
Well, I doubt it's my PC, it has 6 gigs of RAM and a Core i7 2 GHz processor. My graphics card is an Intel Sandybridge Mobile, so I'm guessing it's a pretty generic one. Nonetheless, I'm not lacking in power. 

As for VLC, I have the latest version, so I am guessing yes?

[LIST]
[*]I did put a keysDB in ~/.config/aacs. At least, I think I did. There wasn't a folder there so I just made one.
[*]I put the aacs Dynamic Library in /usr/lib/vlc.
[*]As for Mediakeys and udf2.5 I am unsure
[/LIST]
For MakeMKV, I believe I did so, I downloaded two tar files, one for the source, and the other bin, and then extracted them and installed them using the terminal. I followed [these](http://www.makemkv.com/forum2/viewtopic.php?f=3&t=224) steps. MakeMKV works fine and seems to be doing everything that it's supposed to. 

I did start to dump the disc using MakeMKV, but then it said that it would take about an hour so I cancelled the process. If I really have to, I guess I would, but I much rather just pop the disc in and set it up to play. 

And yes, the BD does mount. I get an icon of a disk on my desktop named 52126618_HARRY_POTTER. Same goes for the DVD, it mounted, just wouldn't play. 

~Stardust:KS

---

### Post by BicyclerBoy on 2012-07-19
The dynamic library libaacs.so (or similar) is mean to be in the /usr/lib or usr/lib64...
Then run:
sudo ldconfig

Run VLC from a terminal & have a look at the error messages when you try to access/play the BD.
VLC will tell you that the libaacs is found or not ..
 
The keyBD.cfg file from "whoknowsmyname" is only the mediakeys & host certificates stuff...there are no title VUK keys included..

**If** your BD drive has been revoked (by new BD title) you may need to get a keyDB.cfg with title VUKs (doom9 aacskeys).

All BD drives will get revoked eventually & must have firmware updates to continue to work or the you must use title VUKs in keyDB.cfg or get cracked firmware..

---

