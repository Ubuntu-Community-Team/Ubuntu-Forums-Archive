---
title: "Audio Problem?"
date: 2007-07-26
forum: Multimedia &amp; Video
---

### Post by dgib on 2007-07-26
hey,

I am a new Ubuntu user and i've had nothing but trouble with it lol

I try to login and i get the message:

"x-session-manager: Error while loading shared libraries: Libasound.so.2: Cannot open shared object file: No such file or directory"

i've no idea what caused it just so uz know :)

Also... an additional question....

whats the deal with the dual monitor support? or should i say LACK of support?

sitting here waiting for your replies...

Dave :)

---

### Post by tbroderick on 2007-07-26
Do you have libasound2 installed? 

What video card do you have?

---

### Post by shanlek on 2007-08-22
ok, I have the same sound problem as tbrodrick, I am using a Toshiba Sattelite laptop... and here is the kicker. I have ubuntu running just fine until I tried to install realtek-linux-audiopack-3.5-6. When I did that it appears that the libasound.so.2 library got deleted or something. (yes, I am new to this)

I am unable to log onto my computer except in the failsafe terminal session... please help, this is infuriating.

---

### Post by kazha on 2007-08-31
Had the same problem.
I fixed it by going into recovery mode and writing

aptitude reinstall libasound2

Hope it  will help you too :)

---

