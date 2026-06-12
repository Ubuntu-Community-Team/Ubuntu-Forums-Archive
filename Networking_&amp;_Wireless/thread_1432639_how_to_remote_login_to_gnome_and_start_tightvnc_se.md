---
title: "how to remote login to gnome and start tightvnc server before login"
date: 2010-03-18
forum: Networking &amp; Wireless
---

### Post by alex_linux on 2010-03-18
Hi
Here is my situation.
I would like to remove the monitor from my ubuntu machine, but not until I   can manage it remotely.

Currently I can restart and remotely login via ssh.
The problem is that vnc server does not start until I login....

Is there a way to start vnc via ssh shell? or login to gnome via ssh?
alex@adience:~$ service vncserver start
vncserver: unrecognized service
  
THank You.

---

### Post by jrssystemsnet on 2010-03-18
Add the following to the end of **/etc/rc.local**:

```
su user -c "cd ~user && vncserver -geometry 800x600 :1"
```

Obviously, substitute the actual username for "user" and feel free to specify a different screen resolution.  Also note that the ":1" at the end causes that VNC to run on port 5901, not port 5900.

Finally, be aware that if you have an active GUI session locally, a vnc session as the same user will produce wonky results.  Firefox is one great big honking example of an application that just plain won't work for more than one instance of the same user - if you're running Firefox on the local display, you won't be able to start it from a VNC session.

You might want to consider setting up xrdp to allow you to choose from either controlling a local session (if one exists) or a clean new session (which will be there whether or not a local user is logged in); I've got a cookbook on setting that up here: [http://ubuntuwiki.net/index.php/Xrdp,_installing](http://ubuntuwiki.net/index.php/Xrdp,_installing)

---

### Post by alex_linux on 2010-03-28
Jrs thanks for the reply.
I tried adding that line to rc.local but I did not notice anything different.

I dont know why I can ssh but cannot start up a vncserver after reboot (please note that this is before loging in and starting a session). 

I ended up resolving this as follows:
System-> Administration-> Login Screen
enable autologin

I'll take a look at xrdp as time allows.
 
Cheers.

---

