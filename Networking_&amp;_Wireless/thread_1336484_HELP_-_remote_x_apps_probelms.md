---
title: "HELP - remote x apps probelms"
date: 2009-11-24
forum: Networking &amp; Wireless
---

### Post by BarryDocks on 2009-11-24
Please help, pulling my hair out with this and haven't got much left!

I am trying to start an application running on my server as root user and display the window on my local laptop.

Server IP address is 135.120.135.1
laptop IP address is 135.120.135.8

On the server I have changed sshd_config:
```
X11Forwarding yes
X11DisplayOffset 10

```

on the laptop client I have changed ssh_config:
```
ForwardX11 yes
```
And 
```
$ xhost 135.120.135.1
135.120.135.1 being added to access control list
$ echo $DISPLAY
:0.0
```



I have set up ssh and can easily run the application as a normal user by using:
```
$ssh -X user@135.120.135.1 gedit
```
But this does not give root privileges.

I have ssh'ed into the server and changed to root, then I have tried:
```
~# export DISPLAY=135.120.135.8:0.0
~# echo $DISPLAY
135.120.135.8:0.0
```

But get this when I try to run the app:
```
~# gedit
Error: cannot open display: 135.120.135.8:0.0
```

Any suggestions welcome??!!

Thanks in advance

---

### Post by scorp123 on 2009-11-24
How exactly did you change to root?

And what happens if you try e.g.
```
ssh -X user@remote-server "/usr/bin/gksudo /usr/bin/xterm"
``` (BTW I'm using the default SSH configuration without having changed anything ... so I know that this will work with the default config)

Besides: I'd strongly recommend **[COLOR="Red"]NOT[/COLOR]** to work as root. It's very easy to hose your system if you don't know what you're doing.

.
.
.
.

---

### Post by BarryDocks on 2009-11-25
> **scorp123 said:**
> How exactly did you change to root?

And what happens if you try e.g.
```
ssh -X user@remote-server "/usr/bin/gksudo /usr/bin/xterm"
``` (BTW I'm using the default SSH configuration without having changed anything ... so I know that this will work with the default config)

Works a treat, thanks.  Could you explain how it works?

> 
ThanksBesides: I'd strongly recommend **[COLOR="Red"]NOT[/COLOR]** to work as root. It's very easy to hose your system if you don't know what you're doing.
I realise this, the application I want to start is firestarter GUI for this you must be root!

---

### Post by scorp123 on 2009-11-25
> **BarryDocks said:**
> Works a treat, thanks.  Could you explain how it works? There is not much to explain. "ssh -X" enables X11-forwarding. But you know that already. So whatever X11 program you execute will be returned back to your SSH client's screen. ```
ssh -X user@remote-host xterm
```

So far so good. So we can specify ***any*** GUI program and it will come back to your screen. 

So what's stopping us from getting the graphical ***sudo*** admin-password dialogue displayed on your screen? Nothing. 

And so that's precisely what the **"gksudo"** command does. It's a ***graphical*** variation of **"sudo"** ... That word is important: ***"graphical"***. So different than **"sudo"** (which does a great job for terminal commands) **"gksudo"** will handle the X11 environment correctly and thus also automatically know to which ***$DISPLAY*** it is required to go to and forward that information to whatever application you start. So by using **"ssh -X"** and **"gksudo"** and by telling it what command to start afterwards ... you will get graphical "root" programs displayed on your screen.

BTW, **"gksudo"** is also what you execute everytime when you locally click on a menu item that requires "root" priviledges. 

It's all very easy and works out of the box if you understand how the involved mechanisms work. :D

---

### Post by BarryDocks on 2009-11-25
thank you for taking the time to explain this!

---

