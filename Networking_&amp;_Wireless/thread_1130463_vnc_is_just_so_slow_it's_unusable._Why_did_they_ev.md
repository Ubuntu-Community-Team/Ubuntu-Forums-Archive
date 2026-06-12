---
title: "vnc is just so slow it's unusable. Why did they even include it in Ubuntu?"
date: 2009-04-19
forum: Networking &amp; Wireless
---

### Post by xmrkite on 2009-04-19
Hello, i have vnc installed (the default one that comes with ubuntu)...but it's so slow!!

I've tried this on multiple ubuntu computers and they're all the same. totally unusable. By slow, i mean that i move the mouse one inch, then wait 5-10 seconds, and then the viewer shows where the mouse is. Why would they add this function if it's so unusable?

I've used RDP a lot in the past for windows machines and it's pretty decent. How can i make vnc as fast or even close to as fast as vnc?

-Thanks

---

### Post by rico4295 on 2009-04-19
I use xtightvncviewer. I found it in the package manager. It works for me for what I use it for and it connects to my pc's running windows and ultravnc server.
Not really an answer, just an opinion. Good luck

---

### Post by pytheas22 on 2009-04-19
Which VNC package did you install, and which version of Ubuntu are you using?  I recall there being some substantial performance problems with one of the vncserver packages in Ubuntu 8.04, although I think they were fixed in 8.10.  Also, I've never had problems using the built-in VNC functionality that you can enable by going to System>Preferences>Remote Desktop.

---

### Post by xmrkite on 2009-04-20
i just did a fresh install of intrepid and got all the latest updates for it. Also i have another intrepid computer but that one runs mythbuntu (xfce) and it too is also just as slow.

The mythbuntu one i access locally and it's just so slow, so it's not my internet connection.

I tried xtightvncviewer and it is just as slow as the built in ubuntu one (vino I think it's called).

Also, I've tried connecting from windows computers to other windows computers with vnc and it's fine. I then go from those same windows computers to these ubuntu ones and it's super slow, so i know it has to be on ubuntu's end.

-Thanks for any help you guys can provide.

---

### Post by pytheas22 on 2009-04-20
How are you starting the VNC server?  Did you enable desktop sharing via System>Preferences>Remote Desktop, or are you launching a server from the command line (by typing 'vnc4server' for example)?

Also, if you connect open the VNC client on Ubuntu and connect to localhost, is it still slow?  This would let you know whether it's a networking problem, or something else.

---

### Post by robertcpendleton on 2009-04-20
I've been trying to use VNC between to machines on my local network. The desktop takes a long time to update. It takes so long that I have never seen it update, it only seems to happen when I walk away from the PC for long periods of time.

Both of the PCs are running 9.05 RC1 using the default VNC server and client. The are both connected to my local lan. Connections happen quickly, you can then watch the first picture of the remote desktop fill in. Then you can move the mouse and click on things on the remote desktop.

And ......... then ......... you .......... wait ........... and ..........

I have also tried three other clients, tsclient, xtightvncviewer, and xvnc4viewer. The all connect quickly and then you wait. I have not tried any other VNC servers.

---

### Post by pytheas22 on 2009-04-20
**robertcpendleton**: you might want to give vnc4server a try, rather than the built-in VNC package.  To use vnc4server, first install it:
```

sudo apt-get install vnc4server
```

then open a terminal and type:
```

vnc4server
```

to start a session.  It will prompt you for a password, and then tell you which screen to connect to to access your session.  Does it perform any better?

Also, I'm curious as to whether you experience issues when connecting to a VNC session on localhost, rather than from a remote machine (if you don't know what that means, I can explain better).

---

### Post by xmrkite on 2009-04-20
ok, i tried that and it's much faster...still not as good as remote desktop in windows, but i can live with this. 

Also, i can only get into my ip and :1....how do i get into the main desktop for this? I need to be able to view the windows that are already open on the computer, not start a new session up.

-Thanks

---

