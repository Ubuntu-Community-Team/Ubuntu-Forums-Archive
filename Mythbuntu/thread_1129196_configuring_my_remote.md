---
title: "configuring my remote"
date: 2009-04-18
forum: Mythbuntu
---

### Post by r3vile on 2009-04-18
Hello,
I got a Sky Stat 2 TV Card with a remote control.
The remote control ("TTS35AI") was not listed in the Mythbuntu control center so I downloaded this file : [http://lirc.sourceforge.net/remotes/technisat/TTS35AI](http://lirc.sourceforge.net/remotes/technisat/TTS35AI)
Now i dont know where i have to put this file and how i can configure the command my remote sends (e.g. if i press the "Exit" button on my remote it sends "f" to mythbuntu, but i want it to send "Escape").

-I am using Mythbuntu 8.10
-I updated lirc to 0.8.4 
-the remote workes since i pluged it in, without any further configuration, so until now i have not modified any files

---

### Post by jb5 on 2009-04-18
The config file that tells mythTV what to do with each button press lives in```
~/.lirc/mythtv
```

Make a backup of the existing file and then edit away! :)

The only trouble I've had is when trying to use/define an action for the * button. 
I found that editing the lircd.conf file and changing the '*' to 'star' and then using that definition (star) in my ~/.lirc/mythtv file to map an action resolved that problem i.e. ```
begin
    remote = NOVA-T500
    prog = mythtv
#    button = *
    button = Star
    config = Left
    repeat = 0
    delay = 0
end
```

HTH

---

### Post by r3vile on 2009-04-18
So far so good, but "The remote control ("TTS35AI") was not listed in the Mythbuntu control center so I downloaded this file : [http://lirc.sourceforge.net/remotes/technisat/TTS35AI](http://lirc.sourceforge.net/remotes/technisat/TTS35AI) "
what should i do with this file now.
And why did my remote work without configuring it in the control center?

---

### Post by jb5 on 2009-04-18
I am by no means an expert on this........but,

The directory you need to start looking at is ```
/etc/lirc
```
Which will (should) contain at least two files -> hardware.conf & lircd.conf 

The file you downloaded will be the lircd.conf file. You will need a hardware.conf file also.

With listed remotes :-
hardware.conf is set up by mythtv, so you will need to investigate a suitable config file for your remote.

As for the remote already working, I know that certainly the arrow buttons (and the number buttons also?) often work without any extra configuration, as certain remote control functions are built into olperating system / lirc.

---

### Post by barney_1 on 2009-04-18
If you have a custon lircd.conf file for your remote here's how to use it:

