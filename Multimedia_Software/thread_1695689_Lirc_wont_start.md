---
title: "Lirc wont start"
date: 2011-02-26
forum: Multimedia Software
---

### Post by jackleather on 2011-02-26
Hello. i thought i had created the ultimate media centre with ubuntu 10.10 and xbmc on a mac mini 2006. all has been working fine for a while.

however it would appear that after a recent kernel update (2.6.35-25-generic) my remote stopped working.

i am new to lirc and have tried various things posted around with no joy. however when i rolled back to using 2.6.35-24-generic lirc started and the remote worked again for about 15 mins after which it stopped again. i have tried using 2.6.35-22-generic then 2.6.35-24-generic but cant get the remote to respond again. i have now tried installing the proposed updates and have 2.6.35-27-generic which also made no difference.

i have tried;
installing 'lirc-modules-source'
running 'sudo dpkg-reconfigure lirc-modules-source'

and noted the following in its output;

```
lirc_imon.ko:
Running module version sanity check.

Error! Module version 0.6 for lirc_imon.ko
is not newer than what is already found in kernel 2.6.35-27-generic (0.8).
You may override by specifying --force.
```

it looks like /dev/lirc0 had disappeared. it was there before.

Here are some general observations:

```
uname -r 2.6.35-27-generic

lircd-0.8.7-pre3

/dev/lircd exists
/dev/lirc0 doesnt


/etc/lirc/hardware.conf

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Transceivers/Remotes (all)"
REMOTE_MODULES="lirc_dev mceusb"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
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


lsusb
Bus 004 Device 002: ID 0471:0815 Philips (or NXP) eHome Infrared Receiver
```


Syslog:
```

Feb 26 13:49:33 macsavebox kernel: [   23.200752] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro,commit=0
Feb 26 13:49:34 macsavebox lircd-0.8.7-pre3[1032]: accepted new client on /var/run/lirc/lircd
Feb 26 13:49:34 macsavebox lircd-0.8.7-pre3[1032]: could not get file information for /dev/lirc0
Feb 26 13:49:34 macsavebox lircd-0.8.7-pre3[1032]: default_init(): No such file or directory
Feb 26 13:49:34 macsavebox lircd-0.8.7-pre3[1032]: Failed to initialize hardware
```

```
Feb 26 13:49:37 macsavebox lircd-0.8.7-pre3[1032]: accepted new client on /var/run/lirc/lircd
```

Please could some step me through how i should proceed? my media centre isnt much good with out a remote!

---

### Post by jackleather on 2011-02-28
Think i am getting somewhere after spending hours on this.

i removed lirc-modules-source as this is a bad idea in ubuntu.

next i removed lirc and /etc/lirc and then reinstalled lirc.

after a restart my remote is working again! well sort of...

when i run irw i see repeats. one remote button press = two lines in irw. this of course manifests itself in XBMC.

Does anyone have any ideas?

lsmod | grep mce:
```
rc_rc6_mce              1146  0
mceusb                 11494  0
ir_core                14654  9 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,rc_rc6_mce,ir_nec_decoder,mceusb
```

---

### Post by aeiah on 2011-02-28
looks like you had two lirc drives running.. one module, and one built into the kernel (as your initial error message describes)


your new error sounds familiar, and if im right its related. i came across this the other day, by chance:
[http://forum.xbmc.org/showthread.php?t=93315](http://forum.xbmc.org/showthread.php?t=93315)

---

### Post by jackleather on 2011-02-28
> **aeiah said:**
> looks like you had two lirc drives running.. one module, and one built into the kernel (as your initial error message describes)


your new error sounds familiar, and if im right its related. i came across this the other day, by chance:
[http://forum.xbmc.org/showthread.php?t=93315](http://forum.xbmc.org/showthread.php?t=93315)

Thank you! i had just managed to track this down elsewhere.

as root, the following works for me until lirc is restarted (reboot).

```
echo lirc > /sys/class/rc/rc0/protocols
```

how come the above works as opposed to below (what are these statements doing??):

```
echo none +lirc > /sys/class/rc/rc0/protocols
```

i read that it can go in /etc/rc.local. however this doesnt work as i assume rc.local gets executed before lirc gets started. any idea how i can get around this?



Some more background reading...

Some interesting reading here;

[http://sourceforge.net/mailarchive/forum.php?thread_name=40B9CE83-FD1B-4A7E-A681-162CF118BF1D%40wilsonet.com&forum_name=lirc-list]("http://sourceforge.net/mailarchive/forum.php?thread_name=40B9CE83-FD1B-4A7E-A681-162CF118BF1D%40wilsonet.com&forum_name=lirc-list")

And here:

[http://forum.xbmc.org/showthread.php?t=83344]("http://forum.xbmc.org/showthread.php?t=83344")

The last thread mentions;

```
as root:
rmmod -f rc_rc6_mce
rmmod -f ir_sony_decoder
rmmod -f ir_jvc_decoder
rmmod -f ir_rc6_decoder
rmmod -f ir_rc5_decoder
rmmod -f ir_nec_decoder 
```

the above had the same effect as;

```
echo lirc > /sys/class/rc/rc0/protocols
```

but only until reboot :(

can i blacklist these somehow?

---

### Post by jackleather on 2011-03-01
OK, a couple of things;

1. blacklisting the modules does not stop them getting loaded, i can rmmod them. why?

/etc/modprobe.d/blacklist.conf

```
blacklist rc_rc6_mce
blacklist ir_sony_decoder
blacklist ir_jvc_decoder
blacklist ir_rc6_decoder
blacklist ir_rc5_decoder
blacklist ir_nec_decoder
```

2. last night i was using the remote for sometime. all was well. after i had finished watching a show i went to hit [STOP]. guess what, no response. A moment later it sprang into life again and then died. i had to ssh in and restart lirc to use the remote again. 

syslog:


Mar  1 01:40:54 macsavebox lircd-0.8.7-pre3[858]: caught signal
Mar  1 01:40:54 macsavebox lircd-0.8.7-pre3[2878]: lircd(default) ready, using /var/run/lirc/lircd
Mar  1 01:40:55 macsavebox lircd-0.8.7-pre3[2878]: accepted new client on /var/run/lirc/lircd
Mar  1 01:42:13 macsavebox lircd-0.8.7-pre3[2878]: removed client

---

### Post by aeiah on 2011-03-01
as a dirty hack you could just use sleep in your /etc/rc.local. not really a solution, i know.

in /etc/rc.local
```

sleep 20 && echo lirc > /sys/class/rc/rc0/protocols
```

the thread i linked also mentions putting an rmmod command in rc.local because the module keeps getting loaded despite being blacklisted

---

### Post by jackleather on 2011-03-01
> **aeiah said:**
> as a dirty hack you could just use sleep in your /etc/rc.local. not really a solution, i know.

in /etc/rc.local
```

sleep 20 && echo lirc > /sys/class/rc/rc0/protocols
```

the thread i linked also mentions putting an rmmod command in rc.local because the module keeps getting loaded despite being blacklisted

I had a spelling mistake in rc.local that was causing the issue. :rolleyes:

now 'echo lirc > /sys/class/rc/rc0/protocols' wokrs as advertised.

however there's still the issue from last night were lirc just died after a few hours use...why???

i really dont want to mark this as solved. there appears to be a number of factors involved here, most notably the kernel version we are on with ubuntu. 

when will this issue be resolved by canonical i wonder?

---

### Post by jackleather on 2011-03-04
Here is a related launchpad bug. has some potential workarounds.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/666493](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/666493)

however it concerns me that it was reported in October last year and little appears to have been done.

---

