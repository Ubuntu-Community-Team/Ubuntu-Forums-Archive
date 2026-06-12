---
title: "Ubuntu 12.04 LTS - wifi issue"
date: 2013-02-26
forum: Networking &amp; Wireless
---

### Post by Shunmugavel on 2013-02-26
Hi,

I have recently installed ubuntu 12.04 LTS in my laptop. Everything looks cool, i am pretty much happy with it. But i have a minor regarding wifi and wired connection. 

Ubuntu is unable to find the wireless or wired connections which are available. I have searched and found to try with the below command,

```

rfkill list all

```Output of this command doesn't give me any detail about wifi, it states about the bluetooth device only. Can anyone please help me here?

---

### Post by Shunmugavel on 2013-02-26
All,

I have found the solution for the network issue here,

[http://somethingcomputers.blogspot.in/2012/09/fix-for-atheros-ar-8162-for-ubuntu-1204.html](http://somethingcomputers.blogspot.in/2012/09/fix-for-atheros-ar-8162-for-ubuntu-1204.html)

But the problem is, i don't have proper roles to execute the steps mentioned above in the link. Please find the output below,

```

vel@vel-Satellite-C850:~/vel-home/compat-wireless-2012-02-28-p$ 
vel@vel-Satellite-C850:~/vel-home/compat-wireless-2012-02-28-p$ scripts/driver-select alx
bash: scripts/driver-select: Permission denied
vel@vel-Satellite-C850:~/vel-home/compat-wireless-2012-02-28-p$ sudo scripts/driver-select alx
sudo: scripts/driver-select: command not found
vel@vel-Satellite-C850:~/vel-home/compat-wireless-2012-02-28-p$ make
/bin/sh: 1: cannot create /home/vel/vel-home/compat-wireless-2012-02-28-p/.config: Permission denied
make: *** [.compat_autoconf_compat-wireless-2012-02-28-p] Error 2
vel@vel-Satellite-C850:~/vel-home/compat-wireless-2012-02-28-p$ 

```

Please help.

---

### Post by squigish on 2013-02-26
The directions you linked to have a small error.  Adding the ./ in front of scripts/driver-select alx is necessary to tell ubuntu that you want it to execute a command from the current directory, not from the default path.

```
cd compat-wireless-2012-02-28-p
./scripts/driver-select alx 
sudo make 
sudo make install 
sudo modprobe alx
``` 


The first permission denied error was probably because ubuntu didn't know what you meant by scripts/driver-select

The second one was probably because you forgot to run the command as root (using sudo). 

If you ARE running a command as root, and still get a permission denied error, then there's usually something else going on.  In theory, root has permission to do (almost) anything.

---

### Post by Shunmugavel on 2013-02-27
> **squigish said:**
> The directions you linked to have a small error.  Adding the ./ in front of scripts/driver-select alx is necessary to tell ubuntu that you want it to execute a command from the current directory, not from the default path.

```
cd compat-wireless-2012-02-28-p
./scripts/driver-select alx 
sudo make 
sudo make install 
sudo modprobe alx
``` 


The first permission denied error was probably because ubuntu didn't know what you meant by scripts/driver-select

The second one was probably because you forgot to run the command as root (using sudo). 

If you ARE running a command as root, and still get a permission denied error, then there's usually something else going on.  In theory, root has permission to do (almost) anything.
Hi,

I have even installed it using root user, but still wifi is not enabled and not even shown in the hardware list. Please advice.

---

### Post by Shunmugavel on 2013-02-27
Which driver should i download from the below available list?

[http://linuxwireless.org/download/compat-wireless-2.6/](http://linuxwireless.org/download/compat-wireless-2.6/)

---

