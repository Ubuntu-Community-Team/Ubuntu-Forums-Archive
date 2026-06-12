---
title: "[SOLVED] DVD- &amp;quot;Could not read from resource.&amp;quot;"
date: 2008-07-24
forum: Multimedia Software
---

### Post by Green9090 on 2008-07-24
Every time I've tried to play a DVD on my laptop, it has given me the message 
"An error occurred
Could not read from resource."

I've tried multiple discs, all of which work fine in other laptops (including a nearly identical Ubuntu laptop) and conventional DVD players. 

I do have a DVD read/write drive, and in fact have used it to burn a DVD in the past. I've also burned and read CDs without incident. Any idea why it won't read commercial video DVDs?

---

### Post by Green9090 on 2008-07-24
Anyone?

---

### Post by Green9090 on 2008-07-24
:(

---

### Post by Green9090 on 2008-07-24
:guitar:

---

### Post by mc4man on 2008-07-24
If you've never set a region on the drive that usually will prevent play back. Do you know if a region has been set?
If so (meaning yes, it's been set once at some point) follow thru here and also ck. @ the bottom about setting launch command for vlc (hardy only on the default player, launch comm part)
[http://ubuntuforums.org/showthread.php?p=5182809#post5182809](http://ubuntuforums.org/showthread.php?p=5182809#post5182809)

If not sure about region setting install regionset and with a dvd in the drive run regionset from the terminal
Ex. of set drive
> doug@doug-desktop:~$ regionset
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: SET   [COLOR="Red"]<-[/COLOR]
vendor resets available: 4
user controlled changes resets available: 4
drive plays discs from region(s): 1, mask=0xFE

Would you like to change the region setting of your drive? [y/n]:n


---

### Post by Green9090 on 2008-07-24
I discovered that my region wasn't set, so I set that. After that, the DVD still didn't work, so I followed the instructions in that post you linked to. This makes me able to play the intro from the DVD, but it acts as though that's the whole thing. I can't seem to get it to display the menu.

Thanks for all your help thus far. Anyone got any ideas what else I should try?

---

### Post by Green9090 on 2008-07-24
Oo, never mind. I opened it in VLC media player and it can run it no problem- it was just Totem being dumb. 

Thank you sooo much!

---

### Post by FrancoNero on 2010-01-21
still have that problem in karmic.

ubuntu should drop totem in favor of vlc. there's close to nothing vlc doesn't play so why bother with a different player?

---

### Post by JustSteph on 2010-06-13
I can't get a DVD to play in vlc either. I press play and I hear the disc whirring away but nothing happens.

---

### Post by horlkjee on 2010-12-06
I had the same problem with totem. and VLC player worked right away when I installed it.

---

### Post by jacanterbury on 2010-12-14
[SIZE=2][keywords: ubuntu 10.10 problem playing movies dvd could not read from resource ]

I had the same problem but all I had to do to fix it was enter this command on a terminal screen :-[/SIZE]

*sudo /usr/share/doc/libdvdread4/install-css.sh*


Real easy and it all works fine now (it being the default totem movie player)

Apparently:
[I]    "Unfortunately, DVD support cannot be provided by default in Ubuntu due 
     to legal restrictions in some countries."[/I]
        
more details here 

[https://help.ubuntu.com/9.10/musicvideophotos/C/video-dvd.html](https://help.ubuntu.com/9.10/musicvideophotos/C/video-dvd.html)

NB the first 4 programs mentioned in the link were already installed.
NB2 If you left click on the links that are the 4 program names, what it does is run an 'apt' command which in my case (after a few seconds wait) told me that the app was already installed)



hth

john

---

### Post by salambander on 2010-12-22
Ok, this is driving me mad.

I'm having the same problem - it won't play in VLC or in mplayer, or any other player, and keeps saying "can't read from resource". 

I have tried to reinstall libdvdcss2, but it says "no installation candidate".

I tried the regionset fix, and although I did manage to change the region, it hasn't fixed the "can't read from resource" problem.

Short of reinstalling my whole system, which is more than tempting right now, are there any other fixes? 

In unrelated (or possibly related, I'm not sure) issues, sound no longer works in VLC or any videos (eg YouTube) played through firefox, opera or chrome (but it does for everything else).

Help me, forum-wan-kenobi. You're my only hope!

ETA: Finally, it works! Jacanterbury, my future unborn children are belong to you. :D

---

### Post by lanehartle on 2011-01-16
Thank you, jacanterbury!!

After following the instructions in many posts, and installing I don't know how many extra packages, your simple one-line command did the trick:

[I]sudo /usr/share/doc/libdvdread4/install-css.sh

[/I]I was getting the same "Could not read from resource" that others have reported when I tried to play a standard DVD movie under Ubuntu 10.10.  Everything's working fine now...

Thanks again,
Lane Hartle

---

### Post by K7522 on 2011-02-19
> **jacanterbury said:**
> 
*sudo /usr/share/doc/libdvdread4/install-css.sh*

hth

john

Works!

---

### Post by DAB4970 on 2011-02-20
[I]sudo /usr/share/doc/libdvdread4/install-css.sh

Doing this helped my mplayer.  Before this I also installed regionset.

Thanks everyone.
[/I]

---

### Post by AleKnaui on 2011-04-03
Thank you very much for your help! Worked for me :D

---

### Post by widda on 2011-04-08
> **DAB4970 said:**
> [I]sudo /usr/share/doc/libdvdread4/install-css.sh

Doing this helped my mplayer.  Before this I also installed regionset.

Thanks everyone.
[/I]
This code worked for me, thanks.

---

### Post by erikthedrink on 2011-05-04
:P
Thanks, much, everyone.  After restricted extras, ugly, forbidden, and now this, works!\

---

### Post by CowboyBoats on 2011-05-18
Jacanterbury, your code worked to solve my problem too. Thanks! What did it do?

---

### Post by myyk on 2011-07-23
The same problem led me here.COULD NOT READ FROM RESOURCE 
The terminal command worked great.
sudo /usr/share/doc/libdvdread4/install-css.sh
First time I've been able to USE terminal.:P
THANKS GUYS, YOU'RE THE BEST!!!!!

---

### Post by theller on 2011-11-06
> **jacanterbury said:**
> [SIZE=2]
I had the same problem but all I had to do to fix it was enter this command on a terminal screen :-[/SIZE]

*sudo /usr/share/doc/libdvdread4/install-css.sh*


hth

john

Thanks, that worked for me.

---

### Post by soluckytouselinux on 2011-12-21
Hi everyone. this command worked for me: sudo /usr/share/doc/libdvdread4/install-css.sh Now everything works really good. Long live open source!!!!:D

---

