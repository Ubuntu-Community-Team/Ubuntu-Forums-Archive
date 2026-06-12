---
title: "Help with LIRC- Different Transmitter and Reciever"
date: 2011-04-24
forum: Mythbuntu
---

### Post by stevenc2 on 2011-04-24
So I received a Comcast PACE-50 DTA box.  I also bought a ir blaster from [http://www.irblaster.info/](http://www.irblaster.info/).  I am using mythbuntu 10.10.  

After a bunch of hiccups I got the irblaster working to control the Pace DTA.  I followed the directions here:
[http://regx.dgswa.com/html/node/134](http://regx.dgswa.com/html/node/134)
and here:
[https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/655512](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/655512)

It's working fine now transmitting to the Pace DTA and correctly changes channels when I control mythtv using the keyboard.  The issue is now my IR receiver is no longer working, so I can't use my remote to control mythtv.  I am using a USB reciever and a MCE compatible remote and it was working fine before. 

Any ideas on how I can get the MCE USB receiver working again?  I know it's recieving the signals, because the light is blinking when I press the keys on the remote...the signals just aren't being sent to Mythtv.

Here the contents of the LIRC files:
/etc/lirc/lircd.conf[FONT=Verdana]:
[/FONT]> [FONT=Verdana]
[/FONT]#This configuration has been automatically generated via
#the Ubuntu LIRC package maintainer scripts.
#
#It includes the default configuration for the remote and/or
#transmitter that you have selected during package installation.
#
#Feel free to add any custom remotes to the configuration
#via additional include directives or below the existing
#Ubuntu include directives from your selected remote and/or
#transmitter.

#Configuration for the Windows Media Center Transceivers/Remotes (all) remote:
include "/usr/share/lirc/remotes/mceusb/lircd.conf.mceusb"

#Configuration for the Serial Port (UART) : Direct TV Receiver transmitter:
include "/usr/share/lirc/pace.conf"

**File /usr/local/bin/change-channel-lirc.pl:**

> #!/usr/bin/perl
# Created by regx
# Simple perl script to change channels for Myth

# make sure to set this string to
# the corresponding remote in /etc/lircd.conf
$remote_name = 'DC50X';

$channel=$ARGV[0];
@channel = split(//,$channel);
foreach(@channel){
        #print $_ . "\n";
        `irsend SEND_ONCE $remote_name $_`;
}
sleep 1;
`irsend SEND_ONCE $remote_name ENTER`;
sleep 2;
$channel=$ARGV[0];
@channel = split(//,$channel);
foreach(@channel){
        #print $_ . "\n";
        `irsend SEND_ONCE $remote_name $_`;
}
sleep 1;
`irsend SEND_ONCE $remote_name ENTER`;> 
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
TRANSMITTER="Serial Port (UART) : Direct TV Receiver"
TRANSMITTER_MODULES="lirc_dev lirc_serial"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc1"
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF="/usr/share/lirc/pace.conf"
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




---

### Post by phroman on 2011-04-25
In your /etc/lirc/hardware.conf file, I think your problem bay be this line:
REMOTE="Windows Media Center Transceivers/Remotes (all)"

This identifies your remote by name, in quotes. Try changing it to:
"Windows Media Center Transceivers/Remotes"

This name must match, exactly, the "name" field, in your /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb file. 

If it doesn't, remote receiver no workie.  Let me know if this helps.

---

### Post by stevenc2 on 2011-04-25
> **phroman said:**
> In your /etc/lirc/hardware.conf file, I think your problem bay be this line:
REMOTE="Windows Media Center Transceivers/Remotes (all)"

This identifies your remote by name, in quotes. Try changing it to:
"Windows Media Center Transceivers/Remotes"

This name must match, exactly, the "name" field, in your /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb file. 

If it doesn't, remote receiver no workie.  Let me know if this helps.

I changed the line as you suggested.  It did not work.

Found online somewhere I can type, irw in a terminal to see if LIRC is working correctly.  I did that, and when I use the remote control the light goes off on the IR receiver, but nothing appears in irw.  The same thing I looked at online ([http://osdir.com/ml/hardware.lirc/2006-03/msg00077.html](http://osdir.com/ml/hardware.lirc/2006-03/msg00077.html)) seems to think that the output from "ls -l /dev/lirc*" might be helpful in diagnosing LIRC problems, here is that output


> crw------- 1 root root 61, 0 2011-04-25 19:11 /dev/lirc0
lrwxrwxrwx 1 root root    19 2011-04-25 19:11 /dev/lircd -> /var/run/lirc/lircd
lrwxrwxrwx 1 root root    20 2011-04-25 19:11 /dev/lircd1 -> /var/run/lirc/lircd1Not sure if 3 devices are normal, or if that could be my issue?  I only have 1 transmitter and 1 receiver.

Any other ideas, or files I can post that would be helpful?

---

### Post by azmyth on 2011-04-26
The three lirc dev are normal. You sure your names match properly.

lircd.conf.mceusb
name BlahBlah

/etc/lirc/hardware.conf
REMOTE="Windows Media Center Transceivers/Remotes (all)"

the name must match REMOTE to work. One has quotes the other doesn't.

---

### Post by stevenc2 on 2011-04-26
> **azmyth said:**
> The three lirc dev are normal. You sure your names match properly.

lircd.conf.mceusb
name BlahBlah

/etc/lirc/hardware.conf
REMOTE="Windows Media Center Transceivers/Remotes (all)"

the name must match REMOTE to work. One has quotes the other doesn't.

Ok so I changed the line in /etc/lirc/hardware.conf to read 
REMOTE="mceusb"

I restarted the computer and it didn't work.  I unplugged the USB receiver and replugged it back in, and it worked, but only reads the arrows keys on the keyboard.  I tried restarting it again and it doesn't work until I unplug and replug it back in, and then still only the arrow keys.

I'm tempted to just get this combined transmitter/reciever, since it seems to work out of the box with mythtv - [http://www.usbuirt.com/](http://www.usbuirt.com/) (that is mythcontrol center has an option for UIRT in both transmitter and receiver drop downs)

Here are the first lines from lircd.conf.mceusb
> begin remote

  name        mceusb
  bits                 16
  flags  RC6|CONST_LENGTH
  eps                  30
  aeps                100

  header       2667   889
  one           444   444
  zero          444   444
  pre_data_bits        21
  pre_data        0x37FF0
  gap              105000
  toggle_bit           22
  rc6_mask    0x100000000

---

