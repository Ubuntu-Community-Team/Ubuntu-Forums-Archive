---
title: "X question? Video Probs but can ssh in. Possible to &quot;attach&quot; to a process there?"
date: 2013-06-19
forum: Networking &amp; Wireless
---

### Post by DiagonalArg on 2013-06-19
Hi!  Thanks to Toz I can now ssh into my Ubuntu 12.04 machine which is having video problems.  I have a gedit running under Gnome there with a file that I have not (has never been) saved.  Any way to attach to that gedit and somehow get that file?

----
[Edit: While I'm at it ... I couldn't [COLOR=#000000]mark my previous thread as "solved" - it's not under Thread>>Tools the way it's supposed to be, and I am logged in....][/COLOR]

---

### Post by Toz on 2013-06-19
Hi, me again.
I came across this: [http://stackoverflow.com/questions/12064401/save-on-gedit-remotely]("http://stackoverflow.com/questions/12064401/save-on-gedit-remotely"). 

To mark a thread as solved:
1. Click on the "Edit" button on your first post in the thread.
2. Click on "Go Advanced"
3. Change the Prefix to "[SOLVED]"
4. Save

---

### Post by DiagonalArg on 2013-06-19
Toz. That's incredibly helpful.  Any thoughts on how I could send a carriage return to xdotool?  Would that be ctrl+m?  I'll also need to give a filename, so I'll need to send a whole string.

(Damn, linux is cool!)

---------

(Ah, missed "Go Advanced" when I tried that method to set the prev thread as "Solved".)

---

### Post by steeldriver on 2013-06-19
Depending on what kind of video problems (i.e. if there's a working X session / desktop, you just can't see it because of hardware issues) you could also consider enabling Vino ('Desktop Sharing') and connecting via a VNC client - assuming the original display is :0

```
DISPLAY=:0 gsettings set org.gnome.Vino enabled 'true'
```

---

### Post by DiagonalArg on 2013-06-19
Thanks steeldriver.  There is indeed a running desktop.  (I believe there is some video card issue).

So your code (along with the "DISPLAY=:0" as prefix) would get input to the terminal?

[Edit: Is there a specific client I would then have to use from my (13.04) laptop?  How would I indicate to the client to attach to that desktop rather than creating a new session of some sort?]

---

### Post by steeldriver on 2013-06-19
Yes, input it in your SSH terminal session, then fire up a VNC viewer (depends on your laptop's OS - Remmina, TightVNC etc.) and point it at the remote machine's name or IP on the default port 5900 - if your UFW firewall is still enabled you will need to open port 5900 - or you could tunnel VNC over SSH if opening port 5900 not feasible

Vino is set up to share (mirror) the running desktop by default - you shouldn't need to do anything extra to attach to it

---

### Post by DiagonalArg on 2013-06-19
Ok, I can open the port.  Got a friend waiting. Back in evening. Keeping my fingers crossed until them.

---

### Post by steeldriver on 2013-06-19
Oops, almost forgot, if you have not enabled Desktop Sharing previously you may need to set a new base64 encoded VNC password - just tried this, it seems to work:

```
DISPLAY=:0 gsettings set org.gnome.Vino vnc-password "$(echo -n "newpass" | base64)"
```

where 'newpass' is a password of your choice - good luck and let us know how it goes

---

### Post by DiagonalArg on 2013-06-20
Steeldriver - Thanks.  If you're still around, I'm looking at my laptop and see that your first command effectively sets the checkmark on "Allow Other users to view your desktop".  It does not <<appear>> that I need to set a password, but there is a default checkmark by "You must confirm each access to this machine".  That, I obviously won't be able to do.  Do you have a suggesting how I might be able to uncheck this one?

---

### Post by DiagonalArg on 2013-06-20
Ok, it looks like I need:


```
DISPLAY=:0 gsettings set org.gnome.Vino enabled 'true'
DISPLAY=:0 gsettings set org.gnome.Vino prompt-enabled 'false'
```

(I think I get how to use gsettings!)

Here goes.  :-P

---

### Post by DiagonalArg on 2013-06-20
Do the charanga!!

OMG, you guys both totally saved my butt. :bow:

I had to do:

```
sudo ufw allow 5900 
```

after which Vinarge (the VNC client) had somehow already identified my desktop under Menu item "Bookmarks".  So, I didn't have to set it up.  After that, the desktop just popped up.  

I'm very happy that this worked, though I'm not yet clear how I connected to the correct desktop.  How might I understand this better?  Do I read about X?  VNC?

---

### Post by steeldriver on 2013-06-20
Great! well done for figuring out the missing piece with gsettings, sorry I forgot about that one

TBH I don't know how it works under the hood - but certain VNC servers (Vino, x11vnc) are set up to give you 'desktop sharing' out of the box i.e. they connect to and forward the current running desktop by default, whereas things like vncserver / vnc4server / tightvncserver are used to run independent X server instances on separate displays. By convention the VNC port is 5900 + the display number so 5900 is (usually) the primary local desktop (display :0 in X terminology).

---

