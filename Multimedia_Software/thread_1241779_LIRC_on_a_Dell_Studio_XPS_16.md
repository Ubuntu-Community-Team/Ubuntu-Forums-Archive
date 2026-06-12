---
title: "LIRC on a Dell Studio XPS 16"
date: 2009-08-16
forum: Multimedia Software
---

### Post by seven7seven on 2009-08-16
Hello,

I ran into some problems while trying to get my laptop's integrated IR port (which Dell lists as a ITE IT8512 CIR, but [this]("http://lkml.indiana.edu/hypermail/linux/kernel/0809.1/0461.html") claims the ite8709 contains the CIR) to work with my TV's remote (a Sony RM-887).

Everything should be set up right, unless I get no response from irw when pressing buttons on the remote.

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="ITE8709 CIR port"
REMOTE_MODULES="lirc_dev lirc_ite8709"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF=""
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
LOAD_MODULES="lirc_ite8709"

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

The lircd.conf file contains the definitions for the RM-887 remote, I can paste its content too.

Some other things I thought might be related:

> root@seven-laptop:/home/seven# dmesg | grep lirc
[   14.638864] lirc_dev: IR Remote Control driver registered, major 61 

> root@seven-laptop:/home/seven# cat /var/log/daemon.log | grep lirc

Aug 16 17:42:39 seven-laptop lircd-0.8.4a[5480]: caught signal
Aug 16 17:42:39 seven-laptop lircd-0.8.4a[6744]: lircd(default) ready
Aug 16 17:42:44 seven-laptop lircd-0.8.4a[6744]: accepted new client on /dev/lircd
Aug 16 17:42:44 seven-laptop lircd-0.8.4a[6744]: could not get file information for /dev/lirc0
Aug 16 17:42:44 seven-laptop lircd-0.8.4a[6744]: default_init(): No such file or directory 
Aug 16 17:42:44 seven-laptop lircd-0.8.4a[6744]: Failed to initialize hardware
Aug 16 17:42:55 seven-laptop lircd-0.8.4a[6744]: removed client

(this repeats several times in the output)


Any thoughts on what I can do about it?

I'm running Jaunty (64-bit).

---

### Post by seven7seven on 2009-08-16
Update:

I've set a symlink from /dev/lircd tp /dev/lirc0, now I get this in deamon.log:

```
Aug 16 22:24:53 seven-laptop lircd-0.8.4a[2514]: caught signal
Aug 16 22:24:53 seven-laptop lircd-0.8.4a[6008]: lircd(default) ready
Aug 16 22:25:27 seven-laptop lircd-0.8.4a[6008]: accepted new client on /dev/lircd
Aug 16 22:25:27 seven-laptop lircd-0.8.4a[6008]: accepted new client on /dev/lircd
Aug 16 22:25:58 seven-laptop lircd-0.8.4a[6008]: removed client
Aug 16 22:26:07 seven-laptop lircd-0.8.4a[6008]: accepted new client on /dev/lircd
Aug 16 22:29:17 seven-laptop lircd-0.8.4a[6008]: removed client
Aug 16 22:30:37 seven-laptop lircd-0.8.4a[6008]: caught signal
Aug 16 22:30:37 seven-laptop lircd-0.8.4a[6501]: lircd(default) ready

```

However, no reply from either mode2 or ircw do not return any output.

---

### Post by evaarties on 2010-02-15
Did you find a solution to get this IR to work ?

I've made a post at LIRCs forum:

[http://sourceforge.net/projects/lirc/forums/forum/16772/topic/3407688](http://sourceforge.net/projects/lirc/forums/forum/16772/topic/3407688)

---

### Post by seven7seven on 2010-02-15
Unfortunately no.

I haven't booted Ubuntu in a couple of months; bought a wireless mouse, works pretty good as a substitute.

I'd still like to find a way to use the IR; I'll make sure to follow the post you made.

---

