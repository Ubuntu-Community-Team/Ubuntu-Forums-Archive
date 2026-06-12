---
title: "Ubuntu 7.04, MythTv and WinTv Nova-T 500"
date: 2007-10-04
forum: Multimedia &amp; Video
---

### Post by mascat on 2007-10-04
[SIZE="4"]I have just installed MythTV on my dell machine which has ubuntu pre-installed. I have installed the WinTV Nova-T-500 card and can see freeview channels.

I have tried to install the remote but the remote does not work. I followed the instruction in 

[http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI)

but when I start lirc and run "irw" and press keys on the remote, I dont get any responses. I have followed teh instructions to the letter but no luck.

Anybody knows how to get the remote working with ubuntu and mythtv?

mascat







 [/SIZE]

---

### Post by Scorpuk on 2007-10-05
Not used my Nova-T 500 remote as the cards are in my server. Still to setup my frontend box with a remote, but should have no hassle as I am using an MCE remote and had it working before when I was using a forntend/backend computer.

Anywho can you give me the results from the following commands? (copy and paste is best)


```
dmesg | grep DVB
```


```
ls -l /dev/input/event*
```


and the contents for the following file:

```
sudo gedit  /etc/lirc/hardware.conf 
```

Hopefully something simple to sort out ;-)

---

### Post by mascat on 2007-10-05
Hi,

Here are the info:

**dmesg | grep DVB**

[   18.210582] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in cold state, will try to load a firmware
[   18.962306] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in warm state.
[   18.962466] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
[   19.075235] DVB: registering frontend 0 (DiBcom 3000MC/P)...
[   19.633060] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
[   19.638761] DVB: registering frontend 1 (DiBcom 3000MC/P)...
[   20.202004] input: IR-receiver inside an USB DVB receiver as /class/input/input4
[   20.202052] dvb-usb: Hauppauge Nova-T 500 Dual DVB-T successfully initialized and connected.


**ls -l /dev/input/event*:**

crw-rw---- 1 root root 13, 64 2007-10-05 22:27 /dev/input/event0
crw-rw---- 1 root root 13, 65 2007-10-05 22:27 /dev/input/event1
crw-rw---- 1 root root 13, 66 2007-10-05 22:27 /dev/input/event2
crw-rw---- 1 root root 13, 67 2007-10-05 22:27 /dev/input/event3
crw-rw---- 1 root root 13, 68 2007-10-05 22:27 /dev/input/event4
crw-rw---- 1 root root 13, 69 2007-10-05 22:28 /dev/input/event5
crw-rw---- 1 root root 13, 70 2007-10-05 22:28 /dev/input/event6

**sudo gedit  /etc/lirc/hardware.conf:**

# /etc/lirc/hardware.conf
#
# Arguments which will be used when launching lircd
LIRCD_ARGS=""

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER="dev/input"
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE=""
MODULES=""
#LIRCD_ARGS="--device=/dev/lirc0"
#MODULES="lirc_pvr150"

# Default configuration files for your hardware if any
LIRCD_CONF="/etc/lirc/lircd.conf"
LIRCMD_CONF=""

I hope this gives info info to find out whats happening.

thx
mascat

---

### Post by Scorpuk on 2007-10-06
I think I see where the guide has let you down:


On the guide he has the following for dmesg | grep DVB


```
[   34.787147] input: IR-receiver inside an USB DVB receiver as /class/input/input4
```


and then the follwing for :/etc/lirc/hardware.conf

```
# Run "lircd --driver=help" for a list of supported drivers.
DRIVER="dev/input"
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE="/dev/input/event4"
MODULES=""
```


So for yours try adding in :


```

# /etc/lirc/hardware.conf
#
# Arguments which will be used when launching lircd
LIRCD_ARGS=""

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER="dev/input"
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
[COLOR="Red"]DEVICE="/dev/input/event4"[/COLOR]
MODULES=""
#LIRCD_ARGS="--device=/dev/lirc0"
#MODULES="lirc_pvr150"

# Default configuration files for your hardware if any
LIRCD_CONF="/etc/lirc/lircd.conf"
LIRCMD_CONF=""

```


Just to confirm the bit you change is:

[COLOR="Red"]DEVICE="/dev/input/event4"[/COLOR]


I am presuming input4 = event4 ;-)


Let us know how ya get on.

---

### Post by mascat on 2007-10-06
[SIZE=3]Hi,

Thanks. I added the DEVICE="/dev/input/event4" to the _/etc/lirc/hardware.conf_ file but it made no difference. The _irw_ does not detect any key presses and just sits there.

The Nova-T card is a PCI card and I am a bit confused that it thinks the  input is coming from inside a USB device i.e. _IR-receiver inside an USB DVB receiver as /class/input/input4 _. This might be a red-herring though.[/SIZE]  

Not sure how else I test it.

---

### Post by Scorpuk on 2007-10-06
The Nova-T 500 is actually a usb controller with the two tuners connected to that.

Personally I haven't tried the IR part of the card and probably won't as they are sitting in my server.



Not entirely sure what could be the problem.



I'd give it a go on my server, but I wont be home until next weekend so can't really do much more on this.


Good luck though!

---

### Post by mascat on 2007-10-06
Ok, I'll keep playing with it to see if I can fix it.

mascat

---

### Post by sygin on 2007-10-14
Hi Mascat, 

I have my setup working very well, remote and all.

See: [http://ubuntuforums.org/showthread.php?p=3530236#post3530236](http://ubuntuforums.org/showthread.php?p=3530236#post3530236)

Cheers
Sygin

---

