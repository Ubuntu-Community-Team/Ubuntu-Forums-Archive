---
title: "new MCE IR rcvr, works in ir-keytable, not in LIRC irw or FE"
date: 2014-02-12
forum: Mythbuntu
---

### Post by Dave_Alverson on 2014-02-12
I am running mythtv 0.27 on mythbuntu 12.04.  I have been using IR on a PVR150 for years (most recently with ir-kbd-i2c and devinput)  but am switching to an MCE IR receiver (Rosewill RHRC-11002). The remote presses show up fine in ir-keytable but not in LIRC.  Something in the path from kernel to lirc to myth is not working.




with lirc stopped, here is ir-keytable:
```
root@dvr:~# ir-keytable
Found /sys/class/rc/rc0/ (/dev/input/event3) with:
    Driver mceusb, table rc-rc6-mce
    Supported protocols: NEC RC-5 RC-6 JVC SONY LIRC other 
    Enabled protocols: NEC RC-5 RC-6 JVC SONY LIRC other 
    Repeat delay = 500 ms, repeat period = 125 ms

```
and here running test mode and pressing OK and EXIT
```
root@dvr:~# ir-keytable -t
Testing events. Please, press CTRL-C to abort.
1392257404.500113: event MSC: scancode = 800f0422
1392257404.500116: event key down: KEY_OK (0x0160)
1392257404.500117: event sync
1392257404.606106: event MSC: scancode = 800f0422
1392257404.606108: event sync
1392257404.857691: event key up: KEY_OK (0x0160)
1392257404.857693: event sync
1392257412.864740: event MSC: scancode = 800f0423
1392257412.864745: event key down: KEY_EXIT (0x00ae)
1392257412.864746: event sync
1392257412.970668: event MSC: scancode = 800f0423
1392257412.970669: event sync
1392257413.221694: event key up: KEY_EXIT (0x00ae)
1392257413.221695: event sync

```

here are the relevent entries in /proc/bus/input/devices (I think the second one is also for this device)
```
I: Bus=0003 Vendor=147a Product=e03e Version=1201
N: Name="Media Center Ed. eHome Infrared Remote Transceiver (147a:e03e)"
P: Phys=usb-0000:00:12.0-2
S: Sysfs=/devices/pci0000:00/0000:00:12.0/usb3/3-2/3-2:1.0/rc/rc0/input3
U: Uniq=
H: Handlers=kbd event3 
B: PROP=0
B: EV=100013
B: KEY=fff 0 200108fc32e 237605100000000 0 700158000 419200004001 8e968000000000 10000000
B: MSC=10


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="MCE IR Keyboard/Mouse (mceusb)"
P: Phys=/input0
S: Sysfs=/devices/virtual/input/input4
U: Uniq=
H: Handlers=sysrq kbd mouse1 event4 
B: PROP=0
B: EV=100017
B: KEY=30000 7 ff87207ac14057ff febeffdfffefffff fffffffffffffffe
B: REL=3
B: MSC=10

```here is my udev rule and the dev files: /etc/udev/rules.d/10-local.rules 
SUBSYSTEM=="input",ATTRS{name}=="Media Center*",SYMLINK="input/irmce"


/dev/input# ls -l
```
crw-r----- 1 root root 13, 67 Feb 10 21:04 event3
...
lrwxrwxrwx 1 root root      6 Feb 10 21:04 irmce -> event3

```



