---
title: "need help installing Realplayer for Linux"
date: 2007-04-09
forum: Multimedia &amp; Video
---

### Post by christinanilsen on 2007-04-09
I downloaded Realplayer 10 for Linux [here]("http://www.real.com/linux/index.html")

first I saved the .bin file to my desktop.  then i tried to install it, but I get an error message: "couldn't display "home/christina/Desktop/Realplayer10Gold.bin"

then i tried downloading the .rpm version and when i try to install this by double-clicking the icon on my desktop, i get another error message - this time that the file can't be opened because the file type is unsupported.

i've already enabled the multiverse and universe repositories.

i've also noticed that in trying to download files directly from websites - when they are .bin files - i can never get them to install.  

(<1 week using ubuntu on my T20 IBM thinkpad - so please please don't skip steps in instructions, espec. if involving scripts in the Terminal ...)
thanks!

---

### Post by WiseElben on 2007-04-09
You might need to set the permissions so that you can execute the .bin file. Do this in a terminal:

```

$ cd
$ cd Desktop
~/Desktop$ chmod 777 Realplayer10Gold.bin
~/Desktop$ ./Realplayer10Gold.bin

```

That should start the installation.

EDIT: In case you forgot, type (or copy and paste) the commands after the "$"'s.

---

### Post by christinanilsen on 2007-04-09
hi.  that script isn't quite working ...

when i enter this line (below) in Terminal, I receive an error message

code: 
$ chmod 777 Realplayer10Gold.bin

error:
No such file or directory

this doesn't make sense to me b/c I can see the Realplayer10Gold.bin file sitting on my desktop.

what do you think the problem is?

---

### Post by Hortinstein on 2007-04-09
yuck, why use real player at all, get VLC or something like it...

---

### Post by christinanilsen on 2007-04-09
well ... because i'm trying to access a streaming online radio station (klara ... Belgian national radio) which tells me i need to download quicktime, realplayer or windows media player.  the stream doesn't work with mplayer.  i was thinking/hoping that i could make realplayer work in linux and get the stream that way ...

got a better idea?

---

### Post by RomeReactor on 2007-04-09
Hi. It looks to me like all of this is a typo: It's not "Real**p**layer10GOLD.bin", it's "Real**P**layer10GOLD.bin"; so, in the terminal

```
cd Desktop
```

and

```
sudo chmod +x RealPlayer10GOLD.bin
```

then

```
./RealPlayer10GOLD.bin
```

---

### Post by christinanilsen on 2007-04-10
thanks!  RealPlayer is now INSTalled.

now if I could just get the freakin' Klara streamin' radio site to work ...

---

### Post by dthomasdigital on 2007-04-14
Thanks for the instructions this worked for me, and I was having issues.

---

### Post by lindau on 2007-05-13
> **christinanilsen said:**
> thanks!  RealPlayer is now INSTalled.

now if I could just get the freakin' Klara streamin' radio site to work ...

I have installed RealPlayer, but can't get it to work in Firefox. Any Ideas:lolflag:

---

### Post by cgbier on 2007-05-13
Yep, I get the message "couldn't find player in system path"!

Any solution to that?

---

