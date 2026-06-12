---
title: "Remote desktop via SSH using krfb - almost there"
date: 2010-08-02
forum: Networking &amp; Wireless
---

### Post by LAD29 on 2010-08-02
Hi all,

I've been trying to work out a way to connect my kubuntu workstation at home into my kubuntu server at the office so I can control the desktop as I've no other way to control it (kubuntu server is installed on hyper-v server and cannot for the life of me get the mouse to work in the virtual environment)

Anyway, I'm trying to use krfb via a SSH tunnel.

I've read various posts, forums and how to guides and am stuck at what looks to be the, or almost the final hurdle.

On my server, my ~/.kde/share/config/krfbr file has the following content:

```
[Invitations]
invitation_num=0

[Notification Messages]
systemtrayquitDesktop Sharing=false

[Security]
allowUninvitedConnections=true
askOnConnect=false
uninvitedConnectionPassword=<SetPasswordHere>
```

I connect to my server via ssh using the following command:

```
ssh -p22 -L10000:xx:xx:xx:xx:5900 username@yy.yy.yy.yy
```

where xx etc is the internal IP address of my server and yy etc is the public address of my router.

The ssh tunnel works fine and I can rummage around the server via command line to my hearts content.

I then fire up another terminal and try:

```
krdc localhost:10000
```

This opens up krdc but immediately tells me that the "VNC server closed the connection." and I just have a blank blue screen instead of the server's desktop.

I feel I'm missing something therefore at the server side which is preventing the VNC connection from establishing.

Can anyone help me finish off my solution?

If I close the krdc session and go back to my terminal window I see the following:

```
_IceTransSocketUNIXConnect: Cannot connect to non-local host kubuntu
_IceTransSocketUNIXConnect: Cannot connect to non-local host kubuntu
Qt: Session management error: Could not open network socket
krdc(19175)/kdeui (kdelibs): Attempt to use QAction "remote_desktop_dockwidget" with KXMLGUIFactory! 
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /home/user/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
```


None of which means anything to a novice such as myself ;)

Cheers.

---

### Post by bettlebrox on 2010-08-02
You could try using NX or FreeNX instead. It runs over SSH and it works very well. See instructions here:

[https://help.ubuntu.com/community/FreeNX#Installing%20the%20FreeNX%20server%20on%20Ubuntu%20Lucid%20%2810.04%29](https://help.ubuntu.com/community/FreeNX#Installing%20the%20FreeNX%20server%20on%20Ubuntu%20Lucid%20%2810.04%29)

---

### Post by LAD29 on 2010-08-03
Hi,

Thanks for the pointer... I'm almost installed but am stuck on trying to install the nxsetup binaries required to complete the install.

How do I download the nxsetup.tar.gz file and then open the tar file from the command line?

I figured wget should do it but what path do I enter to get the file?

Cheers.

---

### Post by ahbart on 2010-08-03
other suggestion:
```
ssh -C -Y -p portnumber user@ip-address
```
This enables you to start application (with gui) like gedit of even sudo synaptic over a compressed connection.

---

### Post by LAD29 on 2010-08-03
> **ahbart said:**
> other suggestion:
```
ssh -C -Y -p portnumber user@ip-address
```
This enables you to start application (with gui) like gedit of even sudo synaptic over a compressed connection.

Hi, thanks for the post.

However, this gives me a remote command line to the server not a gui desktop.

Is that what you meant?

Cheers.

---

### Post by ahbart on 2010-08-03
Well not exactly. Yes it is a commandline. But you can start graphical applications, like gedit, gnome-system-monitor, synaptic, nautilus, etcetera.

---

### Post by LAD29 on 2010-08-03
> **ahbart said:**
> Well not exactly. Yes it is a commandline. But you can start graphical applications, like gedit, gnome-system-monitor, synaptic, nautilus, etcetera.

Thanks, I will make a note of that. Not quite what I need for this problem but will definitely come in handy at some point. :)

---

### Post by ahbart on 2010-08-03
> **LAD29 said:**
> 
```
ssh -p22 -L10000:xx:xx:xx:xx:5900 username@yy.yy.yy.yy
```

Does it make a difference if you put spaces in there?
```
ssh -p 22 -L 10000:xx:xx:xx:xx:5900 username@yy.yy.yy.yy
```
You can also try:
```
ssh -p 22 -L 10000:xx:xx:xx:xx:5900 -N -f -l username yy.yy.yy.yy
```

