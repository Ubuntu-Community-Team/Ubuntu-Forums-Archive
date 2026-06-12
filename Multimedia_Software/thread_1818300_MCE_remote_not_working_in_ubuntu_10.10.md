---
title: "MCE remote not working in ubuntu 10.10"
date: 2011-08-04
forum: Multimedia Software
---

### Post by Dr Bones on 2011-08-04
Hi,

I installed ubuntu 10.10 a couple of months ago and have yet to get my MCE RC-6 remote control to work with it.  I have searched different posts as to how to possibly remedy the problem as I have never run onto this problem with the previous releases of ubuntu as the installation of lirc was follow the on screen setup and it just worked right out of the box.  I believe as others have said in other posts it has to do with the fact the remote modules were moved to the kernel and therefore are causing headaches for people setting this up.  

I unlike many people who have posted have not got this working but where my problem is different is that I am getting no output from running irw, whereas it seems that so many different people have the problem that only certain keys are working.  I have found a thread where it starts that the original poster has my same problem and the thread is hijacked and the conversation is brought back to this only certain keys work (arrow and the like) and it is being detected as a keyboard.  I reitterate that I receive no output at all from irw.

I will try and be as verbose as possible and ask if there is some info I am missing, but here is a list of the different outputs that may help people diagnose my problem:

uname -a
[PHP]
Linux bebeau-desktop 2.6.35-30-generic #56-Ubuntu SMP Mon Jul 11 20:01:08 UTC 2011 x86_64 GNU/Linux
[/PHP]

dmesg
[PHP]
[   14.401252] IR JVC protocol handler initialized
[   14.406194] IR Sony protocol handler initialized
[   14.407062] lirc_dev: IR Remote Control driver registered, major 249 
[   14.407062] Registered IR keymap rc-rc6-mce
[   14.407062] input: Media Center Ed. eHome Infrared Remote Transceiver (1784:0001) as /devices/virtual/rc/rc0/input7
[   14.407062] rc0: Media Center Ed. eHome Infrared Remote Transceiver (1784:0001) as /devices/virtual/rc/rc0
[   14.407062] mceusb 4-2:1.0: Registered Topseed eHome Infrared Transceiver on usb4:3
[   14.407062] usbcore: registered new interface driver mceusb
[   14.410005] rc rc0: lirc_dev: driver ir-lirc-codec (mceusb) registered at minor = 0
[   14.411252] IR LIRC bridge handler initialized
[/PHP]

cat /proc/bus/input/devices (I left out the portion of the output that does not apply)
[PHP]
I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="Media Center Ed. eHome Infrared Remote Transceiver (1784:0001)"
P: Phys=usb-0000:00:12.0-2/input0
S: Sysfs=/devices/virtual/rc/rc0/input7
U: Uniq=
H: Handlers=kbd event7 
B: EV=100003
B: KEY=fff 0 108fc326 217604100000000 0 118000 418000100001 9e968000000000 10000000
[/PHP]

lsusb
[PHP]
Bus 008 Device 003: ID 1058:1102 Western Digital Technologies, Inc. 
Bus 008 Device 002: ID 046d:0a0b Logitech, Inc. ClearChat Pro USB
Bus 008 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c051 Logitech, Inc. G3 (MX518) Optical Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 1784:0001 TopSeed Technology Corp. eHome Infrared Transceiver
Bus 004 Device 002: ID 046d:c30e Logitech, Inc. UltraX Keyboard (Y-BL49)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[/PHP]

lsmod | grep lirc
[PHP]
ir_lirc_codec           3888  0 
lirc_dev               11209  1 ir_lirc_codec
ir_core                16906  9 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,rc_rc6_mce,ir_nec_decoder,mceusb
[/PHP]

/etc/lirc/hardware.conf

Note: I have tried a few different things as per these different links I have found and will the different configurations I have tried with none of the configurations working(the link preceeds the config setup I have tried) 

