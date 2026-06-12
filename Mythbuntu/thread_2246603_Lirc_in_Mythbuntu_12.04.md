---
title: "Lirc in Mythbuntu 12.04"
date: 2014-10-01
forum: Mythbuntu
---

### Post by neutron68 on 2014-10-01
I have a serial IR receiver/transmitter designed by [Iguannaworks]("http://www.iguanaworks.net/products/series-transceiver/").

I've had lirc and an IR remote running since 2009 in another Mythtv pc running on Knoppmyth R5.5.
I've been running both Knoppmyth and Mythbuntu on separate machines for 5 years now.  

I'm FINALLY getting around to getting lirc and the IR remote working on Mythbuntu 12.04. :P
I'm trying to get the IR remote running in Mythbuntu 12.04, but I'm not quite there.

I went through the Mythbuntu Control Centre setup for the IR remote, but it doesn't have my RCA remote in the list nor options for the Iguannaworks Serial IR Receiver and Serial IRblaster, so I think I'm stuck doing the configuration manually, correct?

I have the following in place:
1.  /etc/lirc/lirc.conf is present  (owned by root)
2.  /etc/lirc/hardware.conf is present (owned by root)
3.  /home/mythtv/.mythtv/lircrc is present  (owned by mythtv)

At present, irrecord works and responds to the Iguannaworks IR receiver, but irw gives an error when I try and run it:
> eric@Mythbuntu:~/Desktop$ irw
connect: No such file or directory

My /etc/serial.config file currently looks like this:
> /dev/ttyS0 uart none

This is my /etc/lirc/hardware.conf file:  (**this has been edited since the original posting date, to reflect the working version**)
> # /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="serial IR receiver"
REMOTE_MODULES="lirc_dev lirc_serial"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="/etc/lirc/lircd.conf"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Serial Port (UART)"
TRANSMITTER_MODULES="lirc_dev lirc_serial"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc0"
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF="/etc/lirc/lircd.conf"
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

Need more info?
See any obvious problems?

Thanks,
Eric

---

### Post by neutron68 on 2014-10-05
I got a little farther!

I had to tweak the hardware.conf file a little.  (I updated the post above with the version that is now working.)

I also discovered that my lircd.conf file, that I manually copied into /etc/lirc/ , had been overwritten by an auto-generated file created during the Mythbuntu Control Centre setup process, and thus my RCA remote signals weren't being recognized!

Now, irw runs and returns data when an IR button is pressed!
> eric@Mythbuntu:~/Desktop$ irw
0000000000f310ce 00 tv-1 rca-dtc-100
0000000000f320cd 00 tv-2 rca-dtc-100
0000000000f330cc 00 tv-3 rca-dtc-100
0000000000f330cc 01 tv-3 rca-dtc-100
0000000000f340cb 00 tv-4 rca-dtc-100
0000000000f350ca 00 tv-5 rca-dtc-100
0000000000f360c9 00 tv-6 rca-dtc-100
0000000000f370c8 00 tv-7 rca-dtc-100
0000000000f380c7 00 tv-8 rca-dtc-100
0000000000f380c7 01 tv-8 rca-dtc-100
0000000000f580a7 00 tv-down rca-dtc-100
0000000000f580a7 01 tv-down rca-dtc-100
0000000000f560a9 00 tv-left rca-dtc-100
0000000000f560a9 01 tv-left rca-dtc-100

I've got a /home/mythtv/.mythtv/lircrc file in place.  (owned by mythtv)
But, when I press keys on the IR remote (like up, down, left and right arrows) the Mythtv frontend interface does not respond.

Here's a sample:
> # MythTV LIRC config file for the RCA rca-dtc-100 remote
# remote has bright green power, ch+, ch-, vol+, vol- buttons
# Sticker on the inside of battery compartment
#     says CRK76CA2
#     
#
# /home/mythtv/.mythtv/lircrc
#
#
#
### MYTHTV SETTINGS FOR IT'S CONTROL
#
# Program Guide
begin
   remote = rca-dtc-100
   prog = mythtv
   button = tv-guide
   config = F2
   repeat = 0
   delay = 0
end

# Previous Channel
begin
   remote = rca-dtc-100
   prog = mythtv
   button = tv-go-back
   config = H
   repeat = 0
   delay = 0
end

# OK/Select
begin
   remote = rca-dtc-100
   prog = mythtv
   button = tv-ok
   config = Space
   repeat = 0
   delay = 0
end

