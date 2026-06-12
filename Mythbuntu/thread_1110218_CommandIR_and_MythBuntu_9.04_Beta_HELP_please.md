---
title: "CommandIR and MythBuntu 9.04 Beta HELP please"
date: 2009-03-29
forum: Mythbuntu
---

### Post by efether on 2009-03-29
Let's see...how to make a long story short --  I used to run MythTV on top of Fedora, but I upgraded my system, so decided to try MythBuntu.  At first, I tried 8.10, but kept getting MySQL errors, so thought I'd try 9.04 Alpha 6.1, because it was suppose to fix the MySQL issues.  It did, and was stupid easy to set up.  Loved it.  However, my OLD USB-IR Blaster is a pain to set up, with custom LIRC builds...and really didn't want to go through all of that again, so I did some research and found that CommandIR was the one to get.  SO....I ponied up the $100 and got the CommandIR Mini and one IR emitter.  It came yesterday (Saturday, March 28th).  I hooked it up, I followed the instructions...and....NOTHING.  I'm not worried about Remotes right now, I just want it to change channels on my Dish Network JVR 2700 receiver.  I get nothing.  I then tell it to use my Mac Mini Remote, to see if IRW works...nothing.  I was up until 4:30am trying to get this thing to work...I didn't work that hard on my old USB-IRB.

So...here are the details --

First...I followed the instructions on the CommandIR web page --