[source]("http://www.cyberciti.biz/tips/tunneling-vnc-connections-over-ssh-howto.html")

---

### Post by LAD29 on 2010-08-03
> **ahbart said:**
> Does it make a difference if you put spaces in there?
```
ssh -p 22 -L 10000:xx:xx:xx:xx:5900 username@yy.yy.yy.yy
```

No difference, still get the same error in the terminal window as above.


> **ahbart said:**
> You can also try:
```
ssh -p 22 -L 10000:xx:xx:xx:xx:5900 -N -f -l username yy.yy.yy.yy
```

[source]("http://www.cyberciti.biz/tips/tunneling-vnc-connections-over-ssh-howto.html")

This command didn't work at all, just threw up the "usage: ssh...." info afterwards.

Will have a read through the URL you've attached too.

Thanks.

---

### Post by LAD29 on 2010-08-03
> **bettlebrox said:**
> You could try using NX or FreeNX instead. It runs over SSH and it works very well. See instructions here:

[https://help.ubuntu.com/community/FreeNX#Installing%20the%20FreeNX%20server%20on%20Ubuntu%20Lucid%20%2810.04%29](https://help.ubuntu.com/community/FreeNX#Installing%20the%20FreeNX%20server%20on%20Ubuntu%20Lucid%20%2810.04%29)

Installed FreeNX also to try this alternative.  Took a bit of messing to get the nxsetup file in place but a mix of http/ftp and scp got the file in place.  Ran setup and completed the install of the server side.

Downloaded the client and installed that to my local machine.

Configured a connection and tried to connect.  From what I can tell the SSH tunnel establishes and then the attempt to pull up the remote desktop fails.  These are the details from the client:-

```
Info: Proxy running in client mode with pid '1994'.
Session: Starting session at 'Tue Aug  3 11:02:25 2010'.
Info: Connection with remote proxy completed.
Info: Using ADSL link parameters 512/24/1/0.
Info: Using cache parameters 4/4096KB/16384KB/16384KB.
Info: Using pack method 'adaptive-7' with session 'kde'.
Info: Using ZLIB data compression 1/1/32.
Info: Using ZLIB stream compression 4/4.
Info: No suitable cache file found.
Info: Forwarding X11 connections to display ':0.0'.
Info: Listening to font server connections on port '12004'.
Session: Session started at 'Tue Aug  3 11:02:26 2010'.
Session: Terminating session at 'Tue Aug  3 11:02:26 2010'.
Info: Waiting the cleanup timeout to complete.
Warning: Parent process appears to be dead. Exiting watchdog.
```

So...either way I'm attempting to remote desktop it seems I'm getting kicked out at the last hurdle.

---

### Post by LAD29 on 2010-08-03
Just a quick thought, but could the problem be I'm trying to call up a remote desktop and there is currently a desktop running on the server?

Do I need to try to open a different display whilst trying to forward X?

Sorry if this is nonsense, just trying to learn as I read!!

Cheers.

---

### Post by LAD29 on 2010-08-03
Installed NX to a windows client.... looks to be trying.... got a screen pop up with the red !M logo in the middle and it slowly looks to be trying to load the desktop.

---

### Post by ahbart on 2010-08-03
Just guessing. Could it be that X forwarding is disabled?
Check that X11Forwarding is set to yes in /etc/ssh/sshd_config.
Or have a look at this thread: [link]("http://ubuntuforums.org/showthread.php?t=628525")

---

### Post by LAD29 on 2010-08-03
> **ahbart said:**
> Just guessing. Could it be that X forwarding is disabled?
Or have a look at this thread: [link]("http://ubuntuforums.org/showthread.php?t=628525")

Checked my ssh config file, X forwarding looks to be enabled.

Will read through the link.  Cheers.

---

### Post by LAD29 on 2010-08-03
> **ahbart said:**
> You can also try:
```
ssh -p 22 -L 10000:xx:xx:xx:xx:5900 -N -f -l username yy.yy.yy.yy
```

[source]("http://www.cyberciti.biz/tips/tunneling-vnc-connections-over-ssh-howto.html")

Oops....just reread this... I had entered the command incorrect when I tried it before mistakenly putting username**@** in the command.

I've retried this and with a few bits of messing I've got a connection albeit one that is at the moment impossible to work with.... getting somewhere though!!

Thanks ahbart. :)

---

### Post by ahbart on 2010-08-03
Nice for you!

---

### Post by LAD29 on 2010-08-03
ahbart, I was just wondering.

