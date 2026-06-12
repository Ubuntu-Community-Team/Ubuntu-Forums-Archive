---
title: "pvr-350 remote and irblaster"
date: 2008-04-01
forum: Mythbuntu
---

### Post by drfoz on 2008-04-01
i have a a problem, that when i go to ir devices in mythbuntu control center  and select "hauppauge tv card" for my remote, it works. but when i select serial dish controller for my irblaster neither works. wondering if anybody has a fix for this.

---

### Post by foxbuntu on 2008-04-02
please post your lircd.conf and hardware.conf from the non-working state.

---

### Post by drfoz on 2008-04-02
```
brian@brian-desktop:~$ cat  /etc/lircd.conf
#This configuration has been automatically generated via
#the Ubuntu LIRC package maintainer scripts.
#
#It includes the default configuration for the remote and/or
#transmitter that you have selected during package installation.
#
#Feel free to add any custom remotes to the configuration
#via additional include directives or below the existing
#Ubuntu include directives from your selected remote and/or
#transmitter.

#Configuration for the Hauppauge TV card remote:
include /usr/share/lirc/remotes/hauppauge/lircd.conf.hauppauge

#Configuration for the Serial Port (UART) : Dish Receiver transmitter:
include /usr/share/lirc/transmitters/dish/general.conf
```


```
brian@brian-desktop:~$ cat /etc/lirc/hardware.conf
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Hauppauge TV card"
REMOTE_MODULES="lirc_dev lirc_i2c"
REMOTE_DRIVER=""
REMOTE_DEVICE=""
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Serial Port (UART) : Dish Receiver"
TRANSMITTER_MODULES="lirc_dev lirc_serial"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
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
```

---

### Post by Kheops_74 on 2008-04-13
Any news? I have the same problem. I have a pvr150 and Hardy Heron. The remote work fine alone but nothing works if i choose a remote and a transmitter.

In your hardware.conf, there is no device (REMOTE_DEVICE=""). Do you have one when your remote works?

Thanks

---

### Post by Kheops_74 on 2008-04-26
Do you made more test? I'm not able to get the IR Blaster work at this time.

---

### Post by laga on 2008-04-26
I wonder if this bug report is related? [https://bugs.launchpad.net/mythbuntu/+bug/222250](https://bugs.launchpad.net/mythbuntu/+bug/222250)

I assume we're seeing two issues in this thread:

a) PVR-350 remote + serial IR blaster not working
b) PVR-150 remote + PVR-150 IR blaster not working

The bug report I've posted above probably only applies to case b).

---

### Post by thafemann on 2008-04-26
PVR-500 same issue.

Tom

---

