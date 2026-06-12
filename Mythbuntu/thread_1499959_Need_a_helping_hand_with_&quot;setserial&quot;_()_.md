---
title: "Need a helping hand with &quot;setserial&quot; (?) home brew IR blaster"
date: 2010-06-02
forum: Mythbuntu
---

### Post by ryry46d9 on 2010-06-02
Ubuntu 10.04 x64 Desktop 
```
uname -a
```
> Linux set-top 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux

mythTV 0.23.0+fixes24158-0ubuntu2

Lirc 0.8.6-0ubuntu4.1

A SIIG.inc JJ-P20212 (ver.2) (since my Abit IP35-E has no serial)

home brew serial IR blaster 

Motorola DCT2244

I'm kind of lost + stuck. Under win XP MCE I was able to use winlirc to blast a channel to my cable box. but under Mythbuntu and Ubuntu I am not able to. I have read so many different how-to and none have worked so far.

here is some random answers. In hope, some one can tell me what I'm doing wrong.

```
sudo lshw
``` reports my serial devices in two places:

> *-communication
                description: Serial controller
                product: CyberSerial (2-port) 16650
                vendor: Siig Inc
                physical id: 5
                bus info: pci@0000:05:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: driver=serial latency=0
                resources: irq:23 ioport:cf00(size=8) ioport:ce00(size=8)

