---
title: "Cyberlink Remote button map"
date: 2009-07-16
forum: Multimedia Software
---

### Post by zootoxin on 2009-07-16
I have this remote 
[img]http://www.altechco.com/images/cyber.jpg[/img]

The Volume works but I would like to have all the buttons functional mainly for XBMC. 

Has anyone here managed to map the buttons? 

I tried unsuccessfully to use Lirc. 

If you have managed to map the buttons or even (better still) got the remote Fully functional on XBMC please could you send me the config files. 

Thanks 

Zoot

---

### Post by piginabox on 2009-10-02
PLEASE IGNORE MY RAMBLING POSTS AND CUT TO THE CHASE BELOW (March 2010).
I'VE TIDIED UP MY CONFIG FILES AND ATTACHED THEM.
========================================================================


The remote has some 'special' buttons in a white (grey) box area near the top.

I have all the buttons working below the white box (volume, arrows, play, FFW,RW, numbers).

Above the white box I have only the power button working.

Within the white box I have the Record, Radio, Back and Info/EPG buttons working.

What files do you need to see?
hardware.conf
lircd.conf
and my mythtv lircrc?

I warn you in advance that they are fairly messy as I edited the mythbuntu config files i had for a hauppauge remote. I also tried several auto lirc and remote apps without success. The resulting files have had to be butcher by hand once I got half an idea of what I was doing.
The remote shows up as two input device keyboards which is why it stumps the auto lirc generator. I got mine for £5.99 including delivery (June 2009).

---

### Post by piginabox on 2009-10-02
The important line here is
REMOTE_LIRCD_ARGS="--device=`grep -l 'TopSeed' /sys/class/input/input*/name | tail -n1 | sed -e s'|/name||' | sed -e s'|sys/class/input/input|dev/input/event|'` --driver=dev/input"
which compensates for the eventX changing e.g. remote event3 becomes event4 if a mouse is connected.
sourced from [http://cjo20.net/remote.htm](http://cjo20.net/remote.htm) (thanks)

p.s. this file was edited and was originally for a Hauppauge Nova 500


```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Hauppauge Nova-T 500"
REMOTE_MODULES=""
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge_novat500"
REMOTE_LIRCD_ARGS="--device=`grep -l 'TopSeed' /sys/class/input/input*/name | tail -n1 | sed -e s'|/name||' | sed -e s'|sys/class/input/input|dev/input/event|'` --driver=dev/input"


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

---

### Post by piginabox on 2009-10-02
I used the lirc generator to make these files originally. the lircd.conf just links to the remote-specific conf file found below it.

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
#include "/usr/share/lirc/remotes/hauppauge/lircd.conf.cyberlink"
```



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
         Guide                    0x0082
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
         Play                     0x00CF
         Pause                    0x0077
         Stop                     0x00A6

	SkipBack		0x00A5
	Rewind			0x00A8
	Fwdwind			0x00D0
	SkipFwd			0x00A3


#         Rewind                   0x00A8
#         SkipBack                 0x0195
#         SkipFwd                  0x00D0
#         Fwdwind                  0x00A3
#         SkipFwd                  0x00A5


#         1                        0x0002
#         2                        0x0003
#         3                        0x0004
#         4                        0x0005
#         5                        0x0006
#         6                        0x0007
#         7                        0x0008
#         8                        0x0009
#         9                        0x000A
#         *                        0x0037
#         0                        0x000B
#         #                        0x0029
#         one                      0x004F
#         two                      0x0050
#         three                    0x0051
#         four                     0x004B
#         five                     0x004C
#         six                      0x004D
#         seven                    0x0047
#         eight                    0x0048
#         nine                     0x0049
#         ten                      0x0052
#         Red                      0x018E
#         Green                    0x018F
#         Yellow                   0x0190
#         Blue                     0x0191
     end codes

end remote


```

---

### Post by piginabox on 2009-10-02
Lastly my ~/.mythtv/lircrc file.
This translates remote button presses to keyboard controls e.g. 'Play' button in to the letter 'P'


```
# LIRCRC Auto Generated by Mythbuntu Lirc Generator
# Author(s): Mario Limonciello, Nick Fox
# Created for use with Mythbuntu
begin
    remote = NOVA-T500
    prog = mythtv
    button = Play
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = ArrowRight
    config = Right
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = Mute
    config = |
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = VolumeDown
    config = [
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = SkipBack
    config = Q
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = SkipFwd
    config = Z
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = Rewind
    config = <
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = Stop
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = 7
    config = 7
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = VolumeUp
    config = ]
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = 1
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = ArrowDown
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = 0
    config = 0
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = 5
    config = 5
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = 2
    config = 2
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = 4
    config = 4
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = Pause
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = OK
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = Menu
    config = M
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = 6
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = ArrowUp
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = ChannelDown
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = Record
    config = R
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = BackExit
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = 3
    config = 3
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = ChannelUp
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = Fwdwind
    config = >
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = 8
    config = 8
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = 9
    config = 9
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = Guide
    config = S
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = ArrowLeft
    config = Left
    repeat = 0
    delay = 0
end

```

---

### Post by mfdeath on 2010-01-28
I did the steps like in the post above but only up-down-left-right and ok button + 0-9 work for me (like they did before with native system support as mouse+keyboard device)

The TopSeed Combo Device seems to be input 4 and 5 in my machine...

Can I do some testing what's wrong with my configuration?

system is 9.10 Mythbuntu 
cyberlink remote as above

---

### Post by piginabox on 2010-02-23
i reinstalled my mythtv and the above steps worked. did you use the hardware.conf in my second reply? i forgot too when i did my reinstall and only the 0-9 buttons worked. i copied the hardware.conf over to /etc/lirc and restarted lirc - sudo service lirc restart - and all was well.

---

### Post by piginabox on 2010-03-05
I've found other keymappings for Cyberlink remotes on various websites which sometimes differ from the hex map codes that work for me so there may be several variants of the remote. Mine looks exactly like the one pictured by the OP.

For mythtv users, the 'Clear' button at the bottom doesn't need to be mapped by lirc. Just edit the key setup from within mythtv > Utilities / Settings > Edit Keys. Then GLOBAL and edit the DELETE key and to use 'Del' as well as 'D' for deletion.

I've attached my /etc/lirc/hardware.conf, ~/.mythtv/lircrc and my /etc/lirc/lircd.conf
I've tidied them up. I don't use all the keys but I have all the mappings - set attached file.

---

### Post by piginabox on 2010-05-22
If you're still having trouble do the following
install mythbuntu-lirc-generator with
(open Terminal in Accessories menu)
sudo apt-get install mythbuntu-lirc-generator

then run it with

mythbuntu-lirc-generator

then using the files from my previous post

copy hardware.conf and lircd.conf to /etc/lirc/
copy lircrc to ~/.mythtv/

reboot or in Terminal restart lirc with
sudo service lirc restart


if any probs please PM me

---

