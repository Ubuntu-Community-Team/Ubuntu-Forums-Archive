---
title: "LIRC issues"
date: 2008-04-16
forum: Mythbuntu
---

### Post by karlec on 2008-04-16
I have been having a hard time getting my MCE remote to work in my Mythbuntu setting and would welcome any help suggestions.
My settings:
[LIST]
[*]OrigenAE case (X11) with IR receiver/LCD
[*]USB-UIRT2
[*]dish receiver
[*]Hardy/Mythbuntu
[/LIST]

The only time that I've been able to get the remote to work is when I use the Irtrans software that comes with the case (irserver).  Since I can't seem to find a way to control the dish receiver with the **irserver**/USB-UIRT combination, I am now trying to simply use LIRC, and that is were I'm having my problems.  
I have installed LIRC using the automated  Mythbuntu to set-up but it is simply not working.
For instance, **irw** returns the following
```
connect: Connection refused
```

```
**dmesg | grep -i lirc**
```
```
[   59.223465] lirc_dev: IR Remote Control driver registered, at major 61 
[   59.271406] lirc_mceusb2: Philips eHome USB IR Transciever and Microsoft MCE 2005 Remote Control driver for LIRC $Revision: 1.33 $
[   59.271410] lirc_mceusb2: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>
[   59.292093] usbcore: registered new interface driver lirc_mceusb2
```

When I check, the frontend logs reveal the following:

```
2008-04-16 18:56:29.027 JoystickMenuClient Error: Joystick disabled - Failed to read /home/karlec/.mythtv/joystickmenurc
mythtv: could not connect to socket
mythtv: Connection refused
2008-04-16 18:56:29.040 lirc_init failed for mythtv, see preceding messages
```

backend logs:
```
2008-04-16 19:31:33.803 Connected to database 'mythconverg' at host: localhost
irsend: could not connect to socket
irsend: Connection refused
irsend: could not connect to socket
irsend: Connection refused
2008-04-16 19:31:35.244 ret_pid(0) child(7936) status(0x0)
irsend: could not connect to socket
irsend: Connection refused
2008-04-16 19:31:36.247 ret_pid(7936) child(7936) status(0x100)
2008-04-16 19:31:36.252 ChannelBase: external tuning program exited with error 1
irsend: could not connect to socket
irsend: Connection refused
irsend: could not connect to socket
irsend: Connection refused
2008-04-16 19:31:37.812 ret_pid(0) child(7947) status(0x0)
irsend: could not connect to socket
irsend: Connection refused
```

I don't think that it is a permission issue based on the following:

```
**ls -l /dev/lir***
```
```
srw-rw-rw- 1 root root 0 2008-04-16 18:51 /dev/lircd
srw-rw-rw- 1 root root 0 2008-04-16 18:51 /dev/lircd1
```

However I am not seeing a **/dev/lirc0**  Could that be the problem?

I would really appreciate some insight on this.

Thanks for any help

---

### Post by karlec on 2008-04-16
bump!

Anybody?

---

### Post by elj4176 on 2008-04-17
Which version of mythbuntu are you using? 

I was having trouble with ilirc and and irblaster with an MCE remote on 7.10. As soon as I upgraded to 8.04 the setup was much easier.
I can't give much more help that that on this issue.

---

### Post by karlec on 2008-04-17
I am using 8.04.   I also had the same problem trying to set it up in 7.10.  Where it not for my dish receiver I would have stuck with IRtrans since it came with the box.  This is somewhat frustrating!

As I said I would really appreciate any help that could get me over this final hump.

Thanks

---

### Post by rtrevor on 2008-04-17
I don't know if this is what you're supposed to do but in my /etc/lirc/hardware.conf I've been using
REMOTE_DEVICE="/dev/input/by-path/pci-2-1--event-ir"

You could try checking what's in /dev/input/by-path/ and try changing /etc/lirc/hardware.conf to point to the IR device listed there (if there is one)?

---

### Post by karlec on 2008-04-17
I don't have anything in in /dev/input/by-path/ that relates to IR devices.

---

### Post by majoridiot on 2008-04-17
> **karlec said:**
> I would really appreciate some insight on this.
Thanks for any help

to help with troubleshooting, please post copies of your:

/etc/lirc/hardware.conf
/etc/lirc/lircd.conf
and
~/.lircrc

---

### Post by karlec on 2008-04-18
> **majoridiot said:**
> to help with troubleshooting, please post copies of your:

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
REMOTE_LIRCD_ARGS="-d /dev/lirc0 --output=/dev/lircd --listen"

#Chosen IR Transmitter
TRANSMITTER="USB-UIRT2 : Dish Receiver"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER="uirt2_raw"
TRANSMITTER_DEVICE="/dev/lirc1"
TRANSMITTER_LIRCD_CONF="dish/general.conf"
TRANSMITTER_LIRCD_ARGS="-d /dev/lirc1 --output=/dev/lircd1 --connect=localhost:8765 --pidfile=/var/run/lircd2.pid"

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


/etc/lirc/lircd.conf

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

#Configuration for the Windows Media Center Remotes (new version Philips et al.) remote:
include /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb

#Configuration for the USB-UIRT2 : Dish Receiver transmitter:
include /usr/share/lirc/transmitters/dish/general.conf
```


and
~/.lircrc

```
#Custom lircrc generated via mythbuntu-lirc-generator
#All application specific lircrc files are within ~/.lirc
include ~/.lirc/mythtv 
include ~/.lirc/mplayer 
include ~/.lirc/xine 
include ~/.lirc/vlc 
include ~/.lirc/xmame 
include ~/.lirc/xmess 
include ~/.lirc/totem 
include ~/.lirc/elisa 
```

Please let me know if I need to post anything else.

Thanks

---

### Post by majoridiot on 2008-04-18
> **karlec said:**
> ```
##Feel free to add any custom remotes to the configuration
#via additional include directives or below the existing
#Ubuntu include directives from your selected remote and/or
#transmitter.

#Configuration for the Windows Media Center Remotes (new version Philips et al.) remote:
include /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb

#Configuration for the USB-UIRT2 : Dish Receiver transmitter:
include /usr/share/lirc/transmitters/dish/general.conf 
```

Please let me know if I need to post anything else.

Thanks

do the two files listed in those **include**s exist and with read permissions set correctly?

if so, please post the contents of those two included .conf files, so we can see the configuration.

---

### Post by karlec on 2008-04-18
Here are the files and their permissions settings


```
[COLOR="Blue"]gedit /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb[/COLOR]
```
```
#
# RC-6 config file
#
# source: http://home.hccnet.nl/m.majoor/projects__remote_control.htm
#         http://home.hccnet.nl/m.majoor/pronto.pdf
#
# used by: Philips
#
#########
#
# Philips Media Center Edition remote control
# For use with the USB MCE ir receiver
#
# Dan Conti  dconti|acm.wwu.edu
#
# Updated with codes for MCE 2005 Remote additional buttons
# *, #, Teletext, Red, Green, Yellow & Blue Buttons
# Note: TV power button transmits no code until programmed.
# Updated 12th September 2005
# Graham Auld - mce|graham.auld.me.uk
#
# Radio, Print, RecTV are only available on the HP Media Center remote control
#

begin remote

  name mceusb
  bits           16
  flags RC6|CONST_LENGTH
  eps            30
  aeps          100

  header       2667   889
  one           444   444
  zero          444   444
  pre_data_bits 21
  pre_data      0x37FF0
  gap          105000
  toggle_bit     22
  rc6_mask     0x100000000


      begin codes

	Blue	0x00007ba1
	Yellow	0x00007ba2
	Green	0x00007ba3
	Red	0x00007ba4
	Teletext	0x00007ba5

# starts at af
        Radio    0x00007baf
        Print    0x00007bb1
        Videos   0x00007bb5
        Pictures 0x00007bb6
        RecTV    0x00007bb7
        Music    0x00007bb8
        TV       0x00007bb9
# no ba - d8

        Guide    0x00007bd9
        LiveTV   0x00007bda
        DVD      0x00007bdb
        Back     0x00007bdc
        OK       0x00007bdd
        Right    0x00007bde
        Left     0x00007bdf
        Down     0x00007be0
        Up       0x00007be1

        Star       0x00007be2
        Hash       0x00007be3

        Replay   0x00007be4
        Skip     0x00007be5
        Stop     0x00007be6
        Pause    0x00007be7
        Record   0x00007be8
        Play     0x00007be9
        Rewind   0x00007bea
        Forward  0x00007beb
        ChanDown 0x00007bec
        ChanUp   0x00007bed
        VolDown  0x00007bee
        VolUp    0x00007bef
        More     0x00007bf0
        Mute     0x00007bf1
        Home     0x00007bf2
        Power    0x00007bf3
        Enter    0x00007bf4
        Clear    0x00007bf5
        Nine     0x00007bf6
        Eight    0x00007bf7
        Seven    0x00007bf8
        Six      0x00007bf9
        Five     0x00007bfa
        Four     0x00007bfb
        Three    0x00007bfc
        Two      0x00007bfd
        One      0x00007bfe
        Zero     0x00007bff
      end codes

end remote
```

```
ls -l /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb
```
```
-rw-r--r-- 1 root root 2393 2008-04-18 08:24 /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb
```


```
[COLOR="Blue"]gedit /usr/share/lirc/transmitters/dish/general.conf[/COLOR]
```
```
# This config file is based on the information posted by Endaf Jones at
# http://www.gossamer-threads.com/lists/mythtv/users/196566#196566
#
# brand:                       JVC/RCA
# model no. of remote control:
# supported devices:           Dish Network (Echostar)
#                                - JVC 2700 receiver
#                                - JVC 4700 receiver
#                                - JVC 49xx receiver
#                                - JVC 50xx receiver
#                                - RCA 31x receiver
#                              and several other Dish receivers using the
#                              "blue button" remotes
#
# Unit code selection (1-16) is performed by specifying the appropriate
# value for post_data
#  1=0x000             2=0x200             3=0x100             4=0x300
#  5=0x080             6=0x280             7=0x180             8=0x380
#  9=0x040            10=0x240            11=0x140            12=0x340
# 13=0x0C0            14=0x2C0            15=0x1C0            16=0x3C0
#
# Each has been implemented in this config file with the remote names "dish#"
# where the hash/pound/number sign ("#") is a code number from 1 through 16.
# There is also a remote called "dish" (without a number), for users with only
# one receiver, that uses remote code 1 (DISH's default).
#
# The duty_cycle (the percentage of time during a pulse that infrared light is
# being sent) is commented because some hardware transmitters don't support its
# use.
#
# The discrete power functions (power_on and power_off) can be used to ensure
# the power state of the receiver.  However, they probably shouldn't be used in
# a channel change script as the receiver will require a significant delay
# after a power_on before it is capable of receiving/responding to additional
# commands (such as channel numbers).  Instead, assuming most of your recording
# is during prime-time, you may want to set a cron job to run a "power_on"
# command for each of your receivers about 5 or 10 minutes before primtetime.


