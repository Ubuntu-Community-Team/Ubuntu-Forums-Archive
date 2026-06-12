---
title: "XBMCbuntu IR-receiver no response in irw or ir-keytable -t but works 100% in win7"
date: 2013-12-07
forum: Multimedia Software
---

### Post by timsanou on 2013-12-07
Hi I really hope to find some help here, because I've run out of possible solutions. I'm usually of the opinion that everything has been asked before and i can find it with some Googling, but in this case I feel I've tried everything i could find and need someone to tell my I'm doing it all wrong and it's a really simple fix I've just been overlooking.

I installed xbmcbuntu-12.2.Intel-NVIDIA it runs
[LIST]
[*]Ubuntu 12.10
[*]Linux 3.5.0-44-generic
[/LIST]

My IR receiver is "0471:0815 Philips (or NXP) eHome Infrared Receiver"

What I've tried so far:
[LIST]
[*]tried different combinations of reconfigure selection "Windows Media Center Transceivers/Remotes (all)" and "Microsoft Windows Media Center V2 (usb) : Direct TV Receiver"
[*]purged and reinstalled lirc
[*]ir-keytable without lirc and with lirc
[*]blacklisted anything i could find to do with mce and lirc then tried with lirc and ir-keytable
[*]installed 13.10 and tried there this didn't help
[/LIST]

Situation now:
[LIST]
[*]Re-installed everything is default after installation
[*]no irw or ir-keytable(not currently installed) response at all, never during anything testing have I ever had any response
[*]Tried it in Windows 7 machine just 5min ago to be 100% sure and could control OS seconds after plugging it in
[*]I'm open to trying anything, i would be ecstatic if I could get any sort of response in Linux from pressing a button on that thing.
[/LIST]

dmesg seems to have it registering fine.
```

[  317.276052] usb 1-2: new full-speed USB device number 3 using ohci_hcd[  317.744778] usb 1-2: New USB device found, idVendor=0471, idProduct=0815
[  317.744780] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  317.744781] usb 1-2: Product: eHome Infrared Transceiver
[  317.744782] usb 1-2: Manufacturer: Philips
[  317.744783] usb 1-2: SerialNumber: PH00WFo3
[  317.864026] Registered IR keymap rc-rc6-mce
[  317.864143] input: Media Center Ed. eHome Infrared Remote Transceiver (0471:0815) as /devices/pci0000:00/0000:00:06.0/usb1/1-2/1-2:1.0/rc/rc0/input5
[  317.864187] rc0: Media Center Ed. eHome Infrared Remote Transceiver (0471:0815) as /devices/pci0000:00/0000:00:06.0/usb1/1-2/1-2:1.0/rc/rc0
[  317.884975] IR NEC protocol handler initialized
[  317.886536] IR RC5(x) protocol handler initialized
[  317.887934] IR RC6 protocol handler initialized
[  317.889505] IR JVC protocol handler initialized
[  317.910507] IR Sony protocol handler initialized
[  317.933916] IR SANYO protocol handler initialized
[  317.991261] input: MCE IR Keyboard/Mouse (mceusb) as /devices/virtual/input/input6
[  317.992832] IR MCE Keyboard/mouse protocol handler initialized
[  318.000876] rc rc0: lirc_dev: driver ir-lirc-codec (mceusb) registered at minor = 0
[  318.000878] IR LIRC bridge handler initialized
[  318.056846] mceusb 1-2:1.0: Registered Philips eHome Infrared Transceiver with mce emulator interface version 1
[  318.056846] mceusb 1-2:1.0: 2 tx ports (0x0 cabled) and 2 rx sensors (0x0 active)
[  318.056846] usbcore: registered new interface driver mceusb

```

cat /proc/bus/input/devices
```


I: Bus=0003 Vendor=0471 Product=0815 Version=0000
N: Name="Media Center Ed. eHome Infrared Remote Transceiver (0471:0815)"
P: Phys=usb-0000:00:06.0-2
S: Sysfs=/devices/pci0000:00/0000:00:06.0/usb1/1-2/1-2:1.0/rc/rc0/input5
U: Uniq=
H: Handlers=kbd event5
B: PROP=0
B: EV=100013
B: KEY=fff 0 0 200 108fc32e 2376051 0 0 0 7 158000 4192 4001 8e9680 0 0 10000000
B: MSC=10


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="MCE IR Keyboard/Mouse (mceusb)"
P: Phys=/input0
S: Sysfs=/devices/virtual/input/input6
U: Uniq=
H: Handlers=sysrq kbd mouse2 event6
B: PROP=0
B: EV=100017
B: KEY=30000 0 7 ff87207a c14057ff febeffdf ffefffff ffffffff fffffffe
B: REL=3
B: MSC=10



```


