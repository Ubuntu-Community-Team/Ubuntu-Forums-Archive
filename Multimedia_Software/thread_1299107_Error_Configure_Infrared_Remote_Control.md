---
title: "Error Configure Infrared Remote Control"
date: 2009-10-23
forum: Multimedia Software
---

### Post by twinkler on 2009-10-23
Dear all,

I recently switched to Ubuntu 9.4 32bit. Now I am trying to set up an infrared remote control which works fine in Windows.

I installed lirc. Then in the "System Menu" - "Infrared Remote Control" appeared. If I start this and click on "auto-detect" it finds "Windows Media Center Remote".

It says the device is /dev/lirc0

Hitting buttons on the remote control results in nothing. Hence I tried to update the Update Remote Control funtion. This results in the following error:

```
Updating Remote Configuration Files

Rejected send message, 1 matched rules; 
type="method_call", sender=":1.39" 
(uid=1000 pid=4581 comm="/usr/bin/python /usr/bin/gnome-lirc-properties ")
 interface="org.gnome.LircProperties.Mechanism" 
member="InstallRemoteDatabase" error name="(unset)" 
requested_reply=0 destination=":1.42" 
(uid=0 pid=4649 comm="/usr/bin/python -m gnome_lirc_properties.backend ")
```when trying irw /dev/lirc0

I get "connect permission denied"

when trying irw and hitting the remote buttons I get noting 

lsusb gives me

```
Bus 001 Device 006: ID 046d:c03e Logitech, Inc. Premium Optical Wheel Mouse
Bus 001 Device 004: ID 057c:5601 AVM GmbH AVM FRITZ!WLAN Stick
Bus 001 Device 003: ID 05e3:0605 Genesys Logic, Inc. USB 2.0 Hub [ednet]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 045e:006d Microsoft Corp. eHome Remote Control Keyboard keys
Bus 002 Device 002: ID 04a9:2220 Canon, Inc. CanoScan LIDE 25
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
```lsmod | grep usb 
usbhid                 42336  0 
lirc_mceusb            16608  1 
lirc_dev               19892  1 lirc_mceusb

dmesg | grep lirc
[   10.463753] lirc_dev: IR Remote Control driver registered, major 61 
[   10.507013] lirc_dev: lirc_register_plugin: sample_rate: 80
[   11.121087] usbcore: registered new interface driver lirc_mceusb
[   11.121093] lirc_mceusb: USB Microsoft IR Transceiver Driver v0.2

It seems that I cant use the graphical interface to "train" my remote and irw is not working either. 

When I do a sudo /etc/init.d/lirc stop
and then a


sudo cat /dev/lirc0 

I get funny characters each time I hit the remote contol buttons. So something is going trough!

R&#65533;&#65533;&#65533;&#65533;&#65533;
 &#65533;RFR&#65533;&#65533;

my hardware.conf is pretty empty, though...but how can I fill it sensibly?

```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="None"
REMOTE_MODULES=""
REMOTE_DRIVER=""
REMOTE_DEVICE=""
REMOTE_LIRCD_CONF=""
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


```Does anyone know what I need to do to configure my remote?

Any help is appreciated. Sorry that all my dumps here are pretty confused but I already tried a lot here during the last days....

Cheers

Torsten

---

### Post by twinkler on 2009-10-25
Dear all,

I finally got it working. I did a re-install of Ubuntu. Then I installed lirc again. It asked me during the installation which Remote and Reciver I want to use. I used a Philips Remote (because I've got an RC6) and a custom receiver. Then I was able to set up everything with the graphical user interface. I guess the problem where the missing conf files which I was now able to provice during the Installation.

Cheers Torsten

---

