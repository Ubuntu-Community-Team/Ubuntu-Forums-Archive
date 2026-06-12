---
title: "Y0400052 remote with eyetv dtt stick"
date: 2011-06-06
forum: Multimedia Software
---

### Post by krusty8 on 2011-06-06
im trying to use a Y0400052 remote control from my leadtek winfast analog tv receiver pci card with a elgato eyetv dtt dvb-t usb stick. i know theres plenty of 'how do i get my infrared remote controller working' infos out there but im kind of lost. feel free to direct me to an appropriate place. part of my confusion is that im both lost on a very general level AND on a very specific level.

back in the days when i had a desktop and was using the leadtek pci card the remote was working ok via lirc. now it seems that there is this new way of handling remotes via devinput and 'events' so im unclear - do i need lirc anymore?

on a very specific level i try the following

pluggin in the stick yields 

```
$ dmesg
Jun  5 20:18:27 xenon kernel: [ 1012.145923] IR NEC protocol handler initialized
Jun  5 20:18:27 xenon kernel: [ 1012.156562] IR RC5(x) protocol handler initialized
Jun  5 20:18:27 xenon kernel: [ 1012.170871] IR RC6 protocol handler initialized
Jun  5 20:18:27 xenon kernel: [ 1012.178489] IR JVC protocol handler initialized
Jun  5 20:18:27 xenon kernel: [ 1012.192222] IR Sony protocol handler initialized
Jun  5 20:18:27 xenon kernel: [ 1012.197335] lirc_dev: IR Remote Control driver registered, major 251 
Jun  5 20:18:27 xenon kernel: [ 1012.198688] IR LIRC bridge handler initialized
Jun  5 20:18:28 xenon kernel: [ 1012.227662] dib0700: loaded with support for 15 different device-types
Jun  5 20:18:28 xenon kernel: [ 1012.280409] dvb-usb: found a 'Elgato EyeTV DTT' in cold state, will try to load a firmware
Jun  5 20:18:28 xenon kernel: [ 1012.295223] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
Jun  5 20:18:28 xenon kernel: [ 1012.499129] dib0700: firmware started successfully.
Jun  5 20:18:28 xenon kernel: [ 1013.000469] dvb-usb: found a 'Elgato EyeTV DTT' in warm state.
Jun  5 20:18:28 xenon kernel: [ 1013.000637] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
Jun  5 20:18:28 xenon kernel: [ 1013.000816] DVB: registering new adapter (Elgato EyeTV DTT)
Jun  5 20:18:29 xenon kernel: [ 1013.253104] DVB: registering adapter 0 frontend 0 (DiBcom 7000PC)...
Jun  5 20:18:29 xenon kernel: [ 1013.488232] DiB0070: successfully identified
Jun  5 20:18:29 xenon kernel: [ 1013.520250] Registered IR keymap rc-dib0700-rc5
Jun  5 20:18:29 xenon kernel: [ 1013.520596] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1d.7/usb2/2-2/rc/rc0/input12
Jun  5 20:18:29 xenon kernel: [ 1013.520793] rc0: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1d.7/usb2/2-2/rc/rc0
Jun  5 20:18:29 xenon kernel: [ 1013.521031] dvb-usb: schedule remote query interval to 50 msecs.
Jun  5 20:18:29 xenon kernel: [ 1013.521043] dvb-usb: Elgato EyeTV DTT successfully initialized and connected.
Jun  5 20:18:29 xenon kernel: [ 1013.523099] usbcore: registered new interface driver dvb_usb_dib0700

```now i can watch tv with kaffeine, and there seems to be an ir-receiver at input12

EDIT: after unplugging and replugging it became input13

```
$ ls /sys/class/rc/rc1/input13/
capabilities  device  event12  id  modalias  name  phys  power  properties  subsystem  uevent  uniq

```indicates that input13 has something to do with event12, now