> *-serial UNCLAIMED
             description: SMBus
             product: 82801I (ICH9 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fdffd000-fdffd0ff ioport:500(size=32)
BIOS ghost code?

```
dmesg | grep ttyS
```
> [    0.778080] 0000:05:03.0: ttyS0 at I/O 0xcf00 (irq = 21) is a ST16650V2
[    0.798435] 0000:05:03.0: ttyS1 at I/O 0xce00 (irq = 21) is a ST16650V2

IRQ:21? I did a ```
sudo setserial /dev/ttyS0 uart 16550A port 0x03f8 irq 4 baud_base 115200
``` but apond reboot it defaulted back to 21

```
setserial -G /dev/ttyS0
```
> /dev/ttyS0 uart unknown port 0xcf00 irq 21 baud_base 921600 spd_normal

```
irsend -d /dev/lircd SEND_ONCE DCT2000 2
```
> irsend: timeout

/etc/lirc/hardware.conf :
> #Chosen Remote Control
REMOTE="Home-brew (16x50 UART compatible serial port)"
REMOTE_MODULES="lirc_dev lirc_serial"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Command IR : Motorola Cable box"
TRANSMITTER_MODULES="lirc_dev lirc_cmdir"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc1"
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
REMOTE_SOCKET=""
TRANSMITTER_SOCKET=""


/etc/lirc/lircd.conf :
> include "/usr/share/lirc/extras/transmitters/motorola/dctxxxx.conf"

```
dmesg | grep -i lirc
```
> [   24.069367] lirc_dev: IR Remote Control driver registered, major 61 
[   25.041294] lirc_serial: auto-detected active low receiver
[   25.041297] lirc_dev: lirc_register_driver: sample_rate: 0
[   25.041383] lirc_serial $Revision: 5.104 $ registered


```
ls -l /dev/lirc*
```
> crw-rw---- 1 root root 61, 0 2010-06-01 04:34 /dev/lirc0
srw-rw-rw- 1 root root     0 2010-06-01 04:34 /dev/lircd
lrwxrwxrwx 1 root root    20 2010-06-01 04:34 /dev/lircd1 -> /var/run/lirc/lircd1


```
irsend LIST DCT2000 ""
```
> irsend: 000000000000b3f2 HELP
irsend: 000000000000aff9 POWER
irsend: 0000000000000ff7 MUTE
irsend: 000000000000a3f3 PAGE+
irsend: 00000000000023fb PAGE-
irsend: 00000000000097f6 LOCK
irsend: 000000000000b7f4 EXIT
irsend: 000000000000d3f6 AUP
irsend: 00000000000053fe ADOWN
irsend: 00000000000093f1 ALEFT
irsend: 00000000000013f9 ARIGHT
irsend: 00000000000077f8 OK
irsend: 000000000000f3f4 GUIDE
irsend: 00000000000067f9 MENU
irsend: 0000000000004ff3 VOL+
irsend: 0000000000008ffb VOL-
irsend: 00000000000037fc LAST
irsend: 00000000000057fa FAV
irsend: 0000000000002ff5 CH+
irsend: 000000000000cffd CH-
irsend: 00000000000017fe A
irsend: 0000000000001bf1 B
irsend: 000000000000ebf9 C
irsend: 0000000000007ff0 1
irsend: 000000000000bff8 2
irsend: 0000000000003ff4 3
irsend: 000000000000dffc 4
irsend: 0000000000005ff2 5
irsend: 0000000000009ffa 6
irsend: 0000000000001ff6 7
irsend: 000000000000effe 8
irsend: 0000000000006ff1 9
irsend: 000000000000ffff 0
irsend: 000000000000d7f2 BYPASS
irsend: 000000000000f7f0 MUSIC
irsend: 00000000000063fd STOP
irsend: 00000000000007ff PAUSE
irsend: 000000000000e3f5 PLAY
irsend: 00000000000087f7 REW
irsend: 00000000000073fc REC
irsend: 00000000000047fb FFWD


I'm sure there is more I have done, this is just what I'm remembering from the top of my head to get ya started.
thank you

---

### Post by ian dobson on 2010-06-02
Hi,

Hi,

Have a look here [http://www.mythbuntu.org/documentati...stallation.pdf](http://www.mythbuntu.org/documentati...stallation.pdf) chapter 12, you need to copy the configuration file generated by setserial to /etc

sudo cp /var/lib/setserial/autoserial.conf /etc/serial.conf

I'm not sure if it'll help but maybe. Your serial port is a USB to serial?

Regards
Ian Dobson

---

### Post by ryry46d9 on 2010-06-02
serial and that link is dead :(

I build this [http://www.lirc.org/transmitters.html](http://www.lirc.org/transmitters.html) and was tested under windows with the same gear the only thing that changes was the OS

---

### Post by ian dobson on 2010-06-02
Hi,

OK here's the link [http://www.mythbuntu.org/documentation/mythbuntu_8.04_installation.pdf](http://www.mythbuntu.org/documentation/mythbuntu_8.04_installation.pdf)

Regards
Ian Dobson

---

### Post by azmyth on 2010-06-03
You need to set your serial port to "none" not to 16550A. The best way to do this is by

sudo dpkg-reconfigure setserial

This way if you do any upgrades you won't lose the none setting.

---

### Post by ryry46d9 on 2010-06-04
@ ian dobson: I did as they said and still no blasting

@ azmyth: sudo dpkg-reconfigure setserial only give me this screen shot then exits 
[IMG]http://ryry.mine.nu/printscreen/setserial.png[/IMG]

with this error after exit:
> dpkg: warning: obsolete option '--print-installation-architecture', please use '--print-architecture' instead.
dpkg: warning: obsolete option '--print-installation-architecture', please use '--print-architecture' instead.


also on reboot it goes back to :
> /dev/ttyS0 uart unknown port 0xcf00 irq 21 baud_base 921600 spd_normal

---

### Post by azmyth on 2010-06-06
From looking at your image, you should've chosen the top choice. If that doesn't work, just edit or create the serial.conf in the etc directory and you'll need to add

/dev/ttyS0 uart none

then reboot then check 

setserial -g /dev/ttyS*

and it should say unknown for ttyS0. If it says anything else, something went wrong.

If you do it manually, you'll have to make a backup and remember that if you do an upgrade you could lose the serial.conf file.

---

### Post by ryry46d9 on 2010-06-10
The sad part is this card works under windows XP + winlirc. I just tested it to make sure the IRled was still good. 

so how do I mark this as solved? I forget. 

I have another box that has on-board serial + Ubuntu and the blaster worked fine, just hope its fast enough (dual 1.0Ghz P3's 2GB ram). No digital

pci card box:
> ryry@set-top:~$ dmesg | grep ttyS0
[    0.768347] 0000:05:03.0: ttyS0 at I/O 0xcf00 (irq = 21) is a ST16650V2

on-board box:
> ryry@chat:~$ dmesg | grep ttyS0
[    1.216662] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.217607] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

what ever "ST16650V2" mean, its bad news for me ;)

---

### Post by dnilsson on 2010-06-10
Hi,

I have the same homebrew hardware working fine with Ubuntu 10.04, not sure if you were able to solve this or not?

What seems strange to me in your config is that the device you are using as a transmitter is actually using the lirc_cmdir driver. The lirc_serial driver used for the homebrew transmitter seems to be defined as an IR receiver in your config. Maybe I'm missing something though...? This is what my hardware.conf file looks like (I only have a transmitter on this box though)

```
cat /etc/lirc/hardware.conf

```> 
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
TRANSMITTER="Serial Port (UART) : VIP1500"
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

```
cat /etc/serial.conf
```> /dev/ttyS0 uart nonelircd.conf is however custom in my case since the STB is not following any known IR standard. Lots of work to get this file working...

```
cat /etc/lirc/lircd.conf
```> # Motorola (former Kreatel) VIP-1500 IPTV STB

begin remote

  name vip1500_remote
  bits           24
  flags RC6|CONST_LENGTH
  eps            30
  aeps          100

  header       2568   1250
  one           323   323
  zero          323   323
  pre_data_bits 9
  pre_data      0x01EF
  gap           74200
  toggle_bit    0
  rc6_mask      0x100000000
  frequency     56000


      begin codes
       Zero_down  0xFFE2F0
       Zero_up    0x7FE2F8
        One_down  0xFFA6F0
        One_up    0x7FA6F8
        Two_down  0xFF96FF
        Two_up    0x7F96F7
      Three_down  0xFF86FE
      Three_up    0x7F86F6
       Four_down  0xFFE3F1
       Four_up    0x7FE3F9
       Five_down  0xFFD3F0
       Five_up    0x7FD3F8
        Six_down  0xFFC3FF
        Six_up    0x7FC3F7
      Seven_down  0xFFB3FE
      Seven_up    0x7FB3F6
      Eight_down  0xFFA3FD
      Eight_up    0x7FA3F5
       Nine_down  0xFF93FC
       Nine_up    0x7F93F4
         OK_down  0xFFF0FF
         OK_up    0x7FF0F7
      end codes

end remote


---

### Post by ryry46d9 on 2010-06-11
Ok that makes more sense. 

but, it was just that serial card not liking Ubuntu 
So I'm doing a ```
sudo do-release-upgrade
``` on the other box right now. 

I ran the same setup on this other box and got irsend -d /dev/lircd SEND_ONCE DCT2000 2 , irsend -d /dev/lircd SEND_ONCE DCT2000 poweroff to do what they where told. I think I had to change it to ```
TRANSMITTER_MODULES="lirc_dev lirc_serial"
``` like you said and I changed the dctxxxx.conf file to whats inside the DCT2224. although I have a dct2244 

on a side rant:
1) serial is suppose to be serial, who went and changed the rules?
2) if I can record a show while watching it on my Xbox306 and the desktop recording it under "media center" using a ATI A-I-W 2006 edition all that the same time. why does myth(?) lock /dev/video0 & why does ATI not give me a driver.
3) why does each new version requirer a DB upgrade that isnt backwards compatibly. my tvtunner is still video0, my recored tv is still in /mythtv (WTF) 

No need to reply as there just rants (I know the answers). and this is what I get for being lazy and relying on .deb files, instead of building from source ):P

---

