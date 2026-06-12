---
title: "How can I get my TV@nywhwere Plus remote to work?"
date: 2009-08-10
forum: Mythbuntu
---

### Post by derrick1985 on 2009-08-10
Hi,

My TV tuner card is a TV@nywhere plus which works great, with the exception of the remote. The only remote in the list I have to choose from is TV@nywhere master, which isn't the exact same keymaps. For me right now, up is down, down is up, and none of the enter keys/left click/right click keys will work. Is there anyone who has a proper keymap for the remote, or can tell me how to set it up? It's not a USB IrDA unfortunately, so i'm not sure where to go with this.

---

### Post by SiHa on 2009-08-11
As it's almost working, it looks like your LIRC setup is OK. You could try irrecord to record a new lircd.conf.

---

### Post by derrick1985 on 2009-08-11
> **SiHa said:**
> As it's almost working, it looks like your LIRC setup is OK. You could try irrecord to record a new lircd.conf.

How would I do this? I'm new to LIRC, never had any need before to use it.

---

### Post by SiHa on 2009-08-11
Have a look in /etc/hardware.conf.

This will tell you what driver you are using (if any) and what device you are using for the receiver.

Then you need to stop lirc:```
sudo /etc/init.d/lirc stop
```

Then run ```
irrecord --driver=xxxx --device=xxxx ~/lircd.conf
``` and follow the instructions - it should guide you through recording a new file for your remote. I've just used **~/lircd.conf** so it goes in your home directory, but you can put it anywhere you like.
**Hint** you should use standard names for the keys, so that your lircrc can map them correctly. You could look at your current lircd.conf for these. The file **/etc/lirc/lircd.conf** should have an include statement that points to your current configuration.

To test the new file, comment out the above include, and add one pointing to the newly recorded file. Restart lirc:```
sudo /etc/init.d/lirc start
```Then run irw and press some buttons.

If all has gone well irw will correctly identify all the buttons you recorded.

Hopefully that will be it, restart Myth and it will work. If you're still missing a few, you may need to modify your lircd.conf to ensure the keynames match those specified in your lircrc **/home/mythuser/.lircrc** (or the mythtv configuration pointed to within this file). **mythuser** is the user that the frontend runs as.

Best of luck,

Simon

---

### Post by derrick1985 on 2009-08-11
I'm getting an error when trying to start irrecord

rockwelltv@rockwelltv:~$ irrecord --driver=devinput --device=lirc0 ~/lircd.conf

irrecord -  application for recording IR-codes for usage with lirc

Copyright (C) 1998,1999 Christoph Bartelmus(lirc@bartelmus.de)

irrecord: initializing 'lirc0'
irrecord: unable to open 'lirc0'
irrecord: could not init hardware (lircd running ? --> close it, check permissions)


I tried doing this with lirc started and lirc stopped (sudo /etc/init.d/lirc stop or start) and it won't budge.

This is the major part of the file. 

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="MSI TV@nywhere Master"
REMOTE_MODULES=""
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="msi/lircd.conf.tvanywhere"
REMOTE_LIRCD_ARGS=""

i'm not sure exactly what I am doing wrong.

---

### Post by SiHa on 2009-08-12
Well your IR device is **/dev/lirc0**, but you have it as **lirc0** in the irrecord commandline.

Try ```
rockwelltv@rockwelltv:~$ irrecord --driver=devinput **--device=/dev/lirc0** ~/lircd.conf

```

I have to admit, it's been a year since I needed to play with irrecord, so I've probably forgotten some of the tricks to try and get it working.

---

### Post by derrick1985 on 2009-08-12
> **SiHa said:**
> Well your IR device is **/dev/lirc0**, but you have it as **lirc0** in the irrecord commandline.

Try ```
rockwelltv@rockwelltv:~$ irrecord --driver=devinput **--device=/dev/lirc0** ~/lircd.conf

```

I have to admit, it's been a year since I needed to play with irrecord, so I've probably forgotten some of the tricks to try and get it working.

Sorry, that command I put in there was another try I used.

I'm sure that I tried it with the /dev/ in front, but still yielded the same results. I'll tray later today and see what happens.

---

### Post by hphd-Blokkolnam on 2009-08-13
I managed to start irrecord, I had the same error message like you had, I think you forgot to put sudo beforethe irrecord command like this:

```
sudo irrecord --driver=devinput --device=/dev/input/event6  ~/lircd.conf
```This works for me, and I get some info, but after that I get this:

