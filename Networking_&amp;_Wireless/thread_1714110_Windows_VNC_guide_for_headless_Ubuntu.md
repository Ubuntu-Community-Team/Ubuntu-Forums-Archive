---
title: "Windows VNC guide for headless Ubuntu"
date: 2011-03-24
forum: Networking &amp; Wireless
---

### Post by fboecom on 2011-03-24
No question but just a guide for someone that may be interested.

The information below describes a Windows desktop(all versions including 7-64bit) using VNC to create a remote desktop on a headless Ubuntu computer (no permanent attached monitor or keyboard; I installed the desktop version) on 10.x - but actually nothing has changed since a long time, the gnome bug is still there, so here is this guide, still useful I believe. Thanks to[ [COLOR="Blue"]Steven Harman[/COLOR] ]("http://stevenharman.net/blog/archive/2008/12/13/vnc-to-a-headless-ubuntu-box.aspx") for the main contribution regarding the gnome bug.
This guide: 
[list]Is necessary since starting VNC without being logged in on an interactive session is not so obvious &#8211; whereas it is very much so from a use case perspective. Further we want to use Gnome rather than X11 and there is a nasty bug in Gnome preventing normal keyboard using a VNC session. [/list]
[list]Knows there are possible security issues with VNC, but for a simple home network and quick access this procedure is fine and simple. You can kill the VNC process after you&#8217;ve finished your work too.[/list]
[list]Presumes you have admin rights on your computers as well as possibly (if needed) know how to find ip addresses in your lan and edit ../etc/hosts for your server name(s). [/list]
[list]Does *NOT * address autostart VNC after (re)boot since there are other posts for that and I prefer starting it using PuTTY. A bit safer.
[/list]
_**INSTALLING**_
***On windows*** 
[[COLOR="blue"]Install PuTTY[/COLOR]]("http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html") (Fine on Win7-64ultimate)
Install [[COLOR="blue"]realvnc client[/COLOR]]("http://www.realvnc.com/products/free/4.1/winvncviewer.html") (excellent windows vnc client and free)

***On Ubuntu 10*** (you&#8217;ll need a monitor+keyboard for installing openssh, after that all can be run remotely through PuTTY):
Install openssh and realvnc server:
```
sudo apt-get install openssh-server vnc4server
```
(see [[COLOR="Blue"]community[/COLOR] ]("http://wiki.ubuntu-nl.org/community/Openssh-server")for configuration options)
Set the password (and auto create a .vnc subdir):
```
vncserver 
```
if you want to change the password, type:
```
vncpasswd
```
Create a file (for instance in your home directory) called (for instance) vncstart
```
nano vncstart
```
Enter there:
```
#!/bin/sh
echo resetting keyboard..
gconftool --set /desktop/gnome/peripherals/keyboard/kbd/layouts --type List --list-type String [aa]
echo starting vnc X session..
vncserver -geometry 1280x1024 -depth 24
```

Edit the geometry numbers to make a display to your requirements.
Make it executable:
```
chmod +x vncstart
```

Adapt  xstartup in subdir .vnc 
```
nano .vnc/xstartup
```
remove some lines and add the gnome session, so that xstartup looks like:
```
#!/bin/sh
[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
gnome-session &

```
_**NORMAL OPERATION**_
On windows, start PuTTY and specify your Ubuntu host and connect. 
In the security box accept to continue/allow access.
Log in. then start vnc with:
```
./vncstart
```
Watch for vnc server to issue a **display number. *Remember***.
On windows again, start realvnc; specify host:#, where # is the remembered display numberm enter the password and connect.
The host:display could look like: 
```
UU10server:1
```

If you are done, close the VNC viewer window; if you want to stop the vncserver, in PuTTY, type:
```
(sudo) vncserver &#8211;kill :#
``` 
, where # is the display number. The number is displayed on the top window frame of the running realvnc program.
You can run a number of different remote desktop sessions, differentiated just by their display number.
Enjoy, like me, every day.

---

