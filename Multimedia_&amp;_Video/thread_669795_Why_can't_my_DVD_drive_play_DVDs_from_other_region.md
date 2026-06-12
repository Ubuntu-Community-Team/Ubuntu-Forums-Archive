---
title: "Why can't my DVD drive play DVDs from other regions?"
date: 2008-01-16
forum: Multimedia &amp; Video
---

### Post by Textureglitch on 2008-01-16
This one has been bugging me for some time.

My Toshiba Satellite Pro L20 laptop has the following dual-layer DVD burner drive: MATSHITADVD-RAM UJ-841S
I simply **cannot** get this thing to play DVDs with a different region code than region 2.

Specifically, I want it to run some region 1 DVDs that I've bought in the USA.
Everytime I try this, the program either crashes or I get a blank screen with brief, screeching bits of sound every 10 seconds as if it's trying to read the DVD but it's getting a ton of read errors and it's going very, very slowly.

To my knowledge, libdvdcss should not care about region codes at all?

Let me get the obvious things out of the way first:
[LIST]
[*]All region 2 DVDs I have ever played in it run perfectly.
[*]I have tried with Totem-xine, VLC, Xine, SMPlayer and various other frontends for Mplayer.
[*]I have a region set on the drive, region 2 to be specific. The aptly-named 'regionset' program confirms this.
[*]The drive is RPC 2, as most drives tend to be.
[*]I have tried many different region 1 discs, so it is not just a problem with a specific movie.
[*]The same discs play just fine in VLC on my Windows computer.
[/LIST]

VLC fails with the following error right after libdvdread has retrieved all the keys for the different VOB files on the disc:
```
libdvdread: Found 7 VTS's
libdvdread: Elapsed time 1
libdvdnav: Suspected RCE Region Protection!!!

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1522 ***
*** for info_length % sizeof(uint32_t) == 0 ***

libdvdnav: ifoRead_VOBU_ADMAP vtsi failed - CRASHING
vlc: vm.c:214: ifoOpenNewVTSI: Assertion `0' failed.
Aborted (core dumped)

```

I have of course googled this error, but found nothing but some unrelated issues and then a few other people who seem to have the same problem as me with the region coding thing, but no solution to the problem.

Running Mplayer gets me a lot of other errors about invalid IFO files, can't find matching colorspace, Vdecoder Init failed, and finally when it says 'starting playback', the a52 library gives me resampling errors and failed CRC checks.

I suspect that perhaps the laptop or the dvd drive are simply not fast enough to run a real-time deCSS and buffering of a DVD with a miss-matched regioncode. Is there a way to check if this is the case?
And is there really a difference between running deCSS on a disc with the same region code as the drive, and running it on one that is different?

---

### Post by Sef on 2008-01-17
> I suspect that perhaps the laptop or the dvd drive are simply not fast enough to run a real-time deCSS and buffering of a DVD with a miss-matched regioncode. Is there a way to check if this is the case?
And is there really a difference between running deCSS on a disc with the same region code as the drive, and running it on one that is different?

Region codes are set up, so one region cannot play another region's disks.  There are region free dvd players that will play any region, but laptops are usually restricted to a particular region.  In computers, this is hardwired in today.  There is software that says it will make your dvd player all region, but also this software could bork your computer, i.e., make it unusable.

---

### Post by eye208 on 2008-01-17
> **Textureglitch said:**
> ```
libdvdread: Found 7 VTS's
libdvdread: Elapsed time 1
libdvdnav: Suspected RCE Region Protection!!!

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1522 ***
*** for info_length % sizeof(uint32_t) == 0 ***

libdvdnav: ifoRead_VOBU_ADMAP vtsi failed - CRASHING
vlc: vm.c:214: ifoOpenNewVTSI: Assertion `0' failed.
Aborted (core dumped)

```
To make sure the error is in libdvdcss and not in libdvdread/libdvdnav, try copying the DVD contents to your harddisc using [vobcopy](http://packages.ubuntu.com/gutsy/utils/vobcopy) and then open one of the .vob files with VLC or another player. I have a DVD that just cannot be played with menus, but the actual video can be viewed just fine by opening the VOBs.

Is the drive of your Windows computer set to the same region?

---

### Post by mc4man on 2008-01-17
When there is a region mismatch vlc will brute force the retrieval of the css keys and in most cases is successful. However most MAT_****_A laptop drives will not allow access to encrypted sectors when a region mismatch is found and there's _nothing_ thats going to change that. This behavior is not a requirement of region coding, just what panasonic has chosen to do. My hl-dt-st-blah blah laptop drive will playback from other regions. Your only choice is to rip the title (with another drive) or replace the drive.

---

### Post by finite9 on 2008-06-21
this used to be so easy with Windows.  There was a utility that you could launch to effectively bypass the drives region coding and then you could start a hacked copy of powerdvd or other hacked software player that did not check region coding.

Why is it now so difficult?  Is it because its a laptop drive?  or is it because drive manufacturers in general have changed tactics?  When I had a desktop, I used to just download and install hacked BIOS upgrades and always made sure I bought a drive that could be made region free.

I am trying to find out if this is possible now, because I do not have Windows any more, and only run laptops, and I desperately want to rip my region 1 DVDs because I made the mistake of buying a home cinema system that is only region 2.

---

### Post by mc4man on 2008-06-22
@finite9
unless you have a matshita drive you shouldn't have any problem ripping region 1 (if you can play it back you can rip it) This issue with matshita occurs in windows also - the only way around it is a rc1 firmware flash, unfortunately there are almost none for laptop drives (matshita in particular). Your best (if indeed you have one of these drives) is to do your ripping on another machine.

edit if this is your problem there is 1 very limited work around let me know

---

### Post by finite9 on 2008-06-23
> **mc4man said:**
> @finite9
unless you have a matshita drive you shouldn't have any problem ripping region 1 (if you can play it back you can rip it) This issue with matshita occurs in windows also - the only way around it is a rc1 firmware flash, unfortunately there are almost none for laptop drives (matshita in particular). Your best (if indeed you have one of these drives) is to do your ripping on another machine.

edit if this is your problem there is 1 very limited work around let me know

Dunno what I was thinking when I wrote this...I can play any region DVDs on my DVD laptop drive with Totem, VLC or Mplayer.  I think maybe that once when I tried this, I had issues playing Gladiator R1 on the drive but that was 3 years ago, and maybe I concluded at the time that Linux behaved like Windows and could only read the region of the drive setting.

I just successfully ripped a R1 disc of Thomas the Tank Engine :) so it was not an issue.  I use K9Copy despite being a gnome fan.  Find DVDrip not as good as K9copy.  Are there other rippers for gnome that are up to the same standard as k9copy?

---

### Post by mc4man on 2008-06-23
If your aim is to shrink(or re author) down to dvd5 size then k9's transcoding method is as good or better than any gui linux app.
There is a free ver. of dvd rebuilder that works well in wine, requires some .dll work in wine to setup. The quality of re encoding vs. transcoding can be much better depending on source type, quality and amount of re compression. For the most part though you should be good with k9.
If you just wanted to rip to VIDEO_TS full size then vobcopy is the best at that.

---

