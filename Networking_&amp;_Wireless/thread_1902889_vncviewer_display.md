---
title: "vncviewer display"
date: 2012-01-01
forum: Networking &amp; Wireless
---

### Post by liquid_legs on 2012-01-01
hey peoples

i have just set up learnt how to setup an ssh server correctly, i have also setup a vnc server but when i want to connect to a remote computer using vncviewer in the terminal it comes up with an error message saying "cant open display"

---

### Post by 2F4U on 2012-01-01
Are you starting vncviewer over a ssh tunnel and is the vncserver on the other machine properly configured and working?

---

### Post by liquid_legs on 2012-01-01
yes im running on it an ssh tunnel, the vncserver is working and im pretty sure its properly configured.
i was also wondering if its possible to only connect to computers over a lan and not the internet

---

### Post by liquid_legs on 2012-01-01
ok nope its, not configured properly or running, i thought i was.

i know this when i had read through this page
[https://help.ubuntu.com/community/VNC/Servers](https://help.ubuntu.com/community/VNC/Servers)

im using tight vnc and it tells me that if the servers not running i might need to uncomment the $fontpath lines in /etc/vnc.conf.

but the problem is with this, is that i cant find config file anywhere. it seems that a vnc.conf dosent exitst.
i found this startup script for vnc in the .vnc folder in the home folder but im not sure if this is what im looking for or is the reason why its not working.

#!/bin/sh

xrdb $HOME/.Xresources
xsetroot -solid grey
#x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#x-window-manager &
# Fix to make GNOME work
export XKL_XMODMAP_DISABLE=1
/etc/X11/Xsession

---

### Post by liquid_legs on 2012-01-01
ok no, i figured out the problem but sadly vncviewer still cant open display.

---

### Post by liquid_legs on 2012-01-01
hmm ok i seem to have figured out how to get the vncviewer to show display. hmm mabey i should try and figure out the problem my self in a bit more detail beofre asking the question cause as you people can most the questions i have asked ive just answerd my self

but one more question. i was succesfully able to connect to myself but if i want to connect to another remote computer does the ssh and vnc server have to be running on it

---

