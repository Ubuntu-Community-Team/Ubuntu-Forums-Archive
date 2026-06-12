---
title: "Unable to transmit with USB-UIRT"
date: 2008-12-18
forum: Multimedia Software
---

### Post by wombatU42 on 2008-12-18
Hi,

I've been building my Mythbuntu box slowly over the last while (...years...) and have now encountered an problem that I've not been able to solve by my usual techniques (Google mostly with some blind luck)

The source of my TV signal is a satellite receiver (Bell Expressvu 3100) that goes into a PVR-350 card.  The box itself is running Mythbuntu 8.04.  Remote control is a cheap $10 RCA with a USB-UIRT receiver/transmitter.  I have progressed through the problems as I encountered them, first the wireless network, then the incoming signal, then the remote.  I can now rebuild this machine in less than 4 hours if I had to....

My current problem is getting the USB-UIRT to transmit to the satellite receiver to change the channels for me.  Using the USB-UIRT to receive signals is working fine.

I have gotten the USB-UIRT to transmit, or at least when I use the "IRSEND" command for lirc the USB-UIRT light flashes.  But nothing happens on the receiver.  

After my research I've noted that upon restarting LIRC, the following error is in /var/log/syslog: "uirt2_raw: checksum error"

My /etc/lirc/hardware.conf:
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Custom"
REMOTE_MODULES=""
REMOTE_DRIVER="usb_uirt_raw"
REMOTE_DEVICE="/dev/ttyUSB0"
REMOTE_LIRCD_CONF="/usr/share/lirc/remotes"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Custom"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER="usb_uirt_raw"
TRANSMITTER_DEVICE=""
#TRANSMITTER_LIRCD_CONF="/usr/share/lirc/transmitters/expressvu.conf"
#TRANSMITTER_LIRCD_ARGS="-d /dev/ttyUSB0 --output=/dev/lircd"
TRANSMITTER_LIRCD_ARGS="-d /dev/ttyUSB0"

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
FORCE_NONINTERACTIVE_RECONFIGURATION="true"
START_LIRCMD=""

```

My /etc/lirc/lircd.conf
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

#Configuration for the Custom remote:
include /usr/share/lirc/remotes/rca.conf

include /usr/share/lirc/transmitters/dish/3100.conf

```

/var/log/syslog after LIRC restart
```
Dec 16 22:08:14 photon lircd-0.8.3pre1[6690]: caught signal
Dec 16 22:08:14 photon lircd-0.8.3pre1[6685]: removed client
Dec 16 22:08:14 photon lircd-0.8.3pre1[6685]: caught signal
Dec 16 22:08:14 photon lircd-0.8.3pre1[6738]: lircd(userspace) ready
Dec 16 22:08:14 photon lircd-0.8.3pre1[6743]: lircd(userspace) ready
Dec 16 22:08:14 photon lircd-0.8.3pre1[6738]: accepted new client from 127.0.0.1
Dec 16 22:08:14 photon lircd-0.8.3pre1[6743]: connected to localhost
Dec 16 22:08:14 photon lircd-0.8.3pre1[6738]: uirt2_raw: checksum error
Dec 16 22:08:15 photon lircd-0.8.3pre1[6738]: uirt2_raw: UIRT version 0905 ok

```

/var/log/syslog after 'irsend SEND_ONCE 3100 power
```
Dec 16 22:08:58 photon lircd-0.8.3pre1[6738]: accepted new client on /dev/lircd
Dec 16 22:08:58 photon lircd-0.8.3pre1[6738]: uirt2_raw: UIRT version 0905
Dec 16 22:08:58 photon lircd-0.8.3pre1[6738]: removed client

```

