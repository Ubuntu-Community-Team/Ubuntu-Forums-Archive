---
title: "auto connect"
date: 2009-06-05
forum: Networking &amp; Wireless
---

### Post by digitalmusic on 2009-06-05
Can anyone help with this probably simple problem. I've just installed a 3com wireless router and only using wired as yet. I've actually got no problems with the internet connection, everything works just fine.
The problem is that I can't get the connection to connect automatically on boot up. The only way I can connect is to open firefox and type in the gateway address, then on the status page click connect - then everything is fine. So I don't want to mess up any internet settings - just have auto connect at boot up. Any help appreciated.

---

### Post by ajgreeny on 2009-06-05
It should normally do this at boot up, so try right clicking on the network manager applet on the panel, highlight the wired connection,  choose edit connection and then make sure that the two tick boxes for Connect automatically and Available to all users are both selected.  Hopefully that will do the trick.

---

### Post by kerry_s on 2009-06-05
> **digitalmusic said:**
> Can anyone help with this probably simple problem. I've just installed a 3com wireless router and only using wired as yet. I've actually got no problems with the internet connection, everything works just fine.
The problem is that I can't get the connection to connect automatically on boot up. The only way I can connect is to open firefox and type in the gateway address, then on the status page click connect - then everything is fine. So I don't want to mess up any internet settings - just have auto connect at boot up. Any help appreciated.

the fact you can connect to the router, tells me your connection is good, which means the problem is in the router. you need to go through the router settings and set it up properly.

---

### Post by digitalmusic on 2009-06-05
Have just reinstalled network manager. Icon appears in tray with small red cross by its side. Wired network appears but underneath it says "device is unmanaged". Right click to show connection information gives error box with no active connections found - which is obviously not the case as I'm online now typing this. If I click edit connections there is nothing showing in wired. Is network manager really needed? Further help required please.

---

### Post by ajgreeny on 2009-06-05
When you rught click the icon is the "Enable networking" box checked?  If not, do so and try rebooting if needed.  It seems weird that it says no connections when you are connected, but I have no other ideas on how to overcome this problem.

---

### Post by digitalmusic on 2009-06-07
have followed instructions from another thread which resets nm settings. Now in network manager connection shows as ifupdown (eth 0) - it shows wired connection and connect automatically is ticked. It still doesn't auto connect though.

---

### Post by digitalmusic on 2009-06-07
Have seen that some people say ditch Network Manager and use Wicd, so have uninstalled network manager and replaced with wicd.
Same problem - wicd shows connected when it's not so only way to connect is as my first post.
Any more suggestions welcomed.

---

### Post by cariboo on 2009-06-07
If you have uninstalled network-manager-gnome already, install gnome-network-admin to see if that works.

---

### Post by digitalmusic on 2009-06-07
Yep - been there - done that - still doesn't work.
But thanks for the reply.

---

