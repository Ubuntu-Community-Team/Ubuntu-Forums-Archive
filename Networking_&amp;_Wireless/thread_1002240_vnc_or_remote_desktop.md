---
title: "vnc or remote desktop"
date: 2008-12-04
forum: Networking &amp; Wireless
---

### Post by v_dragon on 2008-12-04
seems i cant get any solution to work for controlling an xubunutu remotely.
I have installed and setup every vncserver there seem to be in the various threads, even installed Vino - nothing works

i get 'connection reset by peer (104)' on the vnc's
and with Vino i get nothing...no errors just nothing in vncveiwer or a blank screen in remote desktop viewer...

The workstation i am connecting from is Ubuntu 8.04 and the xubuntu is 8.04 ... ideas before i take a hammer to it?
(i'd rahter not have to use Vino and an autologin)

---

### Post by ByteJuggler on 2008-12-04
Are you sure the Xubuntu desktop is starting properly?

Do the following:

1.) Install pacakge "vncserver" on the machine you want to control.  From a terminal, this is:
```
sudo apt-get install vncserver
```

2.) Edit the file ~/.vnc/xinitrc, to contain:
```
#!/bin/sh
exec /usr/bin/xfce4-session

```
To edit the file, enter: 
```
gedit ~/.vnc/xinitrc 
```
Or alternatively browse to the file and right click->Open.

3.) On the machine from which you want to control the other machine, ensure you have an ssh client installed.  For Windows this can be "Putty", it should be installed by default on Ubuntu.

4.) On the machine from which you want to control, make sure you have a VNC client installed.  For Windows this may be "UltraVNC".  There's several clients on linux.

Now, this is how to get a remote GUI session up.  It basically consists of logging in via SSH, then starting the VNC server, then connecting to it with a VNC client:
1.) SSH into the machine you want to remote control with VNC.  Enter:

```
ssh username@remote-machine
```
Enter the password when prompted

2.) Start a VNC Server instance.  Enter:
```
vncserver
```
The computer should print something like:
```
New 'remote-machine:1 (username)' desktop is remote-machine:1
```

3.) Now VNC to the remote machine.  For clients (such as Ultravnc on windows) who require it, remember to include the ":1" in the display address.  

This should work, to bring up a full desktop via VNC.  

Alternatively, why don't you just install [NX from NoMachine]("http://www.nomachine.com/")?  Works a charm.  Install server on the server, install the client on the client, and voila.  Better remote desktop sessions than VNC.

---

### Post by v_dragon on 2008-12-05
"package vncserver is not available, but is referred to by another package"

I did install Vino but when remoting to it i get a blank grey screen ...

