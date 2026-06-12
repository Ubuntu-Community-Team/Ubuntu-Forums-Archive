---
title: "nVidia GeForce 8500 GT Problems help!"
date: 2007-09-04
forum: Multimedia &amp; Video
---

### Post by DaBuddahN on 2007-09-04
Hello, I'm new to Linux in general and I'm doing my best to make sense of all this new stuff, and it's kool. But I'm having serious trouble configuring X on my new nVidia Geforce 8500 GT (512MB) card. I need some serious help, I've been at it for like a week with minimal progress. 

The dpkg-reconfigure xserver-xorg command has yielded no help. 

Please help and leave me your suggestions and ideas. :) Previously, I was ignored in the forum, so please dont do it again ;__;

---

### Post by tonym on 2007-09-04
You need to provide a bit more info.  You say you are having "serious trouble" but what does this mean?

Does your display work at al?  What messages do you get?

I'm not surprised you were ignored if you didn't provide any information!

---

### Post by tseliot on 2007-09-04
Boot in Recovery Mode (select it from the GRUB menu)

type:
```
dpkg-reconfigure xserver-xorg
```

select the "vesa" driver and press ENTER whenever you don't know the answer to a question.

then type:
```
reboot 
```

and boot as usual

On next reboot the Xserver should work fine


NOTE: if the problem is not solved try using "vga" or "fbdev" instead of "vesa" and try again.

---

### Post by DaBuddahN on 2007-09-04
My initial post was much more detailed than this one. I typed this one befoire going to college so my bad. Anyways. Yes, I have used the dpkg command to no avail. I have Ubuntu 6.06, AMD 64 version. And I did the "vesa" driver thing. I havent tried the others though, thanks for the suggestions, I will try it as soon as possible. And no, I see aboslutely nothing. I have to load the recovery mode to actually be able to do anything with commands. It just goes dark when I load Ubuntu normally. Yeah, a bit more detailed now. :)

---