root@dvr:/dev/input# lsmod |grep 'ir\|rc'
```
ir_lirc_codec          12859  0 
lirc_dev               19204  1 ir_lirc_codec
ir_mce_kbd_decoder     12777  0 
ir_sony_decoder        12510  0 
ir_jvc_decoder         12507  0 
ir_rc6_decoder         12507  0 
rc_rc6_mce             12502  0 
ir_rc5_decoder         12507  0 
ir_nec_decoder         12507  0 
rc_core                26412  10 ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,rc_rc6_mce,ir_rc5_decoder,ir_nec_decoder,mceusb

```
Here is evtest, again pressing OK and EXIT
```
root@dvr:/dev/input# evtest /dev/input/irmce 
Input driver version is 1.0.1
Input device ID: bus 0x3 vendor 0x147a product 0xe03e version 0x1201
Input device name: "Media Center Ed. eHome Infrared Remote Transceiver (147a:e03e)"
Supported events:
  Event type 0 (EV_SYN)
  Event type 1 (EV_KEY)
    Event code 28 (KEY_ENTER)
    Event code 103 (KEY_UP)
    Event code 105 (KEY_LEFT)
    Event code 106 (KEY_RIGHT)
    Event code 108 (KEY_DOWN)
    Event code 111 (KEY_DELETE)
    Event code 113 (KEY_MUTE)
    Event code 114 (KEY_VOLUMEDOWN)
    Event code 115 (KEY_VOLUMEUP)
    Event code 119 (KEY_PAUSE)
    Event code 128 (KEY_STOP)
    Event code 142 (KEY_SLEEP)
    Event code 161 (KEY_EJECTCD)
    Event code 164 (KEY_PLAYPAUSE)
    Event code 167 (KEY_RECORD)
    Event code 168 (KEY_REWIND)
    Event code 174 (KEY_EXIT)
    Event code 207 (KEY_PLAY)
    Event code 208 (KEY_FASTFORWARD)
    Event code 210 (KEY_PRINT)
    Event code 212 (KEY_CAMERA)
    Event code 224 (KEY_BRIGHTNESSDOWN)
    Event code 225 (KEY_BRIGHTNESSUP)
    Event code 226 (KEY_MEDIA)
    Event code 352 (KEY_OK)
    Event code 356 (KEY_POWER2)
    Event code 358 (KEY_INFO)
    Event code 365 (KEY_EPG)
    Event code 366 (KEY_PVR)
    Event code 368 (KEY_LANGUAGE)
    Event code 369 (KEY_TITLE)
    Event code 370 (KEY_SUBTITLE)
    Event code 372 (KEY_ZOOM)
    Event code 373 (KEY_MODE)
    Event code 377 (KEY_TV)
    Event code 385 (KEY_RADIO)
    Event code 386 (KEY_TUNER)
    Event code 387 (KEY_PLAYER)
    Event code 389 (KEY_DVD)
    Event code 392 (KEY_AUDIO)
    Event code 393 (KEY_VIDEO)
    Event code 398 (KEY_RED)
    Event code 399 (KEY_GREEN)
    Event code 400 (KEY_YELLOW)
    Event code 401 (KEY_BLUE)
    Event code 402 (KEY_CHANNELUP)
    Event code 403 (KEY_CHANNELDOWN)
    Event code 407 (KEY_NEXT)
    Event code 412 (KEY_PREVIOUS)
    Event code 425 (KEY_PRESENTATION)
    Event code 512 (KEY_NUMERIC_0)
    Event code 513 (KEY_NUMERIC_1)
    Event code 514 (KEY_NUMERIC_2)
    Event code 515 (KEY_NUMERIC_3)
    Event code 516 (KEY_NUMERIC_4)
    Event code 517 (KEY_NUMERIC_5)
    Event code 518 (KEY_NUMERIC_6)
    Event code 519 (KEY_NUMERIC_7)
    Event code 520 (KEY_NUMERIC_8)
    Event code 521 (KEY_NUMERIC_9)
    Event code 522 (KEY_NUMERIC_STAR)
    Event code 523 (KEY_NUMERIC_POUND)
  Event type 4 (EV_MSC)
    Event code 4 (MSC_SCAN)
  Event type 20 (EV_REP)
Testing ... (interrupt to exit)
Event: time 1392257762.500229, type 4 (EV_MSC), code 4 (MSC_SCAN), value 800f0422
Event: time 1392257762.500232, type 1 (EV_KEY), code 352 (KEY_OK), value 1
Event: time 1392257762.500234, -------------- SYN_REPORT ------------
Event: time 1392257762.607225, type 4 (EV_MSC), code 4 (MSC_SCAN), value 800f0422
Event: time 1392257762.607227, -------------- SYN_REPORT ------------
Event: time 1392257762.857696, type 1 (EV_KEY), code 352 (KEY_OK), value 0
Event: time 1392257762.857697, -------------- SYN_REPORT ------------
Event: time 1392257765.982074, type 4 (EV_MSC), code 4 (MSC_SCAN), value 800f0423
Event: time 1392257765.982078, type 1 (EV_KEY), code 174 (KEY_EXIT), value 1
Event: time 1392257765.982080, -------------- SYN_REPORT ------------
Event: time 1392257766.089069, type 4 (EV_MSC), code 4 (MSC_SCAN), value 800f0423
Event: time 1392257766.089071, -------------- SYN_REPORT ------------
Event: time 1392257766.337693, type 1 (EV_KEY), code 174 (KEY_EXIT), value 0
Event: time 1392257766.337694, -------------- SYN_REPORT ------------

```
Here is my hardware.conf
```
root@dvr:/etc/lirc# more hardware.conf
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Linux input layer (/dev/input/eventX)"
REMOTE_MODULES="ir_rc6_decoder lirc_dev"
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/irmce"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="devinput/lircd.conf.devinput"
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



```But when I run irw, nothing happens when I press any buttons, and no button presses are seen in the FE. Could it be something in X eating the presses?  Or is is related to the device also having the event4 entry with kbd and mouse handlers?