i currently have vnc4-server install and configured via several postings i have found in ubuntu forums (lots of postings there by people that also can't get it to work and the thread started in 2006)

Chacking on NX..now!

---

### Post by ByteJuggler on 2008-12-05
> **v_dragon said:**
> "package vncserver is not available, but is referred to by another package"

What version of Ubuntu are you running?  Package "vncserver" is in Universe repo for dapper, feisty and gutsy.  For Hardy and Intrepid there's the package is called "tightvncserver" instead.  Try replacing "tightvncserver" for "vncserver" in the "apt-get install" command.  The rest of the stuff stays the same.  One other thing, you should run

```
vncpasswd 
```

This will set a passwd for connecting to your VNC session. (You only need to do this once, not every time you login and run "vncserver".

---

### Post by v_dragon on 2008-12-05
new DL of Xubuntu 8.04 (Xfce) i tried tight but will try again. nomachine is...complex..but using just the defaults i get 'cant run the gnome-session...' make sure its in PATH and you have rights..the instructions are confising me a bit.

Thanks for your quick responces, i have had no luck elsewhere - i have been using Ubuntu for a yeah or so now but was a windows only user...im still learning

doing what you list i still get:
VNC Viewer Free Edition 4.1.1 for X - built Apr 16 2008 13:02:40
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.

Fri Dec  5 22:45:06 2008
 CConn:       connected to host 192.168.1.12 port 5901

Fri Dec  5 22:45:07 2008
 main:        read: Connection reset by peer (104)

---

### Post by ByteJuggler on 2008-12-06
> **v_dragon said:**
> new DL of Xubuntu 8.04 (Xfce) i tried tight but will try again. nomachine is...complex..but using just the defaults i get 'cant run the gnome-session...' make sure its in PATH and you have rights..the instructions are confising me a bit.

Thanks for your quick responces, i have had no luck elsewhere - i have been using Ubuntu for a yeah or so now but was a windows only user...im still learning

doing what you list i still get:
VNC Viewer Free Edition 4.1.1 for X - built Apr 16 2008 13:02:40
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.

Fri Dec  5 22:45:06 2008
 CConn:       connected to host 192.168.1.12 port 5901

Fri Dec  5 22:45:07 2008
 main:        read: Connection reset by peer (104)

Are you running any firewalls/traffic blockers anywhere?  Connection reset by peer suggests something interfering with your network traffic.  Also, please install a VNC viewer on the server machine you're trying to control, and verify you can connect to a VNC server started from the command prompt like that.  (E.g. open a terminal window, run vncserver, then try to connect with a viewer to that server just started.  You should get another X desktop doing that, and should be able to connect without too much trouble.)

Re Nomachine NX, it should'be really be that complex, basically you should be able to get away like this:

On the server:
1.) Install the client package (right click->Open with GDebi, or enter "sudo dpkg -i nxclient.deb" or whatever from a command prompt.)
2.) Install the node package
3.) Install the server package.
(The order of installing the packages is important.)

On the client:
1.) Install the client package
2.) Run the client, connect to the server.  It should work with defaults.  That's it.

---

### Post by Cool Javelin on 2008-12-15
v_dragon, My personal preference is to use x11vnc rather then any of the VNC derivatives like tightVNC or vino.

x11vnc will show your real desktop (on display 0.) the others create a new desktop (display :1 for example) and they don't get setup with your icons or anything. They don't even get an application bar. I have tried them and having a blank desktop is basically useless.

I am recalling these instructions from memory, so some experimentation may be needed,

In a terminal do: apt-get x11vnc, or use the synaptic package manager.

Once installed, to run the server, I enter the following:

x11vnc  -display :0 -24to32 -usepw -forever

I have made a script called start_x11vnc and the line reads:

/usr/bin/x11vnc  -display :0 -24to32 -usepw -forever

The extra path info is needed because I intend to run this script before logging in and there is no default path at that point.

the -display :0 tells the server to show your desktop, not make a new fresh empty one

My video screen is low res, so I need the -24to32 to get vnc viewers to work.

the -usepw tells it to use the password you previously created for VNC logins. if there is none, it will ask you for one, make it, and won't ask again.

The -forever option tells x11vnc not to quit when the user logs out (this will allow you to log back in later without having to restart the server.)

I hope this helps you.

Now if I could only get this server to startup automatically when I boot the computer, preferably before the login screen appears. 

I am still working on that.

Mark.

---

### Post by RomanIvanov on 2008-12-15
Cool Javelin, cool post, please tell how to set up x11vnc bash file as autorunable before login.

---

### Post by v_dragon on 2008-12-15
thanks all...some of these i have tried but i see a few minor command differences...project is put on side burner for now,,,will retunr to it after the holidays

---

### Post by Cool Javelin on 2008-12-16
RomanIvanov: as soon as I figure it out, you will be the second to know  :)

I will put the keywords "x11vnc before login" you can search for that from time to time.

---

### Post by krunge on 2008-12-16
> **Cool Javelin said:**
> 

My video screen is low res, so I need the -24to32 to get vnc viewers to work.

Really?  Could you post the details?  x11vnc info + xdpyinfo output. Thanks.
> 

Now if I could only get this server to startup automatically when I boot the computer, preferably before the login screen appears. 


See the section marked "Continously" here:

[http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager](http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager)

---

### Post by cirobr on 2008-12-18
> **v_dragon said:**
> seems i cant get any solution to work for controlling an xubunutu remotely.
I have installed and setup every vncserver there seem to be in the various threads, even installed Vino - nothing works

