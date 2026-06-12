---
title: "Networkmanager gone after update (8.04)"
date: 2009-03-17
forum: Networking &amp; Wireless
---

### Post by muschen on 2009-03-17
In short; the networkmanager is gone.

I'm not really any good at linux, but basicly I'm running Ubuntu 8.04 on an IBM T43 laptop, and after the lastes update though the automatical update, I left my computer for a little while, and when I came back and unlocked the screen, the network manager was completely gone.
I've tried to get it back somehow, (right clicking to find it), but it seems to have disappeared, and I'm not able to go online at all. How do I fix it?

---

### Post by nixscripter on 2009-03-17
Make sure it's still installed by running in the terminal: ```
nm-applet
``` It should reappear. If it says "command not found," run this to reinstall ```
sudo apt-get install network-manager-gnome
```

Hope this helps.

---

