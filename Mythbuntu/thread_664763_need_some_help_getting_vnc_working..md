---
title: "need some help getting vnc working."
date: 2008-01-11
forum: Mythbuntu
---

### Post by onesojourner on 2008-01-11
I have used vnc (read vino) to connect one computer running gnome to another. I am not sure how to set anything up though when running gnome on one computer and mythbuntu on the other. I have enabled vnc in the mythbuntu set up but thats all I have.

---

### Post by murchball on 2008-01-11
Use Terminal Server Client on the ubuntu box to connect to Mythbuntu. You'll need the ip address of the myth box. If it isn't installed, use Synaptic to install tsclient.

---

### Post by onesojourner on 2008-01-26
#!/bin/sh

# Uncomment the following two lines for normal desktop:
# unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
xfce4-panel & xfwm4

I changed the bottom line to look like this and all is going well.

---