[http://www.commandir.com/content/view/37/54/](http://www.commandir.com/content/view/37/54/)

In particular, the MythBuntu pages --

[http://www.commandir.com/content/view/53/75/](http://www.commandir.com/content/view/53/75/)

And yes, I did tell tell the CommandIR to use the IR Emitter in port #1 --
> irsend set_transmitters 1

Here's an excerpt out of /var/log/messages showing the discovery of the CommandIR unit --

> Mar 29 03:04:07 MythTV kernel: [ 1833.165632] commandir: CommandIR USB device now attached to commandir0
Mar 29 03:04:07 MythTV kernel: [ 1833.165638] commandir: commandir0 reset
Mar 29 03:04:07 MythTV kernel: [ 1833.165641] commandir: COMMANDIR0:
Mar 29 03:04:07 MythTV kernel: [ 1833.165642]  TX Enabled: 1, 2, 3, 4
Mar 29 03:04:07 MythTV kernel: [ 1833.165643]  RX: commandir0
Mar 29 03:04:07 MythTV kernel: [ 1833.165644]  LCD: commandir0
Mar 29 03:04:07 MythTV kernel: [ 1833.165676] usbcore: registered new interface driver commandir

Also, when I do a 'lsusb' it shows up (the Cygnal Integrated Products, Inc.)--

> Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0aec:3050 Neodio Technologies Corp. ND3050 8-in-1 Card Reader
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 10c4:0003 Cygnal Integrated Products, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


While slightly modified from the download version from the CommandIR pages for my appropriate remote/Satellite box, here is my /etc/lirc/lircd.conf file --

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

#Configuration for the None remote:
include "/usr/share/lirc/remotes/apple/lircd.conf.macmini"

#Configuration for the Command IR : Dish Receiver transmitter:
include "/usr/share/lirc/transmitters/dish/general.conf"


Here's my /etc/lirc/hardware.conf (again, changed for my equipment) --

> # /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Apple Mac mini USB IR Receiver"
REMOTE_MODULES=""
REMOTE_DRIVER="commandir"
REMOTE_DEVICE=""
REMOTE_LIRCD_CONF="/usr/share/lirc/remotes/apple/lircd.conf.macmin"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Command IR : Dish Receiver"
TRANSMITTER_MODULES="lirc_dev lirc_cmdir"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc0"
TRANSMITTER_LIRCD_CONF="/usr/share/lirc/transmitters/dish/general.conf"
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
FORCE_NONINTERACTIVE_RECONFIGURATION="true"
START_LIRCMD=""


LIRC doesn't start as a daemon, I get the following error when I execute '/etc/init.d/lirc start' (quote ticks excluded, used to show actually command used).

> $ sudo /etc/init.d/lirc start
 * Loading LIRC modules
   ...done.
 * Starting remote control daemon(s) : LIRC 
   ...fail!

I attribute the 'fail' the the wrong modules in the hardware.conf file.  Also, the '/dev/lirc0' doesn't exist.  Only pointer there is the '/dev/lircd'.  I've tried the every config I could think of  ... from "" to '/dev/lircd' to the default '/dev/lirc0'.  Nothing. The hardware.conf file was downloaded from CommandIR, ... above is the default with the only alterations to the correct files for my command sets (remotes, satellite box).  An error I'll hunt down once I can get it working with manual lircd start.  When launching LIRC manually, with this command 'sudo lircd -n --driver=commandir' I get the following --

> lircd-0.8.4a[19421]: lircd(commandir) ready

So, I'm thinking LIRC is working okay (btw, I'm running LIRC 0.8.4a).  When I fire up 'irw' it shows this --

> lircd-0.8.4a[19421]: lircd(commandir) ready
lircd-0.8.4a[19421]: accepted new client on /dev/lircd
lircd-0.8.4a[19503]: Child Initializing CommandIR Hardware
lircd-0.8.4a[19421]: CommandIR driver initialized


Again, everything looking good.  However, I never get any lights on the CommandIR when I point a remote at it, nor do I get any feedback when I click on the buttons of the Mac Remote (I'll change the remote later, it's not important to me just yet...I've always used an IR Keyboard for control.  Will get a better remote once I get everything else working).

Okay, so I close 'irw' and send the command 'irsend send_once dish 2', trying to simply change the channel on the box to '2'....here's the feedback from lircd --

> ircd-0.8.4a[19421]: lircd(commandir) ready
lircd-0.8.4a[19421]: accepted new client on /dev/lircd
lircd-0.8.4a[19503]: Child Initializing CommandIR Hardware
lircd-0.8.4a[19421]: CommandIR driver initialized
lircd-0.8.4a[19421]: removed client
lircd-0.8.4a[19421]: LIRC_deinit but keeping warm
lircd-0.8.4a[19421]: accepted new client on /dev/lircd
lircd-0.8.4a[19421]: removed client
lircd-0.8.4a[19421]: LIRC_deinit but keeping warm


When I hit <ctrl>-C to close lircd, I get the following error --

> lircd-0.8.4a[19503]: Waiting for signals to finish transmitting before shutdown

and the lircd process keeps running.  I have to 'kill -9' it to kill it. This tells me that LIRC is trying to talk to the CommandIR, but isn't...

I also make sure all the incorrect modules are not loaded.  When I run 'sudo rmmod lirc_cmdir commandir lirc_dev' I get --

> 
ERROR: Module lirc_cmdir does not exist in /proc/modules
ERROR: Module commandir does not exist in /proc/modules
ERROR: Module lirc_dev does not exist in /proc/modules


so, I know nothing is hanging around that isn't suppose to be.  

I'm out of ideas.  Remember, I never get any light besides a BLUE led on the CommandIR box.  It never acknowledges any remote pointed at it, and from what I can tell...the emitter never emits.

Help, please.  Next option is to blow away MythBuntu and go back to either 8.10 and work out the mysql issues...and then re-tackle this one...or roll-my-own again around Fedora.

Thanks,

Eric
[email]eric@thefetherfamily.org[/email]

---

### Post by efether on 2009-03-30
Well...after hours of pointless effort...I put my old USB-IRT back on the box...and got it working in 30 minutes.

Now I just have to return the CommandIR and get my $$$ back.

-Eric

---

### Post by bcjenkins on 2009-04-13
You are not alone. This just started happening to me as well on ArchLinux and I installed Jaunty today hoping it was just a bad package in that distro. I have not seen an improvement. 

B

---

