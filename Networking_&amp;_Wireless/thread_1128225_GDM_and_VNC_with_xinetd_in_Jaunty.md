---
title: "GDM and VNC with xinetd in Jaunty"
date: 2009-04-17
forum: Networking &amp; Wireless
---

### Post by PhDLinux on 2009-04-17
Something that has worked in 8.04 and 8.10 seems broken in 9.04. It's the combination of xinetd with Xvnc to get a fresh Gnome login window from some remote machine. Does anyone have this working?

xinetd is running well. When I give the command "vncviewer localhost:1" it gives me a fresh window in which the traditional grey background and black X are ready to work. There is just no display manager.

Xnvc is working. When I start a server with "vncserver :2" from the command line instead of asking xinetd to do so automatically, I get a session that the vncviewer can see. Of course, it's a persistent user-specific session, and this is not quite what I want. Last time I had problems getting this combination of services set up (in 8.10), the solution was to add the option "-extension XFIXES" to the Xvnc command line. This option is still in place.

xdmcp is working and gdm is set up right. When I use another machine on the same network to say "X :1 -query <servername>", I get a nice graphical login screen and everything works.

This is Xvnc Free Edition version 4.1.1 with Ubuntu 9.04 beta. I have tried editing the xinetd.d/vnc config file to run the Xvnc command as "root" instead of "nobody". That didn't help. I have tried editing the "-query <hostname>" string in that file to "-query 127.0.0.1". No joy. I have considered using the more primitive XDM to replace GDM, and if somebody can make remote logins work this way I will switch, too. 

My last hope is that this problem originates with a bug that somebody else will fix soon. The file /var/log/Xorg.0.log includes these lines:
```
(II) LoadModule: "vnc"
(II) Loading /usr/lib/xorg/modules/extensions//libvnc.so
dlopen: /usr/lib/xorg/modules/extensions//libvnc.so: undefined symbol: NumCurrentSelections
(EE) Failed to load /usr/lib/xorg/modules/extensions//libvnc.so
(II) UnloadModule: "vnc"
(EE) Failed to load module "vnc" (loader failed, 7)
```
This is for the X server running natively on the server box, but perhaps it is still a problem for Xvnc servers. I don't know. If you do, please comment.

---

### Post by PhDLinux on 2009-04-18
Update (workaround): I can get an XDM login prompt over VNC, so I'm going to use that and move on.

Details: I used the synaptic package manager to install xdm. The package manager asked which display manager to use as the default, and I selected xdm. After installation finished, it was necessary to shut down GDM and start XDM manually using these console commands:
```
$ sudo /etc/init.d/gdm stop
$ sudo /etc/init.d/xdm start
```
(This saved me rebooting; I assume that xdm will load automatically next time I reboot.)

Two XDM configuration files needed editing (before starting XDM) to permit XDMCP access from other machines: /etc/X11/xdm/xdm-config and /etc/X11/xdm/Xaccess.

I still can't explain what was broken. My top suspect is the IPv6 setup on my server. The jaunty install there is a "distribution upgrade" from Hardy via Intrepid, not a clean installation from scratch. It carried forward some old tweaks to disable IPv6. There were problems getting XDM, DMCP, etc., to work well with IPv6 in the recent past. Perhaps these problems still exist, or perhaps my stale config files are incompatible with recent repairs and broke things for me alone. ... Now that I have a working setup, I am not going to risk breaking anything by doing the experiments needed to decide which is which.

I hope this helps somebody. (At the very least, it will help me: Googling for this page will let me devote the few brain cells I have left to remembering other stuff.)

---

### Post by dbaxps on 2009-04-18
I've got same problem with Ubuntu Server RC 9.04 (Ubuntu Desktop installed via tasksel) running as PV DomU at Xen Dom0 for Xvnc Server.
In text only environment ran:-
# apt-get install xdm
responded as you advised and got remote VNC
session connected to box (just one X-terminal).

---

### Post by PhDLinux on 2009-04-19
Congratulations for getting something working. If you want a full gnome session when you log in with xdm, create a file named .xsession containing exactly this one line:
```
/usr/bin/gnome-session
```
(I also got the one-xterm failsafe session when this file was missing or incorrect.) This file belongs in the home directory of the user who logs in with xdm.

---

