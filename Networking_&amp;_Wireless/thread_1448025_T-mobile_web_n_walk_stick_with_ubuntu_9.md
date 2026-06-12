---
title: "T-mobile web n walk stick with ubuntu 9"
date: 2010-04-06
forum: Networking &amp; Wireless
---

### Post by fifty56 on 2010-04-06
hi,

I've read many threads, but still stacked in the problem. Here's my system so far:

a new install of ubuntu 9.10, on an asus eee pc, and my t-mobile usb stick (which works with ubuntu 8 on my other machine)

lsusb:[INDENT][FONT=Courier New]Bus 001 Device 002: ID 13d3:5126 IMC Networks 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 004: ID 0af0:6971 Option 
Bus 004 Device 002: ID 0b05:1788 ASUSTek Computer, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[/FONT][/INDENT]/etc/usb_modeswitch.conf:[INDENT][FONT=Courier New]DefaultVendor=  0x0af0
DefaultProduct= 0x6971
TargetClass=    0xff
MessageEndpoint=0x05
MessageContent="55534243785634120100000080000601000000000000000000000000000000"[/FONT][/INDENT]/etc/udev/rules.d/51-hso-udev.rules[INDENT][FONT=Courier New]ATTRS{idVendor}=="6971", ATTRS{idProduct}=="0af0", RUN+="/usr/sbin/ozerocdoff -wi 0x%s{idProduct}"

SUBSYSTEM=="usb_device", SYSFS{idVendor}=="6971", SYSFS{idProduct}=="0af0, SYSFS{bDeviceClass}=="ff", RUN+="/usr/sbin/ozerocdoff -wi 0x%s{idProduct}"

SUBSYSTEM=="usb", SYSFS{idProduct}=="0af0", SYSFS{idVendor}=="6971", RUN+="/usr/sbin/usb_modeswitch"[/FONT]

here I'm not sure whether I need usb_device or usb (?)
[/INDENT]ls -la /dev/ttyHS*[INDENT][FONT=Courier New]crw-rw---- 1 root dialout 251, 2 2010-04-05 22:22 /dev/ttyHS2[/FONT][/INDENT]When I plug in my stick to an usb port, I cannot see any modem in the network manager, neither a 3g connection. 

what should I do to see the usb as a 3g modem?

---

### Post by alexfish on 2010-04-06
Hi

you could try looking at the Pharscape  site here

[http://www.pharscape.org/](http://www.pharscape.org/)

[SIZE=2]Pharscape Forum [http://www.pharscape.org/forum/index.php](http://www.pharscape.org/forum/index.php)[/SIZE]

also can you have a read of this thread here, although it is for the option device as sold by orange, the thread my help, also take a look at the last post by Pharscape,
I could also suggest if you have other means of access to the Internet is to fully update your system and see if it works before attempting and updates on specific drivers or cofigurations


[http://ubuntuforums.org/showthread.php?t=1351612](http://ubuntuforums.org/showthread.php?t=1351612)

could also post details of this output from the terminal with this command

Code:

dmesg | grep -e "modem" -e "tty" 


this will indicate which lines the modem is using and also any drivers allocated

also from a separate terminal

Code:

tail -f /var/log/syslog

this shows what is happening in real time. use this command before plugging the modem in ,then see what the outputs are

thanks in advance

alexfish

---

### Post by fifty56 on 2010-04-06
here we go:

tail -f /var/log/syslog

[INDENT][FONT=Courier New]Apr  6 14:25:58 mayflower-laptop kernel: [  577.452029] usb 3-1: new full speed USB device using ohci_hcd and address 2
Apr  6 14:25:58 mayflower-laptop kernel: [  577.671286] usb 3-1: configuration #1 chosen from 1 choice
Apr  6 14:25:59 mayflower-laptop kernel: [  579.041811] usb 3-1: USB disconnect, address 2
Apr  6 14:26:01 mayflower-laptop kernel: [  580.588041] usb 3-1: new full speed USB device using ohci_hcd and address 3
Apr  6 14:26:01 mayflower-laptop kernel: [  580.803513] usb 3-1: configuration #1 chosen from 1 choice
Apr  6 14:26:01 mayflower-laptop kernel: [  580.875127] hso: /build/buildd/linux-2.6.31/drivers/net/usb/hso.c: 1.2 Option Wireless
Apr  6 14:26:01 mayflower-laptop kernel: [  580.877080] hso0: Disabled Privacy Extensions
Apr  6 14:26:01 mayflower-laptop kernel: [  580.878719] usbcore: registered new interface driver hso
Apr  6 14:26:01 mayflower-laptop kernel: [  580.911194] Initializing USB Mass Storage driver...
Apr  6 14:26:01 mayflower-laptop kernel: [  580.911366] usbcore: registered new interface driver usb-storage
Apr  6 14:26:01 mayflower-laptop kernel: [  580.911374] USB Mass Storage support registered.
Apr  6 14:26:01 mayflower-laptop usb_id[2018]: unable to access '/devices/pci0000:00/0000:00:04.0/usb3/3-1/3-1:1.0/tty/ttyHS0'
Apr  6 14:26:01 mayflower-laptop usb_id[2019]: unable to access '/devices/pci0000:00/0000:00:04.0/usb3/3-1/3-1:1.0/net/hso0'
Apr  6 14:26:01 mayflower-laptop modem-manager: (ttyHS2) opening serial device...
Apr  6 14:26:01 mayflower-laptop modem-manager: (ttyHS2): probe requested by plugin 'Option High-Speed'
Apr  6 14:26:01 mayflower-laptop usb_id[2020]: unable to access '/devices/pci0000:00/0000:00:04.0/usb3/3-1/3-1:1.0/tty/ttyHS1'
Apr  6 14:26:01 mayflower-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:04.0/usb3/3-1/3-1:1.0/net/hso0, iface: hso0)
Apr  6 14:26:01 mayflower-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:04.0/usb3/3-1/3-1:1.0/net/hso0, iface: hso0): no ifupdown configuration found.
Apr  6 14:26:01 mayflower-laptop NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:04.0/usb3/3-1/3-1:1.0/net/hso0, iface: hso0)
Apr  6 14:26:13 mayflower-laptop modem-manager: (ttyHS2) closing serial device...
Apr  6 14:27:08 mayflower-laptop wpa_supplicant[896]: CTRL-EVENT-SCAN-RESULTS 


