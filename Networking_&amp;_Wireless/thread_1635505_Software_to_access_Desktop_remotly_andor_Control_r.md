---
title: "Software to access Desktop remotly and/or Control remotly"
date: 2010-12-01
forum: Networking &amp; Wireless
---

### Post by Mobidoy on 2010-12-01
I have won my fight and my father in law accepted to give gnu/linux a try as his server and to run on the computer of the new company he is starting. 

One feature he would like is to be able to access his work desktop (graphicaly) from home. On my side, I would like to be able to control his desktop from home if I need to show him things.

I already can SSH in terminal to install and maintain stuff but, to move the mouse around and point him where to click or what to use would be invaluable.

 What are my options ?

---

### Post by PRC09 on 2010-12-01
You can try out Teamviewer,I use it to maintain parents machine, works fine for me and works with Windows or Ubuntu.....


[http://www.teamviewer.com/index.aspx](http://www.teamviewer.com/index.aspx)

---

### Post by Mobidoy on 2010-12-01
Good option to help him with his home computer but, I would end up Illegal when connecting to his system or his employees system for work issues.... 

But surely something to look into

---

### Post by CharlesA on 2010-12-02
> **Mobidoy said:**
> Good option to help him with his home computer but, I would end up Illegal when connecting to his system or his employees system for work issues.... 

But surely something to look into

Look for remote support software.

You could use VNC, but it's terribly insecure. FreeNX would be a good idea if you need to access a GUI.

---

### Post by Mobidoy on 2010-12-02
> **CharlesA said:**
> Look for remote support software.

You could use VNC, but it's terribly insecure. FreeNX would be a good idea if you need to access a GUI.

So VNC is not an option then, cannot play with the security of his network when that was one of my main feature with stability.... 

If it was only me, I would be ok with terminal but, no way I can move the mouse to show him things and, even worst would be to have him connect remotly thru terminal to work from home :)

---

### Post by CharlesA on 2010-12-02
Well, you can tunnel VNC over SSH, and while it's secure (as long as you set VNC to listen to localhost and connect that way), it's still terribly slow. I guess it would work in a pinch, but I wouldn't like dealing with the slow responsiveness.

---

