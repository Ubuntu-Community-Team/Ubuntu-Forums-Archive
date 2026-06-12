---
title: "Remote Admin. via VNC"
date: 2006-06-18
forum: Multimedia &amp; Video
---

### Post by PsypherPunk on 2006-06-18
I've got Ubuntu (Drake) set up as a fileserver without a monitor or keyboard and access it via VNC from another  machine. Originally I had monitor attached for the installation. However, since detaching it Ubuntu is stuck in 640x480.

Under 'Screen Resolution' there are no other resolutions listed - is there any way to get a higher resolution?

---

### Post by scxtt on 2006-06-18
check your definitions in /etc/X11/xorg.conf -- see what driver it's setup to use and see what resolutions are defined ...

and if that makes no difference - just force it to use a different resolution when you start up VNCserver, here's my alias for starting a server:
```
alias vncserver='vncserver -geometry 1600x1200 -depth 24'
```

---

### Post by PsypherPunk on 2006-06-18
I've tried restricting the resolutions in xorg.conf but it still appears inx 640x480 (running the 'nvidia' driver).

i don't think i'm actually running vncserver - i've just set it up via System->Preferences->Remote Desktop. Certainly, vncserver doesn't show as an active process.

---

### Post by scxtt on 2006-06-18
that's vino, which shares your :0 connection, instead of creating another (like :1, :2, etc.) ... so the problem you're having is most likely the result of :0 not having a monitor plugged into it ... i've never tried it like that (i generally use a :0 connection after i've already logged in - used to use vino, now use X11vnc) ...

my suggestion would be to install vncserver and use that ... that way you can control each :X connection you create ...

---

### Post by PsypherPunk on 2006-06-19
[QUOTE=scxtt]that's vino, which shares your :0 connection, instead of creating another (like :1, :2, etc.)[/QUOTE]

That's rather what i'd hoped to achieve, viewing an existing session rather than starting another. Is there no way to either configure vino to alter the X settings or get X to overlook the absent monitor?

---

### Post by scxtt on 2006-06-19
well, if you don't plan on having a monitor hooked up to the box you want to vino/VNC into, then you'll never really have a :0 connection (unless you started one to begin with and NEVER kill it) ...

i used to use a similar setup and all i ever did was restart the box, let it sit at a GDM login and then start a new VNC connection anytime i wanted to graphically connect to it ... my thinking is that whenever you want to use a remote server, the concept of :0 goes right out the window ...

i'd at least recommend giving VNC a try and seeing if it solves your 640x480 problem ...

---

