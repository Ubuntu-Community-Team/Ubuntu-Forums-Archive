---
title: "X11vnc and Logon"
date: 2011-09-20
forum: Networking &amp; Wireless
---

### Post by spambas on 2011-09-20
Hi,

I will try to explain my situation first:

- One server machine with a VNC repeater. (ubuntu 10.10)
- a few clients with x11vnc is repeater mode. (ubuntu 10.10)
- clients are connected through pptp vpn.

I have made a shell script which I put in /etc/ppp/ip-up.d/, because it can only connect to the repeater if the vpn connection is there, and contains one line:
x11vnc -loop -connect repeater=ID:12345678+10.215.0.1:5500 -timeout 600
why these options?
-connect repeater=ID:12345678+192.168.0.1:5500 <-- connect to the repeater with id 12345678
-loop <-- when there has been a viewer-repeater-server connection, the server has to sign in again at the repeater
-timeout 600 <-- every 10 minutes the server signs in again, if there was no viewer connection yet. this is to let the server sign up again if the repeater has been reset. (which you cannot check)

because it is in the ip-up.d folder, it is started by the root user.  when I boot it up to the login screen, it signs up great. every 10 minutes it signs in again. works like a charm. I can connect and disconnect a viewer as many times as I like.

Now I log in with my own user. after the 10 minute timeout the server disconnects from the repeater, as it should, BUT IT NEVER SIGNS IN AGAIN!!! I can see the process in the system monitor. 

I log off again and get back tot the log in screen again. PLING!!! server signing up to the repeater.

How can I resolve this problem. I don't get it...

---

### Post by josephmills on 2011-09-20
what is the pid of the  x11vnc and also of the VNC repeater? I am real new to bash but there has to be a way to say if this prosses is not running then runt x script. but like I said I am real new to bash.

---

### Post by spambas on 2011-09-20
> **josephmills said:**
> what is the pid of the  x11vnc and also of the VNC repeater? I am real new to bash but there has to be a way to say if this process is not running then runt x script. but like I said I am real new to bash.

The repeater is an application which keeps in mind what ip's+id's are connected. this runs on pc1 the x11vnc server runs on pc2, so i can't check if the process is running. btw, both the processes are running, but the server thinks it is still signed up, but the repeater has no record of that. 

But that's not my problem anyway ;) thanks for your reaction though :D

---

### Post by spambas on 2011-09-20
one addition:

I tried to log in as root. now it keeps running :confused:

So, the problem is only occurring when I log in as another user.... :(

---

### Post by josephmills on 2011-09-20
permissions ?

---

### Post by spambas on 2011-09-20
> **josephmills said:**
> permissions ?

that's what I thought, but permissions for what? the script? or permission to use the vpn tunnel? or...

---

### Post by spambas on 2011-09-21
I am a little further on in figuring this out now. I've added the log option to check what is happening.

when running as root It says: 
```
*** XOpenDisplay failed. No -display or DISPLAY.
*** Trying ":0" in 4 seconds.  Press Ctrl-C to abort.
*** 1 2 3 4
*** XOpenDisplay of ":0" succesful.

Using X display 0


```

when logged in as a different user:

```
XOpenDisplay failed. No -display or DISPLAY.
Trying ":0" in 4 seconds.  Press Ctrl-C to abort.
1 2 3 4
No protocol specified

***************************************
*** XOpenDisplay failed (:0)

*** x11vnc was unable to open the X DISPLAY: ":0", it cannot continue.
*** There may be "Xlib:" error messages above with details about the failure.
```

What I get from this is that the X server is down for this session. not sure why.

I've read in the X11vnc FAQ that you can search for the running X display with the -find option. 

problem is, it wont work with the repeater option!

```
wait_for_client: invalid -connect string: repeater=ID:12345678+10.215.0.1:5500
caught signal: 15
```

WHAAA. I'm getting crazy! :confused:

---