### Post by dbaxps on 2009-04-19
I was able to start gnome session just typing in X-term
/usr/bin/gnome-session .Creating .xsession didn't help.
It remind me pretty old Debian trick. I'll try it without xdm ;)
Go :-
# apt-get remove xdm
# /etc/init.d/gdm start
Just in case:-
# reboot 
Login as root
# vncserver
Remote vncviewer login to display 1
Start in X-term /usr/bin/gnome-session. It gives Gnome Session
with no problem . Old debian way exactly ;)
I believe been running  xdm with wrong config files. That should be a reason why creating .xsession file ih home folder wouldn't help me.

Adjusting  ~/.vnc/xstartup file to run gnome-session at remote login.

1.First

# Uncomment the following two lines for normal desktop:
# unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
/usr/bin/gnome-session &
# twm &

2.Second

# Uncomment the following two lines for normal desktop:
unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc

/usr/bin/gnome-session &

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
twm &

No xdm manager requiered

---

### Post by dbaxps on 2009-04-19
I've also noticed :-

[http://ipv6-or-no-ipv6.blogspot.com/2009/03/remote-desktop-viewer-vnc-over-ipv6.html](http://ipv6-or-no-ipv6.blogspot.com/2009/03/remote-desktop-viewer-vnc-over-ipv6.html)

However , i didn't support IP6v on the lan. Attempt to build 
vinagre 2.24 on Ubuntu Intrepid failed. It just will take some time
to start work with IP6v due to vinagre appears to be A VNC Client for the GNOME Desktop. Backward compatibility still looks broken.

---

### Post by dbaxps on 2009-04-19
IP6v auto discovery Ubuntu Jaunty PV DomU via remote Ubuntu Intrepid Server on the same LAN :-
[http://bderzhavets.wordpress.com/2009/04/19/setup-vnc-at-ubuntu-jaunty-server-pv-domu-at-xen-34-dom0-kernel-2630-rc1-tip/](http://bderzhavets.wordpress.com/2009/04/19/setup-vnc-at-ubuntu-jaunty-server-pv-domu-at-xen-34-dom0-kernel-2630-rc1-tip/)

---

### Post by dbaxps on 2009-04-21
Activation Remote Desktop access causes vino-server to start up
automatically. As appears it&#8217;s PPID is ID of /usr/bin/gnome-session.

---

### Post by abt on 2009-05-10
Hi,

I appear to be in exactly the same boat as everyone else.  I used to have this working under 8.10 - which I assume was to do with the /edgy package for vnc4server - but I can no longer download edgy packages.  Supposedly, the /edgy package fixed a bug.

There were instructions in a previous post for modifying ~/.vnc/xstartup - but they make no sense to me.  They have two sets of modifications that appear to be to the same file - but they are different (eg. the gnome-session appears in two different places, but only once in 1. and once in 2.).  I'm an intermediate user when it comes to VNC (because it's a PAIN IN THE BUM to set up), but i'm a beginner at most other things :)

If you can help me, I would appreciate it.
Summary of my current situation is,

- My goal is to be able to login to a remote session once my server is powered up
- I can login to a remote session, but only as root.  However, I must first access the server via a regular login, generate a command prompt and issue "vn4cserver :1 -query localost ...." (note: -once and -inetd parameters do not seem to work at the command prompt)
- If I try the "service" method, I get the gray screen with the x-cursor (as other users have described above).

Any help would be appreciated.  This has taken me over 12 hours, which is still better than the 80 hours it took me under 8.04 - the first time :)

Thanks in advance for your help!
ABT

---

### Post by abt on 2009-05-10
> **dbaxps said:**
> I was able to start gnome session just typing in X-term
/usr/bin/gnome-session .Creating .xsession didn't help.
It remind me pretty old Debian trick. I'll try it without xdm ;)
Go :-
# apt-get remove xdm
# /etc/init.d/gdm start
Just in case:-
# reboot 
Login as root
# vncserver
Remote vncviewer login to display 1
Start in X-term /usr/bin/gnome-session. It gives Gnome Session
with no problem . Old debian way exactly ;)
I believe been running  xdm with wrong config files. That should be a reason why creating .xsession file ih home folder wouldn't help me.

Adjusting  ~/.vnc/xstartup file to run gnome-session at remote login.

1.First

# Uncomment the following two lines for normal desktop:
# unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
/usr/bin/gnome-session &
# twm &

2.Second

# Uncomment the following two lines for normal desktop:
unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc

/usr/bin/gnome-session &

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
twm &

