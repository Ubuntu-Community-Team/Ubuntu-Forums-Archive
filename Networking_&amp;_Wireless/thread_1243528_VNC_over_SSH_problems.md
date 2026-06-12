---
title: "VNC over SSH problems"
date: 2009-08-18
forum: Networking &amp; Wireless
---

### Post by RyanGT on 2009-08-18
I am trying to run VNC over SSH according to this 
[https://help.ubuntu.com/community/VNC?action=show&redirect=VNCOverSSH](https://help.ubuntu.com/community/VNC?action=show&redirect=VNCOverSSH)

but I am running into problems.  It seems like x11vnc or other programs are already using port 5900 so I get error messages like this when I try to ssh in with port forwarding on 5900:

ryan|11:31 AM|~$ ssh -L 5900:localhost:5901 192.168.1.107
bind: Address already in use
channel_setup_fwd_listener: cannot listen to port: 5900
Could not request local forwarding.

Port forwarding of a different port works:
ssh -L 5903:localhost:5903 192.168.1.107

but then I couldn't connect to the desktop:
x11vnc -safer -localhost -nopw -once -auth /var/lib/gdm/:0.Xauth -display :3 &
results in a long message that includes
*** x11vnc was unable to open the X DISPLAY: ":3", it cannot continue.

On the client side, vino-server is running on 5900, but I can't seem to kill it:
ryan|11:48 AM|scripts$ netstat -tap|grep LISTEN
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
tcp        0      0 *:swat                  *:*                     LISTEN      -               
tcp        0      0 *:git                   *:*                     LISTEN      -               
tcp        0      0 *:http-alt              *:*                     LISTEN      -               
tcp        0      0 *:ssh                   *:*                     LISTEN      -               
tcp        0      0 localhost:ipp           *:*                     LISTEN      -               
tcp        0      0 *:3128                  *:*                     LISTEN      -               
tcp        0      0 *:smtp                  *:*                     LISTEN      -               
tcp6       0      0 [::]:git                [::]:*                  LISTEN      -               
tcp6       0      0 [::]:netbios-ssn        [::]:*                  LISTEN      -               
tcp6       0      0 [::]:5900               [::]:*                  LISTEN      5883/vino-server
tcp6       0      0 [::]:www                [::]:*                  LISTEN      -               
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN      -               
tcp6       0      0 [::]:microsoft-ds       [::]:*                  LISTEN      -             

What do I need to do to get this working?

Thanks,

Ryan

---

### Post by RyanGT on 2009-08-18
I think I solved this.  Turning off vino on my client solved the problem of not being able to use 5900 (I would still like to know how to use a different port with vnc).  I ran the command
vino-preferences
and unchecked the box "Allow others to view your desktop".  This freed port 5900 on the client.

I am now using this script to connect:

#!/bin/sh

ssh 192.168.1.107 -f -L 5900:localhost:5900\
        x11vnc -safer -localhost -nopw -once -auth /var/lib/gdm/:0.Xauth -display :0 \
        && sleep 5 \
        && vncviewer localhost:0




Ryan

---

### Post by superprash2003 on 2009-08-18
wow.. that was quick!!:)

---

### Post by issih on 2009-08-18
Ok...

First of all, you have a few separate things going on.

1) at your end (the client end) you had a program using port 5900, hence using that port as the end point for your ssh tunnel didn't work, that is obviously why turning off the offending program allows it to work.

To work around it you can just set up the tunnel differently.

```
ssh 192.168.1.107 -f -L 5903:localhost:5900\
```

That tunnel should forward port 5900 on the server to 5903 on the local computer (hence avoiding the local conflict), you then run vncviewer connecting to port 5903 (i.e. vncdisplay :3) on the local computer and things should work.

Alternatively, you can set up the server to use a different port entirely (i.e. to use 5903 rather than 5900 at the server end). In your attempt to do this you used entirely the wrong option, the -display option is used to grab the X11 display you want to view remotely, not to select the vncport you want to use. You probably don't have 3 X displays on the remote server, and that is why it didn't execute at all. I think you need to use the -rfbport option to do that, but I'm not 100% sure.

Assuming you make that work, an ssh tunnel with 5903:localhost:5903 would be correct, or indeed whatever number you want locally (the first 59xx) provided it doesn't clash with local services, the remote port obviously must match the one you choose for the vncserver to run on.

Hope that helps

---

