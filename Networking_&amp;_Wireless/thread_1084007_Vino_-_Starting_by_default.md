---
title: "Vino - Starting by default"
date: 2009-03-01
forum: Networking &amp; Wireless
---

### Post by MrQuincle on 2009-03-01
Dear all,

When I compare my two Ubuntu systems I have one not starting Vino on default. The other however, does start Vino by default and it shows up as: ```
/usr/lib/vino/vino-server --oaf-activate-iid=OAFIID:GNOME_RemoteDesktopServer --oaf-ior-fd=17
```

I know I can start Vino from the command-line by:
```
/usr/lib/vino/vino-server
```
I discovered that manual changes to ~/.gconf/desktop/gnome/remote_access/%gconf.xml doesn't work, but need to be done through gconftool-2. Such like:```
gconftool-2 -s -t bool /desktop/gnome/remote_access/use_alternative_port true
```

The vino-preferences utility works too. So, I can start Vino and even restart it with different configuration parameters. But I want to start it automatically after booting.

Where is it normally started in Ubuntu? 

Kind regards,

Anne

---