No xdm manager requiered
Hi dbaxps,
You have more of an idea of what you're talking about than I do - but you seem to indicate that this post fixes XDCMP login via VNC (if I'm using the right terminology).

I don't understand your instructions about modifying ~/.vnc/xstartup - because it appears to be the same file, but you modify it at two different times in two different ways!?!?!?!?!?!

If you can help shed light on this, I would be grateful!
Thanks in advance

ABT
PS i'm a point and click man - whose only real command-line journey with Ubuntu/Linux in the last 10 years is "remote desktops" in VNC...

---

### Post by PhDLinux on 2009-05-11
The components "GDM" and "with xinetd" are important parts of the thread title and the problem raised in the original post. The procedure recommended by dbaxps drops both these features: all that remains is "VNC". It's nice that this is working, but it does not solve the original problem.

I have long-term relationships with two VNC servers.

(1) At home, I have root access, so my headless Ubuntu server runs xinetd. When I request a session, it gives me a fresh XDM login screen (I couldn't get GDM to work) and I can use it as if my keyboard and mouse were plugged straight into the server. Logging out closes the session. Replacing the pretty GDM with the ugly XDM made logging in a little less impressive for all users on the home network, but at least it works. The command(s) in ~/.xsession get executed by XDM at the beginning of a session.

(2) At work, I am just one of many unprivileged users. There I have no influence over the xinetd daemon, so I had to follow dbaxps's method. I installed the VNC server in one of my personal user directories. When I am sitting at home wanting a remote desktop, step 1 is to start a desktop session by connecting to the office machine by SSH and starting vncserver. (This automatically starts the applications in the work box's ~/.vnc/xstartup.) Step 2 is to logout of the office machine (the VNC server keeps running) and start the VNC client on my home machine, instructing it to connect to the VNC server running at the office. No root access is needed on either box to make this work. The session's connection status is quite different, however. The VNC server and its associated desktop just keep running on the office machine, regardless of whether the home viewer is connected and viewing them or not. This can create interesting situations: if I leave an active OpenOffice session running on the virtual VNC desktop when I go to work and login at my desk, requesting a new OpenOffice session seems to do nothing. But actually the session is simply starting on the virtual desktop instead of the active one. Likewise for firefox. These issues, plus the security concern of leaving an open session going for days at a time, explain my preference for the setup in paragraph (1).

Solving my original problem would allow me to switch back from XDM to GDM in item (1). I hope this little story helps to clarify the similarities and differences between two feasible approaches.

---

### Post by dbaxps on 2009-05-11
You have just 2 options to go. Which one to choose is up to you.

---

### Post by dbaxps on 2009-05-11
[QUOTE=PhDLinux;7255352]The components "GDM" and "with xinetd" are important parts of the thread title and the problem raised in the original post. The procedure recommended by dbaxps drops both these features: all that remains is "VNC". It's nice that this is working, but it does not solve the original problem.

I have long-term relationships with two VNC servers.

(1) At home, I have root access, so my headless Ubuntu server runs xinetd. When I request a session, it gives me a fresh XDM login screen (I couldn't get GDM to work)
9.04
***********************************************************************
Activation Remote Desktop access causes vino-server to start up
automatically. As appears it’s PPID is PID of /usr/bin/gnome-session. Vino-server stop/start via command line :-

gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled false
gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled true

View :-
[http://lxer.com/module/newswire/view/119128/index.html](http://lxer.com/module/newswire/view/119128/index.html)
***********************************************************************

---

### Post by abt on 2009-05-11
Hi,
From my perspective, I'm looking to create a remote gnome desktop session - and i'm not so fussed on how I achieve that goal :)

i've tried the following method,
gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled false
gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled true

and it did nothing for me other than kill my default VNC session :)

My server is called "Ubuntu".  I used to run the local account (aka. default login account) from Ubuntu:5900 and the "remote session" from Ubuntu:5901.  When I issued the "false" command above, I managed to terminate my "local account" VNC session :)