1. Copy it to /etc/lirc (you should make a backup of your old file first:
```
sudo cp /etc/lirc/lircd.conf lircd.backup
sudo cp /LOCATION/OF/DOWNLOADED/lircd.conf /etc/lirc/lircd.conf
```

2. Restart lirc
```
sudo /etc/init.d/lirc restart
```

3. Test to see if it worked.  In a terminal window type "irw".  You should get a blank line and nothing else.  Press some buttons on the remote, you should see an output similar to this:
```
000000000000000a 00 Down lircd.conf.conf
```
If not, there's still something wrong.

4. Map the keys to work with mythtv.  That's the part that jb5 was talking about a few posts ago.

---

### Post by jb5 on 2009-04-19
Another piece of the puzzle is setting hardware.conf to point to the corrct device.

From [here](http://parker1.co.uk/mythtv_ubuntu2.php) - hardware.conf should look something like ```
# /etc/lirc/hardware.conf
#
# Arguments which will be used when launching lircd
LIRCD_ARGS=""

#Don't start lircmd even if there seems to be a good config file
START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER="dev/input"
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE="/dev/input/event2"
MODULES=""

# Default configuration files for your hardware if any
LIRCD_CONF=""
LIRCMD_CONF=""
```

I think the important line is ```
DEVICE="/dev/input/event2"
```
You will need to determine the correct event number for your ir remote, mine is event7 for instance. ```
ls -al /dev/input/by-path
```should display a line that contains "ir - device" associated with an "event number" (I'm not at my myth box so can't show the exact output). 

Edit your hardware.conf to match your setup.

---

### Post by r3vile on 2009-04-19
my remote seems to be event4, so i added this to hardware.conf
```
main@HTPC:~$ ls -al /dev/input/by-path
total 0
drwxr-xr-x 2 root root 180 2009-04-19 16:13 .
drwxr-xr-x 4 root root 320 2009-04-19 16:13 ..
lrwxrwxrwx 1 root root   9 2009-04-19 16:13 pci-0000:00:02.0-usb-0:1:1.0-event-kbd -> ../event1
lrwxrwxrwx 1 root root   6 2009-04-19 16:13 pci-0000:00:02.0-usb-0:1:1.1- -> ../js0
lrwxrwxrwx 1 root root   9 2009-04-19 16:13 pci-0000:00:02.0-usb-0:1:1.1-event- -> ../event2
lrwxrwxrwx 1 root root   9 2009-04-19 16:13 pci-0000:00:02.0-usb-0:2:1.0-event-mouse -> ../event3
lrwxrwxrwx 1 root root   9 2009-04-19 16:13 pci-0000:00:02.0-usb-0:2:1.0-mouse -> ../mouse1
lrwxrwxrwx 1 root root   9 2009-04-19 16:13 pci-0000:00:02.0-usb-0:5:1.0-event-ir -> ../event4
lrwxrwxrwx 1 root root   9 2009-04-19 16:13 platform-pcspkr-event-spkr -> ../event7

```

the hardware.conf is now:
```
# /etc/lirc/hardware.conf
#
# Arguments which will be used when launching lircd
LIRCD_ARGS=""

#Don't start lircmd even if there seems to be a good config file
START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER="dev/input"
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE="/dev/input/event4"
MODULES=""

# Default configuration files for your hardware if any
LIRCD_CONF=""
LIRCMD_CONF=""
```

now i tried to restart lirc, but there was an error 

```
main@HTPC:~$ sudo /etc/init.d/lirc restart
[sudo] password for main: 
 * Stopping remote control daemon(s): LIRC                               [fail] 
 * Loading LIRC modules                                                  [ OK ] 
 * Starting remote control daemon(s) : LIRC                              [fail] 
main@HTPC:~$ irw
connect: No such file or directory
main@HTPC:~$ 

```

what went wrong?

---

### Post by jb5 on 2009-04-20
Hmm, not sure I'm afraid, reached the end of my limited knowledge - sorry.
The only other thing might be to try a cold boot, long shot but not too difficult to try.

For what it's worth here are my current conf files:-
/etc/lirc/hardware.conf
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Hauppauge Nova-T 500"
REMOTE_MODULES=""
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/event7"
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge_novat500"
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

/etc/lirc/lircd.conf
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

#Configuration for the Hauppauge Nova-T 500 remote:
include "/usr/share/lirc/remotes/hauppauge/lircd.conf.hauppauge_novat500"

```

/usr/share/lirc/remotes/hauppauge/lircd.conf.hauppauge_novat500
```
#
# brand:                       Hauppauge NOVA-T-500
# model no. of remote control: Hauppage Nova-T-500 Snowboard Shape Silver over Black
#

begin remote

 name  NOVA-T500
 bits           16
 eps            30
 aeps          100

 one             0     0
 zero            0     0
 pre_data_bits   16
 pre_data       0x1
 gap          199999
 toggle_bit      0


     begin codes
         Go                       0x0162
         Power                    0x0074
         TV                       0x0179
         Videos                   0x0189
         Music                    0x0188
         Pictures                 0x00E2
         Guide                    0x016D
         Radio                    0x0181
         ArrowUp                  0x0067
         ArrowLeft                0x0069
         OK                       0x0160
         ArrowRight               0x006A
         ArrowDown                0x006C
         BackExit                 0x009E
         Menu                     0x008B
         VolumeUp                 0x0073
         VolumeDown               0x0072
         PrevCh                   0x016B
         Mute                     0x0071
         ChannelUp                0x0192
         ChannelDown              0x0193
         Record                   0x00A7
         Rewind                   0x00A8
         SkipBack                 0x0195
         Play                     0x00CF
         Pause                    0x0077
         Stop                     0x0080
         Fwdwind                  0x00D0
         SkipFwd                  0x0197
         1                        0x0002
         2                        0x0003
         3                        0x0004
         4                        0x0005
         5                        0x0006
         6                        0x0007
         7                        0x0008
         8                        0x0009
         9                        0x000A
         star                        0x0037
         0                        0x000B
         #                        0x0029
         one                      0x004F
         two                      0x0050
         three                    0x0051
         four                     0x004B
         five                     0x004C
         six                      0x004D
         seven                    0x0047
         eight                    0x0048
         nine                     0x0049
         ten                      0x0052
         Red                      0x018E
         Green                    0x018F
         Yellow                   0x0190
         Blue                     0x0191
     end codes

end remote


```

---

### Post by BicyclerBoy on 2009-04-22
true & false need to be "quoted"

DRIVER="dev/input"

think this is wrong and should be
REMOTE_DRIVER="devinput"

REMOTE_ & TRANSMITTER_ missing from most lines ?

May be it defaults to REMOTE_ but I doubt it.

BB

---

### Post by BicyclerBoy on 2009-04-22
r3vile
I am probably wrong when I stated your file has errors.
I have seen examples with quoted & un-quoted true/false.

A lot of posted examples of Linux files are not completely right (IMHO). 
Like with most of my Linux education to date, I not be sure if your file is incorrect or not.
I can not find out what is the correct format of this file.
There seems to have been some bugs around the auto-generation of this file.
The format & the list of valid keywords probably changes with each version.
Almost need to be a C++ geek and read the source code listings to find out what is allowed.

Sorry.

---

### Post by AlecJ on 2009-04-22
> **r3vile said:**
> Hello,
I got a Sky Stat 2 TV Card with a remote control.
The remote control ("TTS35AI") was not listed in the Mythbuntu control center so I downloaded this file : [http://lirc.sourceforge.net/remotes/technisat/TTS35AI](http://lirc.sourceforge.net/remotes/technisat/TTS35AI)
Now i dont know where i have to put this file and how i can configure the command my remote sends (e.g. if i press the "Exit" button on my remote it sends "f" to mythbuntu, but i want it to send "Escape").

-I am using Mythbuntu 8.10
-I updated lirc to 0.8.4 
-the remote workes since i pluged it in, without any further configuration, so until now i have not modified any files

Hi there is a full guide here for your remote.

[http://www.mythtv.co.nz/mythtv/mythtv-articles/installation-of-technisat-skystar-2-dvb-s-with-serial-remote-into-mythbuntu-710/](http://www.mythtv.co.nz/mythtv/mythtv-articles/installation-of-technisat-skystar-2-dvb-s-with-serial-remote-into-mythbuntu-710/)

Worth noting that the ir receiver is not within the card there fore does not enter using Lirc in the same manor. This would be why it fails with lirc.

File types and there usage
 
/etc/lirc/lirc.conf    Key map file ,ie if you recive 0x00007ba1 assine the value "blue" etc


/etc/lirc/hardware.conf   What hardware (remote) to use and where to get the               input from. 

~/.mythtv/lircrc   What to do when a button is recived, ie recive "blue" from remote give "F5" to mythbuntu for example.

within the frontend Utilities/setup / Edit keys    you can see what key do what, then you can change lircrc to suit. Don't rearrange the order of lircrc just change the keys or add new keys to the bottom of the list.

---

### Post by r3vile on 2009-04-22
finally my remote control works :). The problem was in the /etc/lirc/lircd.conf . I dont know why, but the comments were not recognized as comments, so they caused errors. After removing all comments the remote was working.

My next Problem:
it's working with mythtv now, but not with vlc. How can i get my remote to work with vlc?

---

### Post by jb5 on 2009-04-23
Glad you got it working in the end.

To configure your remote for vlc :-```
cp ~/.lirc/vlc ~/.lirc/vlc.old
gedit ~/.lirc/vlc
```I have no idea what the key-mappings are in vlc, but I guess GIYF. :)

Good Luck.

EDIT
P.S. - Out of interest how did you figure out the comments in lircd.conf were the problem?

---

### Post by r3vile on 2009-04-25
When i have tried to start the lirc deamon with
```
 #lircd --nodaemon --device=/dev/input/event2 --driver=dev/input /etc/lirc/lircd.conf

```
then there was an error on line 15 and line 15 was a comment :P

I also fixed my problem with vlc. I just had to activate lirc in the vlc settings ;)

EDIT: I got another problem:
I allways have to start lirc manually with ```
 sudo lircd --nodaemon --device=/dev/input/event2 --driver=dev/input /etc/lirc/lircd.conf

``` because lirc does not start automatically. How can i put "sudo lircd --nodaemon --device=/dev/input/event2 --driver=dev/input /etc/lirc/lircd.conf"  into autostart

---

### Post by r3vile on 2009-04-27
Solved: Lirc did not start automatically, because it could not handle the lircd.conf.
However, since i got another lircd file it works.

---

