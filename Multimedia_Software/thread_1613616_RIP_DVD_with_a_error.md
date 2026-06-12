---
title: "RIP DVD with a error"
date: 2010-11-04
forum: Multimedia Software
---

### Post by WG- on 2010-11-04
I have the following problem. I have a DVD with a error located at a certain time. Each time I watch the DVD and then come to that point Movie Player (or vlc player) returns a error.

Now I want to rip this DVD but all the rippers I tried return a error at that point when they try to rip it. Rippers I tried: 
- dvd::rip
- FFMPEG
- Acidripper
- Avidemux

Now I want to know ain't there a ripper which can read over these errors and still make a decent rip?

---

### Post by mc4man on 2010-11-04
vobcopy will
```
vobcopy -v -m -F 16
```

By default vobcopy will retry 9 times for each unreadable sector or block, so depending on how many there are and how well your drive responds after read errors will determine the time involved.

The only way to lower the read tries is to edit and re-build the source.

[dvdisaster]("http://ubuntuforums.org/showthread.php?p=6139837#post6139837") can also 'skip' unreadable sectors with adjustable read tries - but it produces an encrypted .iso which is fine for pc playback only. (if this is a commercial dvd that is encrypted
(( dvdisaster can also  skip most but not all structure protections

Edit:;
dd can also probably work - similar to dvdisaster, though it may slow to a crawl with read errors (blue adjustable

```
dd if=/dev/sr[COLOR="Blue"]0[/COLOR] of=[COLOR="Blue"]dvd[/COLOR].iso 
```conv=noerror

---

### Post by WG- on 2010-11-04
Ok thanks mc4man, I will try vobcopy tomorrow. I let you know the result.

---

### Post by WG- on 2010-11-05
@mc4man I believe vobcopy worked partially. It correctly ripped the .vob file in which the error was but it had difficulties with another .vob file. I think I will just try that one again tomorrow (:

---

