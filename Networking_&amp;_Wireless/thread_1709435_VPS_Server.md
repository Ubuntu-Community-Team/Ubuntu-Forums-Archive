---
title: "VPS Server"
date: 2011-03-18
forum: Networking &amp; Wireless
---

### Post by wiggly81 on 2011-03-18
hi all..

I have a VPS Server running ubuntu 10.04 with full root access I connect via SSH, I would like to be able to connect to the desktop using vnc but im not sure on how to install and configure the server well i can install with
```
apt-get install vnc4server
```
but how do i configure it to accept connections and is vnc4server the best available i know it doesn't allow drag and drop and it doesent go full screen maybe some alternate vnc suggestions but i would require info on how to set up any serer so i can access the deskto from my PC

Thanx In Advance

---

### Post by wiggly81 on 2011-03-18
my bad I put in wrong section, 
could a mod move this to Server Platforms please

---

### Post by wiggly81 on 2011-03-18
i have now fixed this..
i will try to explain how incase anyone else wants to know.

fist i logged in to SSH
then i installed gnome
```
sudo apt-get install -–no-install-recommends ubuntu-desktop
```
only need the basic desktop not all the software the goes with it...

then i installed vnc4server xinetd  vncviewer
```
sudo apt-get install vnc4server xinetd  vncviewer
```

then i created a vnc password
```
sudo vncpasswd ~/.vncpasswd
```

then i had to start vnc4server using
```
vnc4server
```

then i edited the xstartup file

```
sudo nano ~/.vnc/xstartup
```

```
#!/bin/sh

# Uncomment the following two lines for normal desktop:
# unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
xterm -geometry 80×24+10+10 -ls -title “$VNCDESKTOP Desktop” &
gnome-session &
```

finally i killed the vnc server
```
sudo killall Xvnc4
```
then started the server again
```
vnc4server
```

from this point on i was able to connect to my VPS using xxx.xxx.xxx.xxx:1 where the x's are the ip address of my server

all works as i wanted..

Hope This Helps anyone that was having this type of problem

---