### Remote definition for remotes using remote code 1 (0x000)
begin remote
  name dish

  flags SPACE_ENC|NO_HEAD_REP
  eps 30
  aeps 100

  frequency 56000
#  duty_cycle 32

  one 440 1645
  zero 440 2780

  header 525 6045
  ptrail 450
  gap 6115

  min_repeat 6

  bits 6
  post_data_bits 10

  post_data 0x000

  begin codes
    info                               0
    power_on                           1
    power                              2
    1                                  4
    2                                  5
    3                                  6
    4                                  8
    5                                  9
    6                                  10
    7                                  12
    8                                  13
    9                                  14
    0                                  17
    menu                               11
    select                             16
    cancel                             18
    guide                              20
    view                               22
    tv_vcr                             23
    right                              24
    up                                 26
    recall                             27
    left                               28
    down                               30
    record                             31
    pause                              32
    stop                               33
    sys_info                           36
    asterisk                           37
    pound                              38
    power_off                          39
    sat                                41
    dish_home                          52
    sys_info2                          54
    dish_home2                         56
  end codes
end remote

### Remote definition for remotes using remote code 1 (0x000)
### (Duplicated to allow a "dish" and a "dish1" remote name)
begin remote
  name dish1

  flags SPACE_ENC|NO_HEAD_REP
  eps 30
  aeps 100

  frequency 56000
#  duty_cycle 32

  one 440 1645
  zero 440 2780

  header 525 6045
  ptrail 450
  gap 6115

  min_repeat 6

  bits 6
  post_data_bits 10

  post_data 0x000

  begin codes
    info                               0
    power_on                           1
    power                              2
    1                                  4
    2                                  5
    3                                  6
    4                                  8
    5                                  9
    6                                  10
    7                                  12
    8                                  13
    9                                  14
    0                                  17
    menu                               11
    select                             16
    cancel                             18
    guide                              20
    view                               22
    tv_vcr                             23
    right                              24
    up                                 26
    recall                             27
    left                               28
    down                               30
    record                             31
    pause                              32
    stop                               33
    sys_info                           36
    asterisk                           37
    pound                              38
    power_off                          39
    sat                                41
    dish_home                          52
    sys_info2                          54
    dish_home2                         56
    dvr				       57
    skip_fwd			       55
    skip_back			       54
    fwd				       50
    play			       3
    back			       49
    dish			       52
    page_up			       15
    page_down			       7
  end codes
end remote

### Remote definition for remotes using remote code 2 (0x200)
begin remote
  name dish2

  flags SPACE_ENC|NO_HEAD_REP
  eps 30
  aeps 100

  frequency 56000
#  duty_cycle 32

  one 440 1645
  zero 440 2780

  header 525 6045
  ptrail 450
  gap 6115

  min_repeat 6

  bits 6
  post_data_bits 10

  post_data 0x200

  begin codes
    info                               0
    power_on                           1
    power                              2
    1                                  4
    2                                  5
    3                                  6
    4                                  8
    5                                  9
    6                                  10
    7                                  12
    8                                  13
    9                                  14
    0                                  17
    menu                               11
    select                             16
    cancel                             18
    guide                              20
    view                               22
    tv_vcr                             23
    right                              24
    up                                 26
    recall                             27
    left                               28
    down                               30
    record                             31
    pause                              32
    stop                               33
    sys_info                           36
    asterisk                           37
    pound                              38
    power_off                          39
    sat                                41
    dish_home                          52
    sys_info2                          54
    dish_home2                         56
    dvr				       57
    skip_fwd			       55
    skip_back			       54
    fwd				       50
    play			       3
    back			       49
    dish			       52
    page_up			       15
    page_down			       7
  end codes
end remote

### Remote definition for remotes using remote code 3 (0x100)
begin remote
  name dish3

  flags SPACE_ENC|NO_HEAD_REP
  eps 30
  aeps 100

  frequency 56000
#  duty_cycle 32

  one 440 1645
  zero 440 2780

  header 525 6045
  ptrail 450
  gap 6115

  min_repeat 6

  bits 6
  post_data_bits 10

  post_data 0x100

  begin codes
    info                               0
    power_on                           1
    power                              2
    1                                  4
    2                                  5
    3                                  6
    4                                  8
    5                                  9
    6                                  10
    7                                  12
    8                                  13
    9                                  14
    0                                  17
    menu                               11
    select                             16
    cancel                             18
    guide                              20
    view                               22
    tv_vcr                             23
    right                              24
    up                                 26
    recall                             27
    left                               28
    down                               30
    record                             31
    pause                              32
    stop                               33
    sys_info                           36
    asterisk                           37
    pound                              38
    power_off                          39
    sat                                41
    dish_home                          52
    sys_info2                          54
    dish_home2                         56
    dvr				       57
    skip_fwd			       55
    skip_back			       54
    fwd				       50
    play			       3
    back			       49
    dish			       52
    page_up			       15
    page_down			       7
  end codes
end remote

### Remote definition for remotes using remote code 4 (0x300)
begin remote
  name dish4

  flags SPACE_ENC|NO_HEAD_REP
  eps 30
  aeps 100

  frequency 56000
#  duty_cycle 32

  one 440 1645
  zero 440 2780

  header 525 6045
  ptrail 450
  gap 6115

  min_repeat 6

  bits 6
  post_data_bits 10

  post_data 0x300

  begin codes
    info                               0
    power_on                           1
    power                              2
    1                                  4
    2                                  5
    3                                  6
    4                                  8
    5                                  9
    6                                  10
    7                                  12
    8                                  13
    9                                  14
    0                                  17
    menu                               11
    select                             16
    cancel                             18
    guide                              20
    view                               22
    tv_vcr                             23
    right                              24
    up                                 26
    recall                             27
    left                               28
    down                               30
    record                             31
    pause                              32
    stop                               33
    sys_info                           36
    asterisk                           37
    pound                              38
    power_off                          39
    sat                                41
    dish_home                          52
    sys_info2                          54
    dish_home2                         56
    dvr				       57
    skip_fwd			       55
    skip_back			       54
    fwd				       50
    play			       3
    back			       49
    dish			       52
    page_up			       15
    page_down			       7
  end codes
end remote

### Remote definition for remotes using remote code 5 (0x080)
begin remote
  name dish5

  flags SPACE_ENC|NO_HEAD_REP
  eps 30
  aeps 100

  frequency 56000
#  duty_cycle 32

  one 440 1645
  zero 440 2780

  header 525 6045
  ptrail 450
  gap 6115

  min_repeat 6

  bits 6
  post_data_bits 10

  post_data 0x080

  begin codes
    info                               0
    power_on                           1
    power                              2
    1                                  4
    2                                  5
    3                                  6
    4                                  8
    5                                  9
    6                                  10
    7                                  12
    8                                  13
    9                                  14
    0                                  17
    menu                               11
    select                             16
    cancel                             18
    guide                              20
    view                               22
    tv_vcr                             23
    right                              24
    up                                 26
    recall                             27
    left                               28
    down                               30
    record                             31
    pause                              32
    stop                               33
    sys_info                           36
    asterisk                           37
    pound                              38
    power_off                          39
    sat                                41
    dish_home                          52
    sys_info2                          54
    dish_home2                         56
    dvr				       57
    skip_fwd			       55
    skip_back			       54
    fwd				       50
    play			       3
    back			       49
    dish			       52
    page_up			       15
    page_down			       7
  end codes
end remote

### Remote definition for remotes using remote code 6 (0x280)
begin remote
  name dish6

  flags SPACE_ENC|NO_HEAD_REP
  eps 30
  aeps 100

  frequency 56000
#  duty_cycle 32

  one 440 1645
  zero 440 2780

  header 525 6045
  ptrail 450
  gap 6115

  min_repeat 6

  bits 6
  post_data_bits 10

  post_data 0x280

  begin codes
    info                               0
    power_on                           1
    power                              2
    1                                  4
    2                                  5
    3                                  6
    4                                  8
    5                                  9
    6                                  10
    7                                  12
    8                                  13
    9                                  14
    0                                  17
    menu                               11
    select                             16
    cancel                             18
    guide                              20
    view                               22
    tv_vcr                             23
    right                              24
    up                                 26
    recall                             27
    left                               28
    down                               30
    record                             31
    pause                              32
    stop                               33
    sys_info                           36
    asterisk                           37
    pound                              38
    power_off                          39
    sat                                41
    dish_home                          52
    sys_info2                          54
    dish_home2                         56
    dvr				       57
    skip_fwd			       55
    skip_back			       54
    fwd				       50
    play			       3
    back			       49
    dish			       52
    page_up			       15
    page_down			       7
  end codes
end remote

### Remote definition for remotes using remote code 7 (0x180)
begin remote
  name dish7

  flags SPACE_ENC|NO_HEAD_REP
  eps 30
  aeps 100

  frequency 56000
#  duty_cycle 32

  one 440 1645
  zero 440 2780

  header 525 6045
  ptrail 450
  gap 6115

  min_repeat 6

  bits 6
  post_data_bits 10

  post_data 0x180

  begin codes
    info                               0
    power_on                           1
    power                              2
    1                                  4
    2                                  5
    3                                  6
    4                                  8
    5                                  9
    6                                  10
    7                                  12
    8                                  13
    9                                  14
    0                                  17
    menu                               11
    select                             16
    cancel                             18
    guide                              20
    view                               22
    tv_vcr                             23
    right                              24
    up                                 26
    recall                             27
    left                               28
    down                               30
    record                             31
    pause                              32
    stop                               33
    sys_info                           36
    asterisk                           37
    pound                              38
    power_off                          39
    sat                                41
    dish_home                          52
    sys_info2                          54
    dish_home2                         56
    dvr				       57
    skip_fwd			       55
    skip_back			       54
    fwd				       50
    play			       3
    back			       49
    dish			       52
    page_up			       15
    page_down			       7    
  end codes
end remote

### Remote definition for remotes using remote code 8 (0x380)
begin remote
  name dish8

  flags SPACE_ENC|NO_HEAD_REP
  eps 30
  aeps 100

  frequency 56000
