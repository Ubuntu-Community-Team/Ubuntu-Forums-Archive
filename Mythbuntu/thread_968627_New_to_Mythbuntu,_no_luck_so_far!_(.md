---
title: "New to Mythbuntu, no luck so far! :("
date: 2008-11-02
forum: Mythbuntu
---

### Post by bpowell2005 on 2008-11-02
Hello all!

I'm completely new to Mythbuntu, and I'm not having any luck getting my HTPC up and running like I'd like!

I took an HTPC that was running Mythdora for a couple of years and blew it away for the Mythbuntu 8.10 load.

Here are my specs...

64-bit dual-core processor.
2x Hauppauge 150 PVR cards (only using one though).
Nvidia GeForce 6200 video card. 
Video source is a DirectTV D10 STB.

I'm trying to take S-video out of the STB into the PVR 150...I can get that running. However, the Hauppauge remote will not work (although I set it up in installation) and I can't get the IR led (attached with the Hauppauge remote sensor) to change channels on the STB.

I'm completely new to Mythbuntu...and not terribly Myth Savvy (although I thought I was before this!)

Please help!

I have SSH access to the box right now, but can't get in front of it due to a sleeping child. Please let me know what information you'd like me to grab to help T-shoot this.

Thanks in advance for all of your support. I'm running Hardy on my laptop now for over 6 months and have been loving it...would like to make Ubuntu a part of the HTPC as well!

---

### Post by bpowell2005 on 2008-11-03
Just to add a little information:

The real problem appears to be LIRC right now.

I can get LIRC to respond to the Hauppauge 150 remote if I edit the /etc/lircd.conf file and remark out the line regarding the trasmitter...when I do that, the remote works. 

However, I need the transmitter to work so it can change channels on the DirectTV D10 STB.

I found and downloaded a RC32 remote conf file (the remote for the D10) and tried to use that in the lircd.conf file, but again, the LIRC becomes unresponsive once a transmitter line is selected.

Any ideas anybody? Please?

Thanks!

---

### Post by fryed_1 on 2008-11-03
While I'm still working on getting my IR transmitter going, I noticed that if you use the myth control center to change the IR transmitter, it will change the remote as well and you will have to revert back to your manual settings.

I found it's easier to just setup both (even if they're wrong) to get some default values in there, then edit lircd.conf and hardware.conf from the command line and restart as you need it to test.

If you get the transmitter work, please update with which drivers/modules you used.  I've been just going through ones that would seem compatible one at a time and sending different known codes to my scientific atlanta 2200 stb with no luck yet.

---

### Post by bpowell2005 on 2008-11-03
> **fryed_1 said:**
> While I'm still working on getting my IR transmitter going, I noticed that if you use the myth control center to change the IR transmitter, it will change the remote as well and you will have to revert back to your manual settings.

I found it's easier to just setup both (even if they're wrong) to get some default values in there, then edit lircd.conf and hardware.conf from the command line and restart as you need it to test.

If you get the transmitter work, please update with which drivers/modules you used.  I've been just going through ones that would seem compatible one at a time and sending different known codes to my scientific atlanta 2200 stb with no luck yet.

Yeah, I've noticed that little quirk too. Still no joy getting the transmitter half of the PVR150 IR device working...LIRC is unresponsive any time a transmitter is selected in the lircd.conf....grumble grumble. I'll keep searching the interwebs...hopefully something will come up.

