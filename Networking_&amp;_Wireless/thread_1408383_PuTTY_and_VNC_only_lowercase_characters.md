---
title: "PuTTY and VNC only lowercase characters"
date: 2010-02-16
forum: Networking &amp; Wireless
---

### Post by fboecom on 2010-02-16
[FONT="Arial"]I have constructed a monitor-less ubuntu 9.10 machine for file serving purposes and it works well. It boots nicely, without mouse or keyboard or monitor. 
One requirement is to manage it remotely and have the the VNC capability after a (re-)boot.

So I installed PuTTY on my windows machine and vnc4server, openssh and x11vnc on the ubuntu box. 
To my regret I could not connect RealVNC to the ubuntu machine that has no(t yet) phyiscally a user logged on. 
I found that I *could *connect to the Ubuntu box with PuTTY over SSH, login, and then enter in the PuTTY window:[/FONT]

[FONT="Courier New"]vncserver :1 -geometry 1024x768 -depth 16[/FONT]

[FONT="Arial"]and then:[/FONT]

[FONT="Courier New"]x11vnc -display :1[/FONT]

[FONT="Arial"]RealVNC on the windows box can then connect to the ubuntu box allright.
So far so good. Here comes the strange thing.

When I type in characters, I cannot get uppercase characters to the ubuntu box through VNC (Real /TightVNC no difference).

However the PuTTY window can use uppercase!

And if I don't use PuTTY, hook up a monitor+keyboard on the ubuntu box, reboot, login, then I get the uppercase through VNC OK.

What is the catch?[/FONT]

---

### Post by krunge on 2010-02-16
There is no need to use x11vnc in the setup you describe.  You can connect to vncserver directly.

I.e. you are doing this (I'm not drawing the ssh tunnel aspect):
```
**vncviewer** <--VNC-protocol--> **x11vnc** <--X11-protocol--> **vncserver**
```
but you might was well connect directly:
```
**vncviewer** <--VNC-protocol--> **vncserver**
```
Try that and see if it changes the keyboard behavior.

Also, if all of this is going over your home LAN, you might want to skip the Putty/SSH entirely (to see if it makes a difference if nothing else.)

---

### Post by fboecom on 2010-02-16
[FONT="Arial"]Thanks. OK I understand the duplication with x11vnc. But for some reason it was the only way I got VNC working when not logged on to the ubuntu box after a boot. Without x11vnc the vncviewer would return 'connection refused'.
Thus the VNCviewer - vnc protocol - vncserver works, no problem, but can only be established after I log in to ubuntu. For that I need to hook up a keyboard and monitor and that is what I dont want to do.
The only option I see now is to get ubuntu started with a monitor and keyboard, log in, pull the cables out and then "never" shut it down.[/FONT]

---

### Post by krunge on 2010-02-16
Note that for your setup vncserver listens on TCP port 5901 and x11vnc listens on port 5900. Which port are you directing your vncviewer to?  I.e. tell me what SSH port redirections you have set up and what you tell your vncviewer to connect to. I believe you are simply connecting to the wrong port.

Regarding having a desktop available after reboot you have several options:

1) make (for your user) a crontab entry like: "@reboot vncserver :1"

2) it is also possible to start vncserver on demand from inetd/xinetd, search   these forums for ideas.

3) set up auto login (as your user) and put x11vnc in the 'Startup Commands'

4) to attach x11vnc to the desktop login greeter, look here:

[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager](http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager)[/INDENT]

---

### Post by fboecom on 2010-02-17
[FONT="Arial"]thanks for your multiple suggestions. In the PuTTY config for SSH I see it indeed tunnels to/throug port 5900. For VNCserver I believe you immediately, but I can't see what port realvnc or vncserver uses, that must be standard after installation. Putty/SSH's 5900 was as well.

The fact that I used vncserver AND x11 was just trial and error and it seemed to work - not completely as it turned out. Since my only desire is to have vncserver running AND the vncviewer itself works well, I might as well take your advice to search&configure the boot-start for vncserver and leave the whole lowercase issue (which imho still exists) alone.[/FONT]

---

### Post by krunge on 2010-02-17
'vncserver :1' listens on port 5901, 'vncserver :2' listens on 5902, etc.

The command:
```
netstat -antp
```
is useful in seeing which ports are being listened on and by which program (note: for the wrapper script 'vncserver' the program will actually be Xvnc.) Also, the command "lsof -p <PID>" is also useful for a specific process ID you substitute for <PID>

Not sure what could be causing your keyboard problem. Once you get to normal usage maybe things will be clearer.

---

### Post by fboecom on 2010-02-28
[FONT="Arial"]In the meantime I have found what I needed, I can now open a ssh terminal with putty and then kick off the vncserver. Solution found using the search 'headless server'.

[http://stevenharman.net/blog/archive/2008/12/13/vnc-to-a-headless-ubuntu-box.aspx]("http://stevenharman.net/blog/archive/2008/12/13/vnc-to-a-headless-ubuntu-box.aspx")
and also documented it at:
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1297815&page=2]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1297815&page=2")
the key is to add
 
[FONT="Courier New"]gnome-session &[/FONT]

to the .xstartup file in ~/.vnc
and then, which I already used:

[FONT="Courier New"]vncserver –geometry 1024x768 –depth 24[/FONT]

and finally to **add :1 to the vncviewer hostname**.
(1 or another number, the same that vncserer would return).

I already thought it would be simple, it indeed was.
Strange that this solution is not so obvious in neither documentation nor forums.
Hope this will work for someone else (On Karmac) too.

Thanks for your support anyway.
[/FONT]

---

### Post by fboecom on 2010-02-28
[FONT="Arial"]Wow! I seem to have gotten from bad to worse.. !
Now in VNC it's not only just lowercase, the whole keyboard seems scrambled ... and it seems to be a known (but old?) problem.
Seems to be generated by gnome.
[http://blog.yclian.com/2007/12/3-solutions-to-gnomevnc-keyboard.html](http://blog.yclian.com/2007/12/3-solutions-to-gnomevnc-keyboard.html)
Need to research further before we have a real solutions for a normal problem..
[/FONT]

---

### Post by fboecom on 2010-03-01
[FONT="Arial"]Now the final solution (s):
1. **vnc solution** from
[COLOR="Blue"][http://blog.yclian.com/2007/12/3-solutions-to-gnomevnc-keyboard.html](http://blog.yclian.com/2007/12/3-solutions-to-gnomevnc-keyboard.html)[/COLOR]
Wolfgang Schnerring said...

I have created a file called **vncstart **in my home directory. It contains:

[FONT="Courier New"]#!/bin/sh
echo resetting keyboard..
gconftool --set /desktop/gnome/peripherals/keyboard/kbd/layouts --type List --list-type String [aa]
echo starting vnc X session
vncserver -geometry 1024x768 -depth 24[/FONT]

then 
[FONT="Courier New"]chmod +x vncstart[/FONT] 

and the next time in putty issue:

[FONT="Courier New"]./vncstart[/FONT]

then in the vncviewer access the x server number (eg: via-c7-uu:1) and we are all set.
dammit for the time needed.

2. **install FreeNX**, a better solution and forget all about VNC.[/FONT]

---