i get 'connection reset by peer (104)' on the vnc's
and with Vino i get nothing...no errors just nothing in vncveiwer or a blank screen in remote desktop viewer...

The workstation i am connecting from is Ubuntu 8.04 and the xubuntu is 8.04 ... ideas before i take a hammer to it?
(i'd rahter not have to use Vino and an autologin)
Try this.

[http://ubuntuforums.org/showthread.php?t=1013499](http://ubuntuforums.org/showthread.php?t=1013499)

---

### Post by v_dragon on 2008-12-19
been there - dont that and it's also not the solutions i want. i need remote control without a user needing to be logged in
 but thanks

---

### Post by ByteJuggler on 2008-12-19
> **v_dragon said:**
> been there - dont that and it's also not the solutions i want. i need remote control without a user needing to be logged in
 but thanks

Well, NX does that - what problems did you say you ran into using NX?  Also, using VNC like I described will allow you to bootstrap a VNC session which does not require a user to be logged into the console of the server.  We just need to work with you to get one of the solutions set up to your satisfaction.

---

### Post by hrod beraht on 2008-12-19
> **v_dragon said:**
> seems i cant get any solution to work for controlling an xubunutu remotely.i need remote control without a user needing to be logged in

What are you actually trying to control/accomplish? Run a program? Do some admin chores on the machine? Move files?
In general, the best way to do anything to a remote computer is to do it through SSH.

Bob

---

### Post by v_dragon on 2008-12-20
> **hrod beraht said:**
> What are you actually trying to control/accomplish? Run a program? Do some admin chores on the machine? Move files?
In general, the best way to do anything to a remote computer is to do it through SSH.

Bob

the remote is my HTPC . i want to operate it remotely, mainly the mp3 player. And while its nice that all kinda of things can be done via comand (you can do that in windows too) there is a reason OS's have gui's
^_^


and as far as NX is concerentd (it works great with my CenOS fileserver) it does the same thing as all the vnc's i have tried - connects fine but will not launch a gui interface

---

### Post by ByteJuggler on 2008-12-20
> 
and as far as NX is concerentd (it works great with my CenOS fileserver) it does the same thing as all the vnc's i have tried - connects fine but will not launch a gui interface

What's the exact error message that you're getting/where is it failing?  On the contrary, **NX is not working fine if it's not launching a GUI interface.**  *The whole point of NX is to give you a remote GUI terminal, *so if you're not getting that then it's not working, by definition.  Did you have any errors/problems installing it?  What exactly did you do when you installed it?  Aside: NX uses SSH so you need to make sure that openssh-server is installed on the server before you install NX.  Don't know if I mentioned this before.  (Test SSH before installing NX by ssh'ing to the server from itself, e.g enter "ssh localhost" from a prompt and make sure you get no errors.)

---

### Post by ByteJuggler on 2008-12-20
> **v_dragon said:**
> And while its nice that all kinda of things can be done via comand (you can do that in windows too) there is a reason OS's have gui's

The pedant in me just needs to point out that on the contrary, Windows by default does not have anyting equivalent to SSH.  While Windows has a local shell command prompt, the point of SSH is that it works a) remotely, and b) over a secure tunnel, and c) can act as a proxy for any other traffic.  You cannot by default open a command prompt to a windows box remotely, not to mention having something that can act as a secure pipe.  (It can be done if the right software and configuration is done of course.)

---