hardware.conf has not been modified after installation and plug-in of receiver (i have not done any configuration or selection, all automatic)
/etc/lirc/hardware.conf 
```


# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Remotes (new version Philips et al.)"
REMOTE_MODULES="lirc_dev lirc_mceusb2"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
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

(also default)
/etc/lirc/lircd.conf

```


#This configuration has been automatically generated via#the Ubuntu LIRC package maintainer scripts.
#
#It includes the default configuration for the remote and/or
#transmitter that you have selected during package installation.
#
#Feel free to add any custom remotes to the configuration
#via additional include directives or below the existing
#Ubuntu include directives from your selected remote and/or
#transmitter.


#Configuration for the Windows Media Center Remotes (new version Philips et al.) remote:
include "/usr/share/lirc/remotes/mceusb/lircd.conf.mceusb"



```

I really hope someone has an idea because I'm all out :(

---

### Post by SuperFreak on 2013-12-07
I wish I could offer more help as I am having the same issues with my eHome Philips IR receiver that I am trying to get to work with XBMC.
This is what I found [HERE]("http://wiki.xbmc.org/index.php?title=HOW-TO:Setup_an_MCE_remote_control_in_Linux") but I haven't had any luck so far. You can set LIRC to Linux input layer (/dev/input/eventX)   instead of Windows Media Center Transceivers/Remotes (all)". I then chose None on the next menu and then on the third menu there is a choice for philips eHome IR  or something like that.
Please post any progress you make as I am having a devil of a time with this

---

### Post by SuperFreak on 2013-12-08
After a great deal of hair pulling and gnashing of teeth I came across a post that said that the receiver might have problems with USB 3 ports. Dutifully I reset LIRC menu to Windows Media Center Transceivers/Remotes (all)" and second menu to none after plugging my philips eHome receiver in the USB port. I tried irw in Terminal and Low and Behold it works. It works for XBMC also.
I am not sure if the USB port was your issue but try it in a USB 2 port

Good Luck

---

### Post by timsanou on 2013-12-08
Thanks for sharing your struggles, if it is the USB 3.0 then it is for some weird reason only with Linux because my Win7 machine is also usb 3.0 and running a VM with xbmcbuntu presents the same problem while working fine in windows. I'm going to dig out an old laptop that should still have some USB 2.0 ports and test is on there.

Thanks again for your info.

---

### Post by SuperFreak on 2013-12-08
I have a dual boot with my laptop and the remote worked in Win 7  already. However I rebooted my computer this afternoon and remote was not working in Ubuntu anymore. Once I renconfigured LIRC again with dpkg-reconfigure lirc it worked. Looks like it is not persistenting through reboots.  I will look into it more over the next day and see if I can make it a persistent change

---

### Post by SuperFreak on 2013-12-08
OK A little progress

Following the direction at [THIS]("http://wiki.xbmc.org/index.php?title=HOW-TO:Setup_an_MCE_remote_control_in_Linux") page to change this setting

> The START_LIRCD parameter should be now set to false in /etc/lirc/hardware.conf configuration file.
I found when I rebooted the remote was working. The setting in the file was true and I set it to false

I have to admit I am not very Linux savvy so it is guess work but it seems to work. I will try a second reboot and see if it works. 

Does the computer you are using not have both USB 3 and USB 2 ports?

EDIT: Second reboot and remote still works. Thinking that I may have my remote finally working now. I am using a Logitech Harmony 650 remote with the Philips eHome IR receiver. I tried my Harmony 300 and it works too.

I hope my posts may have helped you

2nd Edit: I am not able to get LIRC to persist after reboots consistently and have started a new thread at [http://ubuntuforums.org/showthread.php?t=2192761]("http://ubuntuforums.org/showthread.php?t=2192761")

---

