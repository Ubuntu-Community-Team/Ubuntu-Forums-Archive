---
title: "can i install xgl/beryl?"
date: 2007-01-16
forum: Multimedia &amp; Video
---

### Post by slimeph on 2007-01-16
I have installed openChrome drivers as described in 
[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

does this mean I could install xgl/beryl?

thanks in advance.

---

### Post by deadgobby on 2007-01-16
[http://ubuntuforums.org/showthread.php?t=263851&highlight=beril](http://ubuntuforums.org/showthread.php?t=263851&highlight=beril)

---

### Post by slimeph on 2007-01-16
Sir, the link posted above is only for nvidia, ati, and intel chips.. Mine is Via S3 Unichrome Pro  IGP which I have installed drivers for as stated above.

Am I in no hope on achieving a 3d desktop?

---

### Post by CowzRule on 2007-01-17
Type the following in a terminal```
glxinfo | grep render
```If you get a line with > direct rendering: YesThen try installing Beryl and see what happens. If the line reads > direct rendering: NoThen Beryl isn't going to work.

---

### Post by slimeph on 2007-01-17
yeah Ive got [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome) fully working sweetly.. Have installed beryl and it wont start complaining about something.. I will post the message.. Anyway.. I am currently using installed ubuntu dapper

another concern: If I would install Xubuntu Edgy and just apt-get gnome would it still work?

---

### Post by brargh on 2007-02-06
It would actually, as long as you use " apt-get install ubuntu-desktop" 
I used it for a while...it was too slow on my old boxes :) 
So went on straight xubuntu from there on :)

---

