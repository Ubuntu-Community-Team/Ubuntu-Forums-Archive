---
title: "Screen Problem | help!"
date: 2007-02-28
forum: Multimedia &amp; Video
---

### Post by nerds in parties on 2007-02-28
Hello there. I'm new and I have just installed Ubuntu 6.10. I have this problem with the screen. it seems like the refresh rate is slow or whatever. For example it takes about 3-4 sec. to maximaze or move a window. Same happens while browsing files or websites. please help.

-and an other thing.. is it possible to have higher resolution from 1024x768?

(i hope i did not bother writing this post to this forum category and not to the noob one)

---

### Post by r4ik on 2007-02-28
Did you install you're graphic card drivers ?

---

### Post by nerds in parties on 2007-02-28
no. if I do it will be ok?

---

### Post by Pikestaff on 2007-02-28
If you want a higher resolution, I recommend reconfiguring xorg:

```
sudo dpkg-reconfigure xserver-xorg
```

And choose the defaults for basically everything until you get to the part where it asks what screen resolutions you want.  Find the one you want and press spacebar to select it, and then press Enter to continue.  Then after you reboot you should be able to choose the screen resolution you want... at least, that's what I did and it worked for me, so hopefully it will work for you too 8) Good luck!

---

### Post by r4ik on 2007-02-28
Yes if you own an ATI or an Nvidia try,

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)


This guide may help a bit overall,

[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

Take you're time and read it the same goes for,

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

Now dont go read it all at once :)

Welcome to Ubuntu !
Good luck !

---

