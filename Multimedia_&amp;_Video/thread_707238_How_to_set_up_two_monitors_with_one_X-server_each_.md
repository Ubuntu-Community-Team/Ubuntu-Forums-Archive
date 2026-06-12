---
title: "How to set up two monitors with one X-server each on one ATI device?"
date: 2008-02-25
forum: Multimedia &amp; Video
---

### Post by havarha on 2008-02-25
Hi!

My spec:

Ubuntu Gutsy
HIS Radeon HD 2600 Pro
Samsung SyncMaster 204B
Panasonic PT-AX100

My goal is to have one X-server and one set of input devices running on my SyncMaster, and one X-server and a differet set of input devices on my projector.  I want to run the monitor at 1600x1200 and the projector at 1280x720.

The X-server on the projector will be running Freevo and a remote of some kind as it's only input device. I want to use the X-server on my SyncMaster for general mangement of the computer and so on. I know a lot can be done remote by ssh, but I want a GUI as well. i don't need any fancy compiz-effects and such, so the only thing I'm focused about is good video playback when it comes to choice of driver.

The best thing would be having both the X-servers starting up at boot, but it's not a must. I have no problem getting both screens up and running on one X-server. I can drag windows from one screen to the other and so on, but that's not the way I want it to be. One reason is to avoid the problem you can get when fullscreening a window. It often stretches over both screens, or it ends up fullscreen on both (not very good when the screens have different resolution/aspect ratio) or only fullscreening on my monitor and leaving the projection screen black.

I have tried to search the forums, but can't find anything on this. I only found posts on people using twinview, xinerama and such. Noone trying ATI and two X-servers :)

Does anyone have any useful tips?

---

### Post by justleen on 2008-02-25
What i've used in the past to start a second X server is
```
 startx -- :1 
```

this was on a single monitor system, which allowed me two have to X sessions, one under the normal ctrl-alt-F7, and one under  F8/F9 etc depedng on the monitor number.
This starts your default X, but im assuming you know how to start a different X session

not really what you wanted, but might point you in the right direction.


EDIT: Just tried on my laptop, ATI, dual screen, Bigdesktop.. gave me an second idential desktop on both monitors.. cant see how to send output to a specific card/display, but im sure it should be along these lines...

---

### Post by havarha on 2008-02-25
Yeah, I have tried doing that, but it tries to open up a new X on my monitor and not on my projection screen. And it crashes, since I try to do it with the layout intended for the projector. But I have not tried doing it when I have bigscreen enabled. I can try that later tonight. The input devices should not be a problem. Just have to define it under ServerLayout in xorg.conf. If i just can get the second X-server up and running on the projector I'll be very happy :)

Thanks for the tip. I'll post back when I have tried it.

---

### Post by justleen on 2008-02-25
thing is, with bigdesktop, it wil open a new session an BOTH monitors..

brainstorm: you'd need to xsessions. one for the monitor, one for the projector.
then startx --with-config-for-monitor 1 
and another time --with-config-for-monitor 2

not sure.. but if you startx, it will read your xconf. in your case you want the first X-session to use a different config then the second X-session



searching on google brings me to this thread, lol :)

---

### Post by havarha on 2008-02-25
Hehe, tell me about it. Have searched a "few" times... :)

The problem is that when I try X :1 it starts a new X on monitor0 and not monitor1...

I'm not sure why, but I think it has something to do with the fact that the projector isn't in use when I start the computer. It doesn't look like ubuntu knows it's there unless I specify to use both monitors in bigdesktop. And starting a new X on the monitor with the projector setup isn't very useful ;)

Is there a way to "discover" a monitor in Ubuntu?
Both are connected at boot, and both display the same things at boot (bios and so on), and that's just how it should be. When Ubuntu fires up I get what I should on the monitor and the projector goes into standby (just a blue screen and searching for input). If I can just get Ubuntu to recognize the projector, without extending or cloning the monitor, and then starting X on the projector... :)

---

### Post by justleen on 2008-02-25
xrandr lists your displays 

or 
sudo aticonfig --query-monitor

when on ati..

---

### Post by havarha on 2008-02-25
Pretty sure I didn't see anything else than the monitor when I ran xrandr, so Ubuntu doesn't know that the projector is there. That's one of my problems. I would like Ubuntu to identify it without extending my desktop on to it, and then having the oportunity to start another X-server on it.

Doesn't look like Ubuntu can use it as long as I don't specify it as primary display or as an extension to the primary monitor in xorg.conf.

I will try aticonfig --query-monitor when I get home from work tonight.

---

### Post by havarha on 2008-02-27
When I run aticonfig --query-monitor it lists:
Connected monitors: tmds1
Enabled monitors: tmds1

When I try to run aticonfig --enable-monitor=tmds2 I get a message saying it failed to enable the display.

It would be so great if I just could run something that would enable the display and run an X-server on it with the specified layout...

EDIT: Or perhaps not... ;)

After actually selecting the correct input device on the projector (d'oh!) I got:
Connected monitors: tmds1, tmds2i
Enabled monitors: tmds1

So I'm going to try to enable tmds2i instead.

---

### Post by havarha on 2008-02-27
I get to enable it, but only as a clone or standalone display.

Tried adding Option "EnableMonitor" "tmds1,tmds2i" in xorg.conf,
and adding an X-server on display:1 in gdm.conf, but it doesn't work :(

Does anyone know of a command letting me enable a display and then starting a new X-server on it?

DISPLAY=:1 startx doesn't work, since I don't have a display 1...

---