#  duty_cycle 32

  one 440 1645
  zero 440 2780

  header 525 6045
  ptrail 450
  gap 6115

  min_repeat 6

  bits 6
  post_data_bits 10

  post_data 0x380

  begin codes
    info                               0
    power_on                           1
    power                              2
    1                                  4
    2                                  5
    3                                  6
    4                                  8
    5                                  9
    6                                  10
    7                                  12
    8                                  13
    9                                  14
    0                                  17
    menu                               11
    select                             16
    cancel                             18
    guide                              20
    view                               22
    tv_vcr                             23
    right                              24
    up                                 26
    recall                             27
    left                               28
    down                               30
    record                             31
    pause                              32
    stop                               33
    sys_info                           36
    asterisk                           37
    pound                              38
    power_off                          39
    sat                                41
    dish_home                          52
    sys_info2                          54
    dish_home2                         56
    dvr				       57
    skip_fwd			       55
    skip_back			       54
    fwd				       50
    play			       3
    back			       49
    dish			       52
    page_up			       15
    page_down			       7    
  end codes
end remote

### Remote definition for remotes using remote code 9 (0x040)
begin remote
  name dish9

  flags SPACE_ENC|NO_HEAD_REP
  eps 30
  aeps 100

  frequency 56000
#  duty_cycle 32

  one 440 1645
  zero 440 2780

  header 525 6045
  ptrail 450
  gap 6115

  min_repeat 6

  bits 6
  post_data_bits 10

  post_data 0x040

  begin codes
    info                               0
    power_on                           1
    power                              2
    1                                  4
    2                                  5
    3                                  6
    4                                  8
    5                                  9
    6                                  10
    7                                  12
    8                                  13
    9                                  14
    0                                  17
    menu                               11
    select                             16
    cancel                             18
    guide                              20
    view                               22
    tv_vcr                             23
    right                              24
    up                                 26
    recall                             27
    left                               28
    down                               30
    record                             31
    pause                              32
    stop                               33
    sys_info                           36
    asterisk                           37
    pound                              38
    power_off                          39
    sat                                41
    dish_home                          52
    sys_info2                          54
    dish_home2                         56
    dvr				       57
    skip_fwd			       55
    skip_back			       54
    fwd				       50
    play			       3
    back			       49
    dish			       52
    page_up			       15
    page_down			       7    
  end codes
end remote

### Remote definition for remotes using remote code 10 (0x240)
begin remote
  name dish10

  flags SPACE_ENC|NO_HEAD_REP
  eps 30
  aeps 100

  frequency 56000
#  duty_cycle 32

  one 440 1645
  zero 440 2780

  header 525 6045
  ptrail 450
  gap 6115

  min_repeat 6

  bits 6
  post_data_bits 10

  post_data 0x240

  begin codes
    info                               0
    power_on                           1
    power                              2
    1                                  4
    2                                  5
    3                                  6
    4                                  8
    5                                  9
    6                                  10
    7                                  12
    8                                  13
    9                                  14
    0                                  17
    menu                               11
    select                             16
    cancel                             18
    guide                              20
    view                               22
    tv_vcr                             23
    right                              24
    up                                 26
    recall                             27
    left                               28
    down                               30
    record                             31
    pause                              32
    stop                               33
    sys_info                           36
    asterisk                           37
    pound                              38
    power_off                          39
    sat                                41
    dish_home                          52
    sys_info2                          54
    dish_home2                         56
    dvr				       57
    skip_fwd			       55
    skip_back			       54
    fwd				       50
    play			       3
    back			       49
    dish			       52
    page_up			       15
    page_down			       7    
  end codes
end remote

### Remote definition for remotes using remote code 11 (0x140)
begin remote
  name dish11

  flags SPACE_ENC|NO_HEAD_REP
  eps 30
  aeps 100

  frequency 56000
#  duty_cycle 32

  one 440 1645
  zero 440 2780

  header 525 6045
  ptrail 450
  gap 6115

  min_repeat 6

  bits 6
  post_data_bits 10

  post_data 0x140

  begin codes
    info                               0
    power_on                           1
    power                              2
    1                                  4
    2                                  5
    3                                  6
    4                                  8
    5                                  9
    6                                  10
    7                                  12
    8                                  13
    9                                  14
    0                                  17
    menu                               11
    select                             16
    cancel                             18
    guide                              20
    view                               22
    tv_vcr                             23
    right                              24
    up                                 26
    recall                             27
    left                               28
    down                               30
    record                             31
    pause                              32
    stop                               33
    sys_info                           36
    asterisk                           37
    pound                              38
    power_off                          39
    sat                                41
    dish_home                          52
    sys_info2                          54
    dish_home2                         56
    dvr				       57
    skip_fwd			       55
    skip_back			       54
    fwd				       50
    play			       3
    back			       49
    dish			       52
    page_up			       15
    page_down			       7    
  end codes
end remote

### Remote definition for remotes using remote code 12 (0x340)
begin remote
  name dish12

  flags SPACE_ENC|NO_HEAD_REP
  eps 30
  aeps 100

  frequency 56000
#  duty_cycle 32

  one 440 1645
  zero 440 2780

  header 525 6045
  ptrail 450
  gap 6115

  min_repeat 6

  bits 6
  post_data_bits 10

  post_data 0x340

  begin codes
    info                               0
    power_on                           1
    power                              2
    1                                  4
    2                                  5
    3                                  6
    4                                  8
    5                                  9
    6                                  10
    7                                  12
    8                                  13
    9                                  14
    0                                  17
    menu                               11
    select                             16
    cancel                             18
    guide                              20
    view                               22
    tv_vcr                             23
    right                              24
    up                                 26
    recall                             27
    left                               28
    down                               30
    record                             31
    pause                              32
    stop                               33
    sys_info                           36
    asterisk                           37
    pound                              38
    power_off                          39
    sat                                41
    dish_home                          52
    sys_info2                          54
    dish_home2                         56
    dvr				       57
    skip_fwd			       55
    skip_back			       54
    fwd				       50
    play			       3
    back			       49
    dish			       52
    page_up			       15
    page_down			       7    
  end codes
end remote

### Remote definition for remotes using remote code 13 (0x0C0)
begin remote
  name dish13

  flags SPACE_ENC|NO_HEAD_REP
  eps 30
  aeps 100

  frequency 56000
#  duty_cycle 32

  one 440 1645
  zero 440 2780

  header 525 6045
  ptrail 450
  gap 6115

  min_repeat 6

  bits 6
  post_data_bits 10

  post_data 0x0C0

  begin codes
    info                               0
    power_on                           1
    power                              2
    1                                  4
    2                                  5
    3                                  6
    4                                  8
    5                                  9
    6                                  10
    7                                  12
    8                                  13
    9                                  14
    0                                  17
    menu                               11
    select                             16
    cancel                             18
    guide                              20
    view                               22
    tv_vcr                             23
    right                              24
    up                                 26
    recall                             27
    left                               28
    down                               30
    record                             31
    pause                              32
    stop                               33
    sys_info                           36
    asterisk                           37
    pound                              38
    power_off                          39
    sat                                41
    dish_home                          52
    sys_info2                          54
    dish_home2                         56
    dvr				       57
    skip_fwd			       55
    skip_back			       54
    fwd				       50
    play			       3
    back			       49
    dish			       52
    page_up			       15
    page_down			       7    
  end codes
end remote

### Remote definition for remotes using remote code 14 (0x2C0)
begin remote
  name dish14

  flags SPACE_ENC|NO_HEAD_REP
  eps 30
  aeps 100

  frequency 56000
#  duty_cycle 32

  one 440 1645
  zero 440 2780

  header 525 6045
  ptrail 450
  gap 6115

  min_repeat 6

  bits 6
  post_data_bits 10

  post_data 0x2C0

  begin codes
    info                               0
    power_on                           1
    power                              2
    1                                  4
    2                                  5
    3                                  6
    4                                  8
    5                                  9
    6                                  10
    7                                  12
    8                                  13
    9                                  14
    0                                  17
    menu                               11
    select                             16
    cancel                             18
    guide                              20
    view                               22
    tv_vcr                             23
    right                              24
    up                                 26
    recall                             27
    left                               28
    down                               30
    record                             31
    pause                              32
    stop                               33
    sys_info                           36
    asterisk                           37
    pound                              38
    power_off                          39
    sat                                41
    dish_home                          52
    sys_info2                          54
    dish_home2                         56
    dvr				       57
    skip_fwd			       55
    skip_back			       54
    fwd				       50
    play			       3
    back			       49
    dish			       52
    page_up			       15
    page_down			       7    
  end codes
end remote

### Remote definition for remotes using remote code 15 (0x1C0)
begin remote
  name dish15

  flags SPACE_ENC|NO_HEAD_REP
  eps 30
  aeps 100

  frequency 56000
#  duty_cycle 32

  one 440 1645
  zero 440 2780

  header 525 6045
  ptrail 450
  gap 6115

  min_repeat 6

  bits 6
  post_data_bits 10

  post_data 0x1C0

  begin codes
    info                               0
    power_on                           1
    power                              2
    1                                  4
    2                                  5
    3                                  6
    4                                  8
    5                                  9
    6                                  10
    7                                  12
    8                                  13
    9                                  14
    0                                  17
    menu                               11
    select                             16
    cancel                             18
    guide                              20
    view                               22
    tv_vcr                             23
    right                              24
    up                                 26
    recall                             27
    left                               28
    down                               30
    record                             31
    pause                              32
    stop                               33
    sys_info                           36
    asterisk                           37
    pound                              38
    power_off                          39
    sat                                41
    dish_home                          52
    sys_info2                          54
    dish_home2                         56
    dvr				       57
    skip_fwd			       55
    skip_back			       54
    fwd				       50
    play			       3
    back			       49
    dish			       52
    page_up			       15
    page_down			       7    
  end codes
end remote

### Remote definition for remotes using remote code 16 (0x3C0)
begin remote
  name dish16

  flags SPACE_ENC|NO_HEAD_REP
  eps 30
  aeps 100

  frequency 56000
#  duty_cycle 32

  one 440 1645
  zero 440 2780

  header 525 6045
  ptrail 450
  gap 6115

  min_repeat 6

  bits 6
  post_data_bits 10

  post_data 0x3C0

  begin codes
    info                               0
    power_on                           1
    power                              2
    1                                  4
    2                                  5
    3                                  6
    4                                  8
    5                                  9
    6                                  10
    7                                  12
    8                                  13
    9                                  14
    0                                  17
    menu                               11
    select                             16
    cancel                             18
    guide                              20
    view                               22
    tv_vcr                             23
    right                              24
    up                                 26
    recall                             27
    left                               28
    down                               30
    record                             31
    pause                              32
    stop                               33
    sys_info                           36
    asterisk                           37
    pound                              38
    power_off                          39
    sat                                41
    dish_home                          52
    sys_info2                          54
    dish_home2                         56
    dvr				       57
    skip_fwd			       55
    skip_back			       54
    fwd				       50
    play			       3
    back			       49
    dish			       52
    page_up			       15
    page_down			       7    
  end codes
