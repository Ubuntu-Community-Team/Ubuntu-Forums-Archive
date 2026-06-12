---
title: "Player as light or lighter than MPC-HC"
date: 2015-08-05
forum: Multimedia Software
---

### Post by Shiv_Patel on 2015-08-05
Hi,

I have a Toshiba NB505 netbook, and when it was on Win7 Starter Edition, the only player that would play 720/1080p films was MPC-HC, as the netbook was otherwise too rubbish to play them on anything else. I have tried VLC, MPV, MPlayer and MPC-HC in Wine (didn't work) to no avail, so does anyone know a player that is as light or lighter than MPC-HC?

Thanks,

Shiv.

---

### Post by SeijiSensei on 2015-08-05
It's more likely a problem with the graphics adapter.  Most netbooks with Atom processors and Intel graphics have a hard time with HD videos, especially if they are encoded with the processor-intensive H.264.  

Also do you still have just the stock 1 GB of memory?  Adding another memory stick might give the machine a bit more breathing room.

---

### Post by monkeybrain20122 on 2015-08-05
But how do you know MPC-HC is actually playing those films in 720p/1080p? Does the netbook even have the screen resolution for 1080p? If you drop enough frames I suppose you can always play  "HD" videos..

---

### Post by Yellow Pasque on 2015-08-06
mpv is probably as light of a player as you'll get. What desktop are you running? Are you using 32-bit or 64-bit? I would think 64-bit would help some, but it may be counterproductive if you only have 1GB of RAM.

I know Atom doesn't support h.264 acceleration in hardware, but I wonder if you have xvideo support?
```
sudo apt-get install x11-utils  #it may already be installed
xvinfo
```

---

### Post by shantiq on 2015-08-07
> **Shiv_Patel said:**
> Hi,

I have a Toshiba NB505 netbook, and when it was on Win7 Starter Edition, the only player that would play 720/1080p films was MPC-HC, as the netbook was otherwise too rubbish to play them on anything else. I have tried VLC, MPV, MPlayer and MPC-HC in Wine (didn't work) to no avail, so does anyone know a player that is as light or lighter than MPC-HC?

Thanks,

Shiv.


av you tried from command-line for mpv    and cvlc ?

---

### Post by Rob Sayer on 2015-08-07
I suspect that others are correct in saying you probably won't get perfect 1080p playback anyway but not all Atom gpu's are the same.  To see what video card and driver is in use see here ...

[http://askubuntu.com/questions/348308/find-graphics-card-driver-details](http://askubuntu.com/questions/348308/find-graphics-card-driver-details)

... and try both terminal commands from the first answer (with the check mark).  Post here, embedded in [Code] tags.

Also, which ubuntu DE version are you using?  Most are not ideal for a 1Gb netbook.  When you read all that stuff about linux breathing life into old hardware or whatever, well, it's true.  But technically Linux is *just the kernel*.  It does not mean that the desktop environment or even the app software is going to run properly.  DEs like Unity or Cinnamon are designed for modern hardware and need as much power as modern Windows does.

I have a 1 Gb intel atom 2600 netbook which has the infamous Intel 3600 GMA (cedarview, which has very poor linux support.  I wouldn't dream of installing Unity on that.  It's actually running mint 17 Mate but I installed the lxde desktop from synaptic.  Haven't used Mate since, and that's a pretty light desktop.  So Lubuntu may be the best choice.

The command line option shantiq suggests may actually work best.  Otherwise, gnome-mplayer is the lightest GUI for mplayer I know of.  I'd try that first so you can get a feel for mplayer performance settings you'll probably need, like frame drop.  But don't expect miracles.  My Atom netbook gpu has no 3D hardware acceleration because Intel outsourced it, and the maker won't provide source code.  So I don't expect it will ever have 3D hardware accel.  N.B. DEs like Unity or Cinnamon require this *just by themselves*.

Fortunately I knew this when I got the netbook and it doesn't bother me that much.  I didn't plan to use it to watch HD video anyway.  But I can see where others may be ticked off.

---