Another plan is to try Mythdora (I've had success with that install before)....but I hate to give up on Ubuntu.

---

### Post by gfowler on 2008-11-03
> **bpowell2005 said:**
> Just to add a little information:

The real problem appears to be LIRC right now.

I can get LIRC to respond to the Hauppauge 150 remote if I edit the /etc/lircd.conf file and remark out the line regarding the trasmitter...when I do that, the remote works. 

However, I need the transmitter to work so it can change channels on the DirectTV D10 STB.

I found and downloaded a RC32 remote conf file (the remote for the D10) and tried to use that in the lircd.conf file, but again, the LIRC becomes unresponsive once a transmitter line is selected.

Any ideas anybody? Please?

Thanks!

Take a look in /etc/lirc/lircd.conf and note which comes first the transmitter include or receiver include.  Try swapping them, putting the transmitter include in first.  As goofy as that may sound I had the near same issue with a PVR-350 remote and a generic IR transmitter.  The system would work if tx include is first.  

Jerry

---

### Post by bpowell2005 on 2008-11-05
First, thanks for your help!

Okay! Some progress! Not there yet though.
Gflower: Thanks for the tip! I switched the transmitter and remote lines, and things are looking up (at least the remote works in IRW again!)

Now, when I try to use irsend to test the blaster, I get "Transmission failed"...I'll paste the code below.

```
mal@Mythbox:~$ irsend send_once directv 1
irsend: command failed: send_once directv 1
irsend: transmission failed

```

Here is the output from dmesg | grep lirc

```
[35037.804785] lirc_pvr150: failed to get data for code 0, key 6000 -- check lircd.conf entries
```

And here is a syslog message:

```
Nov  5 05:33:51 Mythbox lircd-0.8.3[8305]: accepted new client on /dev/lircd
Nov  5 05:33:51 Mythbox lircd-0.8.3[8305]: write failed
Nov  5 05:33:51 Mythbox lircd-0.8.3[8305]: Protocol error 
Nov  5 05:33:51 Mythbox lircd-0.8.3[8305]: error processing command: send_once directv 1
Nov  5 05:33:51 Mythbox lircd-0.8.3[8305]: transmission failed
Nov  5 05:33:51 Mythbox lircd-0.8.3[8305]: removed client
Nov  5 05:33:51 Mythbox kernel: [35037.804785] lirc_pvr150: failed to get data for code 0, key 6000 -- check lircd.conf entries
```

I am stumped! I've put the hauppauge firmware in /lib/firmware...and I think I've set up the hardware.conf and lircd.conf as I should but I'm still not transmitting IR. Any ideas? Anything else you'd like to see? (related to the problem! :) )

I'll post my .conf's below...

Thanks!

lircd.conf
```

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

include /usr/share/lirc/transmitters/directtv/general.conf
#Configuration for the Hauppauge TV card remote:
include /usr/share/lirc/remotes/hauppauge/lircd.conf.hauppauge

#Configuration for the None transmitter:
#include /usr/share/lirc/transmitters/directtv/general.conf
```

hardware.conf

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Hauppauge TV card"
REMOTE_MODULES="lirc_dev lirc_pvr150"
# lirc_i2c" <-- remarked this module out from a above on advice from a forum
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="directv"
TRANSMITTER_MODULES="lirc_dev lirc_pvr150"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc0"
TRANSMITTER_LIRCD_CONF="directtv/general.conf"
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

Remote works fine, so I won't post it's output...but here is the transmitter section:

general.conf

