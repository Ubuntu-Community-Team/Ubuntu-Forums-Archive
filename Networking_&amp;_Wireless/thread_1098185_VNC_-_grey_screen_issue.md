---
title: "VNC - grey screen issue"
date: 2009-03-16
forum: Networking &amp; Wireless
---

### Post by gujumax on 2009-03-16
I have 64-bit Ubuntu server install and then install ubuntu desktop via apt-get.  Then installed vnc4server and started it which gave me this message. Earth is the hostname, logged in as vncuser.
------------------------------------------------------------------
New 'earth:1 (vncuser)' desktop is earth:1

Starting applications specified in /home/vncuser/.vnc/xstartup
Log file is /home/vncuser/.vnc/earth:1.log
------------------------------------------------------------------
After connecting to earth:1 from a client, I get a grey screen with one bash window in white.  

The desktop comes up fine from the console.

Please help.

---

### Post by gujumax on 2009-03-16
I solved the issue by editing /home/vncuser/.vnc/xstart - this is what the file looks like.

#!/bin/sh

# Uncomment the following two lines for normal desktop:
#unset SESSION_MANAGER
#exec /etc/X11/xinit/xinitrc

#[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
#[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
#xsetroot -solid grey
#vncconfig -iconic &
#xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#twm &
gnome-session &

---

