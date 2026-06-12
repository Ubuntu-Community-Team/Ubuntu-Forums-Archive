---
title: "How can I get VLC working with region encoded DVDs?"
date: 2017-04-04
forum: Multimedia Software
---

### Post by Bobby_James on 2017-04-04
I purchased a region 1 DVD. I am in the UK (region 2). I used "regionset" to set the region to 1. I am using 16.04.

However, when I use VLC to "open disc" I get:

 [COLOR=#ff0000]Playback failure:[/COLOR]
 [COLOR=#000000]DVDRead could not open the disc "/dev/sr0".[/COLOR]
 [COLOR=#ff0000]Your input can't be opened:[/COLOR]
 [COLOR=#000000]VLC is unable to open the MRL 'dvd:///dev/sr0'. Check the log for details.[/COLOR]

Some of the more dubious log entries are:
[COLOR=#00008b][I]
dvdnav[/I][/COLOR][COLOR=#008000]* warning: *[/COLOR]cannot open DVD (/dev/sr0)
[COLOR=#00008b]*dvdread*[/COLOR][COLOR=#ff0000]* error: *[/COLOR]DVDRead cannot open source: /dev/sr0
[COLOR=#00008b]*core*[/COLOR][COLOR=#808080]* debug: *[/COLOR]no access_demux modules matched
[COLOR=#00008b]*core*[/COLOR][COLOR=#808080]* debug: *[/COLOR]creating access 'dvd' location='/dev/sr0', path='/dev/sr0'
[COLOR=#00008b]*core*[/COLOR][COLOR=#808080]* debug: *[/COLOR]looking for access module matching "dvd": 25 candidates
[COLOR=#00008b]*core*[/COLOR][COLOR=#808080]* debug: *[/COLOR]no access modules matched
 [COLOR=#00008b]*core*[/COLOR][COLOR=#ff0000]* error: *[/COLOR]open of `dvd:///dev/sr0' failed
 [COLOR=#00008b]*core*[/COLOR][COLOR=#808080]* debug: *[/COLOR]dead input
 [COLOR=#00008b]*core*[/COLOR][COLOR=#808080]* debug: *[/COLOR]changing item without a request (current 1/2)
 [COLOR=#00008b]*core*[/COLOR][COLOR=#808080]* debug: *[/COLOR]nothing to play

The "Files" program shows the name of the DVD on the left hand side. The DVD does spin / make noises, etc. 

Any ideas? Many thanks.

---

### Post by howefield on 2017-04-04
Duplicate thread closed.

---

