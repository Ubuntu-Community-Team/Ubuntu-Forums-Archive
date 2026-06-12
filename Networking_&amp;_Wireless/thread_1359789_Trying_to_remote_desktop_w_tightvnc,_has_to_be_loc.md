---
title: "Trying to remote desktop w/ tightvnc, has to be local?"
date: 2009-12-20
forum: Networking &amp; Wireless
---

### Post by billdotson on 2009-12-20
I installed tightvncserver and have tried to use that as my VNC client. I installed it once while trying to follow some how-to, thought I messed up and then uninstalled it. I re-installed later to try and start over. I started the server and it did not ask for a password the second time. I suppose apt-get remove didn't get rid of config files. Anyway, I can vnc into it using my local IP address (what the other devices on my network can see) but I cannot using my "global" IP. I currently have the DynDns (dynamic dns service) daemon setup therefore my IP is assigned to a certain dyndns username my_name.servegame.org . I tried the DynDns name and just the IP but the VNC client will not connect that way.

I have tried forwarding port 5900 and 5901 (and logging in with those) and neither of my VNC clients will connect that way. They connect almost instantly using the 192.168.x.xx local IP address.

Also, I want to have it set up where the VNC is only usable when the viewing computer is logged in through SSH. I think I have some notes somewhere about how to do it using putty to tunnel VNC through using RSA authentication but that was when I had the VNC working correctly and when I was using Windows programs (I could have conceivable done it with unix programs but the point was to have a portable way to do stuff on my computer at home while I was stuck at school). Now I am not using Windows programs but ones on my Android phone. The VNC viewer programs do work on the device, they just don't want to connect to that global IP (two different VNC programs, I haven't set up the SSH server and tested all that).

Could anyone help? Thanks.

---

### Post by bryonak on 2009-12-20
The standard 'remove' doesn't get rid of config files... this might help ```
sudo aptitude purge PACKAGENAME
```

Can you confirm that your DynDNS setup is working? Does the following allow you to successfully log in? ```
ssh remote_user@remote_server
```



As for the VNC... I'm not sure whether it's exactly what you want, but I wrote a small script that will connect to the specified server via SSH, open a VNC client there and forward the connection to you.
This means that if you have set your remote VNC server to listen only to local, noone but those people with a valid SSH login can connect.
I use vnc4server with this launch command: ```
vnc4server -localhost -geometry 1024x768
```
And this startup config file (~/.vnc/xstartup):
```

#!/bin/sh
[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
fluxbox &

```
Note that you have to install fluxbox for this startup conf ;)

If you have specified "-localhost" with vnc4sever, you can either leave the additional VNC password blank so anyone with a system account on your server can log in... or set a simple one, since the VNC is inaccessible from outside the system.


Now the client script: paste it into a file (I usually call the files vnc.servername), make it executable and link a panel/desktop launcher or keyboard shortcut to it.
You will get a graphical password prompt when launching from a GUI and the usual text prompt when lauching from terminal.
Additionally you can specify the remote VNC display as the first argument when calling the script.

```

#!/bin/bash
# Connects to a (already running) remote VNC server via SSH
# The remote VNC server should preferably listen only to local
#
# Usage: ./this_script
#        ./this_script N
#        (N is the remote display number, usually 1)

VNCCLIENT=vncviewer             # client to connect with
SERVER="XXXX"                   # your remote SSH server
U="$USER"                       # your remote SSH username ($USER == current user)
PORT="22"                       # your remote SSH port
DISP="1"                        # the default display used by the VNC server
OPTIONS="-bgr233"               # very low quality, but quite responsive
PORTFORWARD="-L 5902:localhost:5901"

if [ ! -n "$1" ]; then
  echo "No display set, using :1"
else
  DISP="$1"
fi

ssh -C $PORTFORWARD -p$PORT $U@$SERVER "sleep 1 && $VNCCLIENT $OPTIONS localhost:$DISP"

exit

```

---