[/FONT][/INDENT] dmesg | grep -e "modem" -e "tty" 

[INDENT][FONT=Courier New][    0.001949] console [tty0] enabled
[    1.610110] tty tty19: hash matches
[/FONT][/INDENT]

---

### Post by new_tolinux on 2010-04-06
If I remember well, you have to create it in Network Manager yourself.
As I don't have 9.10 and that stick on hand yet, I'm guessing it was in the "mobile connections" tab, but I'm absolutely not sure about that.

---

### Post by alexfish on 2010-04-06
hi

looking at the messages the modem is at present only seen as the storage device

you could try the usb modeswitch , the latest integrated pkg is 1.1.1 this is a tar file 

full details at

[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

the latest debian  package which will automatically install

                                 
[LIST]
[*][SIZE=2]Usb ModeSwitch Latest     debian Package [/SIZE]1.1.1-1
[/LIST]
    
[LIST]
[*][SIZE=2][http://packages.debian.org/sid/usb-modeswitch](http://packages.debian.org/sid/usb-modeswitch)[Package     ]("http://packages.debian.org/sid/usb-modeswitch")[/SIZE]
[/LIST]
  
looking at the site info, it does not mention any problem with hso drivers

[I]I can suggest this

 plug the modem in , if a device shows up on the desk top , rightclick and eject the device , Check the id's of the modem with the lsusb command before and after the eject, if there is a change in the device id then it should have been recognised as the modem , so check the info with the commands as previously mentioned , if nothing shows in the output of the [/I]dmesg | grep -e "modem" -e "tty" ,other than the two lines you have at present  then try the usb modeswitch. 

if the device is seen as the modem and the driver has loaded, then the Network Manager may see the modem, if so try to configure the device with NM

Added
Note:

The usb_modeswitch.conf file indicates this could be an                            Option iCON 225 HSDPA , here is an extract from the file

 
######################################################
# # Option iCON 225 HSDPA 
# 
# New Firmware. HSO driver support is available at Pharscape ([www.pharscape.org]("http://www.pharscape.org")) 
# 
# Contributor: Matti Viljanen 
 ;DefaultVendor=  0x0af0 
;DefaultProduct= 0x6971 
 ;TargetClass=    0xff

 # only for reference and 0.x versions 

# MessageEndpoint=0x05 

 ;MessageContent="555342431223456780100000080000601000000000000000000000000000000" 

Please note the  usb_modeswitch.conf file " Now Named  usb_modeswitch.setup" is now used only as a reference if you are using the new integrated modeswitch Package

regards

alexfish

---

### Post by fifty56 on 2010-04-06
I've upgraded my usb_modeswitch to 1.1.1, renamed the old .conf file to .setup with the same content. Nothing changed the output of dmesg | grep -e "modem" -e "tty" 
is the same :(

---

### Post by pdc on 2010-04-06
I see you have ozerocdoff already installed?

You shouldn't need both ozerocdoff AND usb_modeswitch;

ozerocdoff is the one for Option devices .....................

suggest delete usb_modeswitch

> make uninstall as from their website ........

---

### Post by pdc on 2010-04-06
Oh ...... and I think you have some errors in your ozerocdoff rules ..

> Default**Vendor**= 0x0af0 

> Default**Product**= 0x6971

 ........ taken from your lsusb and it agrees with other sources

> /etc/udev/rules.d/51-hso-udev.rules

    ATTRS{id**Vendor**}=="**6971**", ATTRS{id**Product**}=="**0af0**", RUN+="/usr/sbin/ozerocdoff -wi 0x%s{idProduct}"

    SUBSYSTEM=="usb_device", SYSFS{id**Vendor**}=="**6971**", SYSFS{id**Product**}=="**0af0**, SYSFS{bDeviceClass}=="ff", RUN+="/usr/sbin/ozerocdoff -wi 0x%s{idProduct}"

    SUBSYSTEM=="usb", SYSFS{idProduct}=="0af0", SYSFS{idVendor}=="6971", RUN+="/usr/sbin/usb_modeswitch"

but if you look, you seem to have mixed up vendor ID and product ID:

out of curiosity, was this a manual entry from you; (or software generated?)

I wonder if correcting that will help; and you could delete usb_modeswitch

---

### Post by fifty56 on 2010-04-07
I've upgraded my usb_modswitch from 0.9.4 to 1.1.1 and the network_manager to 8.1 and everything works. 

Thanks guys for your help!

---

