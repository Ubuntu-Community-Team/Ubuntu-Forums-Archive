---
title: "Jaunty 9.04 Philips NP2900 MediaTomb"
date: 2009-07-17
forum: Multimedia Software
---

### Post by sepia-shots on 2009-07-17
I've just got a Philips NP2900 (which is a superb wifi player) and linked it to my Ubuntu machine using Mediatomb. It all works like a dream EXCEPT Mediatomb won't start at boot up. Any ideas most welcome as I can't even locate any log entries as to why it might be failing.

Many thanks for any help

Pete

---

### Post by sepia-shots on 2009-07-17
The error in the mediatomb log I get is 

2009-07-17 13:55:44    INFO: Checking configuration...
2009-07-17 13:55:44    INFO: Setting filesystem import charset to ANSI_X3.4-1968
2009-07-17 13:55:44    INFO: Setting metadata import charset to ANSI_X3.4-1968
2009-07-17 13:55:44    INFO: Setting playlist charset to ANSI_X3.4-1968
2009-07-17 13:55:44    INFO: Configuration check succeeded.
2009-07-17 13:55:44   ERROR: main: upnp error -117
2009-07-17 13:55:44   ERROR: upnp_cleanup: UpnpUnRegisterRootDevice failed

There's a post that suggests this is because the network card isn't up prior to MediaTomb and therefore to add a sleep 60 into the init.d script. I've done this but it makes no difference.

---

