---
title: "Automated, multi-drive, CD ripping"
date: 2011-06-28
forum: Multimedia Software
---

### Post by mr_mop on 2011-06-28
Hi,

What would the easiest way to do CD ripping with multiple CD drives be?

I want to go through this cycle.
1) Insert CD1
2) Insert CD2
3) Wait
4) CD 1 and CD 2 open
5) Remove CD1 and CD2
6) Go to 1

I want something that will do all the CDDB look ups and download titles and cover art where available.  Anyone got any ideas?

Thanks

MM

---

### Post by mc4man on 2011-06-30
I do use a way that satisfies most of what you want, in this case i use abcde
It's automated in that the only thing done is to insert cd's in the drive(s), everything else is automatic.
As far as the rest everything but album art, not interested enough here to explore if abcde can do - for me any player I use downloads the art in most cases  anyway.

There may be other rippers that can be automated, I happen to use abcde and it's well suited to do so on multiple drives in auto mode.
This method can use up to 10 drives, internal and external
Without getting into how to use and setup abcde, it's pretty simple.
A small script in PATH, then in File Management > Media > Audio cd using the 'open with other application' >  'use a custom command' that points to the script
(creates an userapp.desktop

the script  - 
```
#!/bin/bash
CD=/dev/`echo $1|sed -e "s/.*\(sr[0-9]\).*/\\1/"`
gnome-terminal -e "abcde -N -d //$CD"

```
( the -N means non-interactive, the -d sets device based on the /dev/srX that caused the script to run when cd is inserted

So here I have a ~/bin that I place the script in, in this case named arip8
Then as in screen I set it in FM > media, just the scriptname would suffice though I usually full path anyway (screen1 setting, screen 2 as then seen in FM > Media

Then it's just a matter of inserting the cd's into the drives - I do script it to show in a terminal in case there was an issue, it could just run in background (visible terminal is better, when done the terminal self closes

---

### Post by mr_mop on 2011-06-30
That's great information, thank you very much.  I'll give it a try.  Sounds like that will do just what I want.

Yes, you're right. Album art is less of an issue.  Banshee seems to do a great job of it.

---

### Post by mc4man on 2011-06-30
There are several threads on abcde use, or just ask if need be

Here is a members page on basic use and some sample .abcde.conf's to use or as examples (best to use a custom one in your home folder than the supplied default one

[http://www.andrews-corner.org/abcde.html](http://www.andrews-corner.org/abcde.html)

abcde uses cdparanoia by default, can be set up to use the true cdda2wav if desired, just ask..

Edit: one thread on abcde
[http://ubuntuforums.org/showthread.php?t=535950](http://ubuntuforums.org/showthread.php?t=535950)

---

### Post by mr_mop on 2011-07-01
Great thanks, those sites gave a great starting point for the config file.  I've now tweaked it to my needs and ripped two CD's in parallel last night.  Worked a treat.  This has turned out to be a lot simpler than I'd thought it would be.

MM

---

