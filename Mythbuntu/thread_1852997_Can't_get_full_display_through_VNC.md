---
title: "Can't get full display through VNC"
date: 2011-10-01
forum: Mythbuntu
---

### Post by donb21 on 2011-10-01
I connect to my MythBuntu box remotely using a RealVnc client on a Win7 pc, but the screen is very small (guessing 800 x 600).  Is there a way to get the entire display?  I can use the sliders, but it's not much fun.

---

### Post by Al_Vampyre on 2011-10-01
There should be a setting in VNC's preferences to show the full screen, as well as a percentage for scaling purposes.

---

### Post by donb21 on 2011-10-02
I have an options setup, but it doesn't have anything about full screen.    There is an option for "Allow dynamic desktop sizing", but that didn't have any effect, it still showed the same size.  But, do I really need full screen on the client (win7) side?  I assumed the Vnc-Viewer was showing whatever was being sent.

---

### Post by Al_Vampyre on 2011-10-02
I don't remember changing any settings in VNC on the server side, have you tried a different VNC client to see if that makes a difference? I use Tight VNC on my windows boxes and Remmina on my linux boxes.

---

### Post by nickrout on 2011-10-02
> **donb21 said:**
> I have an options setup, but it doesn't have anything about full screen.    There is an option for "Allow dynamic desktop sizing", but that didn't have any effect, it still showed the same size.  But, do I really need full screen on the client (win7) side?  I assumed the Vnc-Viewer was showing whatever was being sent.Then look for support for your windows client. This is a ubuntu forum, not a windows forum.

The default ubuntu linux client vinagre (which comes up in the menu as something like 'Remote Desktop Viewer') has a scale button which scales the remote desktop to the vinagre windows size.

---

### Post by donb21 on 2011-10-03
OK, that helped.  I tried tightVnc and the display re-scaling worked great.  Only problem is that it draws really slowly.  I changed the theme to the default mythty center and it worked a lot better.  Don't know why, but RealVnc is much faster (maybe by 3X).  It doesn't seem to have an option for re-sizing though.  I guess I'll try it with tightVnc and the default theme.

I tried getting information on the windows vnc sites; but they're kinda confusing.  The docs are pretty old (obsolete selections), command-line switches don't do very well from shorcuts, switches have a couple of forms (couldn't get either to work)...really not very workable.

---

### Post by nickrout on 2011-10-03
Do you REALLY need vnc? What for?

The only thing i have used it for is running mythtv-setup. However I find it better to run it over ssh direct to the x server on my laptop.

```
ssh -Y backendmachine
mythtv-setup
```

The setup gui then comes up on the laptop. Of course the laptop is running linux, but you can set up X on windows with Xming.

---

### Post by donb21 on 2011-10-04
Uhh, yes, VNC is kinda handy.  I don't use it for much, but sometimes I want to see a clone of the screen (usually using selections from the gui), so VNC is just convenient.

I use putty for ssh connections; it remembers connection details, screen size, character encoding, etc.  I tried using cygwin (which is probably much better than putty), but it doesn't do the connection stuff...call me lazy.  

When I ran cygwin, I realized that the app was actually running on the windows box (in emulation) and I had to keep the connection active until it finished (maybe I could have background-ed it, but....).  Besides, the Linux box has like eight times the hp, so I would rather run important stuff on it.

---

### Post by newlinux on 2011-10-04
If you want to create an entirely separate session running from your Linux that can be viewed on your Windows or Linux boxes (and has great compression and even works over WAN) you might consider freenx or nxserver. I use it a ton.

---

