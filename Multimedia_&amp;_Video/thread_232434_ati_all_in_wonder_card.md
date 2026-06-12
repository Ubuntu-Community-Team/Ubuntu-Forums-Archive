---
title: "ati all in wonder card"
date: 2006-08-08
forum: Multimedia &amp; Video
---

### Post by hotpurple on 2006-08-08
Hi Guys and Girls,

I've got a 9800pro AIW card in a pc that I want to make into a PVR box. I've been looking at using MYTHTV, possibly with a Kubuntu install as it appears to be a qt app as opposed to gtk.

What would be required to get the card working with video for linux? Also, can I make the TV out output to widescreen PAL resolution or will I need to go for 800x600 and live with stretched visuals?

Any help would be much appreciated.

Cheers

Chris

---

### Post by barney_1 on 2006-08-09
Hi Chris,

I also have the 9800 pro All In Wonder card.  What a piece of crap when it comes to Ubuntu compatibility (linux compatiblity in general actually).

You will not be able to use this card to record with MythTV.  As far as my research has told me, there is absolutely nothing out there that will allow you to record from the TV-in.

As far as TV out, mine works just fine.

3D acceleration will not currently work for me.  I have fglrx installed but if I don't use:
```
Option  "nodri"
```
in my xorg.conf, my system freezes at a blank screen just before the login screen comes up.  No word on how or when this will be resolved.

As for the rest of your questions, I have no idea.  Sorry.  But good luck!

---

### Post by hotpurple on 2006-08-10
That's odd. My card works fine with fglrx and has full 3d accelleration. I've upgraded to an X850 since in my main box, hence the problem with the 9800pro aiw in an htpc. I did have some trouble with this card though on 5.10. I had to run fglrxconfig before anything would work.

Chris

---

### Post by mordi on 2006-08-12
I, also, would like to know if somebody was able to get tv-in with an ati  aiw 9800pro and how to do it. I have 3d acceleration and tv-out, however I am not able to make the tv tuner work. I can't even see it with lspci.
thank you

---

### Post by ricesteam on 2006-08-18
I think TV capture for the ATI AIW series is not supported. At least that is all I got from my research.  I think it is because of the ATI drivers.

So far I haven't found a viable solution and alot of people are having the same problem.  But the thing is, all of my research is based on unsupported claims.

Some claimed what I said above, and some claimed that it works with Gatos, etc with no evidence to back up their claims.

And since alot of my searches dug up many "me-too's", I have concluded that TV capture for ATI AIW is not yet supported for linux.

---

### Post by mordi on 2006-08-21
from what I read, you are right.

from ati
[http://www.ati.com/products/catalyst/linux.html#8](http://www.ati.com/products/catalyst/linux.html#8)

*The ATI Proprietary Linux driver does not currently provide video capture functionality. Video capture support for most ALL IN WONDER cards should be available from the GATOS project.*

from gatos
[http://gatos.sourceforge.net/supported_cards.php](http://gatos.sourceforge.net/supported_cards.php)

[i]All-in-Wonder Radeon 9700 (Radeon300)
    We have received documentation for this card and sample hardware (thanks to ATI !), work is underway. At this moment we cannot promise a specific timeframe for availability of working drivers or list specific feature that will be supported.[/i]

from mythtv
[http://www.mythtv.org/docs/mythtv-HOWTO-3.html#ss3.1](http://www.mythtv.org/docs/mythtv-HOWTO-3.html#ss3.1)

[i]The All-in-Wonder cards will not work with MythTV

NOTE: The ATI All-in-Wonder cards (which are not the same as the ATI TV Wonder, TV Wonder VE or TV Wonder Pro) will not work as a MythTV capture device because the GATOS [http://gatos.sourceforge.net](http://gatos.sourceforge.net) drivers that are available provide only a limited subset of the V4L API[/i]

..and so on. I believe that at this time there is no tv capture support for the newer ati aiw cards.

---

