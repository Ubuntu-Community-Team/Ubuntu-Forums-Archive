---
title: "K9Copy rips to NTSC dvd while original is PAL"
date: 2008-12-12
forum: Multimedia Software
---

### Post by hanslinux on 2008-12-12
I'm using Ubuntu Hardy 64 bits.
I've updated genisoimage to the Intrepid 64bits version, because the Hardy version has a problem with writing the directory.

I've used K9Copy (original hardy version) to rip a pal-dvd to an iso image and burned that on a rewritable dvd disc.

When playing this disc on my PC no problem at all.

When playing this disc on my standalone dvd-recorder I get the error: TV-system is wrong. When I change the setting of the dvd-recorder from PAL to NTSC, it plays the disc without complaining. 

Is there a way to force the iso-image to be PAL video instead of NTSC? Or is there a bug known in one utils used by k9copy to create the iso image?

---

### Post by jnie on 2009-07-28
I know it's an old question, but there's no answer to it, and I can't find any answers elsewhere.

I'm on Jaunty J. and still experiencing this problem.

Anyone?

*J*

---

### Post by mc4man on 2009-07-28
With a limited number of pal dvd's to ck., k9 does appear to have issues with pal dvd's.
It's somewhat hard to believe comsidering it's usage in pal area's, but it did on 2 I tried.

Note that k9 is **not converting your video to pal**, it's just writing the .ifo's wrong., ranging from totally (from the disk itself) to slightly  butchering. 

From the disk was so bad I had to somewhat discount so I ripped the disk normally to file (VIDEO_TS), reauthored it properly with no compression to a movie only title, and then gave it to k9 to compress and reauthor to dvd5 size. It still got it wrong, making the video appear to be ntsc.

This would be evident if in k9's tree the title's video is shown as ntsc, if so then the output will be seen as ntsc because that's how the 'ifo's will be written.

There doesn't appear to be any setting to adjust this in k9, but you'd think there would be. (maybe this is a dvdauthor issue.

I can't copy and paste from my ifoeditor, so some screens

screen1 shows the movie only feed to k9, properly set as pal (same as on the orig. disk

screen2 shows what k9 did to it, note that in the PGC section the framrate is still proper for pal -  25 fps

screen3 shows the ifo corrected, it must be done for all ifo's, which in a full disk 'rip' and compress would be time consuming

I'd contact k9 and find out what the deal is. (maybe there's a config option or a 'pal version'....?

(( screen 4 shows the ifo for the main title when ripped directly from disk, pure nonsense so not taking too seriously

(note that the VIDEO_TS.IFO was also written wrong

---

### Post by Dolmio on 2010-03-03
> **mc4man said:**
> With a limited number of pal dvd's to ck., k9 does appear to have issues with pal dvd's.
It's somewhat hard to believe comsidering it's usage in pal area's, but it did on 2 I tried.


I have the same problem. When I try to RIP a PAL-DVD K9copy changes the format to NTSC.

I really like K9copy but this issue is a big problem and really makes the program useless for me.

So, if anyone has a suggestion, I will be greatfull.

/Dolmio

---

### Post by mc4man on 2010-03-03
@ Dolmio

Haven't tried k9 with pal dvd since last year, after work maybe I'll see what the latest ver. is doing here 
What version are you using ( if it's the latest I can't believe they haven't fixed this yet

(if so (the latest), and you're doing movie only rips, can explain later how to set the 'ifo's back to pal, for a complete disk rip as mentioned it would be a pita, but certainly do-able

---

### Post by Dolmio on 2010-03-03
> **mc4man said:**
> @ Dolmio

Haven't tried k9 with pal dvd since last year, after work maybe I'll see what the latest ver. is doing here 
What version are you using ( if it's the latest I can't believe they haven't fixed this yet


I am at work right now, so I can't check the version but I am running Ubuntu 9.10 and I installed K9copy with: 
```
sudo apt-get install k9copy
```
I'll check the version later and get back to you :)

> 
(if so (the latest), and you're doing movie only rips, can explain later how to set the 'ifo's back to pal, for a complete disk rip as mentioned it would be a pita, but certainly do-able

Would be great if you could explain how to do that :)
I really would like to use k9copy. It seems to be a great program.

---

### Post by Dolmio on 2010-03-03
> **mc4man said:**
> @ Dolmio
What version are you using ( if it's the latest I can't believe they haven't fixed this yet

It's K9copy Version 2.3.3

I can see, that the newest version i 2.3.5 but I doubt it will make any difference since this has been an issue for years now.

---

### Post by Dolmio on 2010-03-03
> **mc4man said:**
> @ Dolmio

Haven't tried k9 with pal dvd since last year, after work maybe I'll see what the latest ver. is doing here 
What version are you using ( if it's the latest I can't believe they haven't fixed this yet


Perhaps I was mistaking. I have successfully ripped a DVD to disk and when I open the VIDEO_TS folder in K9copy it says that the format i PAL.

[IMG]http://dl.dropbox.com/u/3077035/K9copy.png[/IMG]

I'll burn it to disk later (again) and check if I can play it on my DVD-player.

---

### Post by Dolmio on 2010-03-03
> **mc4man said:**
> @ Dolmio

Haven't tried k9 with pal dvd since last year, after work maybe I'll see what the latest ver. is doing here 


It didn't work. Seems to be PAL after all. Sorry about that.
The DVD (which I burned with K3b) plays fine on my computer but when I try to play it in my Panasonic DVD player it says > No Play - Incompatible TV System Setting. I have burned other DVD's that were ripped in Windows (DVD-shrink, I think) and it worked fine. But it looks the problem isn't the video-format (PAL or NTSC). Must be something else but I have no idea what.

/Dolmio

---

### Post by mc4man on 2010-03-03
Just got back - the error message could mean the .ifo is wrong or something else.

While I don't know of any good linux ifo editors, if need be can show how to use ifoedit in wine. 

Anyway, if your curious you can ck. your burned disk in mediainfo ( i believe it will show what the ifo is written as.

The easest way to install is to add [this ppa]("https://launchpad.net/~shiki/+archive/mediainfo") and then run 
```
sudo apt-get update && sudo apt-get install mediainfo
``` (edit - launchpad may be offline soon for awhile

Then load your dvd in the drive, open mediainfo (application -> sound & video)
Choose file and browse to File system -> media -> cdrom0 (or cdrom1) -> VIDEO_TS and then open the VIDEO_TS.IFO file and/or find the movie titleset and open the .IFO for it 

See what it reports




EDit: did a pal rip with k9 (2.3.4) and it handled it well, checked out fine in ifoEdit ( though didn't have it encode - will see if transcoding changes that

Both a movie only and a movie only reauthor also ck.'ed out fine, seems k9 has resolved this issue.

---

### Post by Dolmio on 2010-03-04
> **mc4man said:**
> Just got back - the error message could mean the 
Then load your dvd in the drive, open mediainfo (application -> sound & video)
Choose file and browse to File system -> media -> cdrom0 (or cdrom1) -> VIDEO_TS and then open the VIDEO_TS.IFO file and/or find the movie titleset and open the .IFO for it 

See what it reports

I'm off to work now but I will try out Mediainfo soon and get back to you. Thanks for your help :)

---

