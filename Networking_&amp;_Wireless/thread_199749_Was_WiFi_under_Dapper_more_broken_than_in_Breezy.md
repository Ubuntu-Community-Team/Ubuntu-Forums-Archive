---
title: "Was WiFi under Dapper more broken than in Breezy?"
date: 2006-06-19
forum: Networking &amp; Wireless
---

### Post by christian.convey on 2006-06-19
I have a HP DV4150, which includes an Intel 2200GB adapter.  Under Breezy the thing worked just beautifully.  Under Dapper, I can connect to unsecured networks, but cannot connect to a network with WEP enabled.  I could connect to that WEP-enabled network when using Breezy.

But more generally, I'm hearing lots of complaints about regressed WiFi behavior as people went from Breezy to Dapper.  Did Dapper have an across-the-board quality drop relative to Breezy?  If so, was there something in the development / release strategy that should be changed?

At this point I'm seriously considering re-installing Breezy, just to get back to a WiFi-compatible laptop.

---

### Post by fritz_monroe on 2006-06-19
I haven't had any problems with my Wifi.  I use a Sony Vaio and upgraded from 5.10 to 6.06.  My home network uses WEP and after the upgrade it worked just fine.  I have not tried to connect to other networks, though.  I use it mainly at home, and since it's been just a couple days since the upgrade, I have not had the chance to connect anywhere else.

I will attempt to get WPA running in the next couple days, so I may end up breaking it then.  Hopefully not.

---

### Post by Stinger on 2006-06-19
[QUOTE=christian.convey]
But more generally, I'm hearing lots of complaints about regressed WiFi behavior as people went from Breezy to Dapper.  Did Dapper have an across-the-board quality drop relative to Breezy?  If so, was there something in the development / release strategy that should be changed?[/QUOTE]

I think the main reason to regressed wifi behaviour is the new wifi kernelmodules which should improve wifi support , but in some cases does the opposite.
For me it resulted in a frozen boot sequence.
I was abel to solve my problem as you can see at the end of this thread:
[Ubuntu 6.06 - ndiswrapper stuff]("http://www.ubuntuforums.org/showthread.php?t=190726")

Did you remember to wote [here]("http://www.ubuntuforums.org/showthread.php?t=191557") ?

---

### Post by christian.convey on 2006-06-19
[quote=christian.convey]I have a HP DV4150, which includes an Intel 2200GB adapter.  Under Breezy the thing worked just beautifully.  Under Dapper, I can connect to unsecured networks, but cannot connect to a network with WEP enabled.  I could connect to that WEP-enabled network when using Breezy.

But more generally, I'm hearing lots of complaints about regressed WiFi behavior as people went from Breezy to Dapper.  Did Dapper have an across-the-board quality drop relative to Breezy?  If so, was there something in the development / release strategy that should be changed?

At this point I'm seriously considering re-installing Breezy, just to get back to a WiFi-compatible laptop.[/quote]

OK, man, I'm really embarassed about this one.  I need to `fess up though so that other people aren't misled by my original post in this thread...

The cafe did, and continues to have, an open access point.  The problem seems to be that when I did a fresh install of Dapper, my laptop lost its memory of my authorizing it to connect to the cafe's access point.

My first clue should have been the warning, "did you run this as sudo?" when I fired up the wlanassistant applet from the Gnome toolbar.  I didn't think carefully about that dialog.  Or more specifically, it never dawned on me that my inability to connect the laptop to the access point related to my earlier failure to run the wlanassistant as root.

Long story short, when I ran it under sudo, it was willing to let me setup a connection to the cafe's access point, and I'm typing this message from the cafe.

I guess I was a little quick to blame Dapper, on account of the other messages I've seen about WiFi under Dapper, and because of the other issues I've personally had with Dapper's stability.

---

