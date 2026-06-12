---
title: "vnc4server  BUGS?"
date: 2011-03-13
forum: Networking &amp; Wireless
---

### Post by nhtrader on 2011-03-13
Mythbuntu 10.10 using xfce 4.8.1
vnc4server 4.1.1

PC1 = Mythbuntu 10.10 using xfce 4.8.1 and vnc4server 4.1.1

PC2 = winXP SP3 (32bit) using tightVNC v1.5.2

First, I can connect btwn both PCs. I'm using PC2 to view desktop of PC1 and here are the problems:

1. After the connection is made, I see an empty desktop from PC1. No open applications; no "Applications Menu"; no upper horizontal panel/taskbar. I do see a few desktop icons and the desktop-background is visible. Basically, I've logged into a new session but most of the functionality is lost.

2. If I click on firefox icon. It opens off centered (down and right of center) to the point that I can't see half of the window. So I try to move its position and it doesn't move.

3. If I click on Opera I get an error prompt: 
because its lock file is active
/home/user/.opera/lock  2 Buttons appear : Yes and No

4. If I click on Geany (text editor), the window opens and I can see the entire window, but I can't move it.


So basically, I have an active connection but its not doing what I expect it to do, and that is to shadow my existing workspace, and allow me to use the workspace as I could if I were there.

Does anyone have any ideas? Does anyone have a working xfce vnc configuration?

---

### Post by tenfishsticks on 2011-04-22
Similar issue: 

Client: Laptop running Jaunty with tightVNC and xrdp with Cisco AnyConnect Client

Server: Two monitor desktop running Lucid with vnc4server

Connected last night and couldn't move within the vnc window, but I could see the upper toolbar.  Tried to adjust desktop to only display main display (hoping for some scaling workaround).  Restarted desktop and came in today to find that I can't move my Firefox window.  

It's taskbar is above the screen edge and none of the hotkeys work anymore!!!  I feel like a double-sided drill bit: screwed no matter which way I go.  Did you ever solve this?

---

