---
title: "Xorg ATI Driver problem"
date: 2006-10-28
forum: Multimedia &amp; Video
---

### Post by martinjh99 on 2006-10-28
I have a problem - I have installed the newest drivers from tseliots repo and the drivers install fine.  The card and accelerated OpenGL worked fine in Dapper - Just not so far in Edgy :(

The problem is that I have no accelerated OpenGL...
```

martin@Anne ~ $ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

```

[http://martinjh.myby.co.uk/xorg/xorg.conf](http://martinjh.myby.co.uk/xorg/xorg.conf)
[http://martinjh.myby.co.uk/xorg/Xorg.0.log](http://martinjh.myby.co.uk/xorg/Xorg.0.log)

---

### Post by sterilegenie on 2006-10-28
Im getting the same problem, Im assuming its a xorg problem but not quite sure how to correct it as of yet.

---

### Post by ronocdh on 2006-10-28
Same here, this is killing me. Dapper ran fine. Would it really help to purchase an nVidia card? Really don't have the cash right now. =/

---

### Post by martinjh99 on 2006-10-29
I think I'm going to go back to Dapper.  I know the acceleration works.  I can get KDE3.5.5 from other repos and FF2 I'll install from mozilla.com so no real losses from not upgrading to Edgy for the time being anyway.  I'd liked to have tried AIGLX though...

---

### Post by Blixter on 2006-10-29
I had the same problem and i did some search on google and found this guide. It's work fine for me:

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

---

### Post by martinjh99 on 2006-10-29
That did the trick!  Thanks for the pointer...

---

### Post by edwin11 on 2006-10-29
[FONT="Verdana"][SIZE="2"][COLOR="Navy"]Seems to have helped me too! Thanks a lot!

To add on, at the step

```
sudo /etc/init.d/gdm force-reload
```

my X froze, but upon reboot, works.



Regards,
Edwin
[/COLOR][/SIZE][/FONT]

---