```
#
# this config file was automatically generated
# using lirc-0.8.1-CVS-pvr150(default) on Thu Nov 23 11:12:04 2006
#
# contributed by Chris Jacobs
#
# brand: DirecTV HD20-100
# model no. of remote control: HD20-100
# devices being controlled by this remote: DirecTV HD20-100
#

begin remote

  name	directv
  flags RAW_CODES
  eps            30
  aeps          100

  ptrail        613
  repeat     0     0
  gap    29767

      begin raw_codes

          name 1
             6000    1150    1250    1100     650     550
              650     550     650     550     650     500
              650    1150     650     550     650    1150
              600

          name 2
             6000    1100    1250    1150     650     550
              650     550     600     550     650     550
             1250     550     650     550    1200     550
              650

          name 3
             6000    1150    1250    1100     650     550
              650     550     650     550     650     550
             1200    1150     650     550    1250    1150
              600

          name 4
             6000    1150    1250    1150     650     500
              650     550     650     550     650    1150
              650     500     650     550    1250    1150
              650

          name 5
             6000    1150    1250    1100     650     550
              650     550     650     500     650    1150
              650    1150     650    1150     600     550
              650

          name 6
             6000    1150    1250    1150     650     500
              650     550     650     550     650    1150
             1200     550     650    1150     650    1150
              600

          name 7
             6000    1100    1250    1150     650     550
              650     500     650     550     650    1150
             1250    1100     650    1150    1250     550
              650

          name 8
             6000    1150    1250    1100     650     550
              650     550     650     550    1200     550
              650     550     650    1150    1200     550
              650

          name 9
             6000    1100    1300    1100     650     550
              650     550     650     500    1250     550
              650    1150     650    1150    1200    1150
              650

          name 0
             6000    1150    1250    1150     650     500
              650     550     650    1150     650     550
              650    1100     650    1150    1250     550
              650

          name dash
             6000    1100    1300    1100     650     550
              650     550     650    1100     650     550
             1250     550     650    1100    1250    1150
              650

          name last
             6000    1100    1300    1100     650     550
              650     550     650     500    1250    1150
             1250    1150    1200    1150     650     550
              650

          name guide
             6000    1100    1300    1100     650     550
              650     550    1250     500    1250     550
              650     550     650     550     600     550
              650

          name up
             6000    1100    1300    1100     650     550
              650     550    1250     500     650     550
              650    1150    1250     500    1250    1150
              650

          name down
             6000    1150    1250    1100     650     550
              650     550    1250     500     650     550
             1250     550    1250    1150     600     550
              650

          name left
             6000    1150    1250    1150     650     500
              700     500    1250     550     650     550
             1250    1100    1250    1150     650    1150
              600

          name right
             6000    1150    1250    1100     650     550
              650     550    1250     500     650    1150
              650     550    1250    1100     650    1150
              650

          name select
             6000    1150    1250    1100     700     500
              650     550    1250     550     650    1100
              650    1150    1250    1150    1200     550
              650

          name action
             6000    1150    1250    1150     650     500
              650     550    1250     550    1250     550
              600    1150     650     550     650    1150
              650

          name list
             6050    1100    1250    1150     650     500
              650     550    1250     550    1250     550
             1200     550     650     550    1250     550
              650

          name info
             6000    1100    1250    1150     650     550
              650     500    1250     550    1250    1150
             1250     500     650    1150     650    1150
              650

          name back
             6000    1150    1250    1150     650     500
              700     500    1250     550     650    1150
             1200    1150     650     550     650     550
              650

          name power
             6000    1150    1250    1100     650     550
             1250     550     650     550     650     500
              650     550    1250    1150    1250     500
              650

          name exit
             6000    1150    1250    1150     650     500
              650     550    1250     550     650    1150
             1200     550    1250    1150    1250    1100
              650

          name ch-
             6000    1100    1250    1150     650     550
              650     500     650     550    1250    1150
             1250     550    1200     550    1250    1150
              650

          name ch+
             6000    1100    1300    1100     650     550
              650     500     700     500    1250    1150
              650    1150    1200     550    1250     550
              650

      end raw_codes

end remote

```

---

### Post by RoyalPro on 2008-11-05
Yeah I say make your own .conf file with your directtv remote at the top and the haupauge remote that works under it and just have it in the remote section.  I couldn't get mine to work in the transmitter section, but with them combined in the remote section is how I got it working.  And again I had to put the "blaster"/transmitter part above the remote in my custom conf.

Here is a link to my post, if others would like to see it.
[http://ubuntuforums.org/showthread.php?p=6110256#post6110256]("http://ubuntuforums.org/showthread.php?p=6110256#post6110256")

---

### Post by gfowler on 2008-11-06
I note that both the receiver and transmitter are the same device (lirc0).  I don't have a PVR-150 so can't tell you if that is normal or not.  With a PVR-550 rx and a generic tx I have two devices (lirc0 and lirc1).  This may be just smoke and mirrors, but may give you a direction to persue.

Jerry

---

