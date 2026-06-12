---
title: "[SOLVED] HOWTO Configure computers for remote access using VNC and Vinagre"
date: 2008-12-16
forum: Networking &amp; Wireless
---

### Post by cirobr on 2008-12-16
**Introduction**

This article aims to summarize configuration of Ubuntu machines to be remotely accessed. All configurations were successfully tested on both Hardy and Intrepid. VNC (Virtual Network Computing) and its client Vinagre are the core packages.

**Important Note: At the time this article was written, safety features for protection against &#8220;sniffers&#8221; from obtaining unencrypted passwords flowing to remote computers are not covered, as this subject is not fully understood by the author, who commits to resume to that at a later stage. Anyone who is familiar with the topic and wants to cooperate is very welcome.**

Two typical scenarios are depicted, and each configuration is detailed. In all cases, it is assumed there are two computers in use: the local and the remote ones. The remote one is targeted to be accessed, whilst the local one is the enabler for that.

1.&#8220;Help Desk&#8221; type of access: The local user requests access to the remote user, which shall accept the request.
2.&#8220;Administrator&#8221; type of access: The remote machine is accessed by the administrator, who usually has a specific account (user name/password) on that machine. The remote login takes place exactly as if the remote user is in front of the machine. The remote user may even ignore that his computer is being accessed.

**Help Desk access**

The default installation of Hardy and Intrepid, both tested by the author, have, in principle, all the needed packages for the task. All configuration is done through the GNOME interface on the remote system:

Go to System > Preferences > Remote Desktop. The window &#8220;Remote Desktop Preferences&#8221; is opened.

On tab General, check the following boxes:
Allow other users to view your desktop;
Allow other users to control your desktop;
Ask you for confirmation.

(Optional)Leave unchecked the box:
Require the user to enter this password. If checked, the typed password will be requested when opening the remote session.

On tab Advanced, leave unchecked all check boxes under Network and Security. Under Notification Area, check &#8220;Only display an icon when there is someone connected&#8221;.

Restart the computer (preferable) and test connection on the machine you have just configured, by typing the below command on Terminal. A fake remote connection (actually, a local connection) is established and you shall see the standard GNOME welcome screen:
> vinagre localhost:5900

Most likely, port 5900 will work. In general, ports can be 5900 to 5909.

**Administrator access**

The default installation of both Hardy and Intrepid seem not to fulfil all the needs, therefore extra packages (all in Ubuntu repositories) have to be installed on the remote system. Here, both the GNOME and the Terminal interfaces are used:

Go to System > Administration > Login Window:
Remote tab, choose Style as &#8220;Same as Local&#8221; and &#8220;Default&#8221; Welcome Message.

Button &#8220;Configure XDMCP&#8221; will then show up. Click on it.
Window &#8220;XDMCP Login Window Preferences&#8221; will show up. Uncheck &#8220;Honor indirect requests&#8221;. Close all windows.

Open Terminal:

Install the missing packages:
> sudo apt-get install vnc4server xinetd

Edit the Gnome Desktop Manager configuration file:
> sudo gedit /etc/gdm/gdm.conf

Find the below text and uncomment the &#8220;RemoteGreeter&#8221; line. Save and close the file.
```
# The greeter for xdmcp logins, usually you want a less graphically intensive
# greeter here so it's better to leave this with gdmlogin
RemoteGreeter=/usr/lib/gdm/gdmlogin
```

Set the VNC password. It will be required when authenticating the remote connection:
> sudo vncpasswd /root/.vncpasswd

Add VNC service to xinetd. Probably, an empty file is created:
> sudo gedit /etc/xinetd.d/Xvnc

Paste the following lines onto the file. Save it and close it.
```
service Xvnc
{
	type = UNLISTED
	disable = no
	socket_type = stream
	protocol = tcp
	wait = yes
	user = root
	server = /usr/bin/Xvnc
	server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd -extension XFIXES
	port = 5901
}
```

Restart the computer (preferable, rather than just restarting xinetd, VNC) and test connection on the machine you have just installed VNC, by typing the below command on Terminal. A fake remote connection (actually, a local connection) is established and you shall see the standard GNOME welcome screen:
> vinagre localhost:5901

Note that the code on file Xvnc explicitely defines port 5901.


**Establishing remote connection**

**Note: When this article was written, Hardy and Intrepid had different versions of Vinagre installed (respectively 0.5.1 and 2.24.1). There are slight differences between them. The below description considers Hardy.**

On remote computer's GNOME, choose Applications > Internet > Remote Desktop Viewer. The application Vinagre will show up. Click on Connect.

On Host, type the IP address of the machine you want to access remotely. For instance:
192.168.0.100