---

### Post by alien878 on 2014-02-13
Since you are setting up a new remote and ir-keymap is already working, you might want to just skip lirc.  When I switched, I found that keypresss responses were much more accurate when lirc was taken out of the picture.

Disable lirc in the mythbuntu-control-center and a MCE remote should "just work".  Most of the mappings should be reasonable, but you can always tweek them with ir-keymap and/or the keymappings in mythtv setup.

---

### Post by Dave_Alverson on 2014-02-13
So if you do it that way, for example, would the keymap entry for the play button be changed to a 'P' which is what myth is expecting?

---

### Post by alien878 on 2014-02-13
Probably... in most cases, the default keymaps are reasonable out of the box (ex. Play is P).  MCE remotes are used a lot, so I expect the defaults are very good.  I have a lesser know remote and all the basic keys (play, record, pause, digits, up, down, menu, etc.) worked by default.  I had to remap some of the less obvious ones I wanted to use (ex. red, green, blue, etc.).

The easiest way to check is to use ir-keymap -t and see what happens.  If it gives something else, the easiest thing to do is add the key to the key mappings in mythtv setup.  Alternatively, you can modify the ir-keymap keymap, but that is a bit more work.

Actually, you can skip the ir-keymap check all together.  If a key doesn't work, go into mythtv setup and add the key to the key mapping for the function you want by pressing it on the remote.

---

### Post by Dave_Alverson on 2014-02-13
So I disabled lirc and some remote buttons now work in myth: the 4 arrow buttons and maybe the digits.  According to ir-keytable, Play sends KEY_PLAY which is 0xCF.  OK sends KEY_OK which is 0x160.  So I agree I could change the kernel keymap for the other buttons to send what Myth wants, but then its kinda hard coded to Myth.  Which isn't so bad because thats what I would be using 99% of the time.

But I did have lirc working with the kernel driver for the PVR-150, and it should be possible for lirc to do the same translations for my new remote.  Somehow I think the problem is related to mceusb also acting/appearing as a keyboard.

---

### Post by alien878 on 2014-02-14
Modifying the keymap is described here:

[http://atterer.org/mythtv-xmbc-remote-control-without-lirc](http://atterer.org/mythtv-xmbc-remote-control-without-lirc)

It might be easier to correct they keys in mythtv's frontend setup under "Edit Keys".  I.e. Make mythtv respond to KEY_PLAY and KEY_OK.  In the setup, use your remote when it asks which the key to use.  That way, you don't have to figure out how to enter KEY_PLAY.  Instead just press play.

FYI:  Generally, you cannot use a keymapping from one remote on a different one becaue they will use different scancodes.  I.e. Copying the translations from a PVR-150 remote onto a mceusb remote probably won't work.

---

### Post by Dave_Alverson on 2014-02-18
OK, I now have it working with lirc and devinput. I looked at /sys/class/rc/rc0/protocols before and after stopping lirc:

```
root@dvr:~# cat /sys/class/rc/rc0/protocols 
rc-5 nec rc-6 jvc sony mce_kbd [lirc]
root@dvr:~# service lirc stop
 * Stopping remote control daemon(s): LIRC                               [ OK ] 
root@dvr:~# cat /sys/class/rc/rc0/protocols 
[rc-5] [nec] [rc-6] [jvc] [sony] [mce_kbd] [lirc]

```

I noticed that only the lirc protocol was enabled before I stopped lirc. I know my remote uses RC-6 and that is what ir-keytable reports when I test with ir-keytable and it works. Then I manually started lircd in non-daemon mode:
```
root@dvr:/etc/init.d# lircd -n --driver=devinput --device=/dev/input/event3 --output=/var/run/lirc/lircd

```

Then I started the Myth FE and the remote is working.  So I looked at the lirc init script and noticed that the function that sets the protocol to just lirc (called in_kernel_support), is only called on start when $LOAD_MODULES = "true".  So in hardware.conf, I set LOAD_MODULES="false".  I rebooted and the remote is working in the Myth FE.  Woohoo!

I'm not sure the meaning of lirc in the protocol list for the device, but maybe it is only used for older drivers that do not fit the new in-kernel rc and keymap model.

---

