---
title: "xbox not finding ushare. ushare not working?"
date: 2009-10-01
forum: Networking &amp; Wireless
---

### Post by Xavier Oddmon on 2009-10-01
Hello! Once again, I have a problem I cannot solve, and thus I turn to the ubuntu forums.

Alright, i've got an xbox 360, and a laptop which is currently running jaunty. Following the xbox360media guide, i've installed ushare 1.1a, compiled from source. I've edited the /etc/ushare.conf file to include my music folder, and set USHARE_ENABLE_XBOX=yes. When I start ushare, it seems to be working just fine, locally. 
```

chris@chris-laptop:~/temp/ushare/ushare-1.1a-NeToU$ ushare
uShare (version 1.1a-NeToU), a lightweight UPnP A/V and DLNA Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See http://ushare.geexbox.org/ for updates.
Listening on telnet port 1337
Initializing UPnP subsystem ...
Starting in XboX 360 compliant profile ...
UPnP MediaServer listening on 10.0.0.3:49152
Sending UPnP advertisement for device ...
Listening for control point connections ...
Building Metadata List ...
Looking for files in content directory : /home/chris/Music/
Found 2328 files and subdirectories.

```

xbox still doesn't see it. I've tried starting ushare / booting the xbox / changing to the find media devices screen so many times in every order imaginable at least once. What's more, the laptop is dual boot, and when in windows, it finds WMP's share just fine.

Here's where I have problems: searching for help on this, everyone seems to solve it after either turning off a firewall, changing the config file, or setting the "-x" command line option. Doesn't work here. 

Finally, i'm not sure if it's supposed to show up, but my netgear router's administration page has the option to list UPnP devices. my laptop (10.0.0.3) doesn't show up here. When it's in windows, it does. The xbox (10.0.0.4) does show up in this screen. Don't know what to make of that

Any help is very much appreciated.

---

