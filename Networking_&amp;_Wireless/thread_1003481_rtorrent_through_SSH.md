---
title: "rtorrent through SSH"
date: 2008-12-06
forum: Networking &amp; Wireless
---

### Post by alkamid on 2008-12-06
Hello,

I have two computers: one (client) here at my desk and the second (server) 300km away in my house.

I want to:
1. start rtorrent on server
2. be able to control it both from server and from client through SSH

I have ssh installed and configured properly. I know I can do this using VNC but that's not what I want (as rtorrent is not a graphical app, I just don't need vnc to do this).

I know how to use screen app and to detach rtorrent, but in this case I have to "screen -r" rtorrent on my server while I want it to be running in open window all the time.

Any suggestions?

---

### Post by alkamid on 2008-12-06
bump

---

### Post by alkamid on 2008-12-06
bump

---

### Post by Dr Small on 2008-12-06
So what's the problem? Just detach the screen and move on.
When you come back, reattach the screen again.

---

### Post by alkamid on 2008-12-06
The problem is that I have to write "screen -r some_numbers_(id)" on my server. I want rtorrent to be opened in a window on my server all the time and accessible for me from my laptop from time to time.

---

### Post by Dr Small on 2008-12-06
Why does the screen need to stay open? You can always just leave the SSH session open if you don't care about bandwidth.

Also, if you only have one screen session open, you can just run:
```
screen -r
```

I run bzflag-server via screen, and just detach the screen once I have started it, and reattach it when I need to stop it. Screen was meant to be detached.

---

