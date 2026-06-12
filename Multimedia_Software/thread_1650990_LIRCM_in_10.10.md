---
title: "LIRCM in 10.10"
date: 2010-12-22
forum: Multimedia Software
---

### Post by spiderworm on 2010-12-22
Hi,

I have an infrared remote control successfully configured to communicate with my 10.10 ubuntu install, but I would like to be able to move the mouse pointer around with the d-pad on the remote.

After browsing the forums for awhile, the best steps I have been able to find to make this work are:

[LIST=1]
[*]configure LIRC to enable LIRCM
[*]create the lircm.conf file (make sure it's referenced in lirc.conf) 
[*]restart LIRC
[*]add a custom HAL configuration file to handle the device inputs and translate them to mouse movements
[*]restart HAL
[/LIST]

The trouble is, apparently HAL is not in 10.10 anymore?  Does anyone have updated steps to get the mouse pointer controlled by infrared controller button presses?

Thank you in advance,
spiderworm

---

### Post by cross157 on 2011-01-01
Hi Spiderworm, I'm tackling the same issue with 10.10. I don't have an answer for you yet, but I was wondering what you meant by:

> 2. create the lircm.conf file (make sure it's referenced in lirc.conf)

Did you mean lirc**d**.conf and if so, how do you reference lircm.conf in that file?

I'll let you know if I find/figure out a soln in general. Thanks,

---

### Post by cross157 on 2011-01-01
Got it working :-) combination of luck and this wonderful forum. Here's the post I followed:

[http://ubuntuforums.org/showpost.php?p=10194569&postcount=19](http://ubuntuforums.org/showpost.php?p=10194569&postcount=19)

I have a SnapStream Firefly RF remote and following the above worked perfectly. Below are my conf files

/etc/lirc/hardware.conf

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Snapstream_X10_RF"
REMOTE_MODULES="lirc_dev lirc_atiusb"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="atiusb/lircd.conf.atiusb"
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
START_LIRCMD="true"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF="/etc/lirc/lircmd.conf"

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
#START_LIRCMD=""
```

/etc/lirc/lircd.conf
```
# /etc/lirc/lircd.conf
# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.7.0(any) on Fri Mar 11 08:51:45 2005
#
# contributed by
#
# brand: Snapstream Firefly Remote
# model no. of remote control:
# devices being controlled by this remote:
#

begin remote

  name Snapstream_X10_RF
    bits 40
    eps 30
    aeps 100
    one 0 0
    zero 0 0
    gap 219964
    toggle_bit 0

    begin codes
      MAXI 0x0000001481AC0000
      MAXI 0x00000014012C0000
      CLOSE 0x00000014D7020000
      CLOSE 0x0000001457820000
      1 0x00000014628D0000
      1 0x00000014E20D0000
      2 0x00000014E30E0000
      2 0x00000014638E0000
      3 0x00000014648F0000
      3 0x00000014E40F0000
      4 0x00000014E5100000
      4 0x0000001465900000
      5 0x0000001466910000
      5 0x00000014E6110000
      6 0x00000014E7120000
      6 0x0000001467920000
      7 0x0000001468930000
      7 0x00000014E8130000
      8 0x00000014E9140000
      8 0x0000001469940000
      9 0x000000146A950000
      9 0x00000014EA150000
      0 0x00000014EC170000
      0 0x000000146C970000
      BACK 0x000000146B960000
      BACK 0x00000014EB160000
      ENT 0x00000014ED180000
      ENT 0x000000146D980000
      VOL+ 0x000000145E890000
      VOL+ 0x00000014DE090000
      VOL- 0x000000145D880000
      VOL- 0x00000014DD080000
      MUTE 0x000000145F8A0000
      MUTE 0x00000014DF0A0000
      FIREFLY 0x0000001455800000
      FIREFLY 0x00000014D5000000
      CH+ 0x00000014608B0000
      CH+ 0x00000014E00B0000
      CH- 0x00000014618C0000
      CH- 0x00000014E10C0000
      INFO 0x0000001483AE0000
      INFO 0x00000014032E0000
      OPTION 0x0000001484AF0000
      OPTION 0x00000014042F0000
      UP 0x000000146F9A0000
      UP 0x00000014EF1A0000
      LEFT 0x00000014729D0000
      LEFT 0x00000014F21D0000
      DOWN 0x0000001477A20000
      DOWN 0x00000014F7220000
      RIGHT 0x00000014749F0000
      RIGHT 0x00000014F41F0000
      OK 0x00000014739E0000
      OK 0x00000014F31E0000
      MENU 0x00000014719C0000
      MENU 0x00000014F11C0000
      EXIT 0x0000001475A00000
      EXIT 0x00000014F5200000
      REC 0x00000014FC270000
      REC 0x000000147CA70000
      PLAY 0x00000014FA250000
      PLAY 0x000000147AA50000
      STOP 0x00000014FD280000
      STOP 0x000000147DA80000
      REW 0x00000014F9240000
      REW 0x0000001479A40000
      FWD 0x00000014FB260000
      FWD 0x000000147BA60000
      PREV 0x00000014002B0000
      PREV 0x0000001480AB0000
      PAUSE 0x00000014FE290000
      PAUSE 0x000000147EA90000
      NEXT 0x00000014FF2A0000
      NEXT 0x000000147FAA0000
      MUSIC 0x00000014DB060000
      MUSIC 0x000000145B860000
      PHOTOS 0x00000014DA050000
      PHOTOS 0x000000145A850000
      DVD 0x00000014D9040000
      DVD 0x0000001459840000
      TV 0x00000014D8030000
      TV 0x0000001458830000
      VIDEO 0x00000014DC070000
      VIDEO 0x000000145C870000
      HELP 0x00000014D6010000
      HELP 0x0000001456810000
      MOUSE 0x00000014022D0000
      MOUSE 0x0000001482AD0000
      A 0x00000014EE190000
      A 0x000000146E990000
      B 0x00000014F01B0000
      B 0x00000014709B0000
      C 0x00000014F6210000
      C 0x0000001476A10000
      D 0x00000014F8230000
      D 0x0000001478A30000

  end codes

end remote
```

/etc/lirc/lircmd.conf

```
# 
# lircmd config file for Snapstream RF
# 

# ACCELERATOR start max multiplier
ACCELERATOR 1 200 5

# this button activates/deactivates mouse mode
# commenting out keeps it on
ACTIVATE * MOUSE
TOGGLE_ACTIVATE * MOUSE

MOVE_N  * UP
MOVE_E  * RIGHT
MOVE_S  * DOWN
MOVE_W  * LEFT
MOVE_IN * CH+
MOVE_OUT * CH-

BUTTON1_CLICK * MENU
BUTTON3_CLICK * EXIT
```

Good luck with your setup.

---

### Post by AncientPC on 2011-01-24
I'm using the 3 conf files from above on Ubuntu 10.10.  However after plugging in my Snapstream receiver, I don't have a /dev/lirc0.


```
ting@core:/dev$ sudo /etc/init.d/lirc start
 * Loading LIRC modules                                                                                               [ OK ] 
 * Unable to load LIRC kernel modules. Verify your
 * selected kernel modules in /etc/lirc/hardware.conf

```

Do you have any suggestions?  irw also doesn't work since there's nothing to connect to.

---

### Post by daninca on 2011-04-02
Did you ever get this to work?  I'm running into the same issues.

The hardware.conf show above uses the lirc_atiusb driver with only seems to be in the lirc-modules-source package.  

However, this post [http://wilsonet.com/?page_id=95](http://wilsonet.com/?page_id=95) says that driver module is no longer needed, and we should only need to use
REMOTE_LIRCD_ARGS="--driver=atilibusb"
(and only the lirc_dev driver module).  I can't get this to work, and was hoping someone would post a complete (working) configuration.

-Dan

---