### Post by kfrance on 2008-04-26
If you look at the release notes for 8.04, [http://www.mythbuntu.org/8.04/Release_notes]("http://www.mythbuntu.org/8.04/Release_notes"), under the lirc section you can see that the transmitter selection works except for the PVR-150. So their aware of the situation. I hope that their is a fix soon.

---

### Post by ahood on 2008-06-05
I too appear to be having this same problem. I have the hauppauge A415-HPG remote (silver) looking and a serial RS232 transmitter (irblaster.com). The Hauppauge silver remote works when ir transmitter is unchecked. However, if I check ir transmitter in MCC, the remote stops working.

---

### Post by gfowler on 2008-06-06
> **ahood said:**
> I too appear to be having this same problem. I have the hauppauge A415-HPG remote (silver) looking and a serial RS232 transmitter (irblaster.com). The Hauppauge silver remote works when ir transmitter is unchecked. However, if I check ir transmitter in MCC, the remote stops working.

Take a look at your /etc/lirc/lirc.conf file.  The scipt puts the remote before the serial include, swap them, serial include before remote include.  You also my have to reconfigure setserial (see chapter 12 of 8.04 Install guide). You also will need to change your channel change script to use the /dev/lircd1 daemon, i.e. irsend -d /dev/lircd1.

Jerry

---

### Post by ahood on 2008-07-19
> **gfowler said:**
> Take a look at your /etc/lirc/lirc.conf file.  The scipt puts the remote before the serial include, swap them, serial include before remote include.  You also my have to reconfigure setserial (see chapter 12 of 8.04 Install guide). You also will need to change your channel change script to use the /dev/lircd1 daemon, i.e. irsend -d /dev/lircd1.

Jerry

Thank you gfowler!

Your post, plus a post titled[ [COLOR="Blue"]Serial IR Blaster - IRSEND hardware does not support sending[/COLOR]]("http://ubuntuforums.org/showthread.php?t=789608&highlight=ir+blaster") by Don Giovanni,  enabled me figure this serial irblaster configuration. Below were the steps I took.

**Step 1. Edit /etc/lirc/lircd.conf**

Cut and pasted the Serial UART line above the Hauppauge line

Command
> sudo nano /etc/lirc/lircd.conf

Output 
> #This configuration has been automatically generated via
#the Ubuntu LIRC package maintainer scripts.
#
#It includes the default configuration for the remote and/or
#transmitter that you have selected during package installation.
#
#Feel free to add any custom remotes to the configuration
#via additional include directives or below the existing
#Ubuntu include directives from your selected remote and/or
#transmitter.

#Configuration for the Serial Port (UART) : Motorola Cable box transmitter:
include /usr/share/lirc/transmitters/motorola/dctxxxx.conf

#Configuration for the Hauppauge TV card remote:
include /usr/share/lirc/remotes/hauppauge/lircd.conf.hauppauge


*Note: Be sure to remember/write down the location of the irblaster configuration file (e.g., /usr/share/lirc/transmitters/motorola/dctxxxx.conf).*


**Step 2. Check/Configure setserial**
Because I have only one serial port in my system, I commented out the second serial device by placing a hash (#) mark in front of the line. (see page 112 of [[COLOR="Navy"]Mythbuntu Installation Manual[/COLOR]]("http://www.mythbuntu.org/documentation/mythbuntu_8.04_installation.pdf")).

*Note: I used the BIOS to verify the IrQ number and address of the serial device I want to have configured. My BIOS had the serial IrQ as 4 and address as 0x3f8.*

Command
> sudo nano /etc/modprobe.d/lirc-serial

Output
> #COM1 equivalent, /dev/ttyS0
**options lirc_serial irq=4 io=0x3f8**
#COM2 equivalent, /dev/ttyS1
#options lirc_serial irq=3 io=0x2f8


**Step 3. Lirc_serial Driver**

Check to see if lirc_serial driver is running and if so, disable kernel serial support. (see page 112 of [[COLOR="Navy"]Mythbuntu Installation Manual[/COLOR]]("http://www.mythbuntu.org/documentation/mythbuntu_8.04_installation.pdf").

Command to chec if lirc_serial driver is running
> dmesg | grep lirc

Output
> [   70.795657] lirc_dev: IR Remote Control driver registered, at major 61 
[   71.119165] lirc_i2c: chip 0x10020 found @ 0x18 (Hauppauge IR)
[   71.119193] lirc_dev: lirc_register_plugin: sample_rate: 10
**[   71.682351] lirc_serial: auto-detected active high receiver**
[   71.682360] lirc_dev: lirc_register_plugin: sample_rate: 0

Commands to disable kernel serial support.
> sudo apt-get install setserial
> sudo dpkg-reconfigure setserial
When prompted, choose the 'manual' option
> sudo nano /var/lib/setserial/autoserial.conf

Output of Autoserial.conf
> #
###PORT STATE GENERATED USING AUTOSAVE-ONCE###
###AUTOSAVE-ONCE###
###AUTOSAVE-ONCE###
###AUTOSAVE###
#
# If you want to configure this file by hand, use
# dpkg-reconfigure setserial
# and change the configuration mode of the file to MANUAL. If you do not do thi$
# package.
#
**/dev/ttyS0 uart none**
# /dev/ttyS1 uart 16550A port 0x02f8 irq 3 baud_base 115200 spd_normal skip_test

*Note: I commented out the ttyS1 irc 3 device because I physically don't have a second serial port. I replaced the long line that followed ttyS0 uart with 'none', which disables kernel support for this device.*


**Step 4. Copy Channel Change Script**
Copied channel change script to /usr/local/bin

Command to copy channel change script
> sudo cp /usr/share/doc/mythtv-backend/contrib/channel_changers/change-channel-lirc.pl /usr/local/bin/


**Step 5. Irblaster remote name**
We next need to find out the name of irblaster remote as specified in the irblaster configuration file (see Step 1 above).

Command
> sudo nano /usr/share/lirc/transmitters/motorola/dctxxxx.conf

Output of my dctxxxx.conf
> #
# this config file was automatically generated
# using lirc-0.6.6(serial) on Fri Mar 28 22:46:44 2003
#
# contributed by shane bradley
#
#
#
# brand:                       Motorola
# model no. of remote control: DCT2000
# devices being controlled by this remote:
#
                                                                               $
begin remote
 **name  DCT2000**
  bits           16
  flags SPACE_ENC|CONST_LENGTH
  eps            30
  aeps          100
  
  ...truncated


*Note: Write down the remote name (e.g., DCT2000)*


**Step 6. Edit change-channel-lirc.pl**

Command
>  sudo nano /usr/local/bin/change-channel-lirc.pl

Output of change-channel-lirc.pl (see changed lines in **[COLOR="DarkRed"]bold red[/COLOR]**)
> #!/usr/bin/perl

# make sure to set this string to
# the corresponding remote in /etc/lircd.conf
$remote_name = "**[COLOR="DarkRed"]DCT2000[/COLOR]**";

sub change_channel {
        my($channel_digit) = @_;
        system **[COLOR="DarkRed"]("irsend -d /dev/lircd1 SEND_ONCE $remote_name $channel_digit");[/COLOR]**
        sleep 1;
}

$channel=$ARGV[0];
sleep 1;
if (length($channel) > 2) {
        change_channel(substr($channel,0,1));
        change_channel(substr($channel,1,1));
        change_channel(substr($channel,2,1));
} elsif (length($channel) > 1) {
        change_channel(substr($channel,0,1));
        change_channel(substr($channel,1,1));
} else {
        change_channel(substr($channel,0,1));
}
system (**[COLOR="DarkRed"]"irsend -d /dev/lircd1 SEND_ONCE $remote_name ENTER");[/COLOR]**


**Step 7. Edit /etc/lirc/hardware.conf**

Command
> sudo nano /etc/lirc/hardware.conf


Output (see **[COLOR="DarkRed"]red bold[/COLOR]** text below)
> # /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Hauppauge TV card"
REMOTE_MODULES="lirc_dev lirc_i2c"
REMOTE_DRIVER=""
REMOTE_DEVICE="**[COLOR="DarkRed"]/dev/lirc0[/COLOR]**"
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="**[COLOR="DarkRed"]DCT2000[/COLOR]**"
TRANSMITTER_MODULES="lirc_dev lirc_serial"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="**[COLOR="DarkRed"]/dev/lirc1[/COLOR]**"
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



**Step 8. Restart LIRC Daemon**

Command
> sudo /etc/init.d/lirc restart


**Step 9. Test out Serial IRBlaster**
I used my Logitech webcam as described by andymyth at [[COLOR="Blue"]Linux Infrared Remote Control[/COLOR]]("http://www.eggshellskull.com/lirc/trouble/index.php") 

> Testing to see if anything is being emitted from your IR transmitter:
There are two ways to do this. If you are building your own IR transmitter, solder a small LED to it instead of your IR Blaster. This will allow you to actually see if anything is being transmitted, as the LED should kind of flicker.

For those who either don't want to solder on an LED, or who bought an IR Blaster and don't want to risk ruining it, there is a second method. If you have a digital camera, aim it at the IR Transmitter, and watch on the camera's little LCD screen to see live action. The only way this works is by looking on the LCD screen of the camera; the view finder will not work. You *should* be able to see whether or not the IR Blaster is transmitting by running the change_chan.sh script. You can try this with a normal remote by aiming its IR transmitter at the camera and pushing buttons on it while looking at the camera's LCD. If you see lights coming from your IR Blaster, you know it is working, but you probably just have the wrong config. If you don't see lights, it doesn't necessarily mean it's not working, but could indicate a setup problem (my camera never picked up light from my IR Blaster, though it would pick up light from all my other remotes). Many people have reported success in using this method. see [[COLOR="Blue"]Linux Infrared Remote Control[/COLOR]]("http://www.eggshellskull.com/lirc/trouble/index.php") 

---

### Post by Kheops_74 on 2008-07-22
As gfowler said earlier, i swap the remote and the transmitter include in the /etc/lirc/lirc.conf file. I read this tutorial too ([https://help.ubuntu.com/community/InstallLirc/Hardy](https://help.ubuntu.com/community/InstallLirc/Hardy)). My hauppauge pvr150 (remote and IR Blaster) work great with my motorola dsr405 decoder!

Thanks

K

---

### Post by LarryJ2 on 2008-08-10
I wasn't certain the IR Blaster I purchased was working (turned out it was so I still must have a mythbuntu configuration error).  Subsequently  I wrote this script to exercise the  serial IR Blaster while I peered at it with my camera.  

Just plug your serial IRBlaster into your first COM port (/dev/ttyS0) then run this short python script.  It will "wink" your IR emitter on and off so if you have an Infra Red sensitive camera,  at least you can determine if the IR Blaster hardware is emiting.  

One big Caveat:  If you have disabled kernel serial support using setserial as described above (sudo dpkg-reconfigure setserial), this script won't run. You'll be greeted with "Can not configure port... Input/Output Error " exception error and related traceback info. Currently, I don't understand how to restore kernel serial port support in MythBuntu.  So you have been warned: Use this script to check your hardware irblaster on a non-mythbuntu installation.

Also note for DishNetwork Receiver users, in Step 6, the line
**system ("irsend -d /dev/lircd1 SEND_ONCE $remote_name ENTER");**
should be changed to
**system ("irsend -d /dev/lircd1 SEND_ONCE $remote_name select");**
Dishnetwork remotes don't have an "ENTER" key but do have a "Select" key.

Four days and still no channel changer!

Channel changer script works fine from a terminal
```
$ lj@mythtv:/$ /usr/local/bin/change-channel-lirc.pl 200
```
causes the dish receiver to bring up CNN channel200
but either from the mythtv box keyboard or from the remote, entering 
valid channel number does nothing.  I get an error in the
backend log (/var/log/mythtv/backend.log) that says
>  TVRec(3) Error: Failed to set channel to 200.

So I put a couple print statements in the perl change-channel-lirc.pl
script. Apparently, the perl script is not being called.  Apparently
I'm not the first to experience this problem.  In [http://www.gossamer-threads.com/lists/mythtv/users/29005](http://www.gossamer-threads.com/lists/mythtv/users/29005) I read 

> I've figured out what's the problem. It seems that the sourceid of the
cardinput and channel are different somehow. That way, the external
changer command never is called. 

Now if I can only understand what he is talking about! 



Larry

---