my 3100.conf
```
#
# this config file was automatically generated
# using WinLIRC 0.6.5 (LIRC 0.6.1pre3) on Tue Apr 04 06:16:24 2006
#
# contributed by 
#
# brand:             301/501/3100/5100/58xx/59xx
# model:             
# supported devices: 
#

begin remote

  name  3100
  bits           16
  flags SPACE_ENC
  eps            30
  aeps          100

  header        400  6100
  one           400  1700
  zero          400  2800
  ptrail        400
  gap          6200
  min_repeat      4
  toggle_bit      0

  frequency    56000

      begin codes
          info                     0x0000000000000000
          power                    0x0000000000000800
          play                     0x0000000000000C10
          1                        0x0000000000001000
          2                        0x0000000000001400
          3                        0x0000000000001800
          frwd                     0x0000000000001C10
          4                        0x0000000000002000
          5                        0x0000000000002400
          6                        0x0000000000002800
          menu                     0x0000000000002C00
          7                        0x0000000000003000
          8                        0x0000000000003400
          9                        0x0000000000003800
          ffwd                     0x0000000000003C10
          select                   0x0000000000004000
          0                        0x0000000000004400
          cancel                   0x0000000000004800
          guide                    0x0000000000005000
          mute                     0x0000000000005401
          view                     0x0000000000005800
          tv_video                 0x0000000000005C00
          right                    0x0000000000006000
          vol+                     0x0000000000006401
          up                       0x0000000000006800
          recall                   0x0000000000006C00
          left                     0x0000000000007000
          vol-                     0x0000000000007401
          down                     0x0000000000007800
          rec                      0x0000000000007C00
          pause                    0x0000000000008000
          stop                     0x0000000000008400
          sys_info                 0x0000000000009000
          */ptv_list               0x0000000000009400
          #/search                 0x0000000000009800
          sat                      0x000000000000A400
          tv                       0x000000000000A801
          rew                      0x000000000000C410
          fwd                      0x000000000000C810
          skip_back                0x000000000000D810
          skip_fwd                 0x000000000000DC10
      end codes

end remote


```

I'm at the end of my rope with this problem.  Getting pretty close to either switching to cable or buying another transmitter.

Any help would be appreciated.

Thanks,
Phil

---

### Post by arishu on 2009-02-12
Hi everyone,

I need the community's help as well. I purchased a USB-UIRT device back in 2004 from [www.usbuirt.com](www.usbuirt.com) and it has been working fine on my SageTV/XP box. Now I am moving to Mythbuntu and can't make it work.

I have a Windows media center remote which works well for reception, I can control MythTv with it. But I can't make the IR blaster transmit.

I am following [https://help.ubuntu.com/community/Lirc_USB-UIRT](https://help.ubuntu.com/community/Lirc_USB-UIRT) step by step but this just doesn't work...

I do "dmesg | grep -i usb" and it returns the following

ariel@newmega:~$ dmesg | grep -i usb
[    2.117887] usbcore: registered new interface driver usbfs
[    2.117909] usbcore: registered new interface driver hub
[    2.117934] usbcore: registered new device driver usb
[    2.119522] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.527078] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[    4.584259] usb usb1: configuration #1 chosen from 1 choice
[    4.584372] hub 1-0:1.0: USB hub found
[    4.688792] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[    4.748270] usb usb2: configuration #1 chosen from 1 choice
[    4.748399] hub 2-0:1.0: USB hub found
[    4.956484] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[    5.016208] usb usb3: configuration #1 chosen from 1 choice
[    5.016353] hub 3-0:1.0: USB hub found
[    5.092019] usb 2-1: new full speed USB device using ohci_hcd and address 2
[    5.120438] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 4
[    5.180264] usb usb4: configuration #1 chosen from 1 choice
[    5.180432] hub 4-0:1.0: USB hub found
[    5.258372] usb 2-1: configuration #1 chosen from 1 choice
[    5.260220] hub 2-1:1.0: USB hub found
[    5.284772] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 5
[    5.344332] usb usb5: configuration #1 chosen from 1 choice
[    5.344531] hub 5-0:1.0: USB hub found
[    5.448679] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 6
[    5.448703] ehci_hcd 0000:00:13.5: applying AMD SB600/SB700 USB freeze workaround
[    5.460013] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    5.460084] usb usb6: configuration #1 chosen from 1 choice
[    5.460105] hub 6-0:1.0: USB hub found
[    5.616022] usb 2-1: USB disconnect, address 2
[    6.224532] usb 2-1: new full speed USB device using ohci_hcd and address 3
[    6.391154] usb 2-1: configuration #1 chosen from 1 choice
[    6.393095] hub 2-1:1.0: USB hub found
[    6.888022] usb 2-2: new low speed USB device using ohci_hcd and address 4
[    7.064159] usb 2-2: configuration #1 chosen from 1 choice
[    7.142057] usb 2-1.1: new full speed USB device using ohci_hcd and address 5
[    7.257210] usb 2-1.1: configuration #1 chosen from 1 choice
[    7.338054] usb 2-1.3: new full speed USB device using ohci_hcd and address 6
[    7.444157] usb 2-1.3: configuration #1 chosen from 1 choice
[   13.965646] usbcore: registered new interface driver hiddev
[   13.974319] input: HOLTEK Wireless Keyboard/Mouse(2.4G) as /devices/pci0000:00/0000:00:13.1/usb2/2-2/2-2:1.0/input/input3
[   14.000630] input,hidraw0: USB HID v1.10 Keyboard [HOLTEK Wireless Keyboard/Mouse(2.4G)] on usb-0000:00:13.1-2
[   14.010472] input: HOLTEK Wireless Keyboard/Mouse(2.4G) as /devices/pci0000:00/0000:00:13.1/usb2/2-2/2-2:1.1/input/input4
[   14.064666] input,hidraw1: USB HID v1.10 Mouse [HOLTEK Wireless Keyboard/Mouse(2.4G)] on usb-0000:00:13.1-2
[   14.064688] usbcore: registered new interface driver usbhid
[   14.064700] usbhid: v2.6:USB HID core driver
[   14.169148] usbcore: registered new interface driver usbserial
[   14.169160] usbserial: USB Serial support registered for generic
[   14.169187] usbcore: registered new interface driver usbserial_generic
[   14.169189] usbserial: USB Serial Driver core
[   14.314273] usbserial: USB Serial support registered for FTDI USB Serial Device
[   14.890107] ftdi_sio 2-1.3:1.0: FTDI USB Serial Device converter detected
[   14.890330] usb 2-1.3: FTDI USB Serial Device converter now attached to ttyUSB0
[   14.890348] usbcore: registered new interface driver ftdi_sio
[   14.890351] ftdi_sio: v1.4.3:USB FTDI Serial Converters Driver
[   14.890363] usbcore: registered new interface driver lirc_mceusb
[   14.890366] lirc_mceusb: USB Microsoft IR Transceiver Driver v0.2
[  111.878514] type=1503 audit(1234467047.778:5): operation="inode_permission" requested_mask="w::" denied_mask="w::" fsuid=0 name="/dev/ttyUSB0" pid=6768 profile="/usr/sbin/cupsd"


