---
title: "Wireless Connection on Startup"
date: 2010-01-25
forum: Networking &amp; Wireless
---

### Post by mastermindg on 2010-01-25
I've got my wireless card working fine, the only thing is that I have to enter the following EVERY time I log in:

```
sudo iwconfig ra0 essid MYID
```

What can I do to bypass this step?

---

### Post by pastalavista on 2010-01-25
After you are configured and connected, go to System--> Preferences--> Network Connections.. (or right-click the network manager icon in the panel and "edit connections")..click the wireless tab and select your current connection and click "edit" and check the box "connect automatically"

---

### Post by mastermindg on 2010-01-25
Sorry....Forgot to mention that I scrapped Network-Manager and replaced it with WICD. I like the look and feel of it better. I've got it set to automatic in WICD and if I lose connectivity while I'm connected it will reconnect, but it still doesn't connect automatically at startup.

---

### Post by mastermindg on 2010-01-25
I ended up just adding the iwconfig line to the startup function in the wicd daemon script -  /etc/init.d/wicd. It's crude, but effective. I imagine there is a better way, but this will work until I find it.

---