end remote

```

```
ls -l /usr/share/lirc/transmitters/dish/general.conf
```
```
-rw-r--r-- 1 root root 36297 2008-03-24 14:24 /usr/share/lirc/transmitters/dish/general.conf
```


Thanks

---

### Post by majoridiot on 2008-04-18
> **karlec said:**
> Here are the files and their permissions settings...

Thanks

ok... those seem to be sane.

do if you restart lirc manually, does it fail or throw any errors to your logs?

```
$ sudo /etc/init.d/lirc restart
```

just out of curiosity, you are using an MCE remote... you do have an mce usb receiver, correct?

---

### Post by karlec on 2008-04-18
> **majoridiot said:**
> ok... those seem to be sane.

do if you restart lirc manually, does it fail or throw any errors to your logs?

```
$ sudo /etc/init.d/lirc restart
```

When I restart LIRC manually everything seems to be ok on the terminal screen.  The logs(frontend/Backend) generally show the connection refused message or the lirc_init error message.
Maybe related --when I try to activate the LIRC plugin in Totem I also get an error message:
Failed to initialize LIRC.

> **majoridiot said:**
> just out of curiosity, you are using an MCE remote... you do have an mce usb receiver, correct?

Yes, my case came with the Philips mce usb receiver.  At least that is what **dmesg/lsusb** seem to indicate

The case came with the IRtrans/IRserver "combo"  and that works within Mythtv in that I can navigate the screen and select stuff.  So I am somewhat sure that the mce usb receiver is there and working. (I just can't control my stb with that combination yet).  However when I go the LIRC route, nothing at all seems to be working so far.

Thanks, I appreciate your continued assistance.

---

### Post by majoridiot on 2008-04-18
> **karlec said:**
> When I restart LIRC manually everything seems to be ok on the terminal screen.  The logs(frontend/Backend) generally show the connection refused message or the lirc_init error message.
Maybe related --when I try to activate the LIRC plugin in Totem I also get an error message:
Failed to initialize LIRC.



Yes, my case came with the Philips mce usb receiver.  At least that is what **dmesg/lsusb** seem to indicate

The case came with the IRtrans/IRserver "combo"  and that works within Mythtv in that I can navigate the screen and select stuff.  So I am somewhat sure that the mce usb receiver is there and working. (I just can't control my stb with that combination yet).  However when I go the LIRC route, nothing at all seems to be working so far.

Thanks, I appreciate your continued assistance.

ok... are your lirc modules loaded?

```
$ lsmod | grep lirc
```

---

### Post by karlec on 2008-04-18
I am not at home now, but as far as I can remember they were all loading.  I will confirm later today.

Thanks

---

### Post by karlec on 2008-04-18
Modules appear to be loaded per below.

```
 lsmod | grep lirc
lirc_mceusb2           16900  0 
lirc_dev               18248  1 lirc_mceusb2
usbcore               169904  9 lirc_mceusb2,ftdi_sio,usbserial,usbhid,usb_storage,libusual,ehci_hcd,ohci_hcd

```

---

### Post by finlay648 on 2008-04-18
When I originally setup my combined FE/BE using a Ubuntu 7.10 system I had available I had the exact same problem with a mceusb remote. AFAICT the driver was loading but it wasn't creating the /dev/lirc0 device node. Googling the problem suggested that some other driver was probably preventing the lirc_mceusb2 driver from working properly but I could never figure out what in my case. The site I found that indicated that the conflict was with some IR blaster driver IIRC.

I finally decided to revise my configuration and split it into separate FE and BE for noise and heat reasons. When I set up the FE I used MythBuntu 7.10 and the remote just started working properly. As a data point here's the output from my dmesg | grep lirc:

[   14.480000] lirc_dev: IR Remote Control driver registered, at major 61 
[   14.768000] lirc_mceusb2: Philips eHome USB IR Transciever and Microsoft MCE 2005 Remote Control driver for LIRC $Revision: 1.33 $
[   14.768000] lirc_mceusb2: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>
[   15.140000] lirc_dev: lirc_register_plugin: sample_rate: 0
[   15.148000] lirc_mceusb2[2]: Philips eHome Infrared Transceiver on usb3:2
[   15.148000] usbcore: registered new interface driver lirc_mceusb2

and my lsmod | grep lirc:

lirc_mceusb2           14980  1 
lirc_dev               15860  1 lirc_mceusb2
usbcore               138632  5 lirc_mceusb2,usbhid,ohci_hcd,ehci_hcd

which may indicate that your driver is loaded but not being used.

---

### Post by karlec on 2008-04-18
I would hate to think that my only solution is to split backend and frontend.:(

Your **dmesg | grep lirc** seems to return more information than mine, that is probably why I am having this issue.

---

### Post by karlec on 2008-04-19
It must be a problem with LIRC and my mce receiver.  While LIRC was "running" any attempt on my part to test with **irw** would return 
```
unable to connect
```

Now, once again I have stopped LIRC and am using the IRtrans software, that came with the box, and irw is responding properly.  I hope that someone can shed some light on this for me otherwise I need to find a way to control my STB with the IRtrans software.

Again, I would appreciate any help.

---

### Post by finlay648 on 2008-04-19
i figure your problem is the driver. Perhaps this message may relate to your problem.

[http://ge.ubuntuforums.com/showpost.php?p=4525684&postcount=2](http://ge.ubuntuforums.com/showpost.php?p=4525684&postcount=2)

---

### Post by majoridiot on 2008-04-19
> **karlec said:**
> It must be a problem with LIRC and my mce receiver.  While LIRC was "running" any attempt on my part to test with **irw** would return 
```
unable to connect
```

Now, once again I have stopped LIRC and am using the IRtrans software, that came with the box, and irw is responding properly.  I hope that someone can shed some light on this for me otherwise I need to find a way to control my STB with the IRtrans software.

Again, I would appreciate any help.

ok... i just did an install to test your situation.  in mythbuntu 8.04 MCC (fully updated), i set up for the MCE usb (new) remote 
and MCE transmitter to control my motorola cable box.

all i did was check the boxes and install... nothing else.  both irw and the blaster work just fine with no further changes.

i recommend you:

1. unconfig the remote and blaster in MCC and apply the changes.

2. delete /etc/lirc/lircd.conf /etc/lirc/hardware.conf and ~/.lircrc

3. check for updates and apply them

4. when prompted to reboot, shut down entirely.  remove the power cord from the computer, hold the power button down
for 2-3 seconds to fully discharge power,  and then plug in and reboot it.

5.  using MCC, set up the MCE remote and blaster

6.  test with irw and irsend

7.  hopefully, enjoy.

if not, post your progress/problems.

---

### Post by karlec on 2008-04-21
Thanks for the last two responses.  Sorry for not responding earlier, I was away for the weekend, so I was not able to try either.  I will do so when I get home tonight, and will post my findings.

---

### Post by jpm493 on 2008-04-21
sup, this is my first post, so really idk what i am doing....
anyways,
i worked all day trying to get my MCE remote to work with VLC.

this is what I figured out: 

1.  ya need a /etc/lircd.conf file which translates you remote codes into button names
2.  you need a /etc/lirc/hardware.conf file.  The most important line I find in here tells which remote you are using.  e.i. REMOTE="Windows Media Center Remotes (new version Philips et al.)"
3.  running "irw" of course without the quotes will allow you to test your remote.  if this doesn't work try "mode2"  At this point, only irw works for me.  mode2 worked previously while irw was not working.  maybe during configuration another step was made to create this transition.  idk tho...  once irw is working, your remote should be able to control programs.  
4.   ~/.lircrc is NECESSARY and should be the final step.  This took me the longest time to figure out.  .lircrc is the control file that programs like vlc and mythtv use to translate the buttons lirc reads, to program control. 

more info
[EDITED] and copied to the next page, 

good luck, hope this helps.

---

### Post by karlec on 2008-04-22
> **majoridiot said:**
> ok... i just did an install to test your situation.  in mythbuntu 8.04 MCC (fully updated), i set up for the MCE usb (new) remote 
and MCE transmitter to control my motorola cable box.

all i did was check the boxes and install... nothing else.  both irw and the blaster work just fine with no further changes.

i recommend you:

1. unconfig the remote and blaster in MCC and apply the changes.

2. delete /etc/lirc/lircd.conf /etc/lirc/hardware.conf and ~/.lircrc

3. check for updates and apply them

4. when prompted to reboot, shut down entirely.  remove the power cord from the computer, hold the power button down
for 2-3 seconds to fully discharge power,  and then plug in and reboot it.

5.  using MCC, set up the MCE remote and blaster

6.  test with irw and irsend

7.  hopefully, enjoy.

if not, post your progress/problems.

OK,  I've tried your instructions twice and they did not work.  One thing of not is that when I seleted to install the remote and transmitter from MCC I got an error message indicating that MCC could not do it and that I needed to manually run "dpkg-reconfigure lirc'.  I did and again the response to irw was connection refused.

Thanks.

---

### Post by karlec on 2008-04-22
> **finlay648 said:**
> i figure your problem is the driver. Perhaps this message may relate to your problem.

[http://ge.ubuntuforums.com/showpost.php?p=4525684&postcount=2](http://ge.ubuntuforums.com/showpost.php?p=4525684&postcount=2)

Thanks for the link.  I checked it out but it seems like both lirc_mceusb2.ko and lirc_dev.ko were in the right location.

---

### Post by jpm493 on 2008-04-22
ok karlec.  
luckily for you, i deleted what seem to be pretty important packages last night in an effort to solve another problem.  anyways, im starting with a fresh Ubuntu and will try to track all my progress.

---

### Post by jpm493 on 2008-04-22
k, got mine working again, tho it was not by any documentation i could find.  once again tho, I am using lirc with vlc media player.  this stuff should be the same as using mythtv

hey karlec, 
will "mode2"  or  "irw" run, meaning start without refusal ?

if running, do either of these programs get output when remote buttons are mashed ?

---

### Post by majoridiot on 2008-04-22
> **jpm493 said:**
> k, got mine working again, tho it was not by any documentation i could find.

please share what you did to fix your issue, so others reading this thread later can benefit
from your experience.

thanks! :)

---

### Post by majoridiot on 2008-04-22
> **karlec said:**
> OK,  I've tried your instructions twice and they did not work.  One thing of not is that when I seleted to install the remote and transmitter from MCC I got an error message indicating that MCC could not do it and that I needed to manually run "dpkg-reconfigure lirc'.  I did and again the response to irw was connection refused.

Thanks.

please post the resulting hardware.conf lircd.conf and .lircrc, so we can see what resulted
from your changes.

---

### Post by karlec on 2008-04-22
> **jpm493 said:**
> k, got mine working again, tho it was not by any documentation i could find.  once again tho, I am using lirc with vlc media player.  this stuff should be the same as using mythtv

hey karlec, 
will "mode2"  or  "irw" run, meaning start without refusal ?

if running, do either of these programs get output when remote buttons are mashed ?

So far I've gotten nothing back from irw while lircd is running.  Well except for the **connection refused** messages.  What kind of hardware are you using?

---

### Post by karlec on 2008-04-22
> **majoridiot said:**
> please post the resulting hardware.conf lircd.conf and .lircrc, so we can see what resulted
from your changes.

here are the files:

hardware.conf:
```
REMOTE="Windows Media Center Remotes (new version Philips et al.)"
REMOTE_MODULES="lirc_dev lirc_mceusb2"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS=""