I dont like the looks of the last line.

This is my hardware.conf

ariel@newmega:~$ more /etc/lirc/hardware.conf
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="None"
REMOTE_MODULES="lirc_dev lirc_mceusb2"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Custom"
TRANSMITTER_MODULES=""

TRANSMITTER_DEVICE="/dev/lirc0"

TRANSMITTER_LIRCD_ARGS="-d /dev/ttyUSB0"
#Try to load appropriate kernel modules
LOAD_MODULES="false"
TRANSMITTER_DRIVER="uirt2_raw"
TRANSMITTER_LIRCD_CONF="/usr/share/lirc/transmitters"
START_LIRCD="true"
START_LIRCMD=""
LIRCMD_CONF=""
FORCE_NONINTERACTIVE_RECONFIGURATION="true"

I start LIRCD:
ariel@newmega:~$ sudo /etc/init.d/lirc start
 * Starting remote control daemon(s) : LIRC                                         [ OK ] 


this is my lircd.conf:

#Configuration for the Windows Media Center Remotes (new version Philips et al.) remote:
include /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb

#Configuration for the None transmitter:
include /usr/share/lirc/transmitters/pioneer/general.conf


my general.conf:

begin remote

  name  TWC_UR4-P360
  bits           22
  flags SPACE_ENC|CONST_LENGTH
  eps            30
  aeps          100

  header       3337  3378
  one           820  2540
  zero          820   817
  ptrail        820
  gap          100786
  toggle_bit      0

  frequency    56000

      begin codes
          POWER                    0x37C107
          GUIDE                    0x36C127
          MENU                     0x36F920
          INFO                     0x36213B
          UP                       0x36812F
          DOWN                     0x37A10B
          LEFT                     0x37810F
          RIGHT                    0x364137
          SELECT                   0x366133
          PAGEUP                   0x36D924
          PAGEDOWN                 0x37D904
          HELP                     0x376912
          SETTINGS                 0x373918
          EXIT                     0x366932
          A                        0x37E902
          B                        0x36193C
          C                        0x37191C
          LAST                     0x36E123
          FAV                      0x37F101
          DAYMINUS                 0x0E163D
          DAYPLUS                  0x0FE603
          CHUP                     0x377111
          CHDOWN                   0x36F121
          1                        0x36113D
          2                        0x37111D
          3                        0x36912D
          4                        0x37910D
          5                        0x365135
          6                        0x375115
          7                        0x36D125
          8                        0x37D105
          9                        0x363139
          0                        0x373119
          ENTER                    0x363139
          REW                      0x37291A
          PLAY                     0x37990C
          FF                       0x36293A
          REC                      0x375914
          STOP                     0x365934
          PAUSE                    0x374117
      end codes

