---
title: "Restart remote server via frozen but active VNC"
date: 2009-12-21
forum: Networking &amp; Wireless
---

### Post by jpsjps on 2009-12-21
I bet this is a first...

I am using RealVNC to connect to my server at home (latest desktop version and updates installed). This worked like a charm until last week Thursday. The only issue I used to have was a slight sluggishness in mouse movements... which incidentally caused the more serious issue which I am now trying to resolve...

On closing my RealVNC client session, I usually lock the remote screen first before disconnecting the session. In doing so last Thursday, I clicked on the "Power" button in the upper right corner (default desktop config) and, while moving the mouse down towards the "Lock" option, I accidentally clicked on either the option above or below it - I have no idea which option it was because if the sluggish mouse movement. Anyway, this caused my VNC client screen to freeze with no further screen refreshes coming from the server.

Since last Thursday, I can still manage to connect to my remote server at any time but I always get the same frozen desktop screen. Even with the same date & time stamp from the moment it froze last Thursday. The fact that I can connect means the server is still up & running. I can also confirm that other processes are still running in that the remote server is still updating my Dyndns.org alias on a regular basis.
I guess my only solution would be to try and remotely reboot my server but I have no idea how to do this while completely blind...

To make matters worse, my home server is behind a DSL modem that forwards port 5900 to a wireless router which then forwards port 5900 to the home server. This is the only port forwarding configured so I have no option to get any other access to this server except via VNC.

So my question is: If I have a VNC session open, is there any chance of issuing any commands that would make my server reboot. And of course doing this without being able to see what I am doing....

I am hoping for some hacking tips that would allow me to piggy-back an ssl session on top of the open VNC connection or something similar... ;-) 
Any help (or even just a bit of sympathy) would be greatly appreciated

---

### Post by coutts99 on 2009-12-21
Have you not got SSH access? It's kind of good for these situations :)

---

### Post by jpsjps on 2009-12-21
> **coutts99 said:**
> Have you not got SSH access? It's kind of good for these situations :)
Yeah I know it was pretty daft of me to only forward port 5900 which is why I am stranded right now. I am certainly learning the hard way here...

---

### Post by coutts99 on 2009-12-21
Not sure there is much you can do. Anyone at the remote end that can give the server a kick for you?

---

### Post by jpsjps on 2009-12-21
> **coutts99 said:**
> Not sure there is much you can do. Anyone at the remote end that can give the server a kick for you?

Unfortunately not before Jan 1st...
BTW, can anyone tell me exactly what are the options above and below "lock screen" on the power menu? I have not been able to even find out exactly what I clicked on to cause all this misery... it all happened so suddenly...

---

### Post by coutts99 on 2009-12-21
> **jpsjps said:**
> Unfortunately not before Jan 1st...
BTW, can anyone tell me exactly what are the options above and below "lock screen" on the power menu? I have not been able to even find out exactly what I clicked on to cause all this misery... it all happened so suddenly...

Not sure, I'm on KDE not Gnome

Sure someone else will be able to tell you though :)

---