### Post by v_dragon on 2008-12-21
> **ByteJuggler said:**
> What's the exact error message that you're getting/where is it failing?  On the contrary, **NX is not working fine if it's not launching a GUI interface.**  *The whole point of NX is to give you a remote GUI terminal, *so if you're not getting that then it's not working, by definition.  Did you have any errors/problems installing it?  What exactly did you do when you installed it?  Aside: NX uses SSH so you need to make sure that openssh-server is installed on the server before you install NX.  Don't know if I mentioned this before.  (Test SSH before installing NX by ssh'ing to the server from itself, e.g enter "ssh localhost" from a prompt and make sure you get no errors.)

let me clarify - from my Ubuntu workstation i can NX into my CentOS server just fine.

with my Ubuntu workstation i can not NX into the xubuntu workstation - i dont get any errors durring connection, it connects then displays a black screen. with a dialog box saying "Cannot run "gnome-session'. Please, ensure that the requested application is in the system PATH and that you have the appropriate credentials to execute it."  

I can SSH to the machine and do things in command but can't launch a gui

All VNC's i have tried give me the error "read:Connection reset by peer (104)"

SSH localhost works as it should
Thanks for your patience !!!

---

### Post by ByteJuggler on 2008-12-22
> **v_dragon said:**
> with my Ubuntu workstation i can not NX into the xubuntu workstation - i dont get any errors durring connection, it connects then displays a black screen. with a dialog box saying "Cannot run "gnome-session'. Please, ensure that the requested application is in the system PATH and that you have the appropriate credentials to execute it."  


What session type have you chosen for your NX session in your NX client?  If you leave it at the default "Gnome" setting, then of course NX will try to run "gnome-session" which is the program that starts the Gnome desktop.  Now, you don't have Gnome installed (since you've installed Xubuntu), so selecting Gnome in the NX client for the remote session will therefore not work, and can be expected fail with a message such as the above, e.g. "cannot run 'gnome-session'" since of course, gnome-session is not installed!

So in short, you'll have to configure the NX client to run whatever starts your xubuntu desktop (see one of the advanced settings pages on the NX Client to specify the session type.)  I don't offhand know what the command to start the xubuntu desktop is, I'll try to find out and post back exact instructions that will work with NX and Xubuntu.

---

### Post by v_dragon on 2008-12-22
Oooooh...that makes some sense...i tried all the varaitions that NX has and none worked...looking at the configuration files of NX are a bit over my skillset.. I thought Xubuntu used Gnome and xfce ?

---

### Post by ByteJuggler on 2008-12-23
> **v_dragon said:**
> Oooooh...that makes some sense...i tried all the varaitions that NX has and none worked...looking at the configuration files of NX are a bit over my skillset.. I thought Xubuntu used Gnome and xfce ?

1.) No, The Gnome desktop and XFCE desktop are alternatives, they don't work together. (That said, you can run Gnome applications on XFCE through using Gnome libraries, but that's different to running the XFCE desktop so a different matter.)

2.) No editing of config files neccesary, just click the "Configure" button in the NX Client like I mentioned before.  Then see here:
[[IMG]http://img362.imageshack.us/img362/4532/nxclientconfig1lo9.th.png[/IMG]](http://img362.imageshack.us/my.php?image=nxclientconfig1lo9.png)

[[IMG]http://img380.imageshack.us/img380/9441/nxclientconfig2bx7.th.png[/IMG]](http://img380.imageshack.us/my.php?image=nxclientconfig2bx7.png)

Notice a few things: You can specify the desktop session to use, including Gnome, KDE and others.  There's a "Custom" option allowing you to run anything you want (any command you specify.)  Here you specify any application you want to run (so you can in fact run, say, just firefox on the server, and have the window appear on your desktop.  For that you'd want to pick the "Floating Window" option.  In your case however, you want to enter as the command "xfce4-session" (not that surprising given that for Gnome you use "gnome-session"), and you want to tick the "new virtual desktop" option.  Then try to log in, and your virtual desktop should appear.

---

### Post by v_dragon on 2008-12-23
It works!!!!!
Dude...i love you
(^__^)

---

### Post by ByteJuggler on 2008-12-23
> **v_dragon said:**
> It works!!!!!
Dude...i love you
(^__^)

Hey if you want to thank me, please click on the "thanks" ribbon bottom right... :P

---

### Post by war59312 on 2008-12-30
Hi Cool Javelin,

Nice, thanks for the guide. x11vnx working great now.

Just 2 small suggestions, enable solid background color of black and -ncache 10.

[http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-solid](http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-solid)

[http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-ncache](http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-ncache)

Also I had to enable -noxdamage:

[http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-noxdamage](http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-noxdamage)

Without this option it was supper slow, would take seconds before screens would minimize, move, maximize, etc.

Thanks,

Will

---

