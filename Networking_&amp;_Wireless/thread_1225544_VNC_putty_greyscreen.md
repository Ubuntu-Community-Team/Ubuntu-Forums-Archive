---
title: "VNC putty greyscreen"
date: 2009-07-28
forum: Networking &amp; Wireless
---

### Post by age99 on 2009-07-28
Hi, I am trying to access my Ubuntu machine remotely through vista using VNC.  

I was able to connect, but I received a window with a grey background and a mouse.  There is no way (or doesn't seem to be) to access anything through it.  

The steps I followed were: 

1. Installed X11vnc and ssh on the server machine.
2. Ran Putty and set it up to connect to the server (This works fine)
3. Set up Putty to forward port 5900
4. Ran x11vnc -usepw -noshm (I tried without '-noshm' but it threw up an error
5. Ran tightvnc and it connected and brought up the grey screen.

Do I need to modify the .vnc/xstartup?

I was trying to use X through Putty but it was very slow to use simple programs like gedit or nedit, or any other visuals.

Thanks

---

### Post by krunge on 2009-07-28
> **age99 said:**
> 
4. Ran x11vnc -usepw -noshm (I tried without '-noshm' but it threw up an error

I suggest getting rid of "-noshm" and adding ```
-display :0
```  I suspect your $DISPLAY was set via SSH X11 redir and so x11vnc was using *that* redirected display instead of the :0 one on the same machine it is running on.

SHM should always work on the local machine (but obviously not  remotely) Did you do X11 redir with putty?

---

### Post by mobilization on 2011-01-14
I was also getting a blank grey screen when I logged in through VNC. 

I got this working by editing the ~/.vnc/xstartup file:

I commented out the 2nd and 3rd lines, then the normal desktop appeared. 

I also changed the Desktop Manger to Gnome in the last line. 

Then I restarted vncserver and was able to login and see a working Gnome Desktop. 

Here is my working ~/.vnc/xstartup file:

```
#!/bin/sh

# Uncomment the following two lines for normal desktop:
# unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[B]#Comment out the next 2 lines if you see a grey screen when 
#logging in via VNC
[COLOR="rgb(153, 50, 204)"][COLOR="rgb(153, 50, 204)"]##[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
##xsetroot -solid grey[/COLOR][/COLOR][/B]
vncconfig -iconic &
xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
[COLOR="DarkOrchid"]**gnome-session &**[/COLOR]
```

---

### Post by mobilization on 2011-01-14
I was also getting a blank grey screen when I logged in through VNC. 

I got this working by editing the ~/.vnc/xstartup file:

I commented out the 2nd and 3rd lines, then the normal desktop appeared. 

I also changed the Desktop Manger to Gnome in the last line. 

Then I restarted vncserver and was able to login and see a working Gnome Desktop. 

Here is my working ~/.vnc/xstartup file:

```
#!/bin/sh

# Uncomment the following two lines for normal desktop:
# unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[B]#Comment out the next 2 lines if you see a grey screen when 
#logging in via VNC
[COLOR="Purple"]##[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
##xsetroot -solid grey[/COLOR][/B]
vncconfig -iconic &
xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
[COLOR="DarkOrchid"]**gnome-session &**[/COLOR]
```

---

