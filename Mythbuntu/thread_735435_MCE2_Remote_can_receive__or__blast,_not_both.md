---
title: "MCE2 Remote can receive _or_ blast, not both"
date: 2008-03-25
forum: Mythbuntu
---

### Post by zmerch on 2008-03-25
Once my "ancient" Series 1 Tivo quit getting program updates from my hacked-in TivoNet card, I decided to finally build a Myth box, so I bought a capture card, bungled some spare parts, and this is what I have:

1600+ Sempron, 512Meg RAM & 500G HD, Hauppauge PVE-150 MCE low-profile board, Nvidia GeForce 5200... and because the Hauppauge LP card doesn't have a remote, I purchased an E-Data MCE2-compatible remote w/blaster, the DEC-200B. Got that model because it had a blaster (I run an ancient Dish receiver - sense an "Old Fogey" theme here?? ;-) ) and the reviews said that it a) seemed more durable than the Micro$oft flavor, and 2) worked fine with Linux.

I've got most of my Mythbuntu issues solved, and generally happy with the setup as a DVD player (which also died) and base Tivo (one can pause / rewind live TV & that works great) as the remote receiver works fine - but because the blaster's not working, I can't *record* shows or change channels on my dish receiver, the one thing I really loved my TiVo for.

I've read just about every LIRC tutorial I can find, and I've diddled with this for 3 days now - and there's 2 issues with LIRC on my box I can find: 1) LIRC won't restart. It thinks it does, but the remote doesn't work. Rebooting the system, however, makes everything work again, but does add time to the troubleshooting time. 2) I _can_ get the blaster to work - once it does work, the remote part of the system quits working. I can only have "one or the other" active; both won't work at the same time.

