---
title: "[SOLVED] irw errors"
date: 2008-09-10
forum: Mythbuntu
---

### Post by dmdbdd on 2008-09-10
When I try to launch 'irw' nothing happens. Looking at the /var/log/daemon.log, I see the following:[INDENT]...: accepted new client on /dev/lircd
...: could not get file information for /dev/lir$
...: default_init(): No such file or directory
...: caught signal
[/INDENT]My /etc/lirc/hardware.conf looks like this:[INDENT]# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Custom"
REMOTE_MODULES="lirc_dev lirc_i2c"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc/0"
REMOTE_LIRCD_CONF="/usr/share/lirc/remotes/dvico/lircd.conf.fusionHDTV"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
#TRANSMITTER_LIRCD_CONF="/usr/share/lirc/transmitters"
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
[/INDENT]Does anyone have a solution for said problem?

Regards

dmdbdd

---

### Post by SiHa on 2008-09-10
Looks like irw can't find the device

```
...: could not get file information for /dev/lir$
...: default_init(): No such file or directory
```

Are you sure your device is **/dev/lirc/0**? Mine's **/dev/lirc0**.

Failing that...

On my FE/BE machine, I'm using the built in receiver on one of the tuner cards, and the receiver shows up as **/dev/input/event4**.

Garry Parker's guide on MythTV setup is invaluable:
[COLOR="Blue"]
[http://parker1.co.uk/mythtv_ubuntu2.php](http://parker1.co.uk/mythtv_ubuntu2.php)[/COLOR]

If it still isn't working, once you have confirmed what device the receiver is, you can try  ```
mode2 -d <path/to/device>
```That will display the raw Pulse / Space data being received by the receiver, so at least you'll know if that's working OK.

---

### Post by dmdbdd on 2008-09-11
OK, here's where I'm at:


[LIST=1]
[*]Determined that my IR device is '/dev/input/event6' by running 
cat /proc/bus/input/devices
[*]Modified my ' /etc/lirc/hardware.conf' file as follows:
[/LIST]
[INDENT] #/etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Custom"
REMOTE_MODULES="lirc_dev lirc_i2c"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/input/event6"
#REMOTE_DEVICE="/dev/lirc"
REMOTE_LIRCD_CONF="/usr/share/lirc/remotes/dvico/lircd.conf.fusionHDTV"
REMOTE_LIRCD_ARGS="-H dev/input -d /dev/input/event6 -n"
#REMOTE_LIRCD_ARGS=""
[/INDENT]I couldn't test using 'sudo mode2 -d  /dev/input/event6' as this program is does not work with IR receivers built into a tuner card as mine is.

So I tried running 'irw' again and I got the error message "connect: Connection refused".  Next I tried this:[INDENT]'sudo /usr/sbin/lircd -H dev/input -d /dev/input/event6 -n'
[/INDENT]This seemed to get things started correctly as I received the following:[INDENT]...: lircd-0.8.3pre1[6333]: lircd(userspace) ready
[/INDENT]So I opened second terminal and entered 'irw'. I receive the following on the first terminal:[INDENT]...: accepted new client on /dev/lircd
...: initializing '/dev/input/event6'
[/INDENT]OK, looks good so far! Ready to test - back to the second terminal. Pushed some buttons on remote - NOTHING! So I control 'C' out of 'irw' and receive the following on the first terminal:[INDENT]...: removed client
...: closing '/dev/input/event6'
[/INDENT]So at this point it looks like lirc is getting started and initialized correctly it's just not receiving anything from my remote. I know the my IR reciever are working as I can push the number buttons on my remote when I'm at a terminal prompt without 'irw' running and I get output just as if I had typed them on the keyboard.

Does any one have any ideas? I tried everything I found on Parker's site but, could not run 'evtest' as I get the error message "sudo: evtest: command not found".

Regards,

dmdbdd

---

### Post by anonymousdog on 2008-09-11
Refer back to SiHa's post; that's much closer to the correct diagnostic path to take.  It just looks like a typo in your original hardware.conf file.  Take out the extraneous "/" from the remote device name, and you're probably golden.  I'm betting that 'ls /dev/lirc*' returns '/dev/lirc0' and that you don't have a /dev/lirc/0.

---

### Post by Xcerca on 2008-09-11
I'm exactly where you're at , but my remote is a little different.

I found out that it's /dev/usb/hiddev1 by looking in dev for a while and when I do cat /dev/usb/hiddev1 and push buttons on the remote i get an output. 

So then I did irrecord to set up a lircd.conf ( I think thats the file i need to replace) with
irrecord -H sb0540 -d /dev/usb/hiddev1 lirdc.conf

and everything went well , i have the lircd.conf file but i'm not sure if i need to put the one i made with irrecord in the /etc/lirc/ folder , then have my hardware.conf point to that.

but i read your post to see what was going on because 'irw' always said connection refused , so i did

sudo /usr/sbin/lircd -H sb0540 -d /dev/usb/hiddev1 -n

and got

lircd-0.8.3pre1[11578]: you should specify a valid gap value
lircd-0.8.3pre1[11578]: lircd(userspace) ready
lircd-0.8.3pre1[11578]: accepted new client on /dev/lircd
lircd-0.8.3pre1[11578]: initializing '/dev/usb/hiddev1'

then i opened another terminal and did irw , and tried pressing buttons and got nothing,  so is it a problem with the lircd.conf maybe ?

also i did 
cat /var/log/daemon.log | grep lirc
and sometimes i saw 
 initializing '/dev/usb/hiddev1'
 lircd-0.8.3pre1[10626]: can't get exclusive access to events comming from `/dev/usb/hiddev1' interface
 lircd-0.8.3pre1[10626]: accepted new client on /dev/lircd
 lircd-0.8.3pre1[10626]: error reading '/dev/usb/hiddev1'

so i did chmod 666 /dev/usb/hiddev1 and that seems to clear it, but i still have no output in irw.      what should i be seeing in irw if it does work ?

thanks

---

### Post by Xcerca on 2008-09-12
Also , can anybody see if there are any obvious things i need to change in my configs

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="rm-1500"
REMOTE_MODULES="lirc_serial"
REMOTE_DRIVER="sb0540"
REMOTE_DEVICE="/dev/usb/hiddev1"
REMOTE_LIRCD_CONF="creative/lircd.conf.irrecord"
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




and this is /usr/share/lirc/remotes/creative/lircd.conf.irrecord , that i made with irrecord -H sb0540 -d /dev/usb/hiddev1
(which I assume is the one REMOTE_LIRCD_CONF="   points to , maybe if i make it absolute...?)

# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.3pre1(sb0540) on Thu Sep 11 20:51:49 2008
#
# contributed by 
#
# brand:                       lircd.conf.irrecord
# model no. of remote control: 
# devices being controlled by this remote:
#

begin remote

  name  rm-1500
  bits           16
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   16
  pre_data       0x8322
  gap          203989
  toggle_bit_mask 0x0

      begin codes
          play                     0x7986
          next                     0x7A85
          vol-up                   0x629D
          vol-down                 0x639C
          mute                     0x6E91
          stop                     0x857A
          ok                       0x817E
          power                    0x619E
      end codes

end remote

---

### Post by SiHa on 2008-09-13
dmdbdd - 
I note you have no driver specified in your hardware.conf.

Mine is also on event6, as a receiver within a card, so a fairly similar setup to yours.

Here's my config:

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Hauppauge Nova-T 500"
REMOTE_MODULES=""
REMOTE_DRIVER="devinput"
#REMOTE_DEVICE="/dev/input/event6"
REMOTE_DEVICE="/dev/input/irremote"
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

Don't worry about the REMOTE_DEVICE="/dev/input/irremote" line. I followed Garry Parkers guide to set a static device because my system swaps it around at boot. (I've got two cards)

If IRW still doesn't work, ensure LIRC is stopped:
```
sudo /etc/init.d/lirc stop
```
and run irrecord
```
sudo irrecord -d /dev/input/event6 -H devinput <filename>
```
The edit your hardware.conf to point to the new file.
now restart LIRC
```
sudo etc/init.d/lirc start
```
and try IRW again.

---

### Post by dmdbdd on 2008-09-13
I really appreciate your suggestions SiHa. I have my 'hardware.conf' file setup as you suggested - when I run 'irrecord' I get an empty file. Now I'm using '^C' to end 'irrecord - maybe that's the problem. I don't see any info in the 'irrcord' documention on how to end this program. I tried letting it time out and it didn't produce any file at all. Just for testing this sucker I'm calling my record file 'irwtest' and letting it default to my home directory, not that any of that should make a difference for testing 'irrcord'.

I even tried using the force option and still nothing![INDENT]sudo irrecord -f -d /dev/input/event6 -H devinput irwtest
[/INDENT]Every time I push a button on my remote, a dot is displayed - so I know that it's receiving data Below is my 'hardware.conf' as stands now. The remainder of the file not shown has not been modified.[INDENT]
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="DVICO_FusionRemote"
REMOTE_MODULES=""
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/irremote""
REMOTE_LIRCD_CONF="/usr/share/lirc/remotes/dvico/lircd.conf.fusionHDTV"
REMOTE_LIRCD_ARGS=""
[/INDENT]I'm not sure where to go from here - does anyone have any ideas?

---

### Post by SiHa on 2008-09-14
^c is your problem.

When you run irrecord, don't you get any instructions?

Here's what I get...

```
$ sudo irrecord -d /dev/lirc0 irwtest

irrecord -  application for recording IR-codes for usage with lirc

Copyright (C) 1998,1999 Christoph Bartelmus(lirc@bartelmus.de)

This program will record the signals from your remote control
and create a config file for lircd.


A proper config file for lircd is maybe the most vital part of this
package, so you should invest some time to create a working config
file. Although I put a good deal of effort in this program it is often
not possible to automatically recognize all features of a remote
control. Often short-comings of the receiver hardware make it nearly
impossible. If you have problems to create a config file READ THE
DOCUMENTATION of this package, especially section "Adding new remote
controls" for how to get help.

If there already is a remote control of the same brand available at
http://www.lirc.org/remotes/ you might also want to try using such a
remote as a template. The config files already contain all
parameters of the protocol used by remotes of a certain brand and
knowing these parameters makes the job of this program much
easier. There are also template files for the most common protocols
available in the remotes/generic/ directory of the source
distribution of this package. You can use a template files by
providing the path of the file as command line parameter.

Please send the finished config files to <lirc@bartelmus.de> so that I
can make them available to others. Don't forget to put all information
that you can get about the remote control in the header of the file.

Press RETURN to continue.


Now start pressing buttons on your remote control.

It is very important that you press many different buttons and hold them
down for approximately one second. Each button should generate at least one
dot but in no case more than ten dots of output.
Don't stop pressing buttons until two lines of dots (2x80) have been
generated.

Press RETURN now to start recording.
................................................................................
Found const length: 113836
Please keep on pressing buttons like described above.
................................................................................
RC-5 remote control found.
Found possible header: 929 848
Found hidden lead pulse: 925
No repeat code found.
Signals are biphase encoded.
Removed header.
Signal length is 13
Now enter the names for the buttons.

Please enter the name for the next button (press <ENTER> to finish recording)
1

Now hold down button "1".

Please enter the name for the next button (press <ENTER> to finish recording)
2

Now hold down button "2".

Please enter the name for the next button (press <ENTER> to finish recording)
3

Now hold down button "3".

Please enter the name for the next button (press <ENTER> to finish recording)
4

Now hold down button "4".

Please enter the name for the next button (press <ENTER> to finish recording)

Checking for toggle bit mask.
Please press an arbitrary button repeatedly as fast as possible.
Make sure you keep pressing the SAME button and that you DON'T HOLD
the button down!.
If you can't see any dots appear, then wait a bit between button presses.

Press RETURN to continue.
..............................
No toggle bit mask found.
Successfully written config file.

```

---

### Post by dmdbdd on 2008-09-17
OK - many thanks to SiHa :) Well my 'irrecord' must be a different version then yours. When I execute 'irrecord' I get the first boilerplate output that is pretty much the same as what you get, however after the first request to "Press RETURN to continue", I get "Hold down an arbirtrary key" - no instructions on how long to hold it down! So, my problem was that I wasn't holding it down long enongh. After holding an arbirtrary down for several lines of dots, I received addition instructions that are different than yours.

Anyway I was able to generaate enough unique codes for my remote, that I was able to find a 'lircd.conf ' file that matched my remote buttons and codes at:[INDENT][http://lircconfig.commandir.com/lircd.conf/ ]("http://lircconfig.commandir.com/lircd.conf/")
[/INDENT]Now 'irw' works as advertised :)

Regards,

dmdbdd

---

### Post by SiHa on 2008-09-19
> **dmdbdd said:**
>  Well my 'irrecord' must be a different version then yours. 

Interesting!

Glad you got it fixed anyway. Took me a couple of weeks of frustration to get the remote working first time...

---