end remote


then i try too use irsend:

ariel@newmega:~$ irsend SEND_ONCE TWC_UR4-P360 1
irsend: command failed: SEND_ONCE TWC_UR4-P360 1
irsend: hardware does not support sending


What gives? Anyone?

Thanks in advance!!

Ariel

---

### Post by chayzer on 2009-02-15
I've got a similar problem here. Only info I could find was that something got broke in kernel 2.6.22 and up with the ftdi_sio driver (serial driver I believe). Maybe one could get the old source and compile a new driver through dkms or something?

Haven't got around to messing with it yet.. I guess the first step would be to go back to a pre 2.6.22 kernel and verify it works.

---

### Post by chayzer on 2009-02-15
Well I was actually getting the the checksum problems when trying to record using 8.10 with kernel 2.6.27-11. Rolling back to kernel 2.6.25-whatever is in the repos, allowed me to record my remote functions and I when I booted back into my 27 kernel, i can use irsend to turn my motorola box on and off, although I have to repeat the command twice with the -# 2 option.. am still getting checksum errors, but they don't seem to be fatal.

at least I don't have to throw my usb-uirt into a drawer to be forgotten and die.... yet.

---

### Post by chayzer on 2009-02-15
And Ariel, here's my transmitter section from my hardware.conf file.

Your hardware.conf file is set up to try and send through your mceusb dongle. Your usb-uirt device is usually found at /dev/ttyUSB0

```

#Chosen IR Transmitter
TRANSMITTER="USB-UIRT2 : Motorola Cable box"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER="uirt2_raw"
TRANSMITTER_DEVICE="/dev/ttyUSB0"
TRANSMITTER_LIRCD_CONF="motorola/dctxxxx.conf"
TRANSMITTER_LIRCD_ARGS=""

```

Might just be a matter of changing the TRANSMITTER_LIRCD_CONF="motorola/dctxxxx.conf" to TRANSMITTER_LIRCD_CONF="pioneer/general.conf".

---

### Post by wombatU42 on 2009-03-03
Well,  I"m glad to hear that I'm not the only one with this problem.

I managed to solve it!!!

My Setup started to work when I changed the frequency of the transmitter in the .conf file.  If I remember correctly I changed the 'frequency' value to 40000 and it started to work.  I just used the standard .conf file from lirc.org.

Hope this helps.

---

### Post by arishu on 2009-10-02
Hello,

I'm back with another question...

I have Ubuntu 9.04, MCEUSB IR receiver and USB-UIRT IR blaster.

USB-UIRT works perfectly (finally!!) when the MCEUSB is not plugged in, but doesn't work when the IR Receiver is plugged in.

I did my best to read, I feel I am very close, but the darn thing still doesn't work well – they don't play nice with each other!

I see I have two lirc instances running, which should be good...

ariel@newmega-linux:/var/run$ ps ax | grep lirc 
 4386 ?        S<     0:00 [lirc_dev] 
 5432 ?        Ss     0:00 /usr/sbin/lircd --device=/dev/lirc0 --output=/dev/lircd --listen 
 5437 ?        Ss     0:00 /usr/sbin/lircd --driver=uirt2_raw --device=/dev/ttyUSB0 --output=/dev/lircd1 --connect=localhost 8765 --pidfile=/var/run/lircd1.pid 
 5873 pts/1    R+     0:00 grep lirc 





My hardware.conf file

ariel@newmega-linux:/var/run$ more /etc/lirc/hardware.conf 
# /etc/lirc/hardware.conf 
# 
#Chosen Remote Control 
REMOTE="Windows Media Center Remotes (old version MicroSoft USB ID)" 
REMOTE_MODULES="lirc_dev lirc_mceusb" 
REMOTE_DRIVER="" 
REMOTE_DEVICE="/dev/lirc0" 
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb" 
REMOTE_LIRCD_ARGS="" 

