---
title: "TV Tuner Card.. I NEED HELP"
date: 2008-03-25
forum: Multimedia &amp; Video
---

### Post by daringingras on 2008-03-25
I would first like to say that i love ubuntu, i currently duel boot with windows because im a gamer, and although many of my games run under wine.. the few that dont i run under windows..

my general computer usage is under ubuntu 7.10

i own a wintv radio and i had this card working with the old version of ubuntu, a long time ago.. stopped using the card and had it out of the comp for a while, well i put it back in, 

tried starting tvtime., and after that didnt work, i attempted EVERY other program i could find...

nothing.. i tried installing all the video4linux software and mythtv frankly im at a loss


the ONLY part of this card that seems to work for me is the infa red remote control port on the card..

i can control all kinds of stuff on this computer with the hauppage wintv remote.. but i cant get the bloody radio or tv to work or get signal. any help would be greatly apreciated.

thanks

---

### Post by LubOunVtuE on 2008-03-25
I have a TV tuner card in my computer too, but I havent used it in Ubuntu yet.  Can you run an app in WINE to use your card?

---

### Post by daringingras on 2008-03-25
i tried installing the default wintv program in wine.. didnt work, besides i think that it would still need LINUX drivers un ubuntu to work...

---

### Post by jmore9 on 2008-03-25
go to linuxtv.org , a lot of info is there

---

### Post by daringingras on 2008-03-26
nothing there helped me, however, i did manage to get it to work, but it wont stay working
in my root account i went into /dev and found video0 and video1
i have a webcam hooked up to my comp and it is currently defaulted at video0
the tuner card is  video1
now i right clicked and changed the file and user access so the other category could view and use or w.e the setting is. 
then i renamed the video0 file to video1
and the video1 file to video0
and walah.. tvtime worked.. and so did my camorama program with the webcam..
they also worked once i switched back into my non root account

the problem came when i restarted the computer, went into my non root account.. tried to boot up tvtime
and it gave me the error.. cannot open capture device dev/video0



any way i can PERMANANTLY save the changes i made to dev/video0 and dev/video1 ??

---

### Post by Chriis on 2008-04-29
> **daringingras said:**
> nothing there helped me, however, i did manage to get it to work, but it wont stay working
in my root account i went into /dev and found video0 and video1
i have a webcam hooked up to my comp and it is currently defaulted at video0
the tuner card is  video1
now i right clicked and changed the file and user access so the other category could view and use or w.e the setting is. 
then i renamed the video0 file to video1
and the video1 file to video0
and walah.. tvtime worked.. and so did my camorama program with the webcam..
they also worked once i switched back into my non root account

the problem came when i restarted the computer, went into my non root account.. tried to boot up tvtime
and it gave me the error.. cannot open capture device dev/video0


/dev/video
any way i can PERMANANTLY save the changes i made to dev/video0 and dev/video1 ??

Do you find some way around this?
I got EXACTLY the same problem here :(

What i found is if you boot when no webcam pluged in makes tv card be on /video0 else the f*** cam takes video0 and push tvtuner on /video1

Should be a simple solution, but i'm too noob to linux to fix it.

Someone can help us plz?


Chriis :popcorn:

---