# tv-play
begin
   remote = rca-dtc-100
   prog = mythtv
   button = tv-play
   config = Return
   repeat = 0
   delay = 0
end

# tv-stop
begin
   remote = rca-dtc-100
   prog = mythtv
   button = tv-stop
   config = Esc
   repeat = 0
   delay = 0
end


Anyone know another thing to try in troubleshooting this?

Eric

---

### Post by neutron68 on 2014-10-10
I'm seeing different versions of what to do with the lircrc file!
It looks like there may have been some lirc file location changes over time?  

1.
I looked at the (current) [Mythbuntu LIRC help page]("https://help.ubuntu.com/community/LIRC") but it doesn't detail this stage of the process - getting mythtv to respond to specific IR remote key presses.
All it says is 
> Create a configuration file in the users home directory named .lircrc
I think that means **/home/eric/.lircrc** rather than **/home/mythtv/.lircrc**?

2.
The [LIRC web page]("http://www.lirc.org/html/configure.html") says:
> you need a file called .lircrc. It should be placed in your home directory. Optionally you can create a system-wide configuration file located in /etc/lirc/lircrc, which will be used when no .lircrc file can be found in the user's home directory.

3.
The (older) [LIRC guide for Hardy]("https://help.ubuntu.com/community/InstallLirc/Hardy") is a little more complete and says there are several ways to create the lircrc file:
> Mythbuntu LIRC generator

The Mythbuntu Team has developed a python script that will generate a sane remote control mapping to use or at least start from. It grabs all of the possible buttons and remotes from /etc/lirc/lircd.conf and maps them over for MythTV, Xine, MPlayer, VLC, Totem, & Elisa.

Install the application as follows:
$ sudo apt-get install mythbuntu-lirc-generator

To run, simply run:
$ mythbuntu-lircrc-generator
By default, all 6 application configurations are generated for the currently logged in user. Any old configurations will be renamed.

4.
Further down the [LIRC guide for Hardy]("https://help.ubuntu.com/community/InstallLirc/Hardy") it says:
> you will either need to create a standalone lircrc for mythtv in ~/.mythtv/lircrc or create a symbolic link to this file and place all the lircrc related content in /.lircrc

Creating a symbolic link. [ All mythtv buttons will need to be placed in ~/.lircrc with the rest of the applications you use lirc for ]

$ ln -s ~/.lircrc ~/.mythtv/lircrc

5.
In [this 2009 forum thread]("http://ubuntuforums.org/showthread.php?p=6502305") it says they needed a symlink named **/home/<user>/.mythtv/lircrc** which points to the file **/home/<user>/.lirc/mythtv**
I believe that means that your lircrc data needs to be inside the file **/home/<user>/.lirc/mythtv** ?

Eric

---

### Post by neutron68 on 2014-10-11
I got the IR remote working with mythtv!

It turns out that if the IR remote you have is not in the pre-canned list, the LIRC setup scripts inside the Mythbuntu Control Centre will NOT produce a working result.  

I think its a good idea to run the IR setup in the Mythbuntu Control Centre FIRST, to set up your serial port settings for you, and create needed lirc folders and files for you.  
BUT, then you need to go back and clean up - manually copy, edit and rename files yourself.  

I'll post the final working configuration and my how-to, soon.

---

### Post by neutron68 on 2014-10-13
I recommend starting with the Infrared section of the Mythtbuntu Control Centre.  Even if the setup script doesn't have your IR remote in the list, it will create all the file types that need to exist and put them in the right directories for you.  After that is done, you can go back and manually edit the contents of the files to make your remote work right.

In the Mythbuntu Control Centre (Infrared section):
1. check the button "USB & Serial Remote support via LIRC" and click Apply.
2. For those with a serial IR receiver (such as the [Iguanaworks serial IR receiver]("http://www.iguanaworks.net/products/series-transceiver/")), choose "Home-brew (16x50 UART compatible serial port) for your Remote control configuration.
3. if your serial IR receiver also has the ability to send IR from the same device (as the Iguanaworks serial IR does), choose "Serial Port (UART): Direct TV Receiver.
4.  click Forward
5.  select the port your serial device is attached to.  I only have 1 serial port so I chose port 0.  "/dev/ttyS0"
6.  click Forward
7.  when you get back to the Control Centre, it asked me to to choose a remote.  I picked "Hauppague tv card".
8.  I also checked "Generate dynamic button mappings" and "Generate frontend restart mapping", so it would put the lircrc files in place and autostart LIRC at boot.
9.  click Apply
10. Quit out of the Control Centre.


