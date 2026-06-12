---
title: "slow vnc connection"
date: 2009-11-19
forum: Networking &amp; Wireless
---

### Post by RyanGT on 2009-11-19
I am running vnc over ssh using this command:

ssh 146.163.147.238 -f -L 5900:localhost:5900\
        x11vnc -safer -localhost -solid "darkblue" -speeds "dsl" -nopw -once -auth /var/lib/gdm/:0.Xauth -display :0 \
        && sleep 5 \
        && vncviewer localhost:0

I got that with help from the forum and don't understand all of it.  I added the -solid "darkblue" myself, but it doesn't seem to be working.  

My main issue is that the vnc sessions are painfully slow because whenever it needs to re-draw the screen, it re-draws my background picture in at least 24-bit depth.  It is a nice picture of my family, but I don't need to see it over vnc.  There may be other problems with the server thinking it has a faster network connection than it really does.  The server is on a LAN line with a fast network connection, but I am accessing it from home over a connection with mediocre DSL-ish speed.

I love having the ability to connect over vnc, but I don't use it much because it is so slow. 

Thanks,

Ryan

---

### Post by krunge on 2009-11-19
> **RyanGT said:**
> 
ssh 146.163.147.238 -f -L 5900:localhost:5900\
        x11vnc -safer -localhost -solid "darkblue" -speeds "dsl" -nopw -once -auth /var/lib/gdm/:0.Xauth -display :0 \
        && sleep 5 \
        && vncviewer localhost:0

Since you say it is very slow over dsl broadband, I wonder if your vncviewer is using the VNC "raw" encoding because it thinks the connection is to the local machine (i.e. the localhost:0)

I don't know which vncviewer you are using.  Please report what it prints out at when you run 'vncviewer -h' for its help output.

If the viewer is TightVNC, try running it this way:
```
vncviewer -encodings 'copyrect tight hextile' localhost:0
```

Also, x11vnc will report what the preferred encoding is:
```

19/11/2009 22:14:51 Enabling LastRect protocol extension for client 10.0.2.1
19/11/2009 22:14:51 Using tight encoding for client 10.0.2.1

```

There is more info here:
[INDENT][http://www.karlrunge.com/x11vnc/#tunnelling](http://www.karlrunge.com/x11vnc/#tunnelling)[/INDENT]

If it turns out it is using a good encoding like "tight" or "zrle" then we  will move on to getting -solid to work, etc. to try to speed it up.

---

### Post by RyanGT on 2009-11-20
Thanks for your help.  In response to your first question, here is the output of "vncviewer -h":

ryan@ryan-duo-laptop|09:14 AM|scripts$ vncviewer -h

VNC Viewer Free Edition 4.1.1 for X - built Apr 16 2008 13:02:40
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.

usage: vncviewer [parameters] [host:displayNum] [parameters]
       vncviewer [parameters] -listen [port] [parameters]

(I cut the rest of the output.)

Trying

vncviewer -PreferredEncoding=ZRLE localhost:0

helped some but looked ugly.

switching to

xtightvncviewer -encodings "copyrect tight zrle hextile" localhost:0

seems to have helped a great deal.

I am open to other suggestions for fine tuning the performance, but I am fairly happy now.

Thanks,

Ryan

---

### Post by krunge on 2009-11-20
> 
switching to

xtightvncviewer -encodings "copyrect tight zrle hextile" localhost:0

seems to have helped a great deal.

That's good.  In my experience the tightvnc encoding is about 4X faster than ZRLE for photo-image regions (e.g. your background.)  I suppose this is because tightvnc uses jpeg compression.  For non-photo regions zrle may compress a bit better (not sure.)
> 
I am open to other suggestions for fine tuning the performance, but I am fairly happy now.

Regarding your problem with -solid, there have recently been some changes WRT it:

[INDENT]- In KDE4 -solid no longer works (not clear when/if KDE will re-introduce this capability)

- In recent GNOME -solid stopped working due to dbus changes, but this has been fixed upstream in the x11vnc 0.9.9 development version.

- Although tedious, you can always toggle the solid background manually via your desktop configurator.[/INDENT]

There are other ways to speed things up.  A traditional one is to reduce the color depth if you can tolerate the false colors.  There are also tightvnc compression and quality levels that can be tweaked (again, it can start to look odd.)  More info here:

[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-slow-link](http://www.karlrunge.com/x11vnc/faq.html#faq-slow-link)[/INDENT]

Also consider trying x11vnc's client-side caching hack:
[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-client-caching](http://www.karlrunge.com/x11vnc/faq.html#faq-client-caching)[/INDENT]
```
x11vnc -ncache 10 ...
```
(note your viewer may show the pixel cache region.)

---

