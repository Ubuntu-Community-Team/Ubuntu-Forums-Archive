---
title: "gnome-rdp vnc error &quot;xtightvncviewer not installed&quot;"
date: 2009-07-16
forum: Networking &amp; Wireless
---

### Post by malanco on 2009-07-16
hi guys,im using gnome-rdp in jaunty, i can get remote desktop to my windows boxes but everytime i want to connect through vnc i get this error "xtightvncviewer seems not to be installed", but i do have xtightvncviewer, i dunno know what i am doing wrong, i have tightvnc server on my windows box but no luck at all.

any help will be greatly appreciated!!

thanks! :D

---

### Post by malanco on 2009-07-17
bump

---

### Post by kkruecke on 2009-08-12
Did you try:

1. installing xtightvncviwer

 # sudo aptitude install xtightvncviewer

2. Then using Terminal Server Client to connect to the Windows pc

 Applications->Internet->Terminal Server Client 
 Choose the VNC protocl.

---

### Post by ario on 2009-08-29
I tried Applications>Internet>Terminal Server Client. But it runs with RDP Protocol. But not with VNC. When I select VNC as protocol with same settings as when I'm using RDP, It waits for me to press "Connect" button and then nothing happens.
Any Suggestions? Thanks.

---

### Post by Seano1957 on 2009-12-11
Don't know if you found a solution for this but in case anyone else is googling a solution - gnome-rdp is calling xtightvncviewer with --passwd which then calls vncpasswd which is missing if all you have installed is xtightvncviewer.

Installing vnc4-common or vnc4-server should fix it.

I suspect it's calling without a username, password as it works without a ~/.vnc/passwd file.


--s

---

