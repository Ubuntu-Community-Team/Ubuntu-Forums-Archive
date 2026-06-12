---
title: "Remote Desktop Problems"
date: 2009-06-14
forum: Networking &amp; Wireless
---

### Post by filez41 on 2009-06-14
I'm running ubuntu 9.04, 64-bit.  

I tried to start remote desktop, and I have my router forward port 5900 to my machine, but for some reason when I go to configure remote desktop it gives me this:

Your desktop is only reachable over the local network. Others can access your computer using the address localhost.

When I try to connect to my machine even over the local network it fails.  I also have the router forward port 2200 for ssh, which DOES work, so its not a router problem. 

Ideas?
Thanks in advance.

---

### Post by theozzlives on 2009-06-14
You don't need to forward port 5900, should be able to hit Connect > Find and see the computer you have setup.

---

### Post by gradinaruvasile on 2009-06-14
Connect with 
ssh -X user@ip

and after connected

vncviewer localhost

This will export the vnc stream across the ssh connection.
Make sure u activated remote desktop before.

---

### Post by superprash2003 on 2009-06-14
make sure that the ports are open using this online port scanner [http://www.t1shopper.com/tools/port-scanner/](http://www.t1shopper.com/tools/port-scanner/)

---

### Post by filez41 on 2009-06-14
theozzlives:
it doesnt find any, even though I have turned on remote desktop

gradinaruvasile:
when I ssh in and do that I get this:
~$ vncviewer localhost
Error: Can't open display: 

to turn on remote desktop I went to system:Preferences:remote desktop

and I clicked allow others to view your desktop, allow others to control your desktop, and require users to enter this password

am I forgetting to do something?

---

### Post by gradinaruvasile on 2009-06-14
> **filez41 said:**
> theozzlives:
it doesnt find any, even though I have turned on remote desktop

gradinaruvasile:
when I ssh in and do that I get this:
~$ vncviewer localhost
Error: Can't open display: 

to turn on remote desktop I went to system:Preferences:remote desktop

and I clicked allow others to view your desktop, allow others to control your desktop, and require users to enter this password

am I forgetting to do something?

did u do it with

ssh [COLOR="Red"]-X[/COLOR] name@ip

?

---

### Post by filez41 on 2009-06-14
> did u do it with

ssh -X name@ip

?

oh, I missed that, my apologies. the output is:

~$ vncviewer localhost
vncviewer: ConnectToTcpAddr: connect: Connection refused
Unable to connect to VNC server

---

### Post by gradinaruvasile on 2009-06-14
Go back to the remote desktop tab, make sure the
"You must confirm each access to this machine" is UNchecked
 And the upper 2 options checked.

---

### Post by filez41 on 2009-06-14
> Go back to the remote desktop tab, make sure the
"You must confirm each access to this machine" is UNchecked
And the upper 2 options checked. 

[IMG]http://vmreptiles.com/pictures/Screenshot-Remote%20Desktop%20Preferences.png[/IMG]

---

### Post by gradinaruvasile on 2009-06-14
Yes, like that

---

### Post by gradinaruvasile on 2009-06-14
Read this

[https://bugs.launchpad.net/ubuntu/+source/vino/+bug/369181]("https://bugs.launchpad.net/ubuntu/+source/vino/+bug/369181")

---

### Post by gradinaruvasile on 2009-06-14
Ok, there is another way if this is not working.

sudo apt-get install tightvncserver
tightvncpasswd (if u want to set password)
tightvncserver

you will see a display name computername:number

vncviewer computername:number

when done

killall -9 Xtightvnc

---

### Post by filez41 on 2009-06-14
gradinaruvasile, you have been incredibly helpful, thank you.  I have the tightvncserver working(ish), I can log in, now I have something similar to what's described here:

[http://ubuntuforums.org/archive/index.php/t-36140.html](http://ubuntuforums.org/archive/index.php/t-36140.html)

my ~/.vnc/xstartup looks like this:

#!/bin/sh

# Uncomment the following two lines for normal desktop:
unset SESSION_MANAGER
exec /etc/X11/xinit/xinitrc

gnome-session &

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
twm &


but when I start it and log in as you describe below, I get this screen:

[IMG]http://vmreptiles.com/pictures/screenshot.png[/IMG]

this is a vast improvement, but still not quite right.  Thanks again for your help!

---

