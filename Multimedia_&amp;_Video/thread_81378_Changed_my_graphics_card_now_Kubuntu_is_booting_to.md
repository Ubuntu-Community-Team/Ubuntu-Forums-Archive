---
title: "Changed my graphics card: now Kubuntu is booting to console"
date: 2005-10-24
forum: Multimedia &amp; Video
---

### Post by federico_lu on 2005-10-24
Hello everybody,
I was using until now an old nVidia GeForce 2 MX on my computer, and today I changed it with an GeForce 2 TI or 3 TI (didn't look at it exactly, a friend gave it to me fro free and all I know is that the card is better than my old). The computer itself is running fine, and Kubuntu is booting too. But only to console, that's my problem. What do I have to change or update in order to get my card running? I thought it would be no problem and get auto-detected.

Thanks in advance

PS: I have the nVidia drivers installed on my system, if that matters.

---

### Post by rjwood on 2005-10-24
try
 sudo dpkg-reconfigure xserver-xorg
see if that helps

---

### Post by federico_lu on 2005-10-24
[QUOTE=rjwood]try
 sudo dpkg-reconfigure xserver-xorg
see if that helps[/QUOTE]

Thanks for your reply, but I tried that already. Changed nothing.
However, I found out that it definately has something to do with the nVidia driver. If I edit the xorg.config to use the nv driver, it works, but the nvidia doesn't. I just dunno why, because with my old graphic card it worked? I switched the cards again for now, as I don't have much time to play with that, but I want my OpenGL back :roll: 

I also tried to reinstall all nvidia packages but that didn't change anything either.

again thanks in advance for your help, federico

---

### Post by rjwood on 2005-10-24
you may want to take a look at this thread

[http://www.ubuntuforums.org/showthread.php?t=75074&highlight=nvidia](http://www.ubuntuforums.org/showthread.php?t=75074&highlight=nvidia)

I hope this helps

---

