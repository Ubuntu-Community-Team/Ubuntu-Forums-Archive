---
title: "watching a recording logs me off"
date: 2011-04-25
forum: Mythbuntu
---

### Post by tdcarlo on 2011-04-25
Fresh install of 10.10 as a secondary backend.  When I go to watch a recording it says please wait and then takes me to a login screen.  I tried running mythfrontend from a terminal but for error messages but when I log back in the terminal is gone.

When I run control centre, I get a microbridge error. I also get an error when I try to look at mythlogs.  

Any ideas?

thanks

---

### Post by tdcarlo on 2011-04-25
I got the error logs working.  When I try to load a recording on the secondary backend I get this output.  When I get logged out it refers to an unkown X server error

```
#
2011-04-25 20:54:30.843 Found mainmenu.xml for theme 'Mythbuntu'
#
2011-04-25 20:54:31.628 MythContext: Connecting to backend server: 192.168.1.104:6543 (try 1 of 1)
#
2011-04-25 20:54:31.629 Using protocol version 23056
#
2011-04-25 20:54:32.989 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//library.xml
#
2011-04-25 20:54:33.602 New DB connection, total: 2
#
2011-04-25 20:54:33.612 Connected to database 'mythconverg' at host: 192.168.1.104
#
2011-04-25 20:54:33.613 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/recordings-ui.xml
#
2011-04-25 20:54:33.825 MythContext: Connecting to backend server: 192.168.1.104:6543 (try 1 of 1)
#
2011-04-25 20:54:33.825 Using protocol version 23056
#
2011-04-25 20:54:33.890 MythContext: Connecting to backend server: 192.168.1.104:6543 (try 1 of 1)
#
2011-04-25 20:54:33.891 Using protocol version 23056
#
2011-04-25 20:54:35.593 Preview Error: Remote Preview failed, reason given: ERROR_UNKNOWN
#
2011-04-25 20:54:36.803 TV: Attempting to change from None to WatchingPreRecorded
#
2011-04-25 20:54:37.886 RingBuf(myth://192.168.1.104:6543/1561_20110425193900.mpg) Warning: Peek() requested 2048 bytes, but only returning 376
#
2011-04-25 20:54:37.886 NVP::OpenFile(): Error, couldn't read file: myth://192.168.1.104:6543/1561_20110425193900.mpg
#
2011-04-25 20:54:48.409 Deleting UPnP client...
```

thanks for any help

---

### Post by tdcarlo on 2011-04-26
I got the same result with a second fresh install of 10.10.  So I installed 10.4 and upgraded to 10.10 and everything is working.

---