I tried to follow the [http://bderzhavets.wordpress.com/2009/04/19/setup-vnc-at-ubuntu-jaunty-server-pv-domu-at-xen-34-dom0-kernel-2630-rc1-tip/](http://bderzhavets.wordpress.com/2009/04/19/setup-vnc-at-ubuntu-jaunty-server-pv-domu-at-xen-34-dom0-kernel-2630-rc1-tip/) web site, but much of it was not obvious to me.  For example,
1. How to setup the listener on 5901 (aka :1)?
2. Why was this being done inside root account settings (/root/.vnc)?
3. I suspect that the listener on 5901 will require a service meta-data block (eg. /etc/xinetd.d/Xvnc).  What are the settings I need for this meta-data block?

PhDLinux, what does xdm provide you with/not provide you with v/s gdm?  Is xdm basially the "old" user interface that Linux used to have years ago that looks antiquated?

The whole reason I stopped using Windows as the OS for my server is because I couldn't login into a "background session" on the server to perform admin, view RSS logs, etc. without interfering with movies that were playing on the server...

Thanks for the help to date.  Ideas on how to setup this remote gnome desktop are welcome - i'm stuck and am out of options...

Regards,



ABT

---

### Post by lsteffenel on 2009-05-11
Hello, I've found out some clues that can help us.

My configuration is quite basic (remote desktop activated on gnome preferences and the line "/usr/lib/vino/vino-server" on /etc/gdm/Init/Default).

I observed that we have indeed 2 different instances of vino-server (with different configurations).

Instance 1 - this is the vino-server process that runs while I'm logged in. The process runs under the "user" authority, and as a result, I can access (share) my desktop with a vnc client (port 5901).

Instance 2 - When I log out, the vino-server process runs as "root". Not only it gets its properties from another user (the root), but it runs on display :0 (requiring to connect VNC on port 5900). GDM displays well on port 5900, but as soon as I log in, the vino-server process is killed and I lose my connection (as the "user" vino-server starts on port 5901).

I believe that this can easily solved if we are able to run the "logged-out" vino-server process with the same properties and port all the time.  

If you have any idea, I would really appreciate :)

---

### Post by PhDLinux on 2009-05-12
> **abt said:**
> 
PhDLinux, what does xdm provide you with/not provide you with v/s gdm?  Is xdm basially the "old" user interface that Linux used to have years ago that looks antiquated?
I know of three mainstream Display Managers: generic XDM, KDE adapted KDM, and Gnome adapted GDM. These provide the login screen (some with nice pictures and buttons) and handle the authentication required to keep your system secure. After you give your login name and password to the DM, it starts a session. When the session ends (user logs out), the DM takes over management of your machine. The old XDM presents a rather drab grey login window, but it is quite capable of starting a fully-functional modern gnome desktop session. Replacing GDM with XDM costs me a menu on the login screen that lets me select the session type or shut down the machine. I can do both those things with a little command-line magic after logging in, so my only real loss is eye candy. It seems petty to start a whole thread just for that, but I have two reasons: (1) stuff should work--even little stuff; and (2) I'm not far from the front in the battle of linux vs Windows, and in this battle every little advantage is relevant.

---

### Post by billycub on 2009-06-19
I was finally able to get GDM to work over VNC using xinetd.  The culprit *seems* to be that IPv6 is incompatible with GDM.  Through my reading of many many pages, that is actually quite an oversimplification of the problem, but disabling IPv6 solves the problem.

Step by step, here's what I did:

**1) Install xinetd and vnc4server** (sudo apt-get install xinetd vnc4server)

**2) Add xinetd service for Xvnc:**

Create new file /etc/xinetd.d/Xvnc with contents:

```

service Xvnc
{
  socket-type = stream
  protocol = tcp
  wait = no
  user = nobody
  server = /usr/bin/Xvnc
  server_args = -inetd -once -query localhost -SecurityTypes None -geometry 1024x768 -depth 24 -extension XFIXES
  type = UNLISTED
  port = 5900
  disable = no
}

```

Including the "-extension XFIXES" arg was critical; otherwise the VNC window would flash a black screen (briefly) and then quit.

**3) Disable IPv6:**

Create new file /etc/modprobe.d/no-ipv6.conf with contents:
```
alias net-pf-10 off
```

**4) Reboot.**

At least for me, this works.  I also commented out the ipv6 lines at the bottom of /etc/hosts, but I don't know if that's necessary after IPv6 is already disabled.

---

### Post by trusz on 2009-06-30
Been going mad all day trying to get this sorted out.

Billycub, you're awesome :D

---

### Post by d1mag on 2009-07-07
I didn't need to disable IPV6 totally... The main problem was that localhost was looked-up as an ipv6-address in /etc/hosts.
Replacing localhost to 127.0.0.1 in server_args fixed everything for me.
```

  server_args = -inetd -once -query 127.0.0.1 -SecurityTypes None -geometry 1024x768 -depth 24 -extension XFIXES

```