Is there a little golden nugget of info that I need to make this work, or should I just purchase (or build - I'm no stranger to hardware) a serial or parallel blaster - the machine has both ports available.

Any help, pointers, brickbats, LART's, etc. muchly appreciated, and if anyone needs more info (which will probably happen) I am more than happy to provide.

Thanks,
Roger "Merch" Merchberger

---

### Post by KillerKiwi on 2008-03-25
I've got a ms usb 2 dvie and it works fine

You need to make sure you have both remotes in your /etc/lirc/lircd.conf file 
(The remote it recives and the remote it emulates)

You can use irrecord to generate a file for the remote you want to emulate

sudo  irrecord --device=/dev/lirc0 lircd-blaster-config.conf

you then need to merge that by hand, into /etc/lirc/lircd.conf


To restart lircd
sudo /etc/init.d/lirc restart
You will need to restart mythfrontend after doing that as it seems to lose it connection to lircd


Other usful commands...
irsend --device=/dev/lircd1 SEND_ONCE $REMOTE_NAME $digit 
Send a "blast" signal emulating $REMOTE_NAME sending $digit

You should see the diode flash when you do an irsend.. mine does if its an invisble light try looking though a digital camera at it

Your lird.conf MUST be setup for this to work

irw - test receiving remote commands

ircat - test lird is receiving anything 


one day some one will make a nice ui to make this easier.... today is not that day

---

### Post by majoridiot on 2008-03-26
> **zmerch said:**
> Once my "ancient" Series 1 Tivo quit getting program updates from my hacked-in TivoNet card, I decided to finally build a Myth box, so I bought a capture card, bungled some spare parts, and this is what I have:

1600+ Sempron, 512Meg RAM & 500G HD, Hauppauge PVE-150 MCE low-profile board, Nvidia GeForce 5200... and because the Hauppauge LP card doesn't have a remote, I purchased an E-Data MCE2-compatible remote w/blaster, the DEC-200B. Got that model because it had a blaster (I run an ancient Dish receiver - sense an "Old Fogey" theme here?? ;-) ) and the reviews said that it a) seemed more durable than the Micro$oft flavor, and 2) worked fine with Linux.

I've got most of my Mythbuntu issues solved, and generally happy with the setup as a DVD player (which also died) and base Tivo (one can pause / rewind live TV & that works great) as the remote receiver works fine - but because the blaster's not working, I can't *record* shows or change channels on my dish receiver, the one thing I really loved my TiVo for.

I've read just about every LIRC tutorial I can find, and I've diddled with this for 3 days now - and there's 2 issues with LIRC on my box I can find: 1) LIRC won't restart. It thinks it does, but the remote doesn't work. Rebooting the system, however, makes everything work again, but does add time to the troubleshooting time. 2) I _can_ get the blaster to work - once it does work, the remote part of the system quits working. I can only have "one or the other" active; both won't work at the same time.

Is there a little golden nugget of info that I need to make this work, or should I just purchase (or build - I'm no stranger to hardware) a serial or parallel blaster - the machine has both ports available.

Any help, pointers, brickbats, LART's, etc. muchly appreciated, and if anyone needs more info (which will probably happen) I am more than happy to provide.

Thanks,
Roger "Merch" Merchberger


posting copies of your /etc/lirc/hardware.conf and /etc/lirc/lircd.conf would help in troubleshooting this. :)

---

### Post by zmerch on 2008-03-27
Here's an abridged lirc.conf file (I don't think y'all need all the codes, eh?)

[INDENT]```

ztivo@zTivo:/etc/lirc$ cat lircd.conf
#
# RC-6 config file
#
# source: http://home.hccnet.nl/m.majoor/projects__remote_control.htm
#         http://home.hccnet.nl/m.majoor/pronto.pdf
#
# used by: Philips
#
#########
#
# Philips Media Center Edition remote control
# For use with the USB MCE ir receiver
#
# Dan Conti  dconti|acm.wwu.edu
#
# Updated with codes for MCE 2005 Remote additional buttons
# *, #, Teletext, Red, Green, Yellow & Blue Buttons
# Note: TV power button transmits no code until programmed.
# Updated 12th September 2005
# Graham Auld - mce|graham.auld.me.uk
#
# Radio, Print, RecTV are only available on the HP Media Center remote control
#

begin remote

  name mceusb
  bits           16
  flags RC6|CONST_LENGTH
  eps            30
  aeps          100

  header       2667   889
  one           444   444
  zero          444   444
  pre_data_bits 21
  pre_data      0x37FF0
  gap          105000
  toggle_bit     22
  rc6_mask     0x100000000

      begin codes

        Blue    0x00007ba1
        Yellow  0x00007ba2
        Green   0x00007ba3
        Red     0x00007ba4
        Teletext        0x00007ba5

# starts at af
        Radio    0x00007baf
############
##
## Snipped by "Merch" - tonnes of codes won't help debug...
##
############
        Zero     0x00007bff
      end codes

end remote

# =-=-=-=-=-=-=-=-=-=

# This config file is based on the information posted by Endaf Jones at
# http://www.gossamer-threads.com/lists/mythtv/users/196566#196566
# brand:                       JVC/RCA
# model no. of remote control:
# supported devices:           Dish Network (Echostar)
#                                - JVC 2700 receiver
#				(And mine...)

### Remote definition for remotes using remote code 1 (0x000)
begin remote
  name dish

  flags SPACE_ENC|NO_HEAD_REP
  eps 30
  aeps 100

  frequency 56000
#  duty_cycle 32

  one 440 1645
  zero 440 2780

  header 525 6045
  ptrail 450
  gap 6115

  min_repeat 6

  bits 6
  post_data_bits 10

  post_data 0x000

  begin codes
    info                               0
    power_on                           1
   power                              2
   1                                  4
   2                                  5
############
##
## Snipped by "Merch" - tonnes of codes won't help debug...
##
############
   sys_info2                          54
   dish_home2                         56
 end codes
end remote

```[/INDENT]

and my hardware.conf file also (disregard all the extra comments - they were when I was trying to get the blaster working...)

[INDENT]```

ztivo@zTivo:/etc/lirc$ cat hardware.conf
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Remotes (new version Philips et al.)"

# Arguments which will be used when launching lircd
# LIRCD_ARGS="--device=/dev/lirc1 --output=/dev/lircd1 --listen"
# LIRCD2_ARGS="--device=/dev/lirc0 --output=/dev/lircd --connect=localhost:8765 --pidfile=/var/run/lircd2.pid"
LIRCD_ARGS="-d /dev/lirc1 --output=/dev/lircd1 --listen --pidfile=/var/run/lirc0.pid"
LIRCD2_ARGS="-d /dev/lirc0 --output=/dev/lircd --connect=localhost:8765 --pidfile=/var/run/lircd2.pid"
# LIRCD2_ARGS="--device /dev/lirc0 --output=/dev/lircd --connect=localhost:8765 --pidfile=/var/run/lircd2.pid"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER=""
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE=""
# MODULES="lirc_dev lirc_mceusb2"
MODULES="lirc_mceusb2"

# Default configuration files for your hardware if any
LIRCD_CONF="/etc/lirc/lircd.conf"
# LIRCD_CONF="mceusb/lircd.conf.mceusb"
# LIRCD2_CONF="mceusb/lircd.conf.dish"

#LIRCMD_CONF=""
LIRCMD_CONF=""

```[/INDENT]

I'm still just as stumped as I was before on the remote... but I keep trying!

Thanks,
Roger "Merch" Merchberger

---

### Post by majoridiot on 2008-03-27
> **zmerch said:**
> -snip- 
I'm still just as stumped as I was before on the remote... but I keep trying!

Thanks,
Roger "Merch" Merchberger

try using this for your /etc/lirc/hardware.conf
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Remotes (new version Philips et al.)"

# Arguments which will be used when launching lircd
LIRCD_ARGS="-d /dev/lirc0 --output=/dev/lircd --listen"
LIRCD2_ARGS="-d /dev/lirc1 --output=/dev/lircd1 --connect=localhost:8765 --pidfile=/var/run/lircd2.pid"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=false

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER=""
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE=""

MODULES="lirc_dev lirc_mceusb2"

# Default configuration files for your hardware if any
LIRCD_CONF="/etc/lirc/lircd.conf"
LIRCMD_CONF=""
```

next (sudo) edit /etc/init.d/lirc and look for this, toward the bottom:
```
LIRCD_ARGS=`build_args $LIRCD_ARGS`
      start-stop-daemon --start --quiet --exec /usr/sbin/lircd -- $LIRCD_ARGS \
                < /dev/null
```

modify it to this:
```
LIRCD_ARGS=`build_args $LIRCD_ARGS`
      LIRCD2_ARGS=`build_args $LIRCD2_ARGS`
      start-stop-daemon --start --quiet --exec /usr/sbin/lircd -- $LIRCD_ARGS \
                < /dev/null
      /usr/sbin/lircd $LIRCD2_ARGS \
               < /dev/null
```

then *reboot*

when it's back, try the remote.  you can also check it with **irw** from a terminal to see if it
everything is registering.

next, try the blaster:

```
$ irsend -d /dev/lircd1 SEND_ONCE dish power (or whatever code you want to send)
```

see if that works any better.

if there's no love from either the remote or the blaster, try substituting /dev/lircd0 in the
irsend command and/or running
```
$ irw /dev/lircd1
```
to see if the devices are reversed.

---

### Post by zmerch on 2008-03-27
Hrm... I guess I had it close once -- because I saw the following symptom once before during testing, I just figgered I b0rked the config somehow & moved on...

Assuming your instructions are spot-on (which I have no reason to believe they aren't) I'm wondering if there's an issue with my lirc (which I've reinstalled thru apt-get a couple of times), as basically your instructions "worked" - well, almost once. I did exactly what you said, rebooted, remote still works fine, gave the `irsend` command, which "ran normally" (read: without visible error) once but didn't output anything to the dish receiver. All subsequent `irsend`s give this:

[INDENT]```

irsend: could not connect to socket
irsend: Connection refused

```[/INDENT]

I looked in /var/syslog, and this is what I have 

[INDENT]```

Mar 27 15:45:19 zTivo lircd-0.8.2[3404]: caught signal
Mar 27 15:45:29 zTivo lircd-0.8.2[5616]: lircd(userspace) ready
Mar 27 15:45:29 zTivo lircd-0.8.2[5618]: lircd(userspace) ready
Mar 27 15:45:29 zTivo lircd-0.8.2[5616]: accepted new client from 127.0.0.1
Mar 27 15:45:29 zTivo lircd-0.8.2[5618]: connected to localhost
Mar 27 15:45:58 zTivo lircd-0.8.2[5618]: accepted new client on /dev/lircd1
Mar 27 15:45:58 zTivo lircd-0.8.2[5618]: could not open /dev/lirc1
Mar 27 15:45:58 zTivo lircd-0.8.2[5618]: default_init(): No such device
Mar 27 15:45:58 zTivo lircd-0.8.2[5618]: caught signal
Mar 27 15:45:58 zTivo lircd-0.8.2[5616]: removed client

```[/INDENT]

I did this:

[INDENT]```

sudo mknod /dev/lirc1 c 61 1

```[/INDENT]

but that didn't change lirc's behaviour. The last bit'o'info I have is this is what ps ax|grep lirc shows:

[INDENT]```

5671 ?        Ss     0:00 /usr/sbin/lircd --device=/dev/lirc0 -d /dev/lirc0 --output=/dev/lircd --listen
5673 ?        Ss     0:00 /usr/sbin/lircd --device=/dev/lirc0 -d /dev/lirc1 --output=/dev/lircd1 --connect=localhost 8765 --pidfile=/var/run/lircd2.pid

```[/INDENT]

Should there be both a '-d' and '--device' parameter on the command line?

Closer (I guess) but still stumped, and many many thanks!
Roger "Merch" Merchberger

---

### Post by majoridiot on 2008-03-27
> **zmerch said:**
> Closer (I guess) but still stumped, and many many thanks!
Roger "Merch" Merchberger

shutdown your computer, physically unplug the power from the computer, hold the power button down for 3-4 seconds
and then plug in and reboot.

after rebooting like that, please post the current incarnation of your:

/etc/lirc/hardware.conf
/etc/init.d/lirc

and the result of:

```
$ ls -l /dev/lirc* 
```

---

### Post by zmerch on 2008-03-27
Done... I even unplugged something still isn't right; so here's the filez you asked for:

/etc/lirc/hardware.conf

[INDENT]```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Remotes (new version Philips et al.)"

# Arguments which will be used when launching lircd
LIRCD_ARGS="-d /dev/lirc0 --output=/dev/lircd --listen"
LIRCD2_ARGS="-d /dev/lirc1 --output=/dev/lircd1 --connect=localhost:8765 --pidfile=/var/run/lircd2.pid"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=false

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER=""
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE=""

MODULES="lirc_dev lirc_mceusb2"

# Default configuration files for your hardware if any
LIRCD_CONF="/etc/lirc/lircd.conf"
LIRCMD_CONF=""

```[/INDENT]

Here's my /dev/lir* listing:

[INDENT]```

ztivo@zTivo:/etc/lirc$ ls -lAF /dev/lir*
crw-rw---- 1 root root 61, 0 2008-03-27 16:19 /dev/lirc0
srw-rw-rw- 1 root root     0 2008-03-27 16:19 /dev/lircd=
srw-rw-rw- 1 root root     0 2008-03-27 16:19 /dev/lircd1=

```[/INDENT]

ps ax|grep lir  ; sudo irsend -d /dev/lircd1 SEND_ONCE dish 1 ; \
 ps ax|grep lir 

[INDENT]```

ztivo@zTivo:/etc/lirc$ ps ax|grep lirc
3547 ?        S<s    0:00 /usr/sbin/lircd --device=/dev/lirc0 -d /dev/lirc0 --output=/dev/lircd --listen
3549 ?        S<s    0:00 /usr/sbin/lircd --device=/dev/lirc0 -d /dev/lirc1 --output=/dev/lircd1 --connect=localhost 8765 --pidfile=/var/run/lircd2.pid

/etc/lirc$ sudo irsend -d /dev/lircd1 SEND_ONCE dish 1
[sudo] password for ztivo:

ztivo@zTivo:/etc/lirc$ ps ax|grep lirc

3547 ?        S<s    0:00 /usr/sbin/lircd --device=/dev/lirc0 -d /dev/lirc0 --output=/dev/lircd --listen

```[/INDENT]

And the pertinent entries from /var/syslog:

[INDENT]```

Mar 27 20:08:25 zTivo lircd-0.8.2[3549]: accepted new client on /dev/lircd1
Mar 27 20:08:25 zTivo lircd-0.8.2[3549]: could not get file information for /dev/lirc1
Mar 27 20:08:25 zTivo lircd-0.8.2[3549]: default_init(): No such file or directory
Mar 27 20:08:25 zTivo lircd-0.8.2[3549]: caught signal
Mar 27 20:08:25 zTivo lircd-0.8.2[3547]: removed client

```[/INDENT]

Oh, before I forget: I'm running MythTV version 0.21 (Library API      : 0.21.20080304-1); Mythbuntu 7.10 with just about every darned repository enabled I can think of, and other than this small but bothersome problem, I'm *really* liking MythTV... ;-)

Thanks a lot!
Roger "Merch" Merchberger

---

### Post by majoridiot on 2008-03-28
you forgot to post /etc/init.d/lirc ;)

---

### Post by zmerch on 2008-03-28
You are absolutely right - thanks for reminding me. Here it is:

[INDENT]```

#! /bin/sh
### BEGIN INIT INFO
# Provides:          lirc
# Required-Start:    $syslog
# Required-Stop:     $syslog
# Should-Start:      $local_fs
# Should-Stop:       $local_fs
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Starts LIRC daemon.
# Description:       LIRC is used to control different
#                    infrared receivers and transceivers.
### END INIT INFO


load_modules ()
{
        local MODULES_MISSING=false

        for mod in $*
        do
                modprobe -k $mod 2> /dev/null || MODULES_MISSING=true
        done

        if $MODULES_MISSING; then
                echo "#####################################################"
                echo "## I couldn't load the required kernel modules     ##"
                echo "## You should install lirc-modules-source to build ##"
                echo "## kernel support for your hardware.               ##"
                echo "#####################################################"
                echo "## If this message is not appropriate you may set  ##"
                echo "## LOAD_MODULES=false in /etc/lirc/hardware.conf   ##"
                echo "#####################################################"
                START_LIRCMD=false
                START_LIRCD=false
        fi

        if test -x /sbin/udevsettle && [ ! -z $3 ] && [ $3 != "udev" ];
        then
                if ! /sbin/udevsettle; then
                  echo "timeout waiting for devices to be ready"
                fi
        fi
}

build_args ()
{
        local ARGS="$*"

    ## Try to find an lirc device.
    ## udev uses /dev/lirc0
    ## static dev uses /dev/lirc
    ## devfs uses /dev/lirc/0
    if [ -z "$DEVICE" ]; then
        for dev in /dev/lirc0 /dev/lirc /dev/lirc/0; do
                if [ -c $dev ]; then
                                DEVICE="$dev"
                                break
                        fi
                done
        fi

        if [ -n "$DEVICE" ] && [ "$DEVICE" != "none" ]; then
                ARGS="--device=$DEVICE $ARGS"
        fi
        if [ -n "$DRIVER" ] && [ "$DRIVER" != "none" ]; then
                ARGS="--driver=$DRIVER $ARGS"
        fi
        echo $ARGS
}

test -f /usr/sbin/lircd || exit 0
test -f /usr/sbin/lircmd || exit 0
#test -f /etc/lirc/lircd.conf || exit 0
#test -f /etc/lirc/lircmd.conf || exit 0

START_LIRCMD=true
START_LIRCD=true

if [ ! -f /etc/lirc/lircd.conf ] \
        || grep -q "^#UNCONFIGURED"  /etc/lirc/lircd.conf;then
        if [ "$1" = "start" ]; then
          echo "##################################################"
          echo "## LIRC IS NOT CONFIGURED                       ##"
          echo "##                                              ##"
          echo "## read /usr/share/doc/lirc/html/configure.html ##"
          echo "##################################################"
        fi
        START_LIRCD=false
        START_LIRCMD=false
fi
if [ ! -f /etc/lirc/lircmd.conf ] \
        || grep -q "^#UNCONFIGURED" /etc/lirc/lircmd.conf;then
        START_LIRCMD=false
fi

if [ -f /etc/lirc/hardware.conf ];then
        . /etc/lirc/hardware.conf
fi


case "$1" in
  start)

    if [ "$LOAD_MODULES" = "true" ] && [ "$START_LIRCD" = "true" ]; then
        load_modules $MODULES
    fi
    echo -n "Starting lirc daemon:"
    if $START_LIRCD; then
      echo -n " lircd"
      LIRCD_ARGS=`build_args $LIRCD_ARGS`
      LIRCD2_ARGS=`build_args $LIRCD2_ARGS`
      start-stop-daemon --start --quiet --exec /usr/sbin/lircd -- $LIRCD_ARGS \
                < /dev/null
     /usr/sbin/lircd $LIRCD2_ARGS < /dev/null
   fi
   if $START_LIRCMD; then
     echo -n " lircmd"
     start-stop-daemon --start --quiet --exec /usr/sbin/lircmd \
               < /dev/null
   fi
   echo "."
   ;;
 stop)
   echo -n "Stopping lirc daemon:"
   echo -n " lircmd"
   start-stop-daemon --stop --quiet --exec /usr/sbin/lircmd
   echo -n " lircd"
   start-stop-daemon --stop --quiet --exec /usr/sbin/lircd
   echo "."
   ;;
 reload|force-reload)
   if $START_LIRCD; then
     start-stop-daemon --stop --quiet --signal 1 --exec /usr/sbin/lircd
   fi
   if $START_LIRCMD; then
     start-stop-daemon --stop --quiet --signal 1 --exec /usr/sbin/lircmd
   fi
   ;;
 restart)
   $0 stop
   $0 start
   ;;
 *)
   echo "Usage: /etc/init.d/lircd {start|stop|reload|restart|force-reload}"
   exit 1