TRANSMITTER="USB-UIRT2 : Dish Receiver"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER="uirt2_raw"
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF="dish/general.conf"
TRANSMITTER_LIRCD_ARGS=""
START_LIRCD="true"
START_LIRCMD=""
LOAD_MODULES=""
LIRCMD_CONF=""
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
```

lircd.conf:
```
#
# RC-6 config file
#
# source: http://home.hccnet.nl/m.majoor/projects__remote_control.htm
#         http://home.hccnet.nl/m.majoor/pronto.pdf
#
# used by: Philips
#
#########
#
# Philips Media Center Edition remote control
# For use with the USB MCE ir receiver
#
# Dan Conti  dconti|acm.wwu.edu
#
# Updated with codes for MCE 2005 Remote additional buttons
# *, #, Teletext, Red, Green, Yellow & Blue Buttons
# Note: TV power button transmits no code until programmed.
# Updated 12th September 2005
# Graham Auld - mce|graham.auld.me.uk
#
# Radio, Print, RecTV are only available on the HP Media Center remote control
#

begin remote

  name mceusb
  bits           16
  flags RC6|CONST_LENGTH
  eps            30
  aeps          100

  header       2667   889
  one           444   444
  zero          444   444
  pre_data_bits 21
  pre_data      0x37FF0
  gap          105000
  toggle_bit     22
  rc6_mask     0x100000000


      begin codes

	Blue	0x00007ba1
	Yellow	0x00007ba2
	Green	0x00007ba3
	Red	0x00007ba4
	Teletext	0x00007ba5

# starts at af
        Radio    0x00007baf
        Print    0x00007bb1
        Videos   0x00007bb5
        Pictures 0x00007bb6
        RecTV    0x00007bb7
        Music    0x00007bb8
        TV       0x00007bb9
# no ba - d8

        Guide    0x00007bd9
        LiveTV   0x00007bda
        DVD      0x00007bdb
        Back     0x00007bdc
        OK       0x00007bdd
        Right    0x00007bde
        Left     0x00007bdf
        Down     0x00007be0
        Up       0x00007be1

        Star       0x00007be2
        Hash       0x00007be3

        Replay   0x00007be4
        Skip     0x00007be5
        Stop     0x00007be6
        Pause    0x00007be7
        Record   0x00007be8
        Play     0x00007be9
        Rewind   0x00007bea
        Forward  0x00007beb
        ChanDown 0x00007bec
        ChanUp   0x00007bed
        VolDown  0x00007bee
        VolUp    0x00007bef
        More     0x00007bf0
        Mute     0x00007bf1
        Home     0x00007bf2
        Power    0x00007bf3
        Enter    0x00007bf4
        Clear    0x00007bf5
        Nine     0x00007bf6
        Eight    0x00007bf7
        Seven    0x00007bf8
        Six      0x00007bf9
        Five     0x00007bfa
        Four     0x00007bfb
        Three    0x00007bfc
        Two      0x00007bfd
        One      0x00007bfe
        Zero     0x00007bff
      end codes

end remote
```

.lircrc was empty

---

### Post by jpm493 on 2008-04-22
> **karlec said:**
> So far I've gotten nothing back from irw while lircd is running.  Well except for the **connection refused** messages.  What kind of hardware are you using?
yes, I had that problem too for awhile.  

try /dev/lircd [options]
[options] include: start, restart, load, reload, and a few more which i cant remember nor can i remember where i originally read it from

doing this will tell me

> /dev$ sudo lircd restart
lircd: there seems to already be a lircd process with pid 4094
lircd: otherwise delete stale lockfile /var/run/lircd.pid

and from reading this, I would think nothing has changed.  But this was required for me to get irw not to say, connection refused.  I did NOT delete stale lockfile or whatever it was telling me.

im working on a step by step doc for what i did.  And yes, i know this is all vague, but it worked for me and i hope it helps you.

---

### Post by jpm493 on 2008-04-22
any luck yet ?

---

### Post by karlec on 2008-04-22
nope, not yet.

---

### Post by majoridiot on 2008-04-23
> **karlec said:**
> I have been having a hard time getting my MCE remote to work in my Mythbuntu setting and would welcome any help suggestions.
My settings:
[LIST]
[*]OrigenAE case (X11) with IR receiver/LCD
[*]USB-UIRT2
[*]dish receiver
[*]Hardy/Mythbuntu
[/LIST[LEFT]]

ok... your case has a built-in ir receiver.  is this on the usb bus as well?  have you physically disconnected
the case ir receiver to see if it is interfering with the MCE receiver?

i know that i had difficulties with an irmon built-in interfering with an MCE receiver/blaster...

---

### Post by jpm493 on 2008-04-24
This is my LIRC with MCE remote HOWTO: 

note my system:
Ubuntu 7.10 
Philips USB Media Center Edition Remote -shipped with my Dell Inspiron 530, 4/5/08

First off, connect your IR device 

1.  Goto lirc homepage <[http://www.lirc.org/]("http://www.lirc.org/")> and get the most recent version (as of 4/24/08, it is  lirc-0.8.2.tar.bz2)
2.  Extract files to Desktop
3.  In terminal: cd ~/Desktop/lirc*
4.  In terminal: ./setup.sh 
[INDENT]If given a note dialog not found, In terminal: sudo apt-get install dialog
a.)  Choose the appropriate remote from Driver Configuration
b.)  Choose Save Configuration and Run Configure
[/INDENT]
5.  Back in Terminal:  sudo make and then sudo make install
[INDENT]Lirc should now recognize that a remote is present.
Lets test this. In terminal: mode2 
Try pressing any button on the remote, the output should be a hex number
Note, irw does not function yet[/INDENT]
6.  Open Synaptic Package Manager and search for lirc.  Mark install.  Choose the appropriate remote
7.  Restart your computer
8.  Now lets test lirc again.  In terminal: irw
[INDENT]Note, output may be 'Connection Refused'.  In this case
a.)  In terminal:  cd /dev
b.)  In terminal:  sudo lircd restart
c.)  Try irw again
The output should show recognition of the signal transmitted, the correct button pushed, the duration the button was held, and the remote used[/INDENT]
9.  Lirc should now be setup.  However, to my knowledge, programs will not accept remote control commands until the ~/.lircrc file has been created.  

.lircrc is the control file that programs like vlc and mythtv use to translate the buttons lirc reads, to program control.

It has this syntax:
begin
prog = ...
remote = ...
button = ...
repeat = ...
delay = ...
config = ...
mode = ...
flags = ...
end

one example is:

begin
prog = vlc
button = play
config = key-play-pause
end

button corresponds to the name of the remote's button listed within lircd.conf
config corresponds to the program's control

i manually created a .lircrc for use in VLC. My setup is Ubuntu 7.10, Windows MCE remote.
Found here: [http://jpm493.googlepages.com/lircrc.txt](http://jpm493.googlepages.com/lircrc.txt)
if directly used, rename to .lircrc and move to ~/

vlc config commands can be found by running "vlc --help --advanced"



hope all this helps.  time to enjoy your movies and music...
:popcorn:

- j

---

### Post by karlec on 2008-04-24
> **jpm493 said:**
> This is my LIRC with MCE remote HOWTO: 

note my system:
Ubuntu 7.10 
Philips USB Media Center Edition Remote -shipped with my Dell Inspiron 530, 4/5/08

First off, connect your IR device 

1.  Goto lirc homepage <[http://www.lirc.org/]("http://www.lirc.org/")> and get the most recent version (as of 4/24/08, it is  lirc-0.8.2.tar.bz2)
2.  Extract files to Desktop
3.  In terminal: cd ~/Desktop/lirc*
4.  In terminal: ./setup.sh 
[INDENT]If given a note dialog not found, In terminal: sudo apt-get install dialog
a.)  Choose the appropriate remote from Driver Configuration
b.)  Choose Save Configuration and Run Configure
[/INDENT]
5.  Back in Terminal:  sudo make and then sudo make install
[INDENT]Lirc should now recognize that a remote is present.
Lets test this. In terminal: mode2 
Try pressing any button on the remote, the output should be a hex number
Note, irw does not function yet[/INDENT]
6.  Open Synaptic Package Manager and search for lirc.  Mark install.  Choose the appropriate remote
7.  Restart your computer
8.  Now lets test lirc again.  In terminal: irw
[INDENT]Note, output may be 'Connection Refused'.  In this case
a.)  In terminal:  cd /dev
b.)  In terminal:  sudo lircd restart
c.)  Try irw again
The output should show recognition of the signal transmitted, the correct button pushed, the duration the button was held, and the remote used[/INDENT]
9.  Lirc should now be setup.  However, to my knowledge, programs will not accept remote control commands until the ~/.lircrc file has been created.  

.lircrc is the control file that programs like vlc and mythtv use to translate the buttons lirc reads, to program control.

It has this syntax:
begin
prog = ...
remote = ...
button = ...
repeat = ...
delay = ...
config = ...
mode = ...
flags = ...
end

one example is:

begin
prog = vlc
button = play
config = key-play-pause
end

button corresponds to the name of the remote's button listed within lircd.conf
config corresponds to the program's control

i manually created a .lircrc for use in VLC. My setup is Ubuntu 7.10, Windows MCE remote.
Found here: [http://jpm493.googlepages.com/lircrc.txt](http://jpm493.googlepages.com/lircrc.txt)
if directly used, rename to .lircrc and move to ~/

vlc config commands can be found by running "vlc --help --advanced"



hope all this helps.  time to enjoy your movies and music...
:popcorn:

- j
I am happy you got it to work.  Unfortunately my case is a little more complicated than yours.  If my goal was to get LIRC to work with VLC or similar applications, the IRtrans server would have been fine, however, I need to be able to remote control my Dishnetwork receiver and that's what's causing me some major headaches.

---

### Post by karlec on 2008-04-25
I seemed to have made some progress.  I followed each guide of the Ubuntu wiki individually for USB-UIRT and installing LIRC on Feisty.  
My first observation is that the automated scripts seem to produce a completely different result in creating the hardware.conf file than what is on the wiki.  By manually configuring it I am now able to issue some commands (e.g. irw and irsend) without an immediate **Connection Refused** response.  Unfortunately, irw does not seem to respond to the remote.

That may still be due to the fact that no /dev/lirc(x) is being created.  The syslogs are no longer showing lirc_init failures and as a bonus I am now even able to activate the lirc plugin in Totem.

On the other hand, when I test with irsend:
```
irsend -d /dev/lircd SEND_ONCE dish power_off
```
```
irsend: command failed: SEND_ONCE dish power_off
irsend: transmission failed
```

I assume this is related with the same problem observed with irw.


Following is my new hardware.conf which seems to have made the difference so far, so hopefully someone can guide me to the finish line.

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Remotes (new version Philips et al.)"
REMOTE_MODULES="lirc_dev lirc_mceusb2"
REMOTE_DRIVER=""
REMOTE_DEVICE=""
REMOTE_LIRCD_CONF="/etc/lirc/lircd.conf"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="USB-UIRT2 : Dish Receiver"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER="uirt2_raw"
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF="/etc/lirc/lircd.conf"
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
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""
```