[http://ubuntuforums.org/archive/index.php/t-1593122.html](http://ubuntuforums.org/archive/index.php/t-1593122.html)
[PHP]
#Chosen Remote Control
REMOTE="Linux input layer (/dev/input/eventX)"
REMOTE_MODULES=""
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/by-path/usb-0000:00:12.0-2/input0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="devinput/lircd.conf.devinput"
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
[/PHP]

[http://ubuntuforums.org/showthread.php?p=9952389#post9952389](http://ubuntuforums.org/showthread.php?p=9952389#post9952389)
[PHP]
#Chosen Remote Control
REMOTE="Linux input layer (/dev/input/eventX)"
REMOTE_MODULES=""
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/event7"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="devinput/lircd.conf.devinput"
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
[/PHP]

cat /etc/lirc/lircd.conf
[PHP]
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

#Configuration for the Linux input layer (/dev/input/eventX) remote:
include "/usr/share/lirc/remotes/devinput/lircd.conf.devinput"
[/PHP]

I have updated /etc/init.d/lirc such that the line below is as it should as per the following link ([http://www.linuxquestions.org/questions/linux-software-2/ubuntu-10-10-and-lirc-works-843751/](http://www.linuxquestions.org/questions/linux-software-2/ubuntu-10-10-and-lirc-works-843751/))
[PHP]
for protocol in rc5 nec rc6 jvc sony mceusb; do
[/PHP]

I also followed the instructions there with no luck by changing the LOAD_MODULES="true" to "false" and also have tried "true"

I have seen the following thread and the original poster seems to have my same problem but the thread changed direction in that it went to the problem being only detecting some of the key presses

[http://ubuntuforums.org/showthread.php?t=1627289](http://ubuntuforums.org/showthread.php?t=1627289) 

I have also tried uninstalling lirc-modules-source as I remember I had read it may interfere with the modules that are included in the kernel.  This got me to the same place and I got results that like before ended the same with no results with irw.

As you can see I have seen a number of different things but like I said previously I seem to have no output from running irw which others posting seem to differ, so I decided to make this post in hopes of helping others in a situation similar to that of mine  Thank you very much in advance!

---

### Post by Dr Bones on 2011-08-04
Ok so I continued to look into this as it is driving me mad and I stumbled upon another way in which to test lirc besides that of irw.  I did the following to test it.

[PHP]sudo /etc/init.d/lirc stop
[/PHP]

Then I ran the following command
[PHP]sudo mode2 -m --driver=commandir
[/PHP]

It was very interesting as I did get some response when I pressed some of the keys on the remote I did noticed that there was output corresponding to keyboard keys being pressed (the arrow keys and the clear and enter buttons).  Still I have no output in irw when pressing these same buttons.

I also checked /etc/modprobe.d/blacklist as per this link ([http://ubuntuforums.org/showthread.php?t=1382688](http://ubuntuforums.org/showthread.php?t=1382688)) to see if maybe the lirc install was blacklisting the remote and the file was just blank so I assume I have either the wrong location for the file or there are just no blacklisted devices.

I am not sure if this will give someone the needed information in which to help me along on my mission to solve this problem.  Thank you again for the help in advance.

---

### Post by Dr Bones on 2011-08-04
I found another web site ([http://www.commandir.com/content/view/73/88/](http://www.commandir.com/content/view/73/88/)) which I tried as nothing else seems to be working so I figured, hey why not.  Well long story short I still am having problems getting this thing to work.  Well reading the information on this website brought me to installing the Infrared Remote Control package in the ubuntu software center.

Googling the Infrared Remote Control brought me to a website in which the someone said that there remote stopped working when they installed lirc so I removed it to see if the remote buttons did anything then and I noticed that the arrow buttons were working as if I was using the arrow keys on the keyboard to navigate around on the desktop.

I am not sure what to make of this and wonder why when I install lirc, the remote is no longer doing anything at all.  I hope this can help shed some light on the problem.

---

### Post by qong on 2011-08-05
Hey Doc,

i have been having the exact same problem for about 4 days now.
Its driving me craaazy.

On the 1 hand, I dont wanna give up, but on the other hand, I'm seriously considering buying another reciever !!

If I do get any firther with this I'll post it here.

Otherwise, just wanted you to know you're not alone ;)

Good Luck.

---

### Post by Dr Bones on 2011-08-05
Hi Qong,

Your post made me think maybe there is something wrong with the receiver itself or maybe the driver for it.  I also tried using a Logitech Harmony remote which was programmed as a Media Center Remote and that also didn't work.  Both of the remotes worked fine and the receiver used to work about 6 months ago so I am baffled.

After finding that this also did not work I tried the ATI remote wonder I have and it works perfectly (although I don't like how the remote feels so I would rather have the Media Center Remote working).  I guess the next logical thing would be to try and replace the receiver and see if that is the problem.  If anyone has any other ideas I would love to hear them.  Again thanks in advance and have a nice day.

---

### Post by walrus_t on 2011-08-05
Same problem here :(

[http://ubuntuforums.org/showthread.php?p=11120289#post11120289]("http://ubuntuforums.org/showthread.php?p=11120289#post11120289")

I'm also considering buying another remote, but which one?

---

### Post by Dr Bones on 2011-08-06
Hello all,

I tried setting up the remote on my mythtv backend (different machine also with 10.10) and found that it works perfectly, which leads me to believe that there is definitely something software related wrong with the setup.  I was wondering if maybe somehow the module itself is corrupt or something along those lines.  I don't have a time to trouble shoot this now, but I will delve further into this matter later on today.

I had a little bit more time to fiddle around with this and ran the following in order to get this thing to work again.

[PHP]sudo dpkg-reconfigure lirc[/PHP]

I chose the setting for all of the windows media remotes and no transceiver like I had on the computer that it did work on.  I then copied the /etc/lirc/hardware.conf file from the working computer to the non-functioning computer and was again not receiving any signals from the remote.  I ran the following and got a different result on the two machines

[PHP]uname -a[/PHP] 

On the computer that was working the following was listed

Linux bebeau-server 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:32:27 UTC 2010 x86_64 GNU/Linux

Hopefully someone could shed some new light on this matter.  Thank you in advance and have a wonderful weekend!

---

### Post by platosadvisor on 2011-08-24
I am having this exact same issue. Though, when I first installed lirc this afternoon everything worked as prescribed. Then XBMC crashed/hung on exit and left me with a black screen. 
I was heading out and didn't have time to **** around with it, so I did hard shutdown and came back to it later. When I came back, my remote was as unresponsive as yours, Doc.

If you get this figured out, please post here.

Thx

---

### Post by platosadvisor on 2011-08-24
I found this thread....
[http://ubuntuforums.org/showthread.php?p=9984844#post9984844](http://ubuntuforums.org/showthread.php?p=9984844#post9984844)
Option 2 worked for me, thought I'd share.

Now to fix the xbmc crash on exit....

---

### Post by Dr Bones on 2011-08-26
After trying everything I could think of I decided to go the reinstall route as I have my /home directory on a separate partition.  It worked like it had so many different times before and just worked perfectly without any fussing around.  I am not going to mark this thread as solved as hopefully someone will stumble upon this thread and have an idea as to what was the source of the problem in the first place in order to help others who may still have this problem.  Best of luck to all of you.

---

