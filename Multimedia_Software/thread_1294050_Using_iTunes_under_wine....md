---
title: "Using iTunes under wine..."
date: 2009-10-17
forum: Multimedia Software
---

### Post by Baldrick_NZ on 2009-10-17
Hi all,

Having installed a fresh copy of Ubuntu 9.04, and having downloaded and installed iTunes v9.1.8 (XP version) using Wine, I notice that only Quicktime appears to have been installed.

I've tried reinstalling iTunes, but with the same result. I've checked and I'm definately using the iTunes setup.exe.

Apple appear to have bundled both iTunes and Quicktime in the same .exe file (which was about 88mb all up), yet only Quicktime has installed?

Would anyone be as kind as to suggest how one can get iTunes to show up and work?

Thanks in advance,
Baldrick.

---

### Post by vinutux on 2009-10-18
Applications -> wine -> Browse C:\Drive in program files checkout ther is a folder called iTunes And iTunes.exe inside that folder

In Terminal Type this ```
wine /home/[COLOR="YellowGreen"]YOURUSERNAME[/COLOR]/.wine/dosdevices/c:/Program Files/iTunes/iTunes.exe
```

.

---

### Post by Baldrick_NZ on 2009-10-20
> **vinutux said:**
> Applications -> wine -> Browse C:\Drive in program files checkout ther is a folder called iTunes And iTunes.exe inside that folder

In Terminal Type this ```
wine /home/[COLOR="YellowGreen"]YOURUSERNAME[/COLOR]/.wine/dosdevices/c:/Program Files/iTunes/iTunes.exe
```

.

Nope, didn't work. Couldn't find file. Tried re-install, and it asked whether I wanted to repair or remove. Under both options it came back saying itunes couldn't be configured..

I've tried both v7.2 and the latest version. Neither works.

I really need it to buy music. I've tried other iTunes clones, but none compares as well. 

Any help would be greatly appreciated!

---

### Post by vinutux on 2009-10-20
Try version 8 it works for me............

And make it sure you r running latest version of wine (update wine)

---

### Post by linux-hack on 2009-10-20
> **vinutux said:**
> Try version 8 it works for me............

And make it sure you r running latest version of wine (update wine)

can you syncronise an iPhone if its on wine ? i meen does it work how it should ?

---

### Post by vinutux on 2009-10-20
> **boogy9 said:**
> can you syncronise an iPhone if its on wine ? i meen does it work how it should ?

Sorry........Actually I am not iTunes addicted.... I just testing it with wine ..it worked and player my music library.... i am not sure about other features.....

Anyway check this link [http://www.readwriteweb.com/readwritestart/2009/06/songbird-releases-iphone-sync.php]("http://www.readwriteweb.com/readwritestart/2009/06/songbird-releases-iphone-sync.php")

---

### Post by Arkold Thos on 2009-10-20
I would run it on a virtual machine if you really want iTunes, I haven't success at make it work with my iPod. You can always use Songbird, Amarok, etc

---

### Post by maxwellemus on 2009-10-20
just use gtkpod ;)

---

### Post by llawwehttam on 2009-10-20
If you want somthing iTunes like that is open source and built for linux then try songbird
[http://www.getsongbird.com/](http://www.getsongbird.com/)

ive been using it for ages and there are very few problems. Some of the skins are very tasty.

---