Just to hedge my bets, I will activate the IRtrans software with the no_lirc option which allows it to co-exist with lircd.  The added advantage is that I can activate the LCDproc server as well.

From Syslog:
```
Apr 25 00:40:34 Jmyth lircd-0.8.3pre1[7582]: accepted new client on /dev/lircd
Apr 25 00:40:34 Jmyth lircd-0.8.3pre1[7582]: uirt2_raw: checksum error
Apr 25 00:40:35 Jmyth lircd-0.8.3pre1[7582]: uirt2_raw: UIRT version 0905 ok
Apr 25 00:40:35 Jmyth lircd-0.8.3pre1[7582]: uirt2_raw: UIRT version 0905
Apr 25 00:40:35 Jmyth lircd-0.8.3pre1[7582]: uirt2_send: remote not supported
Apr 25 00:40:35 Jmyth lircd-0.8.3pre1[7582]: error processing command: SEND_ONCE dish power_off
Apr 25 00:40:35 Jmyth lircd-0.8.3pre1[7582]: transmission failed
Apr 25 00:40:35 Jmyth lircd-0.8.3pre1[7582]: removed client
```

Thanks for your continued help.

---

### Post by jpm493 on 2008-04-25
hey karlec.  if you get lirc to recognize specific buttons pressed, an alternative to the blaster could be purchasing a nice remote.  i actually own a harmony 550, and i absolutely love it.  Unlike other universal remotes, this can be programmed for unique setups. 
if ya decide to go this route, the remote should be $50 bucks.  I got mine off amazon on sale.

---

### Post by karlec on 2008-04-25
> **jpm493 said:**
> hey karlec.  if you get lirc to recognize specific buttons pressed, an alternative to the blaster could be purchasing a nice remote.  i actually own a harmony 550, and i absolutely love it.  Unlike other universal remotes, this can be programmed for unique setups. 
if ya decide to go this route, the remote should be $50 bucks.  I got mine off amazon on sale.

Thanks JPM.  I actually own a Harmony 880 and I have been able to use it when I get the IRserver going.  But as I said my circumstances are a little different than yours and will require a different set of solutions (unfortunately).

---

### Post by karlec on 2008-04-26
OK.  Latest update.

After manually redoing my hardware conf I am now able to send signal to my dish and turn it on/off by using **irsend** :guitar:

Now the problem is that irw does not provide any feedback and I still cannot use the remote.  I feel so close yet so far!

Can someone help me get the remote to work.???

Again I cannot find a /dev/lirc(x) node being created so I would think that is where my problem is coming from.

---

### Post by Kheops_74 on 2008-04-27
I have the same problem. Here an answer on an other thread. 


