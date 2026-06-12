---
title: "wireless script to run at start up"
date: 2009-06-01
forum: Networking &amp; Wireless
---

### Post by searayman on 2009-06-01
So my wireless wasn't working, but with some help from the forums we got ti working, but I have to run commands in terminal every time i boot up to get it to work. So I run:

sudo modprobe -r b43 ssb wl
sudo modprobe wl
sudo ifconfig eth1 up
sudo ifconfig eth1 up

in a little script but when I added that with start up applications it didnt work....

But when i run the script myself it does, which I think may have something to do with sudo because when I run it myself I type in my password, maybe when it starts up in start up applications it doesn't work and I am thinkign this has to do with not putting in my pasword to run the script.

Any help would be great

---

### Post by t0mppa on 2009-06-01
[Here]("http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/") you go.

---

### Post by searayman on 2009-06-01
> **t0mppa said:**
> [Here]("http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/") you go.

so my script is called wireless

if i place it in /etc/init.d/

then i run this command in terminal:

% update-rc.d wireless defaults 

everything should work at start?

---

### Post by t0mppa on 2009-06-01
Aye, that's the idea. Worked perfectly well for me, when I wrote a similar script for the same reasons. Just don't forget the chmod, it needs to be executable.

---

### Post by searayman on 2009-06-01
> **t0mppa said:**
> Aye, that's the idea. Worked perfectly well for me, when I wrote a similar script for the same reasons. Just don't forget the chmod, it needs to be executable.

i made it executabel by righjt clickign it and goign to permissions and checkign off the box for allow to be executable. That shoudl work too right?

---

### Post by searayman on 2009-06-01
ok I just tried it and i got this:

mike@mike-laptop:~$ % update-rc.d wireless defaults 
bash: fg: %: no such job
mike@mike-laptop:~$

---

### Post by t0mppa on 2009-06-01
Ah sorry, don't use a %, seemed natural for me, so didn't catch that one. No idea why it's in the guide anyway. Just start with the plain update-rc.d part.

---

### Post by searayman on 2009-06-01
> **t0mppa said:**
> Ah sorry, don't use a %, seemed natural for me, so didn't catch that one. No idea why it's in the guide anyway. Just start with the plain update-rc.d part.

ok thanks, now I got this:

mike@mike-laptop:~$ update-rc.d wireless defaults 
update-rc.d: warning: /etc/init.d/wireless missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 Adding system startup for /etc/init.d/wireless ...
   /etc/rc0.d/K20wireless -> ../init.d/wireless
update-rc.d: symlink: Permission denied
mike@mike-laptop:~$ 


kind of confused if that means it worked or didnt....

---

### Post by t0mppa on 2009-06-01
Permission denied for creating the symbolic link sounds like it didn't. Try the same command with sudo infront to see if you get nicer result.

---

### Post by kerry_s on 2009-06-01
use /etc/rc.local without the sudo cause it already runs as root

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

ifconfig eth1 down
modprobe -r b43 ssb wl
modprobe wl
ifconfig eth1 up

exit 0

```

---

### Post by searayman on 2009-06-01
> **kerry_s said:**
> use /etc/rc.local without the sudo cause it already runs as root

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

ifconfig eth1 down
modprobe -r b43 ssb wl
modprobe wl
ifconfig eth1 up

exit 0

```

what do you mean by this

---

### Post by kerry_s on 2009-06-01
press **alt+f2**
type> **gksudo gedit /etc/rc.local**
reboot to see if it works.

only if you didn't do that other stuff yet.

---

### Post by t0mppa on 2009-06-02
It's just another way of setting it up. Rc.local is already run at start up, so you don't have to update the system's awareness to it. On the other hand, if you end up writing more scripts in the long run, having them all in a single file can get a bit complicated.

Anyway, these are the two options available for you. Pick either one. The end result is the same with either way.

---

### Post by searayman on 2009-06-02
> **t0mppa said:**
> It's just another way of setting it up. Rc.local is already run at start up, so you don't have to update the system's awareness to it. On the other hand, if you end up writing more scripts in the long run, having them all in a single file can get a bit complicated.

Anyway, these are the two options available for you. Pick either one. The end result is the same with either way.

ok well i did the first one earlier and as you can see from the output i posted earlier it didnt work

---

### Post by t0mppa on 2009-06-02
Permission denied simply means you're trying to do something that requires root access and for that you just need to add sudo in front of the command you were executing to get past it.

Or then do what kerry_s suggested and then you can delete the script file you already created earlier, since the script contents will then go to rc.local.

---

### Post by searayman on 2009-06-02
> **t0mppa said:**
> Permission denied simply means you're trying to do something that requires root access and for that you just need to add sudo in front of the command you were executing to get past it.

Or then do what kerry_s suggested and then you can delete the script file you already created earlier, since the script contents will then go to rc.local.

ok so I feel like an idiot now for not seeing that...I took like 10m onths off from linux as it was not availabel to me in my location. So it worked now:

mike@mike-laptop:~$ sudo update-rc.d wireless defaults 
[sudo] password for mike: 
update-rc.d: warning: /etc/init.d/wireless missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 Adding system startup for /etc/init.d/wireless ...
   /etc/rc0.d/K20wireless -> ../init.d/wireless
   /etc/rc1.d/K20wireless -> ../init.d/wireless
   /etc/rc6.d/K20wireless -> ../init.d/wireless
   /etc/rc2.d/S20wireless -> ../init.d/wireless
   /etc/rc3.d/S20wireless -> ../init.d/wireless
   /etc/rc4.d/S20wireless -> ../init.d/wireless
   /etc/rc5.d/S20wireless -> ../init.d/wireless
mike@mike-laptop:~$ 


Now I just need to test to see if it works!

---

### Post by searayman on 2009-06-02
it worked, thanks for all the help everyone!

---