```
Hold down an arbitrary button.
.irrecord: gap not found, can't continue irrecord: closing '/dev/input/event6'
```(I hold down a button until I got the above msg.)
:( :confused:

Here : [http://lirc.sourceforge.net/remotes/msi/TV@nywhere](http://lirc.sourceforge.net/remotes/msi/TV@nywhere) I have found a different config file for the remote, now I give it a try...
hmm...I tried it as well, i modified the config files, but nothing changes...

Could you tell me, if your remote still running after you stoped lirc (```
sudo /etc/init.d/lirc stop
```)? I stop lirc, but my remote happily runs on :confused:

---

### Post by derrick1985 on 2009-08-13
> **hphd-Blokkolnam said:**
> I managed to start irrecord, I had the same error message like you had, I think you forgot to put sudo beforethe irrecord command like this:

```
sudo irrecord --driver=devinput --device=/dev/input/event6  ~/lircd.conf
```This works for me, and I get some info, but after that I get this:

```
Hold down an arbitrary button.
.irrecord: gap not found, can't continue irrecord: closing '/dev/input/event6'
```(I hold down a button until I got the above msg.)
:( :confused:

Here : [http://lirc.sourceforge.net/remotes/msi/TV@nywhere](http://lirc.sourceforge.net/remotes/msi/TV@nywhere) I have found a different config file for the remote, now I give it a try...
hmm...I tried it as well, i modified the config files, but nothing changes...

Could you tell me, if your remote still running after you stoped lirc (```
sudo /etc/init.d/lirc stop
```)? I stop lirc, but my remote happily runs on :confused:

Yeah, my remote keeps going. Still haven't found a way to get this damned thing to work. Might just have to bite the bullet and buy a USB-IR and a MCE remote. I can't for the life of me, get this damned remote to work.

---

### Post by derrick1985 on 2009-08-13
Woohoo, finally got something recorded! Now, how do I make this work with myth?


And BTW, hphd-Blokkolnam you pointed me in the right direction. instead of input6, i used 7 and it worked great. The only thing is, the first screen you get to where it says hold, I didn't do, I just pressed a button repeatedly and it worked. It then asked me to map out everything. Here is a copy of the code I was able to get for my remote, hopefully it will be of some use to you. 

```

# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.4a(devinput) on Thu Aug 13 22:09:48 2009
#
# contributed by 
#
# brand:                       /home/rockwelltv/msitvanywhereplus.conf
# model no. of remote control: 
# devices being controlled by this remote:
#

begin remote

  name  /home/rockwelltv/msitvanywhereplus.conf
  bits           16
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   16
  pre_data       0x8001
  gap          151980
  toggle_bit_mask 0x8001004F

      begin codes
          1                        0x004F
          2                        0x0050
          3                        0x0051
          4                        0x004B
          5                        0x004C
          6                        0x004D
          7                        0x0047
          8                        0x0048
          9                        0x0049
          0                        0x0052
          +                        0x004E
          Recall                   0x0081
          source                   0x0182
          scan                     0x00D9
          Mute                     0x0071
          TV/FM                    0x0181
          FF                       0x0192
          RW                       0x0193
          up                       0x00D0
          down                     0x00A8
          record                   0x00A7
          stop                     0x0080
          play                     0x00CF
          minimize                 0x00CE
          zoom                     0x0174
          snapshot                 0x019A
          mts                      0x0170
          ch+                      0x0192
          ch-                      0x0193
          vol+                     0x0073
          vol-                     0x0072
          left                     0x00A8
          right                    0x00D0
          function                 0x008B
          reset                    0x0198
      end codes

end remote



```

---

### Post by hphd-Blokkolnam on 2009-08-14
hmmm... I will try to not hold down a button continously, but pushing it repeatedly as you did...I will check what I get, thanks for the idea! :)

---

### Post by SiHa on 2009-08-14
> Woohoo, finally got something recorded! Now, how do I make this work with myth?

If you make your hardware.conf point to the newly recorded lircd.conf (sorry - forgot about sudo for irrecord - it's been a while), and restart lirc, then run irw, do you get all the proper buttons reported?

If so, then you just need to edit your lircrc, as I explained in my first post. Your Mythtv lircrc config should be **/home/rockwelltv/.lirc/mythtv**

Here's mine as an example. The remote name will be the one specified in lircd.conf, I think. I forgot to change mine from the default recorded one.

 ```
# LIRCRC Auto Generated by Mythbuntu Lirc Generator
# Author(s): Mario Limonciello, Nick Fox
# Created for use with Mythbuntu

begin
    remote = lircd.conf
    prog = mythtv
    button = Videos
    config = F5
    repeat = 0
    delay = 0
end

begin
    remote = lircd.conf
    prog = mythtv
    button = Pictures
    config = F7
    repeat = 0
    delay = 0
end


begin
    remote = lircd.conf
    prog = mythtv
    button = 7
    config = 7
    repeat = 0
    delay = 0
end

begin
    remote = lircd.conf
    prog = mythtv
    button = ArrowRight
    config = Right
    repeat = 2
    delay = 2
end

begin
    remote = lircd.conf
    prog = mythtv
    button = Mute
    config = |
    repeat = 0
    delay = 0
end

begin
    remote = lircd.conf
    prog = mythtv
    button = Skip
    config = Z
    repeat = 0
    delay = 0
end

begin
    remote = lircd.conf
    prog = mythtv
    button = 1
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = lircd.conf
    prog = mythtv
    button = ArrowDown
    config = Down
    repeat = 2
    delay = 2
end

begin
    remote = lircd.conf
    prog = mythtv
    button = Replay
    config = Q
    repeat = 0
    delay = 0
end

begin
    remote = lircd.conf
    prog = mythtv
    button = Pause
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = lircd.conf
    prog = mythtv
    button = Menu
    config = M
    repeat = 0
    delay = 0
end

begin
    remote = lircd.conf
    prog = mythtv
    button = 6
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = lircd.conf
    prog = mythtv
    button = 2
    config = 2
    repeat = 0
    delay = 0
end

begin
    remote = lircd.conf
    prog = mythtv
    button = ChDown
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = lircd.conf
    prog = mythtv
    button = Exit
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = lircd.conf
    prog = mythtv
    button = ChUp
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = lircd.conf
    prog = mythtv
    button = Rewind
    config = <
    repeat = 0
    delay = 0
end

begin
    remote = lircd.conf
    prog = mythtv
    button = FF
    config = >
    repeat = 0
    delay = 0
end

begin
    remote = lircd.conf
    prog = mythtv
    button = Play
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = lircd.conf
    prog = mythtv
    button = VolDown
    config = [
    repeat = 0
    delay = 0
end

begin
    remote = lircd.conf
    prog = mythtv
    button = Stop
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = lircd.conf
    prog = mythtv
    button = VolUp
    config = ]
    repeat = 0
    delay = 0
end

begin
    remote = lircd.conf
    prog = mythtv
    button = 5
    config = 5
    repeat = 0
    delay = 0
end

begin
    remote = lircd.conf
    prog = mythtv
    button = 4
    config = 4
    repeat = 0
    delay = 0
end

begin
    remote = lircd.conf
    prog = mythtv
    button = OK
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = lircd.conf
    prog = mythtv
    button = ArrowUp
    config = Up
    repeat = 2
    delay = 2
end

begin
    remote = lircd.conf
    prog = mythtv
    button = Rec
    config = R
    repeat = 0
    delay = 0
end

begin
    remote = lircd.conf
    prog = mythtv
    button = 9
    config = 9
    repeat = 0
    delay = 0
end

begin
    remote = lircd.conf
    prog = mythtv
    button = 0
    config = 0
    repeat = 0
    delay = 0
end

begin
    remote = lircd.conf
    prog = mythtv
    button = 3
    config = 3
    repeat = 0
    delay = 0
end

begin
    remote = lircd.conf
    prog = mythtv
    button = 8
    config = 8
    repeat = 0
    delay = 0
end

begin
    remote = lircd.conf
    prog = mythtv
    button = Guide
#    config = S
    config = F6
    repeat = 0
    delay = 0
end

begin
    remote = lircd.conf
    prog = mythtv
    button = ArrowLeft
    config = Left
    repeat = 2
    delay = 2
end

```

You need a section for each entry in your lircd.conf, with **button** being the remote button, and **config** being the keypress that you want to pass to Mythtv.

Default keybindings can be found using mythweb at **[http://backend.ip.address/mythweb/settings/mythtv/keys](http://backend.ip.address/mythweb/settings/mythtv/keys)**

You'll notice that some buttons have a non-zero value for **repeat** that's so it will pass multiple events to Mythv if you hold the button down. The number is how many remote events are skipped between each one sent to Myth. This is usually used with a delay, which is the number of extra events skipped before the first repeat event is sent.

---

### Post by derrick1985 on 2009-08-14
Ok all, thanks, I got it to FINALLY work. 

This is what I did for anyone else who is having the same issue.

First, open a terminal and goto /usr/share/lirc/remotes/msi

sudo nano lirc.conf.tvanywhereplus

and paste the below code in. 

```

# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.4a(devinput) on Thu Aug 13 22:09:48 2009
#
# contributed by Derrick Rockwell (derrick dot rockwell at gmail dot com)
#
# brand:                       MSItv@nywhere Plus
# model no. of remote control: 
# devices being controlled by this remote:
#

begin remote

  name  msitvanywhere_plus
  bits           16
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   16
  pre_data       0x8001
  gap          151980
  toggle_bit_mask 0x8001004F

      begin codes
          1                        0x004F
          2                        0x0050
          3                        0x0051
          4                        0x004B
          5                        0x004C
          6                        0x004D
          7                        0x0047
          8                        0x0048
          9                        0x0049
          0                        0x0052
          OK                       0x004E
          Return                   0x0081
          source                   0x0182
          scan                     0x00D9
          Mute                     0x0071
          TV/FM                    0x0181
          up                       0x00D0
          down                     0x00A8
          record                   0x00A7
          stop                     0x0080
          Play                     0x00CF
          ArrowLeft                0x00CE
          ArrowRight               0x0174
          T-shift                  0x019A
          MTS                      0x0170
          ChUp                     0x0192
          ChDown                   0x0193
          VolUp                    0x0073
          VolDown                  0x0072
          Rewind                   0x00A8
          FFWD                     0x00D0
          Function                 0x008B
          reset                    0x0198
	 	 
      end codes

end remote






```

Save and quit.

navigate to /usr/share/lirc

sudo nano lirc.hwdb

Look for the line with the current MSI remote, and add a new line below it and paste this.

```
MSI TV@nywhere Plus;devinput;none;hw_default;msi/lircd.conf.tvanywhereplus;

``` (all on one line)

Save and quit. 

Load up your mythbuntu control centre, and you should see it in the list, select it and hit apply. Now, personally, i'm not sure if this came from me messing around trying to get this to work over and over again, but if you get a prompt saying that dpkg-configure stopped, and asks you to put in your input, just choose it from the dropdown, and hit ok. 

This works for me, and the buttons work like they are labeled, except for the following:

The FM freq up and down buttons are the up and down for navigating through the menus
The minimize and zoom buttons are the left and right for navigating through the menus
The + sign is your ok button
The recall is your back button

I haven't fully tested this yet, so it might be buggy, this is my first time with LiRC and myth in general, so use at your own risk. Any bugs, please report. If you fix it yourself, please post your fix.

Good luck!

---

### Post by hphd-Blokkolnam on 2009-08-23
Hi!

I used your lircd.conf.tvanywhereplus config file. My other lirc files (in /etc/lirc) :

**hardware.conf** :
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="MSI TV@nywhere Plus"
REMOTE_MODULES=""
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/event6"
REMOTE_LIRCD_CONF="/usr/share/lirc/remotes/msi/lircd.conf.tvanywhereplus"
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
```my **lircd.conf** :
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

#Configuration for the MSI TV@nywhere Master remote:
include "/usr/share/lirc/remotes/msi/lircd.conf.tvanywhereplus"

```And this is how i try to set my ** .lircrc** file:

```
begin
    prog = irexec
    remote = MSI TV@nywhere Plus
    button = up
    config = tvtime-command CHANNEL_UP
end
```I have already read several topics on the net about howto setup tvtime with lirc, and i firstly run the "irexec", and after that I launch TVtime. 
But when I press the up button on my remote, irexec doesnt gives back anything (so either TVtime not responding for the button)...but it works for example for the numbers, for the Mute on my remote:

```
andras@andras-desktop:~$ irexec
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/andras/.tvtime/tvtime.xml
tvtime-command: Sending command CHANNEL_1.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/andras/.tvtime/tvtime.xml
tvtime-command: Sending command TOGGLE_MUTE.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/andras/.tvtime/tvtime.xml
tvtime-command: Sending command TOGGLE_MUTE.

```Thanks for any help!
best wishes,


okey, I figured out that, I had also the gnome-lirc-properties app installed on my system, so I have to deal with the /usr/share/gnome-lirc-properties/receivers.conf as well!

---