Re: pvr-350 remote and irblaster
[http://ubuntuforums.org/showthread.php?t=742672](http://ubuntuforums.org/showthread.php?t=742672)

If you look at the release notes for 8.04, [http://www.mythbuntu.org/8.04/Release_notes](http://www.mythbuntu.org/8.04/Release_notes), under the lirc section you can see that the transmitter selection works except for the PVR-150. So their aware of the situation. I hope that their is a fix soon.

---

### Post by majoridiot on 2008-04-28
> **karlec said:**
> OK.  Latest update.

After manually redoing my hardware conf I am now able to send signal to my dish and turn it on/off by using **irsend** :guitar:

Now the problem is that irw does not provide any feedback and I still cannot use the remote.  I feel so close yet so far!

Can someone help me get the remote to work.???

Again I cannot find a /dev/lirc(x) node being created so I would think that is where my problem is coming from.

glad you are making progress!  since manual changes fixed at least part, please post your current
hardware.conf lircd.conf and .lircrc files.

is the MCE usb receiver still showing up with lspci?  do you see any errors related to it or lirc in your
system logs?

---

### Post by karlec on 2008-04-28
> **majoridiot said:**
> glad you are making progress!  since manual changes fixed at least part, please post your current
hardware.conf lircd.conf and .lircrc files.

is the MCE usb receiver still showing up with lspci?  do you see any errors related to it or lirc in your
system logs?

[COLOR="Red"]Warning!![/COLOR] to anyone following this thread, the actual files copied below are from a Windows PC (at work).  So copy and paste would not be a good idea, go the referenced threads (url) instead.

My current hardware.conf:
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Remotes (new version Philips et al.)"
REMOTE_MODULES="lirc_dev lirc_mceusb2"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="/etc/lirc/lircd.conf"
REMOTE_LIRCD_ARGS="-d /dev/lirc0 --output=/dev/lircd --listen"

#Chosen IR Transmitter
TRANSMITTER="USB-UIRT2 : Dish Receiver"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER="uirt2_raw"
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF="/etc/lirc/lircd.conf"
TRANSMITTER_LIRCD_ARGS="-d /dev/ttyUSB1 --output=/dev/lircd1 --connect=localhost:8765 --pidfile=/var/run/lircd2.pid"

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

I am using the lircd.conf from this posting:
[http://ubuntuforums.org/showthread.php?t=578787](http://ubuntuforums.org/showthread.php?t=578787)

```
name dish 
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

  frequency    40000 

      begin codes 
          power                    0x0000000000000800 
          0                        0x0000000000004400 
          1                        0x0000000000001000 
          2                        0x0000000000001400 
          3                        0x0000000000001800 
          4                        0x0000000000002000 
          5                        0x0000000000002400 
          6                        0x0000000000002800 
          7                        0x0000000000003000 
          8                        0x0000000000003400 
          9                        0x0000000000003800 
          up                       0x0000000000006800 
          cancel                   0x0000000000004800 
      end codes 
end remote
```

Since I seem to always have issues with the auto-generated lircrc (whether I use IRtrans or LIRC) I have used the lircrc posted on the following thread:
[http://ubuntuforums.org/showthread.php?t=304807](http://ubuntuforums.org/showthread.php?t=304807)

```
# ~/.mythtv/lircrc
#
# MythTV native LIRC config file for
# the grey&black Hauppauge remote
#
# By Hugo van der Kooij 2005/01/23
# Based on the one by Jarod Wilson, 2003/12/21
# Amalgamated from Jeff Campbell's,
# .lircrc, the mythtv.org docs, and
# a few touches of my own. :)
# 
#

# Channel Up
begin
prog = mythtv
button = CH+
#button = Channel-UP
repeat = 1
config = Up
end

# UP
begin
prog = mythtv
button = Up
repeat = 1
config = Up
end

# Channel Down
begin
prog = mythtv
button = CH-
#button = Channel-DOWN
repeat = 1
config = Down
end

# DOWN
begin
prog = mythtv
button = Down
repeat = 1
config = Down
end

# OK/Select
begin
prog = mythtv
button = OK
config = Space
end

# Play
begin
prog = mythtv
#button = Play
button = Play
config = Return
end

# Stop
begin
prog = mythtv
#button = STOP
button = Stop
config = Esc
end

# Escape/Exit/Back
begin
prog = mythtv
#button = BACK/EXIT
button = Back
config = Esc
end

# Power Off/Exit
begin
prog = mythtv
button = Power
config = Esc
end

# Red means stop!
begin
prog = mythtv
button = RED
#button = Red
config = Esc
end

# Pause
begin
prog = mythtv
button = Pause
repeat = 1
config = P
end

# Mute
begin
prog = mythtv
button = Mute
repeat = 1
config = F9
end

# LEFT
begin
prog = mythtv
button = Left
repeat = 1
config = Left
end

# RIGHT
begin
prog = mythtv
button = Right
repeat = 1
config = Right
end

# Fast forward (30 sec default)
begin
prog = mythtv
button = Rew
repeat = 1
config = Left
end

# Rewind (10 sec default)
begin
prog = mythtv
button = Fwd
repeat = 1
config = Right
end

# Skip forward (10 min default)
begin
prog = mythtv
button = Next
repeat = 1
config = PgDown
end

# Skip backward (10 min default)
begin
prog = mythtv
button = Previous
repeat = 1
config = PgUp
end

# Record
begin
prog = mythtv
button = Record
repeat = 1
config = R
end

# Delete
# begin
# prog = mythtv
# button = BLANK
# repeat = 1
# config = D
# end

# OSD browse
begin
prog = mythtv
#button = GREEN
button = DVDMenu
repeat = 1
config = O
end

# Display EPG while in live TV,
# View selected show while in EPG
begin
prog = mythtv
#button = MENU
button = Guide
repeat = 1
config = M
end

# Scroll up
begin
prog = mythtv
button = VOL+
repeat = 1
config = Right
end

# Scroll down
begin
prog = mythtv
button = VOL-
repeat = 1
config = Left
end

# Scroll up
begin
prog = mythtv
button = KnobCW
repeat = 1
config = Right
end

# Scroll down
begin
prog = mythtv
button = KnobCCW
repeat = 1
config = Left
end

# Bring up OSD info
begin
prog = mythtv
button = Info
repeat = 1
config = I
end

# Change display aspect ratio
begin
prog = mythtv
button = GREEN
repeat = 1
config = W
end

# Seek to previous commercial cut point
begin
prog = mythtv
button = YELLOW
repeat = 1
config = Q
end

# Seek to next commercial cut point
begin
prog = mythtv
button = BLUE
repeat = 1
config = Z
end

# Numbers 0-9

begin
prog = mythtv
button = 0
repeat = 1
config = 0
end

begin
prog = mythtv
button = 1
repeat = 1
config = 1
end

begin
prog = mythtv
button = 2
repeat = 1
config = 2
end

begin
prog = mythtv
button = 3
repeat = 1
config = 3
end

begin
prog = mythtv
button = 4
repeat = 1
config = 4
end

begin
prog = mythtv
button = 5
repeat = 1
config = 5
end

begin
prog = mythtv
button = 6
repeat = 1
config = 6
end

begin
prog = mythtv
button = 7
repeat = 1
config = 7
end

begin
prog = mythtv
button = 8
repeat = 1
config = 8
end

begin
prog = mythtv
button = 9
repeat = 1
config = 9
end


### MPlayer lirc setup

# Show OSD
begin
prog = mplayer
button = DVDMenu
repeat = 1
config = osd
end

# Pause playback
begin
prog = mplayer
button = Pause
repeat = 1
config = pause
end

# Skip ahead a minute if playing
# If paused, resume playing
begin
prog = mplayer
button = Play
repeat = 1
config = seek +1
end

# Stop playback and exit
begin
prog = mplayer
button = Stop
repeat = 1
config = quit
end

# Mute
begin
prog = mplayer
button = Mute
repeat = 1
config = mute
end

# Seek back 10 seconds
begin
prog = mplayer
button = Rew
repeat = 1
config = seek -10
end

# Seek forward 30 seconds
begin
prog = mplayer
button = Fwd
repeat = 1
config = seek +30
end

# Quit
begin
prog = mplayer
button = Back
repeat = 1
config = quit
end

# Seek forward 10 minutes
begin
prog = mplayer
button = Next
repeat = 1
config = seek +600
end

# Seek backward 10 minutes
begin
prog = mplayer
button = Previous
repeat = 1
config = seek -600
end

# Toggle full-screen
begin
prog = mplayer
button = GREEN
repeat = 1
config = vo_fullscreen
end

### Xine lirc setup

begin
prog = xine
button = Play
repeat = 1
config = Play
end

begin
prog = xine
button = Stop
repeat = 1
config = Stop
end

begin
prog = xine
button = Power
repeat = 1
config = Quit
end

begin
prog = xine
button = Pause
repeat = 1
config = Pause
end

begin
prog = xine
button = CH+
repeat = 1
config = EventUp
end

begin
prog = xine
button = CH-
repeat = 1
config = EventDown
end

begin
prog = xine
button = VOL-
repeat = 1
config = EventLeft
end

begin
prog = xine
button = VOL+
repeat = 1
config = EventRight
end

begin
prog = xine
button = OK
repeat = 1
config = EventSelect
end

begin
prog = xine
button = Back
repeat = 1
config = Menu
end

begin
prog = xine
button = Fwd
repeat = 1
config = SpeedFaster
end

begin
prog = xine
button = Rew
repeat = 1
config = SpeedSlower
end

begin
prog = xine
button = VOL+
repeat = 1
config = Volume+
end

begin
prog = xine
button = VOL-
repeat = 1
config = Volume-
end

begin
prog = xine
button = Mute
repeat = 1
config = Mute
end

begin
prog = xine
button = DVDMenu
repeat = 1
config = RootMenu
end

begin
prog = xine
button = Next
repeat = 1
config = EventNext
end

begin
prog = xine
button = Previous
repeat = 1
config = EventPrior
end

begin
prog = xine
button = Info
repeat = 1
config = OSDStreamInfos
end

# begin
# prog = xine
# button = RED
# repeat = 1
# config = Quit
# end

# begin
# prog = xine
# button = RED
# repeat = 1
# config = Quit
# end


```

Now after my changes on the remote section of hardware.conf, my system.log is reporting the following error message:
```
could not open config file REMOTE_LIRCD_ARGS
No such file or directory
...
could not get file information for /dev/lirc
```

---

### Post by majoridiot on 2008-04-29
> **karlec said:**
> I am using the lircd.conf from this posting:
[http://ubuntuforums.org/showthread.php?t=578787](http://ubuntuforums.org/showthread.php?t=578787)

```
name dish 
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

  frequency    40000 

      begin codes 
          power                    0x0000000000000800 
          0                        0x0000000000004400 
          1                        0x0000000000001000 
          2                        0x0000000000001400 
          3                        0x0000000000001800 
          4                        0x0000000000002000 
          5                        0x0000000000002400 
          6                        0x0000000000002800 
          7                        0x0000000000003000 
          8                        0x0000000000003400 
          9                        0x0000000000003800 
          up                       0x0000000000006800 
          cancel                   0x0000000000004800 
      end codes 
end remote
```

there's no remote definition in your lircd.conf... just for the transmitter.  you need to add in your
remote as well.  i'm not at home to check mine, but this one seems sane for that remote.  you may
need a different one, as there are different version of the mce remotes... but i'd see what this one
gets you.  add it to your lircd.conf before the transmitter:

```
################################################################################
# lircd.conf file for the new Microsoft Media Center remote using a new
# Microsoft Media Center receiver.
################################################################################
begin remote

  name mceusb2
  bits           16
  flags RC6|CONST_LENGTH
  eps            30
  aeps          100

  header       2667   889
  one           444   444
  zero          444   444
  pre_data_bits 21
  pre_data      0x37FF0
  gap          105000
  toggle_bit     22
  rc6_mask     0x100000000


      begin codes

# starts at A1
        KEY_BLUE         0x00007BA1
        KEY_YELLOW       0x00007BA2
        KEY_GREEN        0x00007BA3
        KEY_RED          0x00007BA4
        KEY_TELETEXT     0x00007BA5
        KEY_RADIO        0x00007BAF
        KEY_PRINT        0x00007BB1
        KEY_VIDEO        0x00007BB5 # VIDEOS button
        KEY_IMAGE        0x00007BB6 # PICTURES button
        KEY_PVR          0x00007BB7 # RECORDED TV button
        KEY_AUDIO        0x00007BB8 # MUSIC button
        KEY_TV           0x00007BB9
# no BA - D8
        KEY_GUIDE        0x00007BD9
        KEY_TV           0x00007BDA # LIVE TV button
        KEY_DVD          0x00007BDB
        KEY_BACK         0x00007BDC
        KEY_OK           0x00007BDD
        KEY_RIGHT        0x00007BDE
        KEY_LEFT         0x00007BDF
        KEY_DOWN         0x00007BE0
        KEY_UP           0x00007BE1
        STAR             0x00007BE2
        HASH             0x00007BE3
        KEY_PREVIOUS     0x00007BE4 # REPLAY button
        KEY_NEXT         0x00007BE5 # SKIP button
        KEY_STOP         0x00007BE6
        KEY_PAUSE        0x00007BE7
        KEY_RECORD       0x00007BE8
        KEY_PLAY         0x00007BE9
        KEY_REWIND       0x00007BEA
        KEY_FORWARD      0x00007BEB
        KEY_CHANNELDOWN  0x00007BEC
        KEY_CHANNELUP    0x00007BED
        KEY_VOLUMEDOWN   0x00007BEE
        KEY_VOLUMEUP     0x00007BEF
        KEY_INFO         0x00007BF0 # MORE (i) button
        KEY_MUTE         0x00007BF1
        KEY_MENU         0x00007BF2 # START (Windows) button
        KEY_POWER        0x00007BF3
        KEY_ENTER        0x00007BF4
        KEY_CLEAR        0x00007BF5
        KEY_9            0x00007BF6
        KEY_8            0x00007BF7
        KEY_7            0x00007BF8
        KEY_6            0x00007BF9
        KEY_5            0x00007BFA
        KEY_4            0x00007BFB
        KEY_3            0x00007BFC
        KEY_2            0x00007BFD
        KEY_1            0x00007BFE
        KEY_0            0x00007BFF
      end codes

end remote
```

---

### Post by karlec on 2008-04-29
> **majoridiot said:**
> there's no remote definition in your lircd.conf... just for the transmitter.  you need to add in your
remote as well.  i'm not at home to check mine, but this one seems sane for that remote.  you may
need a different one, as there are different version of the mce remotes... but i'd see what this one
gets you.  add it to your lircd.conf before the transmitter:

```
################################################################################
# lircd.conf file for the new Microsoft Media Center remote using a new
# Microsoft Media Center receiver.
################################################################################
begin remote

  name mceusb2
  bits           16
  flags RC6|CONST_LENGTH
  eps            30
  aeps          100

  header       2667   889
  one           444   444
  zero          444   444
  pre_data_bits 21
  pre_data      0x37FF0
  gap          105000
  toggle_bit     22
  rc6_mask     0x100000000


      begin codes

# starts at A1
        KEY_BLUE         0x00007BA1
        KEY_YELLOW       0x00007BA2
        KEY_GREEN        0x00007BA3
        KEY_RED          0x00007BA4
        KEY_TELETEXT     0x00007BA5
        KEY_RADIO        0x00007BAF
        KEY_PRINT        0x00007BB1
        KEY_VIDEO        0x00007BB5 # VIDEOS button
        KEY_IMAGE        0x00007BB6 # PICTURES button
        KEY_PVR          0x00007BB7 # RECORDED TV button
        KEY_AUDIO        0x00007BB8 # MUSIC button
        KEY_TV           0x00007BB9
# no BA - D8
        KEY_GUIDE        0x00007BD9
        KEY_TV           0x00007BDA # LIVE TV button
        KEY_DVD          0x00007BDB
        KEY_BACK         0x00007BDC
        KEY_OK           0x00007BDD
        KEY_RIGHT        0x00007BDE
        KEY_LEFT         0x00007BDF
        KEY_DOWN         0x00007BE0
        KEY_UP           0x00007BE1
        STAR             0x00007BE2
        HASH             0x00007BE3
        KEY_PREVIOUS     0x00007BE4 # REPLAY button
        KEY_NEXT         0x00007BE5 # SKIP button
        KEY_STOP         0x00007BE6
        KEY_PAUSE        0x00007BE7
        KEY_RECORD       0x00007BE8
        KEY_PLAY         0x00007BE9
        KEY_REWIND       0x00007BEA
        KEY_FORWARD      0x00007BEB
        KEY_CHANNELDOWN  0x00007BEC
        KEY_CHANNELUP    0x00007BED
        KEY_VOLUMEDOWN   0x00007BEE
        KEY_VOLUMEUP     0x00007BEF
        KEY_INFO         0x00007BF0 # MORE (i) button
        KEY_MUTE         0x00007BF1
        KEY_MENU         0x00007BF2 # START (Windows) button
        KEY_POWER        0x00007BF3
        KEY_ENTER        0x00007BF4
        KEY_CLEAR        0x00007BF5
        KEY_9            0x00007BF6
        KEY_8            0x00007BF7
        KEY_7            0x00007BF8
        KEY_6            0x00007BF9
        KEY_5            0x00007BFA
        KEY_4            0x00007BFB
        KEY_3            0x00007BFC
        KEY_2            0x00007BFD
        KEY_1            0x00007BFE
        KEY_0            0x00007BFF
      end codes

end remote
```

In addition to the transmitter lircd.conf posted above, I am actually using the same as what you have posted and it was auto-generated by Mythbuntu.  The include link in my hardware.conf is for mceusb/lirc.mceusb.conf.
Now when I use the **--connect=localhost:8765** option in the transmitter section, lirc throws an error and does not start.  In additionm regardless of whatever change I make in the remote section I'm still getting the **could not get file information for /dev/lirc0** error message in the logs and irw is simply not working (no feedback).  At various point I have seen a /dev/lirc being created but even then irw does not respond.

---

### Post by karlec on 2008-05-01
This is extremely disappointing ](*,).  I would surely expect that one of the experienced users would have 'guided' me towards a solution by now.  I have been posting on this for weeks now, and I have not been able to completely get past this one issue.
I have tried almost every recommended course but sadly no cigar.  I am now left with a 'crippled' install and a not too happy fiancee, as I have been spending so much time trying to figure this out.  
I don't consider that the time that I've spent so far as being wasted, considering I started this journey as total newbie to linux in general and that now I can find my way around.  Albeit by tripping over my own feet sometimes (:), OK most of the times).  So many people seem to be having problems with LIRC that there should probably be a sub-forum to deal with just that...

Anyway, my current status: [LIST]
[*]The IR receiver side is still not working.
[*]The transmitter is somewhat working, as I am able to actually change channels (feels very slow) while I am watching TV.  Of course I am using my attached keyboard. :(
[*]My PVR500 is "dual tuning".  Since I have a dish vip622, I set it to dual mode and now I have two separate signals going into the card.
[*]My HVR-1800 is somewhat working.  I can't get a lot of ATSC channels on it so far, maybe 3 or 4.  I kind of expected better perfpormance on it with an amplified radioshack antenna but that is not the case.  I am not using the analog side.
[/LIST]

Why am I stuck??  Somehow LIRC is not automatically creating the needed device nodes (/dev/lirc[0...n].  So no **irw** or any of the LIRC 'tools' is working except for irsend (I have not tried irexec).  Tried to manually create the nodes

```
mknod /dev/lirc c 61 0
```
```
mknod /dev/lirc1 c 61 1
```

when I try to test with
```
irw /dev/lircd1
```
The user prompt comes back immediately.  The system logs return the following message:
```
lircd(userspace) ready
lircd(userspace) ready
accepted new client on /dev/lircd1
could not open /dev/lirc1
default_init(): No such device
caught signal 
```

when I try
```
irw /dev/lircd
```
There is no feedback returned on the console and the logs show the following:

```
lircd(userspace) ready
lircd(userspace) ready
accepted new client on /dev/lircd
uirt2_raw: checksum error
uirt2_raw: UIRT version 0905 ok
```

My current hardware.conf:
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Remotes (new version Philips et al.)"
REMOTE_MODULES="lirc_dev lirc_mceusb2"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc1"
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS="--output=/dev/lircd1 --pidfile=/var/run/lircd1.pid  --listen=8765"

#Chosen IR Transmitter
TRANSMITTER="USB-UIRT2 : Dish Receiver"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER="uirt2_raw"
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF="dish/general.conf"
TRANSMITTER_LIRCD_ARGS="-d /dev/ttyUSB0 --output=/dev/lircd --pidfile=/var/run/lircd.pid"

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

My lirc.conf.mceusb

```
#
# RC-6 config file
#
# source: http://home.hccnet.nl/m.majoor/projects__remote_control.htm
#         http://home.hccnet.nl/m.majoor/pronto.pdf
#
# used by: Philips
#
#########
#
# Philips Media Center Edition remote control
# For use with the USB MCE ir receiver
#
# Dan Conti  dconti|acm.wwu.edu
#
# Updated with codes for MCE 2005 Remote additional buttons
# *, #, Teletext, Red, Green, Yellow & Blue Buttons
# Note: TV power button transmits no code until programmed.
# Updated 12th September 2005
# Graham Auld - mce|graham.auld.me.uk
#
# Radio, Print, RecTV are only available on the HP Media Center remote control
#

begin remote

  name mceusb
  bits           16
  flags RC6|CONST_LENGTH
  eps            30
  aeps          100

  header       2667   889
  one           444   444
  zero          444   444
  pre_data_bits 21
  pre_data      0x37FF0
  gap          105000
  toggle_bit     22
  rc6_mask     0x100000000


      begin codes

	Blue	0x00007ba1
	Yellow	0x00007ba2
	Green	0x00007ba3
	Red	0x00007ba4
	Teletext	0x00007ba5

# starts at af
        Radio    0x00007baf
        Print    0x00007bb1
        Videos   0x00007bb5
        Pictures 0x00007bb6
        RecTV    0x00007bb7
        Music    0x00007bb8
        TV       0x00007bb9
# no ba - d8

        Guide    0x00007bd9
        LiveTV   0x00007bda
        DVD      0x00007bdb
        Back     0x00007bdc
        OK       0x00007bdd
        Right    0x00007bde
        Left     0x00007bdf
        Down     0x00007be0
        Up       0x00007be1

        Star       0x00007be2
        Hash       0x00007be3

        Replay   0x00007be4
        Skip     0x00007be5
        Stop     0x00007be6
        Pause    0x00007be7
        Record   0x00007be8
        Play     0x00007be9
        Rewind   0x00007bea
        Forward  0x00007beb
        ChanDown 0x00007bec
        ChanUp   0x00007bed
        VolDown  0x00007bee
        VolUp    0x00007bef
        More     0x00007bf0
        Mute     0x00007bf1
        Home     0x00007bf2
        Power    0x00007bf3
        Enter    0x00007bf4
        Clear    0x00007bf5
        Nine     0x00007bf6
        Eight    0x00007bf7
        Seven    0x00007bf8
        Six      0x00007bf9
        Five     0x00007bfa
        Four     0x00007bfb
        Three    0x00007bfc
        Two      0x00007bfd
        One      0x00007bfe
        Zero     0x00007bff
      end codes

end remote
```



My conf file for the dish/transmitter

```
### Started with Remote definition from SolarBaby's post complemented by LIRC site's conf file.
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

  name dish 
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

  frequency    40000 

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

my lircrc file

```
# LIRCRC Auto Generated by Mythbuntu Lirc Generator
# Author(s): Mario Limonciello, Nick Fox
# Created for use with Mythbuntu
# Modified by Me to remove the remote lines and various dish remotes

begin
    prog = mythtv
    button = 7
    config = 7
    repeat = 0
    delay = 0
end

begin
    prog = mythtv
    button = right
    config = Right
    repeat = 0
    delay = 0
end

begin
    prog = mythtv
    button = 1
    config = 1
    repeat = 0
    delay = 0
end

begin
    prog = mythtv
    button = down
    config = Down
    repeat = 0
    delay = 0
end

begin
    prog = mythtv
    button = 0
    config = 0
    repeat = 0
    delay = 0
end

begin
    prog = mythtv
    button = pause
    config = P
    repeat = 0
    delay = 0
end

begin
    prog = mythtv
    button = menu
    config = M
    repeat = 0
    delay = 0
end

begin
    prog = mythtv
    button = 6
    config = 6
    repeat = 0
    delay = 0
end

begin
    prog = mythtv
    button = 2
    config = 2
    repeat = 0
    delay = 0
end

begin
    prog = mythtv
    button = cancel
    config = Escape
    repeat = 0
    delay = 0
end

begin
    prog = mythtv
    button = 5
    config = 5
    repeat = 0
    delay = 0
end

begin
    prog = mythtv
    button = info
    config = I
    repeat = 0
    delay = 0
end

begin
    prog = mythtv
    button = 4
    config = 4
    repeat = 0
    delay = 0
end

begin
    prog = mythtv
    button = up
    config = Up
    repeat = 0
    delay = 0
end

begin
    prog = mythtv
    button = recall
    config = R
    repeat = 0
    delay = 0
end

begin
    prog = mythtv
    button = 9
    config = 9
    repeat = 0
    delay = 0
end

begin
    prog = mythtv
    button = 3
    config = 3
    repeat = 0
    delay = 0
end

begin
    prog = mythtv
    button = 8
    config = 8
    repeat = 0
    delay = 0
end

begin
    prog = mythtv
    button = guide
    config = S
    repeat = 0
    delay = 0
end

begin
    prog = mythtv
    button = left
    config = Left
    repeat = 0
    delay = 0
end

```

Seems like all the files are ok to me, and short of unplugging/re-plugging the IR receiver from my MB, I feel like I've tried almost everything.  

What is missing???  :confused: 
What am I doing wrong???? :confused:

---

### Post by Captain_Bodge on 2008-06-06
Stumbled across this thread by Googling because I'm having similar issues. I've not got the same card, but I have an HVR-1100 and had the same lirc problem. 
Your comment right near the start that you weren't getting the right nodes in /dev gave me the flash of inspiration I needed. I've discovered with my card that no /dev/lirc* is created because.. it isn't supposed to be. This card uses /dev/input/event* instead. I wonder if yours does the same? 

Try '[FONT="Courier New"]cat /proc/bus/input/devices[/FONT]'. 
One of my devices is this:
[FONT="Courier New"]I: Bus=0018 Vendor=0000 Product=0000 Version=0000
N: Name="HVR 1110"
P: Phys=i2c-1/1-0071/ir0
S: Sysfs=/devices/virtual/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: EV=100003
B: KEY=100fc312 214a802 0 0 0 0 18000 41a8 4801 9e1680 0 0 10000ffc[/FONT]

So I can see it's event6.

So my hardware.conf looks like this:

[FONT="Courier New"]
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Hauppauge HVR-1100"
REMOTE_MODULES="lirc_dev lirc_i2c"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/input/event6"
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS="-H dev/input -d /dev/input/event6 -n"

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
[/FONT]

Clearly yours won't be quite the same, but it's the REMOTE_DEVICE and REMOTE_LIRCD_ARGS that were the thing I had to change. Everything else was fine out of the box on mythbuntu 8.04. Now when I run irw and push buttons I get things like 

[FONT="Courier New"]0000000080010067 00 Up HVR-1100
000000008001006c 00 Down HVR-1100
0000000080010192 00 Chan+ HVR-1100
0000000080010192 00 Chan+ HVR-1100
0000000080010192 00 Chan+ HVR-1100[/FONT]

I hope this helps, because I feel your pain...

---