On Port, accept the default 5900 (or 5901 for Administrator access). If it doesn't work, you can find the correct port (590x) by scanning the open ports of the remote computer (System > Administration > Network Tools, tab Port Scan).

Click Connect, and connection is established.

**References**

[http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/](http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/)

[http://ubuntuforums.org/showthread.php?t=795036](http://ubuntuforums.org/showthread.php?t=795036)

---

### Post by war59312 on 2008-12-26
Looks like guide is missing a step?

> vncviewer localhost:1

VNC Viewer Free Edition 4.1.1 for X - built Apr 16 2008 13:02:40
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.

Fri Dec 26 22:31:58 2008
 CConn:       connected to host localhost port 5901

Fri Dec 26 22:31:59 2008
 main:        read: Connection reset by peer (104)

And you should always use gksudo for running graphical applications as root.

Mainly because of [http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo) .

So gksudo gedit instead of sudo gedit.

---

### Post by cirobr on 2008-12-27
Hello,

Could not understand what you meant by "missing a step", please expand comment. Anyway, this guide considers vinagre, not vncviewer.

Thanks for the tip on gksudo.

---

### Post by enchesss on 2008-12-28
Unable to get remote desktop to work with local host using these instructions and using gksudo as well

error message says connection to localhost:1 was closed

---

### Post by cirobr on 2008-12-28
> **enchesss said:**
> Unable to get remote desktop to work with local host using these instructions and using gksudo as well

error message says connection to localhost:1 was closed

Scan the ports of your remote computer, from that same computer, and post which ones are open. It is expected to see 590x open (x=1 for admin configuration, x=0,2,3,...,9 for help desk).

---

### Post by cirobr on 2008-12-29
> **enchesss said:**
> Unable to get remote desktop to work with local host using these instructions and using gksudo as well

error message says connection to localhost:1 was closed

I've found a mistyping on my original text (already corrected).

Please use one of the following to test connection locally:

> vinagre localhost:5900

or

> vinagre localhost:5901

---

### Post by artm on 2009-01-08
this is the missing step (for me):

> Add VNC service to xinetd. Probably, an empty file is created:

What do you mean by "add a service to xinetd"?



And why should the choice of VNC client matter? Many of us can't use vinagre because it's way too slow, shouldn't the same setup just work with any VNC client?


Oh, and while I'm at it: are you sure we have to uncomment RemoteGreeter in gdm.conf? Don't the comments in that file just show the default values? (See NOTE at the end of long comment at the top of the file).

---

### Post by artm on 2009-01-09
Notes as I go along: 

I've figured out the adding services to xinetd just to decide why should I bother? I simply start vnc server of my choice with gdm (so I don't have to guess the display number). 

A couple of remaining problems for me: 

- I can't switch remote desktops resolution (vnc connection breaks, most often vnc server crashes)

