---
title: "lirc broken"
date: 2009-02-05
forum: Multimedia Software
---

### Post by Kissell on 2009-02-05
I'm running Ubuntu 8.10 and I had a windows media center remote working with it just fine using lirc so I could control boxee.

Then something broke it, I believe it was a kernel update.  in any case, its not working now.

my kernel is currently "2.6.27-11-generic"

I've tried running the old kernels at the grub boot menu, and that was no help.  I've also tried "apt-get purge lirc" and trying to completely remove it and reinstall it...  but no matter what I do, I can't get lirc to run anymore.

> 
root@server:/etc/init.d# ./lirc start -v
 * Loading LIRC modules                                                  [ OK ] 
 * Unable to load LIRC kernel modules. Verify your
 * selected kernel modules in /etc/lirc/hardware.conf


---

### Post by NT4usB on 2009-02-05
Did you try:
```
dpkg-reconfigure lirc
```
before you uninstalled?
May be needing the kernel source for the new kernel to recompile.
Just guessing on all this. When I was running lirc on Dapper, it **always** needs to be recompiled after a kernel upgrade...
Haven't managed to break lirc since upgrading.

---

### Post by Kissell on 2009-02-05
No luck, when I try to do the reconfigure it says this:

> 
root@server:~# dpkg-reconfigure lirc
 * Stopping remote control daemon(s): LIRC                               [ OK ] 
 * Reloading kernel event manager...                                     [ OK ] 
 * Loading LIRC modules                                                  [ OK ] 
 * Starting remote control daemon(s) : LIRC                              [fail] 


---

### Post by warp99 on 2009-02-05
Go into /etc/lirc and diff the current *.conf files against the dpkg-dist *.conf files. I had a similar problem recently with my Mythbuntu server and the lirc daemon failing until I used the dpkg-dist *.conf files then reconfigured the remote.

---

### Post by Kissell on 2009-02-06
Using the old conf files from /etc/lirc seems to work better. 

At least I can load the daemon now.  However, the remote control still doesn't work...  

But, I'm optimistic that it will work next time I can reboot...  not sure why, but originally when I installed lirc it didn't work until I rebooted, even though the module and daemon were loaded.

---

### Post by Kissell on 2009-02-06
Still not working after reboot.  :(

The daemon loads now, but the remote won't work...  if I do "irw" and press buttons on the remote I get no buttons displayed...  

I installed mythbuntu control center and setup my remote with it, and still nothing...  

hmmm....  i'm completely stumped.

---

### Post by 0nelove on 2009-02-08
similar issue, also using 2.6.27-11-generic, but the errors are slightly different:

> zzz@zzzbox:/etc/lirc$ sudo dpkg-reconfigure lirc
[sudo] password for zzz: 
 * Stopping remote control daemon(s): LIRC                               [fail] 
 * Reloading kernel event manager...                                     [ OK ] 
 * Loading LIRC modules                                                  [ OK ] 
 * Unable to load LIRC kernel modules. Verify your
 * selected kernel modules in /etc/lirc/hardware.conf


warp99, I'll see if I can figure out how to diff...

---

### Post by 0nelove on 2009-02-09
ok, I understand diff, but not sure which files are "dpkg-dist *.conf files"

some things have changed from above in attempting to fix this: I had installed lirc with synaptic.  removed that installation via synaptic.  

wget [http://prdownloads.sourceforge.net/lirc/lirc-0.8.4a.tar.bz2](http://prdownloads.sourceforge.net/lirc/lirc-0.8.4a.tar.bz2)

untar, make configure install...

it seemed to work at first with irw, ...then I somehow broke lirc again.  came back to project after 18 hours & first, got an error when setting up lircrc, then irw didn't work anymore, then saw this:

```
zzz@zzzbox:~$ sudo dpkg-reconfigure lirc
 * Stopping remote control daemon(s): LIRC                               [COLOR="Red"][fail][/COLOR] 
 * Reloading kernel event manager...                                     [ OK ] 
 * Loading LIRC modules                                                  [ OK ] 
[COLOR="Red"] * Unable to load LIRC kernel modules. Verify your
 * selected kernel modules in /etc/lirc/hardware.conf[/COLOR]

```

and the /etc/lirc/hardware.conf:
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Winfast TV2000/XP (card=34)"
REMOTE_MODULES="devinput"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="leadtek/lircd.conf.RM-0010"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""
```

thanks for any tips.  happy to provide whatever logs; I'll keep an eye here.

---

### Post by Kissell on 2009-02-10
I fixed my problem by just removing my files and using the old ones...  didn't bother with diff'ing them...  that fixed it for me.  

The only reason it didn't work after doing that, was my batteries happened to die at the same time.  (but i know that wasn't the original problem, because it was failing to load the daemon until i used the old conf files)

---

