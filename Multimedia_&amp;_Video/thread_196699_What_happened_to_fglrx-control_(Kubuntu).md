---
title: "What happened to fglrx-control? (Kubuntu)"
date: 2006-06-14
forum: Multimedia &amp; Video
---

### Post by Mastus on 2006-06-14
Just installed the brand new Dapper, and installed the xorg-drivers-fglrx and stuff following this guide (driver version 8.25.18)   ([https://wiki.ubuntulinux.org/BinaryDriverHowto/ATI](https://wiki.ubuntulinux.org/BinaryDriverHowto/ATI))

No problems with that - fglrxinfo says correctly "Radeon 9550 Generic"... but when I installed fglrx-control, there is no TV-out tab!  Does the aticonfig utility do the same magic as the ATI control panel? I did manage to get an so-so working tv-out on Breezy...

btw. Next time I'll definitely buy a nvidia card... Don't need hyper-3d acceleration, but I must have the TV out...

---

### Post by scxtt on 2006-06-15
i'm mildy confused on what a Radeon 9550 and TV-out have to do w/ eachother - is this output to a HDTV, not a television signal? ...

---

### Post by Mastus on 2006-06-15
There is three connectors on the board - VGA, DVI and an S-video connector (TV-out)

And no, I don't think my old TV can handle HDTV resolutions ;) 

btw. I managed to found this oddity: when adding "ForceMonitors" "crt1,tv" on xorg.conf and rebooting, ```
aticonfig --query-monitor
``` gives me both on "Enabled displays". When I do ```
 aticonfig --enable-monitor=crt1,tv 
```, I get a scrambled display. Upon rebooting, fglrxinfo gives me the good old MESA-issue...

---

### Post by scxtt on 2006-06-15
i have an X850Pro - so i have those 3 connections as well - i don't think it has anything to do w/ viewing a TV signal using a Radeon card ... i have to use my ATI TV wonder VE for that (cause there's no way, well w/ coax cable) to get a TV-signal into the card (is that what some of those crazy cables that came w/ the card are for? -- if  i had digital cable?)

---

### Post by Mastus on 2006-06-15
I'm not trying to get a TV signal INTO the card (have Hauppauge Nova-T for that), but getting a TV signal OUT of the card so I can watch e.g. movies on TV screen rather than computer monitor.

Are you referring to a VIVO-card (which has composite and S-video inputs)? 9550 has only S-video output.

---

### Post by scxtt on 2006-06-15
i'm not sure what's involved - tho i do think i know what you're referring to, i think i've seen something similar in windows - but i don't have a TV to check it out, or windows installed for that matter :D ... i just watch TV on my 20.1" monitor ... shouldn't you be able to connect an s-video cable (or composite, maybe w/ a vcr?) from your card to the TV (if it has s-video in) and view it that way (maybe config your card to a dual display setup)? ...

---

### Post by vulpes76 on 2006-06-15
I'm trying to do exactly the same thing it's the one thing i really need. I wasn't sure if i needed to install the proprietary driver??, with breezy i had it working after using a website that you answered a couple of questions and it created xorg.conf for you but the site no longer exists! if you find any answers let me know.

---

### Post by TLE on 2006-06-15
[QUOTE=vulpes76]with breezy i had it working after using a website that you answered a couple of questions and it created xorg.conf for you but the site no longer exists! if you find any answers let me know.[/QUOTE]
That site you are talking about is it: [http://www.objorkum.com/scripts/fglrxconfig/](http://www.objorkum.com/scripts/fglrxconfig/)
Because I used that too and it worked like a charm. It is really unfortunate that it isn't there anymore. I haven't gotten my tv-out configured in Dapper yet either :(

If anybody know if it has been moved to another location, please do tell.
Regards TLE

---

### Post by vulpes76 on 2006-06-15
I have just tried the s-video plugged in and then turning my laptop on tv-out appears to work but when I try to play video in totem the screen is just black on the tv while on my laptop screen the video looks fine. anyone got any ideas how i can get the video displayed on the tv?

---

### Post by whatever on 2006-06-15
from aticonfig --help:
```
  --ovon, --overlay-on={0|1}
        Choose which head the hardware overlay should be visible on.  The
        hardware overlay can be used for either OpenGL, video, pseudo-color
```

---

### Post by Mastus on 2006-06-15
Few questions more, if you may...

1) Is the only way of enabling/disabling tv-out from aticonfig --enablexxxxx command? Has the TV-out tab in fglrx-config really been taken away?

2) Should I do the aticonfig --initial=dual-head command to enable the tv out?

Because the drivers are "working". Got 3d-acceleration, no MESA-issues (well except the one thing...read above), and no picture on tv.
The Clone-mode would be fine for me (for start), but I can't get any picture on TV.

I came to conclusion that the "atitvout" utility would enable the tv-out if I used the vesa-driver? Well, I got bad video playback quality w/ vesa in Breezy, so I'd prefer Xv HW accel.

Please post, if you have any picture on tv-out.

---

### Post by vulpes76 on 2006-06-16
can anyone explain how I use this below to switch video overlay to my TV? Does this mean i need to switch each time or will it just work on the laptop when the tv isn't connected?

from aticonfig --help:
Code:

--ovon, --overlay-on={0|1} Choose which head the hardware overlay should be visible on. The hardware overlay can be used for either OpenGL, video, pseudo-color

---