```
$ evtest /dev/input/event12 
Input driver version is 1.0.1
Input device ID: bus 0x3 vendor 0xfd9 product 0x21 version 0x100
Input device name: "IR-receiver inside an USB DVB receiver"
Supported events:
  Event type 0 (Sync)
  Event type 1 (Key)
    Event code 2 (1)
    Event code 3 (2)
    Event code 4 (3)
    Event code 5 (4)
    Event code 6 (5)
    Event code 7 (6)
    Event code 8 (7)
    Event code 9 (8)
    Event code 10 (9)
    Event code 11 (0)
    Event code 41 (Grave)
    Event code 52 (Dot)
    Event code 55 (KPAsterisk)
    Event code 102 (Home)
    Event code 103 (Up)
    Event code 105 (Left)
    Event code 106 (Right)
    Event code 108 (Down)
    Event code 111 (Delete)
    Event code 113 (Mute)
    Event code 114 (VolumeDown)
    Event code 115 (VolumeUp)
    Event code 116 (Power)
    Event code 119 (Pause)
    Event code 128 (Stop)
    Event code 139 (Menu)
    Event code 158 (Back)
    Event code 164 (PlayPause)
    Event code 167 (Record)
    Event code 168 (Rewind)
    Event code 173 (Refresh)
    Event code 207 (Play)
    Event code 208 (Fast Forward)
    Event code 210 (Print)
    Event code 223 (Cancel)
    Event code 226 (Media)
    Event code 352 (Ok)
    Event code 354 (Goto)
    Event code 355 (Clear)
    Event code 358 (Info)
    Event code 363 (Channel)
    Event code 365 (EPG)
    Event code 370 (Subtitle)
    Event code 375 (Screen)
    Event code 377 (TV)
    Event code 385 (Radio)
    Event code 386 (Tuner)
    Event code 388 (Text)
    Event code 389 (DVD)
    Event code 392 (Audio)
    Event code 393 (Video)
    Event code 398 (Red)
    Event code 399 (Green)
    Event code 400 (Yellow)
    Event code 401 (Blue)
    Event code 402 (ChannelUp)
    Event code 403 (ChannelDown)
    Event code 405 (Last)
    Event code 407 (Next)
    Event code 410 (Shuffle)
    Event code 412 (Previous)
  Event type 4 (Misc)
    Event code 4 (ScanCode)
  Event type 20 (Repeat)
Testing ... (interrupt to exit)

```now with a little patience and a lot of pressing buttons on the remote i get _sometimes_ a response like this from evtest 

```
Event: time 1307298574.042934, type 4 (Misc), code 4 (ScanCode), value 151f
Event: time 1307298582.652191, type 4 (Misc), code 4 (ScanCode), value 1f3d
Event: time 1307298584.378077, type 4 (Misc), code 4 (ScanCode), value 1511
Event: time 1307298586.747068, type 4 (Misc), code 4 (ScanCode), value 1f3d
Event: time 1307298600.854554, type 4 (Misc), code 4 (ScanCode), value 1f3d

```so _some_ commuication between the remote control and the computer is established. but a) it doesnt really print one line per butten and b) i dont know what to do next.

i use ubuntu 11.04 and
```
$ uname -a
Linux xenon 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

```any help would be appreciated.

---

### Post by krusty8 on 2011-07-24
ok, i think i almost got it. i uninstalled lirc and  this finally pointed me in the right direction:
[http://sourceforge.net/mailarchive/message.php?msg_id=27453752](http://sourceforge.net/mailarchive/message.php?msg_id=27453752)

firstly, trying different settings with the **ir-keytable -p** until **ir-keytable -t** reliably produced _one_ scancode per each button i pressed on the remote. this worked best for me with : **ir-keytable -pNEC** . next i wanted to try different **ir-keytable -c -w <keytable>** and after searching for a while i found that the remote control keytables are at **/lib/udev/rc_keymaps/** on my system. i ended up taking the **leadtek_y04g0051** file as a starting point to write a suitable keymaps file for my remote.

i still have to find how to automagically load this keymap but for the moment im happy that i finally got kaffeine to react to the most important buttons.

---