At that point, I had the following in place:
1. /etc/serial.conf (owned by root)
2. /etc/lirc/lircd.conf (owned by root) 
3. /etc/lirc/hardware.conf (owned by root)
4. /home/<user>/.lircrc (owned by user)
5. /home/<user>/.lirc/mythtv (owned by user)

The /etc/serial.conf file tells the OS not to use serial port 0, so the serial IR can use it.  The Control Centre scripts wrote this file for you based on the serial port you said you were going to use.
```
/dev/ttyS0 uart none
```

The Control Centre scripts wrote the /etc/lirc/lircd.conf file so that it has INCLUDE lines that point to the lircd files for the remotes you selected.
I manually overwrote the contents of the auto-generated lircd.conf file with the contents of my existing lircd.conf file (from my other mythtv system, which contains the LIRC codes for both my RCA IR remote and my Directv receiver's remote) right into the /etc/lirc/lircd.conf file.
```
# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.0pre4-pvr150(all) on Sun Aug 20 12:02:01 2006
#
# brand: RCA
# model no. of remote control: CRK76CA2 (came with DTC-100 HD receiver)
# devices being controlled by this remote: VCR1, DVD, VCR2, AUX, HD RCVR, TV
#
# Each button sends out a different code for each mode.
# Example:
# the 1 button sends a different code when in VCR1 mode vs. TV mode
# 3 of the keys are the same in all modes:  vol-right, vol-left and mute
#

begin remote

  name rca-dtc-100
  bits           24
  flags SPACE_ENC|CONST_LENGTH
  eps            30
  aeps          100

  header       4044  3942
  one           532  1961
  zero          532   966
  ptrail        539
  gap          65915
  toggle_bit      0

      begin codes
          vol-left                 0xF2E0D1
          vol-right                0xF2F0D0
          mute                     0xF3F0C0
          aux-on-off               0xC3B3C4
          aux-mute                 0xC3F3C0
          aux-who                  0xC6139E
          aux-ch+                  0xC2D3D2

# and so on
```


The /etc/lirc/hardware.conf file contains the configuration to set up the serial port to receive LIRC data.
I edited the script-generated file so both the IR Receiver and IR transmitter use serial port 0 and so my custom /etc/lirc/lircd.con file gets used for both the IR receiver and transmitter.
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Serial Port IR"
REMOTE_MODULES="lirc_dev lirc_serial"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="/etc/lirc/lircd.conf"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Serial Port (UART)"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc0"
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF="/etc/lirc/lircd.conf"
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

The script-generated /home/<user>/.lircrc file points to all program config files in the /home/<user>/.lirc directory.  I didn't edit that file at all.
```
#Custom lircrc generated via mythbuntu-lirc-generator
#All application specific lircrc files are within ~/.lirc
include ~/.lirc/mythtv 
include ~/.lirc/mplayer 
include ~/.lirc/xine 
include ~/.lirc/vlc 
include ~/.lirc/xmame 
include ~/.lirc/xmess 
include ~/.lirc/totem 
include ~/.lirc/elisa
```

The /home/<user>/.lirc/mythtv contains the lircrc file information for passing commands on to mythtv.
I copied the contents of the lircrc file from my other mythtv computer and overwrote the auto-generated contents of the /home/<user>/.lirc/mythtv file
```
# MythTV LIRC config file for the RCA rca-dtc-100 remote
# remote has bright green power, ch+, ch-, vol+, vol- buttons
# Sticker on the inside of battery compartment
#     says CRK76CA2
#
#
#
### MYTHTV SETTINGS FOR IT'S CONTROL
#
# Program Guide
begin
   remote = rca-dtc-100
   prog = mythtv
   button = tv-guide
   config = F2
   repeat = 0
   delay = 0
end

# Previous Channel
begin
   remote = rca-dtc-100
   prog = mythtv
   button = tv-go-back
   config = H
   repeat = 0
   delay = 0
end

# OK/Select
begin
   remote = rca-dtc-100
   prog = mythtv
   button = tv-ok
   config = Space
   repeat = 0
   delay = 0
end

# tv-play
begin
   remote = rca-dtc-100
   prog = mythtv
   button = tv-play
   config = Return
   repeat = 0
   delay = 0
end

#and so on...
```

After a restart of LIRC, my IR remote was able to control mythtv menus and functions!
```
sudo service lirc restart
``` 

My next step is to get the IR Blaster section of the [Iguanaworks serial IR device]("http://www.iguanaworks.net/products/series-transceiver/") to control my Directv receiver.

---