esac

exit 0

```[/INDENT]

Sometimes 3rd shift gets my system all wonky... Sorry about that!

Thanks,
Roger "Merch" Merchberger

---

### Post by majoridiot on 2008-03-28
> **zmerch said:**
> Sometimes 3rd shift gets my system all wonky... Sorry about that!

Thanks,
Roger "Merch" Merchberger

at first glance, everything *looks* ok... but obviously something is wrong.

did you install and do the original config of lirc and the remote using the remote features of MCC or by hand?

---

### Post by zmerch on 2008-05-05
Sorry for the lag in this - and unfortunately, I don't have any answers to this problem for anyone else who might be having issues other than "Try Mythbuntu 8.04."

I noticed in one of the screenshots for the latest Mythbuntu that the blaster setup was GUI, so I took a chance & just slicked & reinstalled. [[ I wanted to set up my media partition(s) as XFS also - much more efficient so I was planning on doing this anyway. ]]

Other than needing to find & edit a small channel changer script (found everywhere on the 'net) it was point & click setup. My remote works *great* now!

Thanks for all the help again!

Laterz,
Roger "Merch" Merchberger

---

### Post by majoridiot on 2008-05-05
> **zmerch said:**
> Sorry for the lag in this - and unfortunately, I don't have any answers to this problem for anyone else who might be having issues other than "Try Mythbuntu 8.04."

I noticed in one of the screenshots for the latest Mythbuntu that the blaster setup was GUI, so I took a chance & just slicked & reinstalled. [[ I wanted to set up my media partition(s) as XFS also - much more efficient so I was planning on doing this anyway. ]]

Other than needing to find & edit a small channel changer script (found everywhere on the 'net) it was point & click setup. My remote works *great* now!

Thanks for all the help again!

Laterz,
Roger "Merch" Merchberger

glad you got it working!  lirc in 8.04 is vastly improved over 7.10.

you've gotta love mythbuntu... it just gets better and better :D

---

