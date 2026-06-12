---
title: "IR Blaster for MythBuntu...Recommendations"
date: 2008-08-15
forum: Mythbuntu
---

### Post by LarryJ2 on 2008-08-15
After four days of hacking and spitting,  I have given up getting my serial IR Blaster working with MythBuntu.  I can call the channel change script from the command line and that works but MythBuntu (MythTV Version   : 16838, MythTV Branch    : branches/release-0-21-fixes, Library API      : 0.21.20080304-1)  never calls the script.  It was suggested that I could put a few cout/printfs in the source code, recompile,  and then figure out what is wrong, but I'm not in the proper frame of mind to attempt that right now.  So I put the serial blaster into my pile of "someday" projects and intend to move on.

Still I would like to control my DishNet/EchoStar receiver.  What works "out of the box"?  For example, I purchased two usb connected StreamZap remotes.  They "just worked".

1.What IR Blaster schemes work "out of the box" with Mythbuntu based on your experience? 

2. I read where the DirectTV sat. receiver can be directly controlled by hardwired connection.   Has anyone got that running? (Maybe it's time to trash my Dish Receiver)

Thanks,

Larry

---

### Post by gfowler on 2008-08-15
> **LarryJ2 said:**
> After four days of hacking and spitting,  I have given up getting my serial IR Blaster working with MythBuntu.  I can call the channel change script from the command line and that works but MythBuntu (MythTV Version   : 16838, MythTV Branch    : branches/release-0-21-fixes, Library API      : 0.21.20080304-1)  never calls the script.  It was suggested that I could put a few cout/printfs in the source code, recompile,  and then figure out what is wrong, but I'm not in the proper frame of mind to attempt that right now.  So I put the serial blaster into my pile of "someday" projects and intend to move on.

Still I would like to control my DishNet/EchoStar receiver.  What works "out of the box"?  For example, I purchased two usb connected StreamZap remotes.  They "just worked".

1.What IR Blaster schemes work "out of the box" with Mythbuntu based on your experience? 

2. I read where the DirectTV sat. receiver can be directly controlled by hardwired connection.   Has anyone got that running? (Maybe it's time to trash my Dish Receiver)

Thanks,

Larry

Larry,
I have been using the IR-Blaster from Leibtech, which consists basically of a serial plug, a 1N914 diode in series with an IR LED to ground. I just stuck the LED to the IR window on the DISH 311 receiver.  All that being said, I would suspect something else (oh yeah, real helpful).  I used the setup in the Mythbuntu Manual to set it all up.  I had trouble with the sequence with the includes for serial IR and remote.in the /etc/lirc/lirc.conf file.  Once that was ironed out it all worked.  I understand this is not much help, just mostly info.

Jerry

---

### Post by rubrboots on 2008-08-15
Larry, I just got my serial irblaster working. I think you should be able to as well. Your serial ports settings in you bios may be different than what is listed in your /etc/modprobe.d/lirc-serial file.Check out these links.

I followed these instructions

[http://ubuntuforums.org/showthread.php?t=742672&highlight=lirc&page=2](http://ubuntuforums.org/showthread.php?t=742672&highlight=lirc&page=2)

Then fixed the serial/irq issue here

[http://ubuntuforums.org/showthread.php?p=5597930#post5597930](http://ubuntuforums.org/showthread.php?p=5597930#post5597930)

---

### Post by LarryJ2 on 2008-08-15
Thanks for the hints.  Before I gave up, I was able to change channels with my serial Blaster if I gave the command from a terminal.  In other words, if I entered this in a terminal window
```
/usr/local/bin/change-channel-lirc.pl 200
```
the dish receiver slowly but deliberately changed to CNN (ch 200).

I have the external channel changer script plugged into the gui blank for it in the backend setup and verified it was there inside the myth database. I even salted the perl script with a couple print statements which convinced me that Myth was not calling the channel change script.   So I'm still baffled and ready to try a different hardware scheme.

---

### Post by ahood on 2008-08-16
> **LarryJ2 said:**
> Thanks for the hints.  ...if I entered this in a terminal window
```
/usr/local/bin/change-channel-lirc.pl 200
```
the dish receiver slowly but deliberately changed to CNN (ch 200).

...convinced me that Myth was not calling the channel change script.

Is lirc running?

I suspect it is, but check by executing the following command in a terminal...

> 
sudo /etc/init.d/lirc stop


If an error message appears, then it probably wasn't running.

If no error message appears, then start it up again with the command...

> 
sudo /etc/init.d/lirc start


Is the contents of [COLOR="Brown"]**/etc/lirc/hardware.conf**[/COLOR] correct?

Check by executing the following command in a terminal.

> 
cat [COLOR="Brown"]**/etc/lirc/hardware.conf**[/COLOR]


The output will be something like...

> 
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Hauppauge TV card"
REMOTE_MODULES="lirc_dev lirc_i2c"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="DCT2000"
TRANSMITTER_MODULES="lirc_dev lirc_serial"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc1"
TRANSMITTER_LIRCD_CONF="motorola/dctxxxx.conf"
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


Specifically, under the section called _#Chosen IR Transmitter_ of [COLOR="Brown"]**/etc/lirc/does hardware.conf**[/COLOR], is the information for the TRANSMITTER, TRANSMITTER_MODULES, TRANSMITTER_DEVICE, and TRANSMITTER_LIRCD_CONF variables correct? 

All four of these parameters are important and must be correct for your system.

Al

---

### Post by jetsurgeon on 2008-08-16
tag

---

### Post by LarryJ2 on 2008-08-16
Ahood:
Is lirc running?
> lj@mythtv:~$ sudo /etc/init.d/lirc stop
[sudo] password for lj: 
 * Stopping remote control daemon(s): LIRC                               [ OK ] 
lj@mythtv:~$ sudo /etc/init.d/lirc start
 * Loading LIRC modules                                                  [ OK ] 
 * Starting remote control daemon(s) : LIRC                              [ OK ] 
lj@mythtv:~$ 

Contents of /etc/lirc/hardware.conf
> lj@mythtv:~$ cat /etc/lirc/hardware.conf
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Streamzap PC Remote"
REMOTE_MODULES="lirc_dev lirc_streamzap"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="streamzap/lircd.conf.streamzap"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Serial Port (UART) : Dish Receiver"
TRANSMITTER_MODULES="lirc_dev lirc_serial"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc1"
TRANSMITTER_LIRCD_CONF="dish/general.conf"
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

Also, I know you didn't ask for it but here's more info:
> lj@mythtv:~$ cat /usr/local/bin/change-channel-lirc.sh
#!/bin/sh

REMOTE_NAME=dish
cmd="$1"

case $cmd in
    [0-9]*)
    for digit in $(echo $1 | sed -e 's/./& /g'); do 
        irsend -d /dev/lircd1 SEND_ONCE $REMOTE_NAME $digit
        sleep 1
        # If things work OK with sleep 1, try this for faster channel changes:
        # sleep 0.3
    done
    ;;

    *)
        irsend -d /dev/lircd1 SEND_ONCE $REMOTE_NAME $cmd
        ;;
esac
lj@mythtv:~$ ls -al /usr/local/bin/change-channel-lirc.sh
-rwxr-xr-x 1 root root 389 2008-08-14 15:51 /usr/local/bin/change-channel-lirc.sh

I've also tried the change-channel-lirc.pl perl script.  Same result.
I've also tried "backend -v channel" to see if anything would appear in the logs.  Nothing seen.

And like I indicated,  if I  "/usr/local/bin/change-channel-lirc.sh 200"
the dish rx pops up to cnn (dishnetwork channel 200)  but channel change doesn't occur if I use the keyboard or remote from within the frontend while in "watchtv" mode.  The remote works fine otherwise.

Grrrr I must be getting old and these software controlled devices are getting the best of me.  I just fired up mythfrontend to make absolutely certain the behavior I was experiencing (no channel change) was still there.   Now it's working!   I'm going to reboot and see if "no channel change" reoccurs.

---

### Post by LarryJ2 on 2008-08-16
I have no idea why but I am now able to change channels!!! And the problem didn't return after a reboot.  So label this one "Fixed: Came clear while testing".

I have another mythbuntu install on another HD.  Later, I'll go through the steps of making that separate installation IRBlaster capable and see what happens.  Assume all was OK if nothing extra is posted here.

Thanks to all for their suggestions and help

Larry

PS.  Just remembered that update flag was set and I downloaded and installed several updates before trying the irblaster.  They didn't appear to be associated with mythbuntu but...

---

### Post by LarryJ2 on 2008-10-21
My current channel change script for my DishNet vip612 satellite receiver includes a  a "power_on" button press in the perl script.  This seems to bring the  vip dishnet receiver out of power save hibernation which it automatically puts itself into after a pre-determined length of inactivity. 
Here's the complete channel-change-lirc.pl script:

```
#!/usr/bin/perl
#
# name the file channel-change-lirc.pl  then place  in  /usr/local/bin, remember to  chmod +xr
#
# make sure to set this string to
# the corresponding remote in /etc/lircd.conf
#
$remote_name = "dish";
#  Next two lines added to get rid of press select message that comes up
#  on Vip612 dish receive when inactive.
system ("irsend -d /dev/lircd1 SEND_ONCE $remote_name power_on");
sleep 5;
system ("irsend -d /dev/lircd1 SEND_ONCE $remote_name select");
sleep 2;

sub change_channel {
        my($channel_digit) = @_;
        system ("irsend -d /dev/lircd1 SEND_ONCE $remote_name $channel_digit");
        sleep 1;
}

$channel=$ARGV[0];
sleep 1;
if (length($channel) > 3) {
        change_channel(substr($channel,0,1));
        change_channel(substr($channel,1,1));
        change_channel(substr($channel,2,1));
    change_channel(substr($channel,3,1));
} elsif (length($channel) > 2) {
        change_channel(substr($channel,0,1));
        change_channel(substr($channel,1,1));
        change_channel(substr($channel,2,1));
} elsif (length($channel) > 1) {
        change_channel(substr($channel,0,1));
        change_channel(substr($channel,1,1));
} else {
        change_channel(substr($channel,0,1));
}
system ("irsend -d /dev/lircd1 SEND_ONCE $remote_name select");

```

---