- When I log out from remote desktop X server seems to restart, taking the vnc server with it. Some seconds later I can connect again and see the login screen, but this is very annoying, especially in combination with timed logins (it's a sort of kiosk which logs in as "default user" if no one else logs in within 30 seconds).

Oh. And the remote login part doesn't matter altogether, remote login may be switched off as with vnc you pretend to login "locally".

---

### Post by Steve H on 2009-02-11
> **cirobr said:**
> **Introduction**

This article aims to summarize configuration of Ubuntu machines to be remotely accessed. All configurations were successfully tested on both Hardy and Intrepid. VNC (Virtual Network Computing) and its client Vinagre are the core packages.

**Important Note: At the time this article was written, safety features for protection against “sniffers” from obtaining unencrypted passwords flowing to remote computers are not covered, as this subject is not fully understood by the author, who commits to resume to that at a later stage. Anyone who is familiar with the topic and wants to cooperate is very welcome.**

Two typical scenarios are depicted, and each configuration is detailed. In all cases, it is assumed there are two computers in use: the local and the remote ones. The remote one is targeted to be accessed, whilst the local one is the enabler for that.

1.“Help Desk” type of access: The local user requests access to the remote user, which shall accept the request.
2.“Administrator” type of access: The remote machine is accessed by the administrator, who usually has a specific account (user name/password) on that machine. The remote login takes place exactly as if the remote user is in front of the machine. The remote user may even ignore that his computer is being accessed.

**Help Desk access**

The default installation of Hardy and Intrepid, both tested by the author, have, in principle, all the needed packages for the task. All configuration is done through the GNOME interface on the remote system:

Go to System > Preferences > Remote Desktop. The window “Remote Desktop Preferences” is opened.

On tab General, check the following boxes:
Allow other users to view your desktop;
Allow other users to control your desktop;
Ask you for confirmation.

(Optional)Leave unchecked the box:
Require the user to enter this password. If checked, the typed password will be requested when opening the remote session.

On tab Advanced, leave unchecked all check boxes under Network and Security. Under Notification Area, check “Only display an icon when there is someone connected”.

Restart the computer (preferable) and test connection on the machine you have just configured, by typing the below command on Terminal. A fake remote connection (actually, a local connection) is established and you shall see the standard GNOME welcome screen:


Most likely, port 5900 will work. In general, ports can be 5900 to 5909.

**Administrator access**

The default installation of both Hardy and Intrepid seem not to fulfil all the needs, therefore extra packages (all in Ubuntu repositories) have to be installed on the remote system. Here, both the GNOME and the Terminal interfaces are used:

Go to System > Administration > Login Window:
Remote tab, choose Style as “Same as Local” and “Default” Welcome Message.

Button “Configure XDMCP” will then show up. Click on it.
Window “XDMCP Login Window Preferences” will show up. Uncheck “Honor indirect requests”. Close all windows.

Open Terminal:

Install the missing packages:


Edit the Gnome Desktop Manager configuration file:


Find the below text and uncomment the “RemoteGreeter” line. Save and close the file.
```
# The greeter for xdmcp logins, usually you want a less graphically intensive
# greeter here so it's better to leave this with gdmlogin
RemoteGreeter=/usr/lib/gdm/gdmlogin
```

Set the VNC password. It will be required when authenticating the remote connection:


Add VNC service to xinetd. Probably, an empty file is created:


Paste the following lines onto the file. Save it and close it.
```
service Xvnc
{
	type = UNLISTED
	disable = no
	socket_type = stream
	protocol = tcp
	wait = yes
	user = root
	server = /usr/bin/Xvnc
	server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd -extension XFIXES
	port = 5901
}
```

Restart the computer (preferable, rather than just restarting xinetd, VNC) and test connection on the machine you have just installed VNC, by typing the below command on Terminal. A fake remote connection (actually, a local connection) is established and you shall see the standard GNOME welcome screen:


Note that the code on file Xvnc explicitely defines port 5901.


**Establishing remote connection**

**Note: When this article was written, Hardy and Intrepid had different versions of Vinagre installed (respectively 0.5.1 and 2.24.1). There are slight differences between them. The below description considers Hardy.**

On remote computer's GNOME, choose Applications > Internet > Remote Desktop Viewer. The application Vinagre will show up. Click on Connect.

On Host, type the IP address of the machine you want to access remotely. For instance:
192.168.0.100

On Port, accept the default 5900 (or 5901 for Administrator access). If it doesn't work, you can find the correct port (590x) by scanning the open ports of the remote computer (System > Administration > Network Tools, tab Port Scan).

Click Connect, and connection is established.

**References**

[http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/](http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/)

[http://ubuntuforums.org/showthread.php?t=795036](http://ubuntuforums.org/showthread.php?t=795036)

Perfect, got it all working now.

I don't suppose you know of a web based vinagre viewer?? In case I'm not at work I could then visit the site and still access vinagre as a client.

---

### Post by cirobr on 2009-02-11
No, I'm not aware of such tool.

---

### Post by artm on 2009-02-12
Real VNC  has java vnc viewer: [http://www.realvnc.com/support/javavncviewer.html](http://www.realvnc.com/support/javavncviewer.html) 


> 

The VNC servers also contain a small web server. If you connect to this with a web browser, you can download the Java version of the viewer, and use this to view the server. You can then see your desktop from any Java-capable browser, unless you are using a proxy to connect to the web. The server listens for HTTP connections on port 5800+display number. So to view display 2 on machine ’snoopy’, you would point your web browser at:

[http://snoopy:5802/](http://snoopy:5802/)

The applet will prompt you for your password, and should then display the desktop.



---

### Post by MedellinManDem on 2009-02-20
I've just stumbled across this today. I see a connection between my two computers, but it asks the computer I'm trying to connect to for confirmation, which defeats the object surely, if I won't be able to allow that confirmation because I'm however many miles away!!!

What do I do?

---

### Post by MedellinManDem on 2009-02-20
I think I figured it out...

I simply unchecked the "ask for confirmation" option box in remote desktop and replaced it with use password.

---

### Post by Steve H on 2009-02-20
> **cirobr said:**
> No, I'm not aware of such tool.

You're right, you know. I've wasted quite a while on this only to realise that I didn't really need it.

Thanks for all the help though.

:p

---

### Post by cirobr on 2009-10-06
Hello,

For some reason, the configuration "Administrator" has stopped working: when attempting to connect to the remote computer, one can see the standard gray X window and the big X cursor. After googling around, have found many posts with similar complaints - and no solution.

If anyone knows what happened, is more than welcome to report here.

Thanks,

Ciro.

---

### Post by Aybara on 2010-09-28
Anyone found a solution for the gray window with the X cursor?

---