#Chosen IR Transmitter 
TRANSMITTER="USB-UIRT2 : Motorola Cable box" 
TRANSMITTER_MODULES="" 
TRANSMITTER_DRIVER="uirt2_raw" 
TRANSMITTER_DEVICE="/dev/ttyUSB0" 
TRANSMITTER_LIRCD_CONF="motorola/dctxxxx.conf" 
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



my lircd.conf file

ariel@newmega-linux:/var/run$ more /etc/lirc/lircd.conf 
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

#Configuration for the Windows Media Center Remotes (old version MicroSoft USB ID) remote: 
include "/usr/share/lirc/remotes/mceusb/lircd.conf.mceusb" 

#Configuration for the USB-UIRT2 : Motorola Cable box transmitter: 
include "/usr/share/lirc/transmitters/motorola/dctxxxx.conf" 
ariel@newmega-linux:/var/run$ 



Note!!!: ignore the motorola part – I changed the contents of dctxxxx.conf to reflect my sattellite remote. 


include "/usr/share/lirc/transmitters/motorola/dctxxxx.conf" 
ariel@newmega-linux:/var/run$ 
ariel@newmega-linux:/var/run$ more /usr/share/lirc/transmitters/motorola/dctxxxx.conf 
# 
# this config file was automatically generated 
# using lirc-0.6.6(serial) on Fri Mar 28 22:46:44 2003 
# 
# contributed by shane bradley 
# 
# 
# 
# brand:                       Motorola 
# model no. of remote control: DCT2000 
# devices being controlled by this remote: 
# 
                                                                                    
begin remote 

name YES 

bits 16 
flags SPACE_ENC|CONST_LENGTH 
eps 30 
aeps 100 
header 9042 4558 
one 555 1682 
zero 555 570 
ptrail 544 
repeat 9041 2296 
pre_data_bits 16 
pre_data 0x213C 
gap 108556 
min_repeat 1 
toggle_bit 0 
begin codes 

power 0x000000000000847B 
1 0x0000000000000CF3 
2 0x000000000000946B 
.
. (deleted to make the post shorter...) 
i 0x00000000000002FD 
end codes 

end remote 






when both are plugged in, MCE remote seems to work fine...

ariel@newmega-linux:/var/run$ irw 
000000037ff07bdc 00 Back mceusb 
000000037ff07bdd 00 OK mceusb 
000000037ff07be1 00 Up mceusb 
000000037ff07be1 01 Up mceusb 
000000037ff07bde 00 Right mceusb 

but IR sending fails – I am trying different commands, I must be doing something wrong with the syntax...

ariel@newmega-linux:/var/run$ sudo irsend LIST "" "" 
[sudo] password for ariel: 
irsend: YES 
irsend: mceusb 
ariel@newmega-linux:/var/run$ 

ariel@newmega-linux:/var/run$ sudo irsend LIST YES "" 
irsend: 000000000000847b power 
irsend: 0000000000000cf3 1 
irsend: 000000000000946b 2 
irsend: 0000000000009c63 3 
.
. (deleted to make the post shorter) 
irsend: 00000000000042bd B 
irsend: 000000000000827d A 
irsend: 00000000000002fd i 
ariel@newmega-linux:/var/run$ 



ariel@newmega-linux:/var/run$ sudo irsend --address=localhost:8765 SEND_ONCE YES 2 
irsend: command failed: SEND_ONCE YES 2 
irsend: hardware does not support sending 

ariel@newmega-linux:/var/run$ sudo irsend -d /dev/ttyUSB0 --address=localhost:8765 SEND_ONCE YES 1 
irsend: command failed: SEND_ONCE YES 1 
irsend: hardware does not support sending 



In fact any kind of irsend I tried didn't work.

 The fact the keyboard is the only way to control Myth is pushing the WAF to zero:) Any ideas?

---

### Post by arishu on 2009-10-03
well what do you know... 

irsend --device=/dev/lircd1 for the USB-UIRT fixed it! :)

hope this helps someone else...

---

### Post by santhony on 2009-12-29
ARISHA ..

Can I see your hardware.conf and lircd.conf ?

I'm trying to get my usb-uirt to work.. according to yours...

Thanks

---

