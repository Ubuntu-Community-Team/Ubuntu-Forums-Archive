---
title: "Remote Desktop connecting but non-funtional."
date: 2009-04-20
forum: Networking &amp; Wireless
---

### Post by m.cowan on 2009-04-20
Hello. I've got a problem with remote desktop; Ubuntu 9.04. 

I connect via OS X "share screen" (vnc) function (which works flawlessly with Linux Mint) however with Ubuntu 9.04 I see the screen, the mouse will move, but it won't update any actions I perform (opening closing menu, closing windows, opening windows, clicking links). When I close the VNC session and reopen it I can see the result of my unseen activities (the window is now minimised) but I can't see it actually happening. Any ideas on what is going on?

Cheers. Matt.

---

### Post by ellucio on 2009-04-21
I have the same error.

Any solution?

Thanks.

Eldo

---

### Post by m.cowan on 2009-04-21
No, I'm afraid not. But it's very annoying. What client are you using to connect to Ubuntu remotely?

---

### Post by ellucio on 2009-04-22
VNC Viewer Free Edition 4.1 for Windows
You ?

---

### Post by gitti on 2009-04-23
I have the same problem. I use compiz, you?

---

### Post by ellucio on 2009-04-23
Will will have something that see the video card?
I have a nvidia 5200
You?

---

### Post by lorstan on 2009-04-24
Not sure if this helps, but I had a similar problem. If Appearance -> Visual Effects is "none", I can VNC in from XP (I use Tight VNC), but if on anything higher (e.g. "Normal" or "Extra") the mouse does not work properly. It also works if I don't use one of the proprietary drivers.

I also had to go back to Nvidia driver version 173 as the latest Nvidia proprietary linux driver did not support my graphics card.

If this doesn't help, good luck...

---

### Post by gitti on 2009-04-24
> **lorstan said:**
> Not sure if this helps, but I had a similar problem. If Appearance -> Visual Effects is "none", I can VNC in from XP (I use Tight VNC), but if on anything higher (e.g. "Normal" or "Extra") the mouse does not work properly. It also works if I don't use one of the proprietary drivers.

I also had to go back to Nvidia driver version 173 as the latest Nvidia proprietary linux driver did not support my graphics card.

If this doesn't help, good luck...

Works fine! Thanks.

But, yesterday, with Ubuntu 8.10, I used compiz and remote desktop together.

Can you understand if the bug is in nvidia drivers or in compiz?

I have a Geforce 8400GS.

Thank you!

---

### Post by ellucio on 2009-04-24
Excelent! Work Fine!!!

You can set this parameters in a terminal using:

To desactivate Visual Effect:
sudo metacity --replace &

To activate:
sudo /usr/bin/compiz --replace ccp &

I make this remotely, and work...

Thank you!!!

---

### Post by gitti on 2009-04-24
> **ellucio said:**
> Excelent! Work Fine!!!

You can set this parameters in a terminal using:

To desactivate Visual Effect:
sudo metacity --replace &

To activate:
sudo /usr/bin/compiz --replace ccp &

I make this remotely, and work...

Thank you!!!

So you make this before you connect? How? ssh?

---

### Post by toreil on 2009-04-24
I had the same problem and switching off all visual effects did work but I don't see why I should. I'm connected through gigabit Ethernet so band with is not a problem

---

### Post by gitti on 2009-04-24
> **toreil said:**
> I had the same problem and switching off all visual effects did work but I don't see why I should. I'm connected through gigabit Ethernet so band with is not a problem

With 8.10 I used remote desktop with visual effects without problems connecting by LAN 100Mbit or remote with ADSL. It isn't a network problem.

---

### Post by toreil on 2009-04-24
I know, I did the same but the bug might have had something to do with the network connection, the more info they have the better

---

### Post by Efros on 2009-04-24
this is a very similar issue to one that was evident in a previous upgrade. If you are using compiz on the target machine the displayed screen in the VNC window does not update. There used to be a way around this by installing xvnc I think, actually now that I've investigated it abit further it is x11vnc

---

### Post by LitilDivil on 2009-04-24
I had the same problem and i solved it by selecting Visual effects to "None". I think this is the right solution for accessing Ubuntu 9.04 remotely from windows xp with RealVNC.
Cheers

---

### Post by Efros on 2009-04-30
I've just got round this by installing x11vnc, not the most satisfactory of solutions as the speed of response is extremely sucky!

---

### Post by gitti on 2009-04-30
> **Efros said:**
> I've just got round this by installing x11vnc, not the most satisfactory of solutions as the speed of response is extremely sucky!

xvnc as client or server?

---

### Post by Efros on 2009-04-30
Sorry that should have been x11vnc, as server

---

### Post by krunge on 2009-04-30
> **Efros said:**
> Sorry that should have been x11vnc, as server

Maybe you need to supply the "-noxdamage" option to x11vnc to work around the Xorg XDAMAGE bug?

Search these forums for "noxdamage" for more info.

---

### Post by gitti on 2009-05-01
Is x11vnc hard to configure, or is auto-configuring as buit-in remote desktop?

---

### Post by Efros on 2009-05-01
> **krunge said:**
> Maybe you need to supply the "-noxdamage" option to x11vnc to work around the Xorg XDAMAGE bug?

Search these forums for "noxdamage" for more info.

Didn't know about that thank you speed is better now!

---

### Post by jmap82 on 2009-06-09
I wrote a short script to turn compiz off when I'm remotely viewing and back on again when I leave.  I'm no wiz at this stuff, so it may not be the best script ever, but you're welcome to use it if you want.

You can copy and paste from my wiki, [_here_]("http://script.jmap82.com/doku.php?id=jmap82sscripts:monitor").

Hope it helps :)

---

### Post by krunge on 2009-06-09
> **jmap82 said:**
> I wrote a short script to turn compiz off when I'm remotely viewing and back on again when I leave.

Ah, looking at the cmds in your script I see for x11vnc (not vino) how one might be able to do the switch automatically like this:
```

x11vnc -afteraccept 'metacity --replace &' -gone 'compiz --replace &' -forever ...

``` 

This runs metacity when the vnc viewer connects, and then restarts compiz when the viewer exits.  If anyone tries it report back here how it went.

---