### Post by Greyed on 2009-04-21
Have you tried any of the settings on VNC?  Some of the protocols are dog slow over the network.  Also depending on what you're doing you might be able to get speedups by using color reduction, removing the background, etc.  These are all standard fare tricks that RDP clients tend to use by default.

---

### Post by xmrkite on 2009-04-21
How do i enable these settings with the ubuntu vino vnc server or client? I haven't been able to find any vnc programs that let you limit the colors or enable compression or something like that.

-Thanks

---

### Post by ionoff on 2009-04-21
Check out FreeNX.

It runs 1000x faster than VNC, it can even make VNC faster and use less bandwidth in some circumstances.

Only problem is it is a new session so it connects as your user, but not to your desktop session like the gnome build-in vnc server (vino).

It works similar to other VNC solutions though.


Trust me, once you go FreeNX and it works properly, you will never go back to VNC unless your forced to.

It is the Remote Desktop/Terminal Services of Linux.

It's also built around more secure principles.

[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

---

### Post by xmrkite on 2009-04-21
OK, freenx seemed really nice, however, how do i log into the active session on my desktop? It seems like freenx starts a new separate session. I need to be able to lock my computer and then go onto my laptop and open up that same session remotely. That's why i went with VNC. But if freenx can do that too, then that seems great.

-Thanks for the help

---

### Post by ionoff on 2009-04-21
> **xmrkite said:**
> OK, freenx seemed really nice, however, how do i log into the active session on my desktop? It seems like freenx starts a new separate session. I need to be able to lock my computer and then go onto my laptop and open up that same session remotely. That's why i went with VNC. But if freenx can do that too, then that seems great.

-Thanks for the help

What I do when I need to do things like that is I load FreeNX with gnome-terminal (custom command) and then I load vinagre or vncviewer or tsclient or rdesktop from it.

Gives benefit of FreeNX and optimizes vnc connection.

Just use gnome's built in VINO.


Note: for some reason the native vnc option fails for me with password issues, which is why I run from console.  Don't forget your & or screen.

Also sometimes, when I know I will be traveling or needing to connect back in, I open a loopback connection to the freenx and run it locally.
That way my applications are already running in an NX session.

The built-in VNC option in NXClient always fails with password options for me.  That is why I run console.  It also allows me to spawn other apps directly instead of the need of an entire desktop/window manager.  Don't forget to use screen or & with different #'s representing stdio if you want to keep things clean.

I used to run local x-servers and ssh-forward them, but it was slow and used lots of BW, where as FreeNX is a lifesaver.

---

### Post by xmrkite on 2009-04-21
OK, i setup the gnome default to allow vnc connections and i *can* vnc in, but still at those horribly slow speeds. So how do i get NX to work through that?

I do see it has an option to use VNC vs gnome, kde, etc but when i do that, i get a error: Opening Password file failed.

Not sure what to do now. But this NX thing was super fast when working on the virtual screen it first got me in, so i cant wait to get it going on my main screens.

-Thanks

---

### Post by xmrkite on 2009-04-23
OK, i figured it out, sort of. If i select Shadow as the desktop, i get into the vnc session.

However, since i have two screens on the computer i'm connecting to, the picture looks horrible (though it's pretty fast). Still, this is a major issue as the screen just get's squished down to my laptops's screen size.

Any ideas how to fix this?

-Thanks

---

### Post by chinarut on 2009-05-31
I'm a Ubuntu newbie and glad after repeated factory reinstalls kept overheating my poor inspiron and shutting it down, Ubuntu seems to be a happy camper :)

anyhoo - i'm having the same performance issues with the built-in Remote Desktop as well - I'm glad i'm not alone.  I am happy a built-in solution is available though!

Similarly, I was able to access the same laptop under the same network configuration using RDC with acceptable performance in the past.

I installed the "vnc4server" pkg as suggested.

> **xmrkite said:**
> Also, i can only get into my ip and :1....how do i get into the main desktop for this? I need to be able to view the windows that are already open on the computer, not start a new session up.

I've got the same question in regards to how to access my main desktop.

xmrkite, have you found an ideal alternative you've been happy with since  u last posted?

---

