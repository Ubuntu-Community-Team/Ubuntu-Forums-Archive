---
title: "Stuck on configuring lirc for pinnacle usb stick 330e"
date: 2011-05-25
forum: Multimedia Software
---

### Post by dancer_69 on 2011-05-25
Hello
I have a pinnacle usb stick(330e) and after I've managed to make it work(both Analog and Digital)
I'm trying to configure the remote control to work with lirc.
I've search a lot for this device' s remote control configuration and I found only this tutorial 
for this specific device(which is unfortunately in Italian):
	[http://tox87.wordpress.com/2009/06/01/hybrid-pro-stick-pctv-pinnacle-330e-id-23040226/](http://tox87.wordpress.com/2009/06/01/hybrid-pro-stick-pctv-pinnacle-330e-id-23040226/)
I found more general usefull and on other places and I've managed the following:
1. Find the input for IR device from
      [COLOR="DarkRed"]cat /proc/bus/input/devices[/COLOR]
	
```
I: Bus=0003 Vendor=2304 Product=0226 Version=0001
N: Name="em28xx IR (em28xx #0)"
P: Phys=usb-0000:00:1a.7-5/input0
S: Sysfs=/devices/pci0000:00/0000:00:1a.7/usb1/1-5/rc/rc0/input3
U: Uniq=
H: Handlers=kbd event10
B: PROP=0
B: EV=100013
B: KEY=c0000 142000 0 0 0 0 10000 190 1 1e0000 0 0 10000ffc
B: MSC=10

```
2. successfully load lirc and make lircd.conf with:
irrecord -H dev/input -d /dev/input/event4 /tmp/lircd.conf
and move it to /etc/lirc.
3. Change the hardware.conf file:
    ```
# /etc/lirc/hardware.conf
    #
    #Chosen Remote Control
    REMOTE="None"
    REMOTE_MODULES=""
    REMOTE_DRIVER=""
    REMOTE_DEVICE=""
    REMOTE_SOCKET=""
    REMOTE_LIRCD_CONF=""
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
    # Arguments which will be used when launching lircd
    LIRCD_ARGS="-d /dev/input/event10 -n"
    #Don't start lircmd even if there seems to be a good config file
    #START_LIRCMD=true
    #Don't start irexec, even if a good config file seems to exist.
    #START_IREXEC=true

    #Try to load appropriate kernel modules
    LOAD_MODULES=true
    # Run "lircd --driver=help" for a list of supported drivers.
    DRIVER="dev/input"
    # If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
    # automatically used instead
    DEVICE="/dev/input/event10"
    MODULES=""
    # Default configuration files for your hardware if any
    LIRCD_CONF="/etc/lirc/lircd.conf"
    LIRCMD_CONF=""

    #Forcing noninteractive reconfiguration
    #If lirc is to be reconfigured by an external application
    #that doesn't have a debconf frontend available, the noninteractive
    #frontend can be invoked and set to parse REMOTE and TRANSMITTER
    #It will then populate all other variables without any user input
    #If you would like to configure lirc via standard methods, be sure
    #to leave this set to "false"
    FORCE_NONINTERACTIVE_RECONFIGURATION="false"

```

This is the final form, but I've tried a lot of different configs.

4. I've managed to forse hal to ignore my IR device according to related lirc documentation topic


And I have stucked here because lirc refuses to recognize and use my device, unless if I
run the daemon with this command:
[COLOR="DarkRed"]sudo /usr/sbin/lircd -H dev/input -d /dev/input/event10 -n [/COLOR]
Then, irw works and I can see the output and the names I defined with lirc.conf
by pressing any remote's button.
But whe lirc starts by [COLOR="DarkRed"]/etc/init.d/lircd restart[/COLOR]
always fails.

Any ideas on how to solve this and finnaly configure my device?

---

### Post by dancer_69 on 2011-05-26
This problem solved!!!
The hardware.conf file need to be like this:
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="em28xx"
REMOTE_MODULES="lirc_dev"
REMOTE_DRIVER="dev/input"
REMOTE_DEVICE="/dev/input/event10"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="etc/lirc/lircd.conf"
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
#LIRCD_ARGS="-H dev/input -d /dev/input/event10" 
#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=true
#Don't start irexec, even if a good config file seems to exist.
START_IREXEC=true 

#Try to load appropriate kernel modules
LOAD_MODULES=true 
# Run "lircd --driver=help" for a list of supported drivers.
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
#DEVICE=""
#MODULES="" 
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

Now the problem is that the programs(except irexec), don't recognize any commands.
I tried to test with vlc, mplayer, kaffeine and none of these can recognize the pushed buttons.
Any help for this??

---

### Post by dancer_69 on 2011-05-26
I feel that I'm talking with myself, but I hope that someone who can help pass this thread.

  I have some problems with lirc still. 
-First is that irexec(now works) doesn't start on reboot. I've enabled this option as you can   see on above hardware.conf file, and I've add an entry to startup programs.

-And the other is that in every reboot only some of the buttons work, and needed to restart lirc daemon to start work all buttons.

---

### Post by dancer_69 on 2011-05-28
None of above problems solved yet.
The only change is that on every reboot **none** of the buttons working until I restart lirc daemon. And maybe I found a solution for irexec, but I didn't test it yet.
[COLOR="Red"]Please give me some help to investigate and(maybe) to solve the restart lirc problem[/COLOR].

---

### Post by dancer_69 on 2011-06-23
After a booting from grub problem I've reinstall ubuntu(from a backup) and now I'm using 64bit version. 
I have again problems to make remote control work.
Now the remote doesn't listed on /proc/bus/input/devices.
  modprobe lirc_dev;dmesg | grep lirc  Give this output:
```
[   20.290652] lirc_dev: IR Remote Control driver registered, major 61 
[  883.404573] lirc_dev: IR Remote Control driver registered, major 61 

```
which means that the remote recognized.
Is there any way to fix this?? Please, give me some hints.
It takes a lot of time and searching to make it work first time, and now doesn't work at all(even as a keyboard device)

---

