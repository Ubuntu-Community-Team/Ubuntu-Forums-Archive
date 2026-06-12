---
title: "Remote Desktop Help"
date: 2009-03-07
forum: Networking &amp; Wireless
---

### Post by jtanner0 on 2009-03-07
Ok, I am trying to remote desktop in to my ubuntu computer at work, from home using winXP. I did all the remote desktop settings on the ubuntu machine.

I opened my VNC viewer, put in the address, and it connected and asked me for a security password (which I did set). I typed in the password, and it seemed to connect, but all I got was a black screen.

I closed the connection, and tried again but now I dont even get the black screen. The VNC viewer asks me for my password, and when I hit ok, it just disappears and no window pops up.

Let me also note that I can SSH into this computer with PuTTy on port 22, no problem.

Anyone have a clue as to why I can get as far as establishing a connection, but no window pops up for the remote desktop? or why the first time I tried to connect I actually had a black screen?

Any help much appreciated.

James

---

### Post by mbn18 on 2009-07-12
I had the same problem, The connection was just way to slow for remote administration over the internet.

I couldn't find a way to configure "Remote Desktop Viewer" to use compression or use less colors. So I just installed vncviewer and initiated the connection using a shell:

> vncviewer -geometry 800x600 212.143.222.77

The default behavior is to display using 8 colors. So its considerably faster.

Does any one know if its possible to tweak the settings of "Remote Desktop Viewer" ?

---