---

### Post by billycub on 2009-07-09
Also note that changing "wait = no" to "wait = yes" in the xinetd script makes VNC always connect to the same session -- which is what I think a lot of people here are actually looking for.

I found that using "wait = yes", and setting the Gnome screensaver to lock screen and require a password on wakeup, was almost entirely equivalent to the experience many admins have with Windows servers.  So, there ya go.

Boy am I glad this is finally working!

---

### Post by Hans Verschoor on 2009-07-13
I'm really fed up to the max with this !!!!!!!!!!!!!!
If I surf the web on this subject I get the feel i'll NEVER be able to install VNC server in my Ubuntu 9.04 server with the configuration that remote users only have to login to their GDM login screen. There are so many pages related to failure that I fear the worst.
I've tried about every suggestion but with no result, that is: "Connection refused" response to the VNC client for the best.
Is it right to say that this whole business is broken in 9.04 ?
Does any one know a real complete and tested scenario to install and configure a VNC server allowing VNC clients to login with their GDM credentials.
And please, refrain from posts like "I got is working under VMware or Cygwin clients", I just want one and simple solution: For a 9.04 server with Gnome X and OS independent VNC clients

---

### Post by smartmeister on 2009-07-13
i just gave up trying to configure that damn vnc4server, this bugger keep reporting "no password configured for vnc auth" while everything is properly set using either

```
sudo vncpasswd /root/.vncpasswd
```and/or
```

vncpasswd /home/$user/.vnc/passwd
```I suppose i'll stick to auto login to get passed the login screen and use a x11vnc script for a while, though if feel thoroughly dissapointed with that security breach

---

### Post by MonkeyCookie on 2009-08-30
> **d1mag said:**
> I didn't need to disable IPV6 totally... The main problem was that localhost was looked-up as an ipv6-address in /etc/hosts.
Replacing localhost to 127.0.0.1 in server_args fixed everything for me.
```

  server_args = -inetd -once -query 127.0.0.1 -SecurityTypes None -geometry 1024x768 -depth 24 -extension XFIXES

```

I found that d1mag's suggestion of changing localhost to 127.0.0.1 in /etc/xinitd.d/Xvnc worked for me.  I was running vnc4server with xinetd in Ubuntu 8.10, and had it working great.  After the upgrade to 9.04, I was just getting the grey screen with the X cursor.  After changing localhost to 127.0.0.1, it is working just as well as it did before the upgrade.

---

### Post by dbaxps on 2009-09-12
> **abt said:**
> Hi dbaxps,
You have more of an idea of what you're talking about than I do - but you seem to indicate that this post fixes XDCMP login via VNC (if I'm using the right terminology).

I don't understand your instructions about modifying ~/.vnc/xstartup - because it appears to be the same file, but you modify it at two different times in two different ways!?!?!?!?!?!


I mean 1 and 2 are two different options. Just one of them have to be
selected.

---

### Post by whittaker007 on 2009-11-28
I can also only manage to get a single shared "remote desktop" type of VNC session running under Karmic. Well that or a black and white X screen with no login. I've tried vncserver, vnc4server, x11vnc, Xvnc, tightvncserver and vino. All I want is to start a virtual desktop session not tied to the current logged-in user's real display, but I can't get one to start. I'm hoping it can be done since it seems to work OK using vncserver on a CetOS box at work...

---

### Post by DolleyFloomia on 2012-07-20
Are you currently a motion picture buff? You love watching movies, not? Now you can do so whilst in the home. It's now a breeze to relish the [watch free movies online](http://www.youtube.com/watch?v=1Gsn6ugFjsE) hottest releases online for the reason that computers and internet has truly revolutionized our everyday living. There are several features of watching movies online when you compare going to a cinema hall or income on a nearby DVD rental store. A great deal of webpages promote that they've free movies, when you enter the site, you must fill a survey or setup an invasive advertisement service on your PC. Fortunately, at this point you do not need to go through it again.   Watch movies online to grab an amusement that's grand in scale, loaded with intensity and alluring rolling around in its charm, but never follow such chancy web usage approaches that can endanger your desires. Web is a vast virtual land that it comes full of limitless possibilities to enjoy online movies. It depends upon our smartness to pick the gems from these opportunities and ignore the luster-less stones. This means having fair familiarity with safe web usage procedures, so that you can have the ability to spot ideal websites to

---

