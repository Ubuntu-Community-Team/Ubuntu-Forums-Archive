---
title: "running xterm via cygwin/X - connect /tmp/.X11-unix/X0: No such file or directory"
date: 2011-03-08
forum: Networking &amp; Wireless
---

### Post by andrea_bio on 2011-03-08
Hi
 
I am trying to connect to a linux Ubuntu 10.04 virtual machine on a remote server via Cygwin/X from windows XP
 
I can login to the machine using this command
$ ssh -Y -p xxx [EMAIL="andrea@heater.cs.man.ac.uk"]machine_name[/EMAIL]
 
I then try and start xterm but get this error
 
connect /tmp/.X11-unix/X0: No such file or directory
 
The file does exist and is owned by root so i changed to root and got this error
 
[EMAIL="root@andrea-vm:/tmp/.X11-unix"]root@andrea-vm:/tmp/.X11-unix[/EMAIL]# Warning: This program is an suid-root program or
is being run by the root user.
The full text of the error or warning message cannot be safely formatted
in this environment. You may get a more descriptive message by running the
program as a non-root user or by removing the suid bit on the executable.
xterm Xt error: Can't open display: %s
 
[EMAIL="andrea@andrea-vm:~$"]In[/EMAIL] case it helps:
echo $DISPLAY
localhost:11.0

 ps -ef| grep X
root     27074 27072  0 Feb11 tty8     00:00:42 /usr/bin/X :0 -br -verbose -auth
 /var/run/gdm/auth-for-gdm-ghIikC/database -nolisten tcp

Please note i am a beginner
 
thanks

---

