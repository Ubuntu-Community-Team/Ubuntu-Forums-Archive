---
title: "BBC DVD playback issues"
date: 2008-07-09
forum: Multimedia Software
---

### Post by dedalus1904 on 2008-07-09
Hey everyone,

So I want to be able to watch my DVDs on my computer. Not a big ask. The vast majority work fine either in Totem-gstreamer, VLC, or mplayer. Unfortunately the minority that won't play include Dr Who (well, any BBC dvd, but Who's the real issue here) and Twin Peaks. As you can imagine, I'm a bit annoyed at this. 

I've trawled through this site and others, but can't find anything that I've not tried already - changing totem's backend to xine, installing VLC (which I'd come to believe was the universal panacea for multimedia problems), installing libdvdcss2 & other major codecs, purging and reinstalling software etc. Does anyone have an answer? As I say, the problem is restricted to specific DVDs, seemingly according to brand (BBC, Universal, etc) - which suggests it's a DRM issue or similar.

Thanks in advance.

Rich

---

### Post by mgmiller on 2008-07-09
It's possible the region setting in your dvd drive needs to be set.

You can change region capabilities for dvd drives from the command line.
first install regionset from synaptic package manager.

Or from command line:
```
sudo apt-get install regionset
```Then insert a readable dvd into the drive.  After it spins up, close anything that ran.
From a terminal window, type the command:
```
 regionset /dev/hda 
``` (or hdc or whatever the drive happens to be.)

  Follow the prompts. It will tell you if the drive has any region encoding on it, what region it is, how many changes are left and asks if you want to change it.

New drives often have no region set on them.  If you have a burner, and it has no region setting, if you burn a dvd it won't play in set top players because of "region incompatibility"
Region 1 is USA, north America.

Here is a link to the rest of the region codes:
[http://en.wikipedia.org/wiki/DVD_region_codes](http://en.wikipedia.org/wiki/DVD_region_codes)

---

### Post by vjones777 on 2008-08-21
> **mgmiller said:**
> ...New drives often have no region set on them.  If you have a burner, and it has no region setting, if you burn a dvd it won't play in set top players because of "region incompatibility"

Not true in my case.  I have a laptop which I beleive has no region set - thank God.  It can play DVDs from UK or US ok and DVDs I burn with it can be read on other PCs and several different set top DVD players.

I'd recommend whenever getting a new PC/lappie, ask if the region is set & stay away from it, if it is.  Of course you may never need to play disks from other regions, in which case you won't care.

PS I don't plan on installing any regionsetting s/w, just IN CASE it sets the region - then I'd be stuck.

---

### Post by mgmiller on 2008-08-22
I ran across my posted fix for this when I got a new burner for my home build puter and after burning movies that played just fine on the computer, would not play in any set top DVD player I had.  

After install the region set as noted above, all subsequent DVD's I create play on everything.

Since you don't know whether there is a region set on your burner, you can't say for sure that it has none.  Since burned dvd's play on set top players, I suspect it does have one set.

---

