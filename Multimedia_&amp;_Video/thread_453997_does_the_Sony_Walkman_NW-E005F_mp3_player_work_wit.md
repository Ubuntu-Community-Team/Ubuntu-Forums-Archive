---
title: "does the Sony Walkman NW-E005F mp3 player work with feisty ?"
date: 2007-05-25
forum: Multimedia &amp; Video
---

### Post by kraymore on 2007-05-25
does the Sony Walkman NW-E005F mp3 player work with feisty ?  

thanks !  

i hope it does.

---

### Post by kraymore on 2007-05-25
it is what i believe an ATTARAC player.. whatever that is.  and it plays files in OMA format.

---

### Post by rajc on 2007-05-28
i have the same problem...
but i found this [http://david.dw-perspective.org.uk/Sony-NW-E00X-Walkman-On-Linux-FreeBSD-MacOSX-etc.html](http://david.dw-perspective.org.uk/Sony-NW-E00X-Walkman-On-Linux-FreeBSD-MacOSX-etc.html)
i havent tryed it yet , but i hope it will help ;)

---

### Post by diablo69er on 2007-05-30
The above did not work--however it did succeed in screwing my mp3 player up--I had to call sony customer service to get it fixed.  So if you did use the above link--bring up the home menu on your mp3 player, click menu, click advanced, clicked format--then ok.

Finally hold the reset button on the back of your mp3 player for 5 secs.

Should work fine on winblows then.

---

### Post by sbennettgso on 2007-05-31
I've tried the above-referenced Java utility.  It sort of works.

I can emulate the player on my Feisty desktop (emulating the player as a directory on the desktop), but the utility doesn't seem to work when executed on my player.  It's really weird.  It seems to work fine either emulated or on the player in Windows, but something about being on the player doesn't work for me.

What I can do is copy the emulated directory structure to my player.  That seems to work OK.

You do have to run it from the command line.  That's one thing to keep in mind.

Apparently some people have gotten it to work on the player in Feisty.  Haven't succeeded in getting much information from anyone about my particular issues though.

Good luck.

Thanks,
Scott

---

### Post by dolson on 2007-06-09
> **diablo69er said:**
> The above did not work--however it did succeed in screwing my mp3 player up--I had to call sony customer service to get it fixed.  So if you did use the above link--bring up the home menu on your mp3 player, click menu, click advanced, clicked format--then ok.

Finally hold the reset button on the back of your mp3 player for 5 secs.

Should work fine on winblows then.

I was setting up Feisty for a friend, and it totally killed her MP3 player. Trying your steps did not fix the problem. It doesn't work in Windows either, and I did contact Sony tech support and they had no solution except to try it on Windows and upgrade to SonicStage 4.3 or whatever, and that didn't fix the problem either.

I don't even know what to say now. The MP3 player was working fine in Debian, but due to a HAL bug in Feisty (my only assumption, considering the bug reports) it's totally f*cked now.

I have to buy her a new one and now install Windows onto her PC.

This is not fun. Not fun at all.

---

### Post by marshall.robert on 2007-06-09
I'm no seasoned user so i dont know if this will work, but could you try using wine with sonic stage, just leaving the mp3 player alone? when i had my network walkman it was recognised by windows as a plain flash drive, and i think i remember it being the same under ubuntu 6.10.
just a thought....

-rob

---

### Post by yogo on 2007-09-24
I have not looked into Wine too much I did try to run it from my Windows drive and I got a the database is corrupt error. I have not tried to install the software yet with wine but most apps work when I access program files on my windows box and right click and choose to open with wine.


The player does work well in Windows, 


My guess is and it is only a guess and that is are there any programs that will make an oma file to add to the mp3?  If so this should work as the only thing that is added is the extra oma, the mp3 is there as well???

Maybe something like this

[http://www.mp3-converter.biz/blaze-media-pro/](http://www.mp3-converter.biz/blaze-media-pro/)

---

### Post by junglee on 2008-01-04
Well i finally worked out a way ..... start windows in a virtual machine ( I used virtual box). mount your USB device(walkman) onto virtual windows and everything after that is piece of cake.

Mounting your walkman onto virtual windows can be a bit of work. Its mostly permission issues and googling for usb and virtual box will give u enough hints to work it out.

I tried wine before this, but stupid SonicStage refuses to start up ..... even after successful install.

WHY EMULATE, WHEN YOU CAN VITUALIZE :)

--
Anuj

---

### Post by kraymore on 2008-01-26
> **dolson said:**
> I was setting up Feisty for a friend, and it totally killed her MP3 player. Trying your steps did not fix the problem. It doesn't work in Windows either, and I did contact Sony tech support and they had no solution except to try it on Windows and upgrade to SonicStage 4.3 or whatever, and that didn't fix the problem either.

I don't even know what to say now. The MP3 player was working fine in Debian, but due to a HAL bug in Feisty (my only assumption, considering the bug reports) it's totally f*cked now.


anyone get this mp3 player working under gutsy ?  if its just a HAL layer i'm thinking it might be fixed by now.  

thank you

---