Is there a way to save the command into a shortcut icon or something, save me from having to type the command out in terminal every time I want to make the SSH connection?

Thanks

---

### Post by ahbart on 2010-08-03
yes, of course. You can create a file with the command in it:
```
gedit /home/user/bin/filename
```
Start the file with:
```
#!/bin/bash
```
followed with the commands to execute.
Then:
```
chmod +x /home/user/bin/filename
```
After that you can execute the command by typing:
```
/home/user/bin/filename
```

Anyone else, correct me if I'm wrong here. But this is how I do it. 
You can also create an alias.

---

### Post by LAD29 on 2010-08-03
Many thanks!!

---

### Post by little_penguin on 2010-08-05
The VNC error message you were getting might be due to the VNC server you were using? AFAIK, most VNC servers don't enable you to connect to an existing X display, they create a new session.
 
However, x11vnc is one VNC server I know of that enables you to piggyback onto an existing X session e.g. for desktop sharing and remote access, i.e. enabling you to view and interact with the currently running desktop. 
 
x11vnc server is developed by Karl Runge who has also written the ssvnc viewer (enhanced tightvnc viewer with in-built SSL/SSH encryption). I've successfully used x11vnc before, but haven't tried ssvnc yet, sounds interesting though.
 
More info and the software can be obtained from his website:
 
x11vnc server
[http://www.karlrunge.com/x11vnc/#downloading](http://www.karlrunge.com/x11vnc/#downloading)
 
ssvnc viewer
[http://www.karlrunge.com/x11vnc/ssvnc.html](http://www.karlrunge.com/x11vnc/ssvnc.html)
 
Regards,
LP

---

### Post by LAD29 on 2010-08-05
> **little_penguin said:**
> The VNC error message you were getting might be due to the VNC server you were using? AFAIK, most VNC servers don't enable you to connect to an existing X display, they create a new session.
 
However, x11vnc is one VNC server I know of that enables you to piggyback onto an existing X session e.g. for desktop sharing and remote access, i.e. enabling you to view and interact with the currently running desktop. 
 
x11vnc server is developed by Karl Runge who has also written the ssvnc viewer (enhanced tightvnc viewer with in-built SSL/SSH encryption). I've successfully used x11vnc before, but haven't tried ssvnc yet, sounds interesting though.
 
More info and the software can be obtained from his website:
 
x11vnc server
[http://www.karlrunge.com/x11vnc/#downloading](http://www.karlrunge.com/x11vnc/#downloading)
 
ssvnc viewer
[http://www.karlrunge.com/x11vnc/ssvnc.html](http://www.karlrunge.com/x11vnc/ssvnc.html)
 
Regards,
LP

Hi, thanks for the pointers.  I have x11vnc running (in some sort of fashion at least) on my server.  To be honest, I've now tried that many different ways and methods from various how-to guides etc I wouldn't be surprised if something is messed up somewhere.

One thing I have noticed is that even with success in one way or another the whole experience is so slow and troublesome that it make the solution almost unusable in the end.

The only way I have this actually working so far is by using the NX Client for Windows (Even the NX Client on a linux local machine won't connect through properly) but once connected I can't do anything.

I can RDP into my Windows workstations no problem and the results are very usable, access to the kubuntu server desktop is pretty much an awful experience by comparison.... so far! ;)

---

### Post by little_penguin on 2010-08-05
yeah I know what you mean... VNC is pretty slow, which is a shame. NX is a lot faster. Have you looked into using teamviewer maybe? They have debs for linux and windows on their website, plus it's very easy and fast:

[http://www.teamviewer.com]("http://www.teamviewer.com/")

Regards,
LP

---

### Post by LAD29 on 2010-08-05
Never heard of teamviewer. Thanks for the pointer, I'll check it out.

Yes, it is a shame about VNC on linux.  VNC seems to work fine on my Windows clients across the LAN so I was hoping that would be my solution for remote access to my Kubuntu Desktop.

I will keep plugging away at it and if I have any joy will post my solution.

Cheers all.

---

### Post by krunge on 2010-08-05
> **LAD29 said:**
> 
One thing I have noticed is that even with success in one way or another the whole experience is so slow and troublesome that it make the solution almost unusable in the end.

You may need to supply the "-noxdamage' option to the x11vnc cmdline. This works around a bug in the Xorg server when compositing is enabled.

Also, are you using an SSH port redirection tunnel for the VNC connection? If so, which vncviewer flavor and version are you using (and on which OS)

---

