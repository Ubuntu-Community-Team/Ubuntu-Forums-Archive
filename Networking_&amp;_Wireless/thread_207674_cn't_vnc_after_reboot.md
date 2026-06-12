---
title: "cn't vnc after reboot"
date: 2006-07-02
forum: Networking &amp; Wireless
---

### Post by snake35 on 2006-07-02
new to ubuntu so please bare with me.
when i reboot ubuntu 5.10 remotely i can't vnc directly in, i have to log in first on the machine, is there a way round this

thanks

---

### Post by DA_uf on 2006-07-17
I could swear I used to be able to remote reboot and be able to get in with vnc on a headless machine.

Yet now on Dapper, I see that you must login to a GNOME login session.
[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)
> Warning! Remote Desktop will only work if there's a GNOME login session

I don't remember which VNC server I used, if that matters.

**Workaround 1 (which I do not like):**
1) Have a user automatically login.
System -> Administration -> Login Window
Enter your password.
Click the Security tab.
Check "Enable Automatic Login".
Select the user you want logged in automatically.
Click Close.

2) Lock the display as soon as you can.
System -> Preferences -> Screensaver
I prefer to select the "Blank screen" screensaver.
Set session as idle after: 1 minute (currently the lowest setting available on Dapper).
Check Activate screensaver when session is idle.
Check Lock screen when screensaver is active.
Click Close.

**Workaround 2 (not really VNC):**
Perhaps I was using XLiveCD [http://xlivecd.indiana.edu/](http://xlivecd.indiana.edu/) from MS Windows.
1) Install **openssh-server**
From a Terminal:
sudo apt-get install openssh-server
Or use Synaptic.
2) Grab and burn the XLiveCD.
Remotely launch the X/GNOME/Graphical application from an ssh shell.  The app will display graphically on your local machine, _but not the whole desktop_.
For example: "sudo synaptic"
You will need to know the commands to launch your apps from the command line.

Also, you can setup the remote X forwarding from another Linux box instead of using the XLiveCD.  After all, they are using Cygwin.

**ANYONE:**
Is there a way (on Dapper) to remotely reboot (say with ssh or vnc) and be able to use VNC without having a user automatically login?

---

### Post by 0NeX0 on 2006-07-18
install the vncserver and vncclient on the host machine, here is a link to a document that explains how. once installed you can simply ssh into the host machine start the vncserver then on ur local machine type in the vncviewer host:port let me know if you need any further assitance

[http://abowman.com/2006/07/02/secure-remote-access-with-vnc-and-ssh/](http://abowman.com/2006/07/02/secure-remote-access-with-vnc-and-ssh/)

---

### Post by DA_uf on 2006-07-19
0NeX0,
Which question are you addressing?

From the (local) client machine (the machine running the VNC viewer), can you reboot the (host) server machine (the machine running the VNC server) and then get back into the (host) server machine using the VNC viewer from the (local) client machine (without first logging into a Gnome session on the (host) VNC server machine)?

One of my variations was VNC and SSH:
ssh -L 5900:localhost:5900 yourUsername@remoteAddress
not
ssh -L 1234:localhost:5900 yourUsername@remoteAddress

But I cannot reboot remotely and get back in anymore (although I don't recall if I ever did -- perhaps I was using XLiveCD).

---

### Post by 0NeX0 on 2006-07-19
okay sorry about that i was a little short

this is my method it work i use it becuse i have 23 computers up in they are all live 24/7 and when i have to do a update i usually just ssh but sometimes i need to log in to them VNC so here is my method

ssh into the host like this
ssh -l (username) (ip address or the host name)
type in vncserver
it will give you something like 
root@park:~# vncserver

New 'X' desktop is park:1

Starting applications specified in /etc/X11/Xsession
Log file is /root/.vnc/park:1.log

then go back to the local computer wich is the one you are currently infront of and type in vncviewer park:1

if you need more help please do not hesitate to ask

---

### Post by scxtt on 2006-07-19
0NeX0's method is the same that i use - and really it's the only way that makes sense ... you wouldn't want a x11vnc/vino/VNC server running when no one is logged into the box - there's just no point - connecting to :0, :1, :2, etc. is more of an 'on-demand' service that isn't too sensible to have waiting for connections on (re)boot ...

---

