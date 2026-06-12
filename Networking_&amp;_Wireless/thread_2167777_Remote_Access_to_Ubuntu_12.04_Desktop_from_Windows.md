---
title: "Remote Access to Ubuntu 12.04 Desktop from Windows"
date: 2013-08-15
forum: Networking &amp; Wireless
---

### Post by ERtzDbX on 2013-08-15
I have been a Ubuntu 9 for a couple years now and I am really surprised to find very little information on doing this now that I am in 12.04.  Or more accurately, very incomplete information.

First, I have tried XRDP but it is cripplingly slow.  As in 20 seconds to display the desktop and 3 or 4 seconds to update after clicking or typing.

Second I tried tightvncserver, but failed to get it to work.  I followed tutorials online but to no avail.

Last I tried Remmina but . . . the only information on that I have found is using it as a client.  Is it only a client?

So what I am looking for is anything that can allow me to remotely access my Ubuntu system from Windows 7.  How to configure XRDP, Remmina setup, VNC Software, anything.
I understand there are certainly tutorials out there so I won't ask specifically for someone to provide details, links to tutorials would be fine.  Anything you guys could provide would be great.  Thanks in advance.

---

### Post by ERtzDbX on 2013-08-16
So what are you all using for remote access?  You can just share what protocol/program you are using so I might be able to get an idea of different ones that work well.

---

### Post by ERtzDbX on 2013-08-19
So uh . . . don't want to get in trouble for bumping too much, but I have been trying vnc with tightvncserver.  Right now, I can only see my blank wallpaper; Unity does not load.  As far as I can tell, this is typical but none of the posted solutions work for me.

[http://askubuntu.com/questions/130110/tightvncserver-on-ubuntu-12-04-server-with-ubuntu-desktop-installed-no-unity](http://askubuntu.com/questions/130110/tightvncserver-on-ubuntu-12-04-server-with-ubuntu-desktop-installed-no-unity)
This solution gives the error "Could not aquire name on session bus" when I attempt to login from Windows and does not show the wallpaper.

[https://www.digitalocean.com/community/articles/how-to-setup-vnc-for-ubuntu-12](https://www.digitalocean.com/community/articles/how-to-setup-vnc-for-ubuntu-12)
This removed the wallpaper but had no other effect.

[http://bookofzeus.com/articles/install-vnc-server-and-vnc-client-on-ubuntu/](http://bookofzeus.com/articles/install-vnc-server-and-vnc-client-on-ubuntu/)
This had the same effect as the first tightvnc installation, but that is likely because I didn't change xstartup.

Surely there is a way to connect to 12.04.  I'm suprised Canonical hasn't provided a way themselves.

---

