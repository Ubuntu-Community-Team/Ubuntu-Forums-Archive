---
title: "Phone Integration?"
date: 2012-11-13
forum: Mythbuntu
---

### Post by NewAmercnClasic on 2012-11-13
Has anyone successfully installed a mixture of packages creating a google voice like application integrating caller-id making theme-able interface (&VM) for MythTV for a Land-line integration?

 I have compiled a list of tech pages that may contribute to this end but I have not found any solid solutions.

[https://code.google.com/p/linux-caller-id/](https://code.google.com/p/linux-caller-id/)
[http://www.ainslie.org.uk/callerid/nopcsoft.htm](http://www.ainslie.org.uk/callerid/nopcsoft.htm)
[http://mgetty.greenie.net/](http://mgetty.greenie.net/)
[http://ubuntuforums.org/showthread.php?t=1953069](http://ubuntuforums.org/showthread.php?t=1953069)
[http://ubuntuforums.org/showthread.php?t=1210204](http://ubuntuforums.org/showthread.php?t=1210204)
[http://ubuntuforums.org/showthread.php?t=1535238](http://ubuntuforums.org/showthread.php?t=1535238)

---

### Post by nickrout on 2012-11-13
> **NewAmercnClasic said:**
> Has anyone successfully installed a mixture of packages creating a google voice like application integrating caller-id making theme-able interface (&VM) for MythTV for a Land-line integration?

 I have compiled a list of tech pages that may contribute to this end but I have not found any solid solutions.

[https://code.google.com/p/linux-caller-id/](https://code.google.com/p/linux-caller-id/)
[http://www.ainslie.org.uk/callerid/nopcsoft.htm](http://www.ainslie.org.uk/callerid/nopcsoft.htm)
[http://mgetty.greenie.net/](http://mgetty.greenie.net/)
[http://ubuntuforums.org/showthread.php?t=1953069](http://ubuntuforums.org/showthread.php?t=1953069)
[http://ubuntuforums.org/showthread.php?t=1210204](http://ubuntuforums.org/showthread.php?t=1210204)
[http://ubuntuforums.org/showthread.php?t=1535238](http://ubuntuforums.org/showthread.php?t=1535238)At one stage there was an addon called mythphone which brought up callerid alerts and so forth. However I think the developer stopped and it is not compatible with recent mythtv versions. Looking at the wiki I see this: [http://www.mythtv.org/wiki/MythPhone](http://www.mythtv.org/wiki/MythPhone)

However if you want to integrate a pots line with your IP network then there are plenty of ATA adaptors around. Once you have IP telephony then some pretty simple scripting will bring up callerid on your screen when the phone rings - mythutil ([http://www.mythtv.org/wiki/Mythutil#Messaging_Access](http://www.mythtv.org/wiki/Mythutil#Messaging_Access)) or xosd will put messages on your screen.

As far as getting an IP telephony app running in mythtv itself, well that will require you to write some c++ code. You could use the mythphone code as a starting point I guess but as you will see from the page linked to, it needs significant work, as well as an understanding of myth coding standards.

Alternatively you could make a menu entry to bring up your favourite IP telephone application, and work out some remote control integration - ie the application would be best if it will respond to keystrokes, not mouse clicks, and even better if those keystrokes can be redefined.

---

