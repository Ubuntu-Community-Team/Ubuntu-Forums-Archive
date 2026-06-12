---
title: "Tightvncserver and Remoter VNC"
date: 2012-05-17
forum: Networking &amp; Wireless
---

### Post by albertone74 on 2012-05-17
Hi there,
I have purchased an app for my iPad called Remoter VNC as I would like to connect to my music server (Asus S1-AT5NM10E) which is running Ubuntu 12.04. I have followed these steps:
 
1- I have installed tightvncserver on my server - NO PROBLEM 
2- I have run “vncpasswd” from the terminal to set the vnc password - NO PROBLEM
3- I have run “vncserver &#8243; at the terminal and when I lunch the app on my Ipad I can only see my Ubuntu desktop (as per the attached file) but without icons at all.
Also please find below what I have got in /home/alberto/.vnc/xstartup
 
#!/bin/sh
xrdb $HOME/.Xresources
xsetroot -solid grey
#x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#x-window-manager &
# Fix to make GNOME work
export XKL_XMODMAP_DISABLE=1
/etc/X11/Xsession
 
I really don't understand where the problem is. I have contacted the app developer and he suggested me to ask here in this forum.
I hope you can help me out with this as I am going nuts.
Many thanks in advance for your kind help.
Regards

---

