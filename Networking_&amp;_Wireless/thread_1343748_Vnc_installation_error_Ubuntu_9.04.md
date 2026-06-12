---
title: "Vnc installation error Ubuntu 9.04"
date: 2009-12-02
forum: Networking &amp; Wireless
---

### Post by tapas_mishra on 2009-12-02
I want to set up VNC on my Ubuntu Machine so that I can remotely control it here is what I have done it 
referring to following blog 
[http://www.ubuntu-unleashed.com/2007/10/setup-vnc-server-for-ubuntu-gutsy.html](http://www.ubuntu-unleashed.com/2007/10/setup-vnc-server-for-ubuntu-gutsy.html)
on executing the command 
x11vnc -forever -usepw -httpdir /usr/share/vnc-java/ -httpport 5800
I got following error 

```

root@tapas-laptop:~# x11vnc -forever -usepw -httpdir /usr/share/vnc-java/ -httpport 5800
02/12/2009 16:28:54 passing arg to libvncserver: -httpport
02/12/2009 16:28:54 passing arg to libvncserver: 5800
02/12/2009 16:28:54 -usepw: found /root/.vnc/passwd
02/12/2009 16:28:54 x11vnc version: 0.9.3 lastmod: 2007-09-30
02/12/2009 16:28:54 
02/12/2009 16:28:54 *** XOpenDisplay failed. No -display or DISPLAY.
02/12/2009 16:28:54 *** Trying ":0" in 4 seconds.  Press Ctrl-C to abort.
02/12/2009 16:28:54 *** 1 2 3 4 
No protocol specified
02/12/2009 16:28:58 

02/12/2009 16:28:58 ***************************************
02/12/2009 16:28:58 *** XOpenDisplay failed (:0)

*** x11vnc was unable to open the X DISPLAY: ":0", it cannot continue.
*** There may be "Xlib:" error messages above with details about the failure.

Some tips and guidelines:

 * An X server (the one you wish to view) must be running before x11vnc is
   started: x11vnc does not start the X server.  (however, see the
   recent -create option if that is what you really want).

 * You must use -display <disp>, -OR- set and export your $DISPLAY
   environment variable to refer to the display of the desired X server.
 - Usually the display is simply ":0" (in fact x11vnc uses this if you forget
   to specify it), but in some multi-user situations it could be ":1", ":2",
   or even ":137".  Ask your administrator or a guru if you are having
   difficulty determining what your X DISPLAY is.

 * Next, you need to have sufficient permissions (Xauthority) 
   to connect to the X DISPLAY.   Here are some Tips:

 - Often, you just need to run x11vnc as the user logged into the X session.
   So make sure to be that user when you type x11vnc.
 - Being root is usually not enough because the incorrect MIT-MAGIC-COOKIE
   file will be accessed.  The cookie file contains the secret key that
   allows x11vnc to connect to the desired X DISPLAY.
 - You can explicity indicate which MIT-MAGIC-COOKIE file should be used
   by the -auth option, e.g.:
       x11vnc -auth /home/someuser/.Xauthority -display :0
       x11vnc -auth /tmp/.gdmzndVlR -display :0
   you must have read permission for the auth file.

 - If NO ONE is logged into an X session yet, but there is a greeter login
   program like "gdm", "kdm", "xdm", or "dtlogin" running, you will need
   to find and use the raw display manager MIT-MAGIC-COOKIE file.
   Some examples for various display managers:

     gdm:     -auth /var/gdm/:0.Xauth
     kdm:     -auth /var/lib/kdm/A:0-crWk72
     xdm:     -auth /var/lib/xdm/authdir/authfiles/A:0-XQvaJk
     dtlogin: -auth /var/dt/A:0-UgaaXa

   Only root will have read permission for the file, and so x11vnc must be run
   as root.  The random characters in the filenames will of course change,
   and the directory the cookie file resides in may also be system dependent.
   Sometimes the command "ps wwwaux | grep auth" can reveal the file location.

See also: http://www.karlrunge.com/x11vnc/#faq

```

---

### Post by krunge on 2009-12-02
Which parts of the 'tips and guidelines' in the output did you not understand? 

There needs to be an X server running and you need to have permission (Xauthority file) to attach to it.

---

### Post by tapas_mishra on 2009-12-02
I am not clear what caused this error
```

XOpenDisplay failed. No -display or DISPLAY.
02/12/2009 16:28:54 *** Trying ":0" in 4 seconds.  Press Ctrl-C to abort.
02/12/2009 16:28:54 *** 1 2 3 4 

```

---

### Post by krunge on 2009-12-02
> **tapas_mishra said:**
> I am not clear what caused this error
```

XOpenDisplay failed. No -display or DISPLAY.
02/12/2009 16:28:54 *** Trying ":0" in 4 seconds.  Press Ctrl-C to abort.
02/12/2009 16:28:54 *** 1 2 3 4 

```
It is best to tell x11vnc which X server display you want it to export via VNC.  You can do this by supplying the cmdline argument, e.g. "-display :0" or you can set the environment variable DISPLAY to the display before starting x11vnc.

If you don't tell x11vnc which X server display to use, he guesses you meant display :0  That is what that message is telling you.

I think he likely guessed correctly and you do want to export display :0   so I think your actual problem is you didn't have permission to attach to it. You will need to find the Xauthority file that contains the secret key that will allow you to attach and supply the path to that file in x11vnc's   -auth cmdline argument as the tips point out.

---

### Post by tapas_mishra on 2009-12-02
I am using VNC for the first time I just now noticed when I opened with GUI from a CentOS machine to the client Machine I was able to view everything can you tell me how to do it on command prompt may be everything I installed is correct but I am not clear with it I want to open it via ssh Session.
though I have set a passwd it is not asking me what I want to do is do an ssh to client machine and then use vnc
I have tried vncviewer <IP of server> it worked but without asking for password I want to do this over ssh.

---

### Post by scottuss on 2009-12-02
Are you using Gutsy?

If not, what's wrong with the built in VNC server and viewer?

That guide is old, and not really relevant.

---

### Post by tapas_mishra on 2009-12-02
I am running Jaunty 
Ok I myself do not remember what have I changed I did a lot of things by the time I started the thread and now replying right now my problem is only that 
I have 2 machines A and B 
I want to do an ssh on A from B 
and then on the terminal want to access the display 
while what is working is I do not do an ssh from B to a simply open a command prompt and type vncviewer <IP of A> I am able to see all the desktop I will google on how to set the passwd in mean while but then how to do it over ssh that is what I would like to know.

---

### Post by scottuss on 2009-12-02
If you want to use the in-built VNC server (vino)

Click System > Preferences > Remote Desktop and enable it from there.

Edit: Also, if you just want to run apps etc you could use SSH X Forwarding.

To do that, run ssh as so:

ssh -X yourname@youripaddress

then, in the terminal, any application you start will actually run on the computer you are sshd into.

---

### Post by tapas_mishra on 2009-12-02
```

root@tapas-laptop:~# vncviewer 192.168.1.85
192.168.1.85 5900
Exception in thread "main" java.awt.HeadlessException: 
No X11 DISPLAY variable was set, but this program performed an operation which requires it.
    at java.applet.Applet.<init>(Applet.java:50)
    at vncviewer.<init>(vncviewer.java:29)
    at vncviewer.main(vncviewer.java:40)

```This is what I got right now

I have set the DISPLAY Variable to :0 but then 
it is not accepting any password which I have set 
```

192.168.1.85 5900
java.net.ConnectException: Connection refused
    at java.net.PlainSocketImpl.socketConnect(Native Method)
    at java.net.PlainSocketImpl.doConnect(PlainSocketImpl.java:333)
    at java.net.PlainSocketImpl.connectToAddress(PlainSocketImpl.java:195)
    at java.net.PlainSocketImpl.connect(PlainSocketImpl.java:182)
    at java.net.SocksSocketImpl.connect(SocksSocketImpl.java:366)
    at java.net.Socket.connect(Socket.java:525)
    at java.net.Socket.connect(Socket.java:475)
    at java.net.Socket.<init>(Socket.java:372)
    at java.net.Socket.<init>(Socket.java:186)
    at rfbProto.<init>(rfbProto.java:93)
    at vncviewer.connectAndAuthenticate(vncviewer.java:193)
    at vncviewer.run(vncviewer.java:122)
    at java.lang.Thread.run(Thread.java:619)
java.net.ConnectException: Connection refused

```

---

### Post by tapas_mishra on 2009-12-02
> **scottuss said:**
> If you want to use the in-built VNC server (vino)

Click System > Preferences > Remote Desktop and enable it from there.

Edit: Also, if you just want to run apps etc you could use SSH X Forwarding.

To do that, run ssh as so:

ssh -X yourname@youripaddress

then, in the terminal, any application you start will actually run on the computer you are sshd into.
No I do not want to use both  you said above I am familiar with it I am concerned about doing it over SSH using Remote Desktop on SSH ,let me know if I am not clear.

---

