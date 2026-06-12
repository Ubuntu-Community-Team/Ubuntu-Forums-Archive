---
title: "Another Remote Question/Issue lirc_imon/mceusb2 ir transmit problems"
date: 2009-02-19
forum: Mythbuntu
---

### Post by rodercot on 2009-02-19
Hey guys,

 So in my slave backend/frontend I swapped the case to a Fusion Black 430 with the imon_pad vfd/ir.

 it is the ffdc device in lsusb not the 0038 device and it is the LCD.

 so here is my issue. I unplugged my M$ 1039 USB Dongle and rebooted I set remotes and transmitters to none in control centre opened up the ubuntu backport source and updated to Lirc 0.8.4a. then I proceeded to setup the ir/vfd in the case lcdproc 0.5.2 with the v3 patch that is common on here and around the web. OK then got the ir working with the mce remote (not the dongle but through the ir in the case oh and with this setup I have a ls -l /dev/lirc* of /dev/lirc0 and the lsmod | grep lirc show that lirc_imon is loaded

 All great - NOW the issue plug in my M$ Dongle to be able to transmit. myth loads the modules on probing no input from me
 ls -l /dev/lirc* is now /dev/lirc0, /dev/lirc1, dev/lircd
 
 The remote portion of my hardware config is loading lirc_dev and lirc_imon with soundgraph ir/vfd as the remote name and /dev/lirc0 as the device now I set the transmiitter up manually by entering 

 M$ V2 : dish control as the transmitter name and lirc_dev lirc_mceusb2 as the modules and /dev/lirc1 as the device and no arguments. 
 
 now as ls -l /dev/lirc* shows /dev/lirc0, /dev/lirc1, /dev/lircd, /dev/lircd1 and lsmod | grep lirc show both modules loaded lirc_imon and lirc_mcesusb2
 
 I have no transmit and every time I reboot /dev/lirc0 and /dev/lirc1 are flipped and I do mean everytime I reboot. 

 So I setup some udev rules symlinking the devices to lirc_imon and lirc_mce and still the same issue.

 Is there a guide for setting up these two devices to work together that is descriptive on setting up the lircd args and how to properly edit the /etc/init.d/script those are the only two things I have not tried yet.

 I have read many post and threads on adding options to init.d/lirc and lircd(which I do not have in my /etc/init.d directory). I am about ready to just unplug this piece o crap vfd and just go back to my M$ remote by itself.

 rgds,

 Dave

---

### Post by rodercot on 2009-02-20
Does anyone have any ideas with this problem? I have been all over the web for a solution. I can either make the ir/lcd work perfectly ALONE or I can unplug that and make the M$ 1039 Remote work perfectly and TRANSMIT - But I cannot make the two work together. 

 All I want is for the imon ir/lcd to receive the commands and the mceusb2 to to transmit the channel changes to the stb. Does no one have a working solution. 

 Thanks,
 
 Dave

---

### Post by rodercot on 2009-02-21
**This fix will only work in 8.10, if you want to set this up in Karmic or Mythbuntu 9.10 see post 11 in this thread.**


Ok Guys I think I have this licked now. What a pile of playing around. 

 Firstly I have collected more than 50 different links to many different sites over the last few days looking for clues to this issue but finally this morning I found this link 

[http://www.eggshellskull.com/lirc/blaster/index.php](http://www.eggshellskull.com/lirc/blaster/index.php)

 and I want to say a BIG BIG thanks to those guys for posting that info in a clean concise manner. I would hate to be totally green at this and try to figure it all out. there is so much conflicting info on the web and revisions of different files although they are all trying to reach a common goal ofcourse :D.

 OK the fix..,

 I have now got this working I believe and WELL!! I cannot believe it either, it has taken me several days and lotso COFFEE - LOL.

  I did not need to recompile lirc several times as the modules for lirc_imon and lirc_mceusb2 are in 0.8.4a to begin with. I did not have to edit the lirc script in init.d at all. I already had lcdproc running with the patches and it was working fine so I just unplugged it until I had the M$ remote and transmitter working correctly. 

 I hooked up my M$ remote usb dongle and got all that working via myth's control panel first - this loaded up my lircrc with the mce remote commands so I would not have to do it later and it also set up the transmitter so it worked. I already had a channel change script I made prior that worked with my dish receiver. Then I shut down and hooked the lcd back up and booted up. LCDd loaded up just fine.

 now i went into /etc/lirc and renamed my hardware and lircd conf files to h and l.conf then I edited the hardware.conf file leaving the transmitter section alone i changed the remote section to 

 remote name = custom
 modules = lirc_dev lirc_imon
 device = /dev/lirc0
 lircd = /etc/lircd.conf

 transmitter was 

 name = mceusb : dish
 modules = lirc_dev lirc_mceusb2
 device = /dev/lirc1
 lircd = ""

 then I went into /etc/rc.local and edited to add (i have no /etc/rc.d/rc.local) so I used /etc.rc.local instead and ran sudo chmod a+x on it. 

 ```
 /sbin/modprobe lirc_mceusb2 
 /sbin/modprobe lirc_imon 
 /usr/sbin/lircd --device=/dev/lirc0 --output=/dev/lircd 
 /usr/sbin/lircd --driver=default --device=/dev/lirc1 --output=/dev/lircd1 --pidfile=/var/run/lircd1.pid 
```
 
  ***a note about this as well I had no /dev/lircd1 at first after making the changes and then I finally added the /dev/lirc1 device to the transmitter section in hardware.conf and restarted lirc and voila!! I had a lircd1.***

 Then I opened up /etc/modprobe.d/aliases and placed this directly at the top of the script after the last # and before the first command in the file

 ```
alias char-major-61-0 lirc_imon
 alias char-major-61-1 lirc_mceusb2
```
 
 ***note the 0 and the 1 in the lines - I believe with this I am forcing these now to use lirc 0 for imon and lirc 1 for mceusb2 upon booting (I assume this would be the same as creating a udev rule for symlinking the devices)*** I initially had created /etc/modprobe.conf and entered these lines in that file but when I issued a shutdown via the remote and powered back on they seemed to be reversed ie lirc0 was lirc1 and vice versa, so I deleted that file and addded the line to the alias file and have rebooted serveral times now off the remote and every time it works (BIG SMILES_HEHEHE!!!)

 And finally the last bit to all this because now when I issue a ls -l /dev/lirc* I have 

 /dev/lirc0
 /dev/lirc1
 /dev/lircd
 /dev/lircd1 

 So I had to edit my /usr/local/bin/channel-change-lirc.pl script changing lircd to lircd1 in all the irsend commands and then it started to transmit fine from the mce dongle when I issued irsend --device=/dev/lircd1 SEND_ONCE dish 1 2 3 4 

 (a note about this I had to join all my lircd files together as one so now I have in that file the mceusb & volume knob definitions for the ir receiever in the antec case and then the mceusb definititons that worked with the M$ dongle so they still function with my lircrc file in myth and finally my dish/express vu receiver definitions. This file is now saved in /etc/lirc as lircd.conf.  

 Regards,

Dave

---

### Post by rodercot on 2009-02-21
continued.. I am attaching the files I used for my config. These are compilations of files I have found around the web or the lirc included defaults, I cannot recall all the people whose sites I have browsed over the past few days so I will just say Thank You to all. 

 Dave

The files:

 **channel-change-lirc.pl **(if you copy this make sure and chmod it first before using.)  

```
REMOTE_NAME=dish
irsend --device=/dev/lircd1 SEND_ONCE $REMOTE_NAME select
sleep 0.5
for digit in $(echo $1 | sed -e 's/./& /g'); do
irsend --device=/dev/lircd1 SEND_ONCE $REMOTE_NAME $digit
sleep 0.5
done
# irsend --device=/dev/lircd1 SEND_ONCE $REMOTE_NAME select 
```

 **hardware.conf**
 
 ```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="custom"
REMOTE_MODULES="lirc_dev lirc_imon"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="etc/lircd.conf"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Microsoft Windows Media Center V2 (usb) : Dish Receiver"
TRANSMITTER_MODULES="lirc_dev lirc_mceusb2"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc1"
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

 **lircd.conf** this includes the volume knob codes as well.

 ```
#
# brand:                        HP 
# model no. of remote control:  TSGH-IR01
# devices being controlled by this remote: HP Slimline S3100y
#
# Derived from MCEUSB2 lircd.conf file (lircd.conf.mceusb) found at:
# https://help.ubuntu.com/community/Install_Lirc_Feisty

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
#
# Updated with codes for MCE 2007 Remote additional buttons
# Visualization, Aspect, SlideShow, Eject
# Note: 
# Renamed some buttons: DVD->DVDMenu, More->MoreInfo, Star->Asterisk, Hash->Pound
# Note: 
# Blue, Yellow, Green, Red, and Teletext buttons do not exist on the HP remote
#
# /etc/lirc/lircd.conf for MCE Remote with IMON LCD IR:
#
#Configuration for MCE Remote using the Soundgraph iMON IR/LCD:
begin remote

  name         mceusb
  bits         32
  eps          30
  aeps        100

  one             0     0
  zero            0     0
  gap         203992
  toggle_bit_mask 0x8000

      begin codes
          Power                0x800F040C
          TV_power             0x800F0465
          Home                 0x800F040D
          Guide                0x800F0426
          LiveTV               0x800F0425
          DVD                  0x800F0424
          Teletext             0x800F045A
          RecordTV             0x800F0448
          Back                 0x800F0423
          Forward              0x800F0414
          Stop                 0x800F0419
          Replay               0x800F041B
          Skip                 0x800F041A
          Play                 0x800F0416
          Record               0x800F0417
          Rewind               0x800F0415
          Pause                0x800F0418
          More                 0x800F040F
          Left                 0x800F0420
          Right                0x800F0421
          Up                   0x800F041E
          Down                 0x800F041F
          OK                   0x800F0422
          Chan_Down            0x800F0413
          Chan_Up              0x800F0412
          Vol_Down             0x800F0411
          Vol_Up               0x800F0410
          Mute                 0x800F040E
          1                    0x800F0401
          2                    0x800F0402
          3                    0x800F0403
          4                    0x800F0404
          5                    0x800F0405
          6                    0x800F0406
          7                    0x800F0407
          8                    0x800F0408
          9                    0x800F0409
          Zero                 0x800F0400
          *                    0x800F041D
          Clear                0x800F040A
          #                    0x800F041C
          Enter                0x800F040B
          Red                  0x800F045B
          Green                0x800F045C
          Yellow               0x800F045D
          Blue                 0x800F045E
          Antec_knob_left      0x01000000
          Antec_knob_right     0x00010000
      end codes

end remote


begin remote

  name        mceusb
  bits                 16
  flags  RC6|CONST_LENGTH
  eps                  30
  aeps                100

  header       2667   889
  one           444   444
  zero          444   444
  pre_data_bits        21
  pre_data        0x37FF0
  gap              105000
  toggle_bit           22
  rc6_mask    0x100000000


      begin codes

#unused by HP remote
	Blue	      0x00007ba1
	Yellow	      0x00007ba2
	Green	      0x00007ba3
	Red	      0x00007ba4
	Teletext      0x00007ba5

#ba6 - bae unused 
        BA6           0x00007ba6
        BA7           0x00007ba7
        BA8           0x00007ba8
        BA9           0x00007ba9
        BAA           0x00007baa
        BAB           0x00007bab
        BAC           0x00007bac
        BAD           0x00007bad
        BAE           0x00007bae

        Radio         0x00007baf
        Print         0x00007bb1

#bb2 - bb4 unused  
        BB2           0x00007bb2
        BB3           0x00007bb3
        BB4           0x00007bb4

        Videos        0x00007bb5
        Pictures      0x00007bb6
        RecTV         0x00007bb7
        Music         0x00007bb8
        TV            0x00007bb9

#bba - bbf unused 
        BBA           0x00007bba
        BBB           0x00007bbb
        BBC           0x00007bbc
        BBD           0x00007bbd
        BBE           0x00007bbe
        BBF           0x00007bbf
#bc1 - bca unused 
        BC1           0x00007bc1
        BC2           0x00007bc2
        BC3           0x00007bc3
        BC4           0x00007bc4
        BC5           0x00007bc5
        BC6           0x00007bc6
        BC7           0x00007bc7
        BC8           0x00007bc8
        BC9           0x00007bc9
        BCA           0x00007bca

        Eject         0x00007bcb
        SlideShow     0x00007bcc
        Visualization 0x00007bcd

#bce - bcf unused 
        BCE           0x00007bce
        BCF           0x00007bcf
#bd1 - bd7 unused 
        BD1           0x00007bd1
        BD2           0x00007bd2
        BD3           0x00007bd3
        BD4           0x00007bd4
        BD5           0x00007bd5
        BD6           0x00007bd6
        BD7           0x00007bd7

        Aspect        0x00007bd8
        Guide         0x00007bd9
        LiveTV        0x00007bda
        DVD           0x00007bdb
#NoGap
        Back          0x00007bdc
        OK            0x00007bdd
        Right         0x00007bde
        Left          0x00007bdf
        Down          0x00007be0
        Up            0x00007be1
#NoGap
        Star          0x00007be2
        Hash          0x00007be3
#NoGap
        Replay        0x00007be4
        Skip          0x00007be5
        Stop          0x00007be6
        Pause         0x00007be7
        Record        0x00007be8
        Play          0x00007be9
        Rewind        0x00007bea
        Forward       0x00007beb
#NoGap
        ChanDown      0x00007bec
        ChanUp        0x00007bed
        VolDown       0x00007bee
        VolUp         0x00007bef
#NoGap
        More          0x00007bf0
        Mute          0x00007bf1
        Home          0x00007bf2
        Power         0x00007bf3
#NoGap
        Enter         0x00007bf4
        Clear         0x00007bf5
#NoGap
        Nine          0x00007bf6
        Eight         0x00007bf7
        Seven         0x00007bf8
        Six           0x00007bf9
        Five          0x00007bfa
        Four          0x00007bfb
        Three         0x00007bfc
        Two           0x00007bfd
        One           0x00007bfe
        Zero          0x00007bff
      end codes

end remote

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


 Have Fun

 Dave

---

### Post by rodercot on 2009-02-21
One more thing I am not sure how to mark this post as solved in the title so if a moderator could do it please or tell me how and I will take care of it. I marked the first post in here as solved.

 Thanks,

 Dave

---

### Post by Hackit on 2009-02-26
Hi Rodercot,

Well I did get my lcd working, and I have a question for you.

I'm using the ir in the fusion case and my cable is plugged into my hauppauge card. I'm not using a dongle yet.

So will your steps work for my setup?

---

### Post by rodercot on 2009-02-26
> **Hackit said:**
> Hi Rodercot,

Well I did get my lcd working, and I have a question for you.

I'm using the ir in the fusion case and my cable is plugged into my hauppauge card. I'm not using a dongle yet.

So will your steps work for my setup?

 Hackit,

 OK I am confused, I understood you were using the mce remote kit from your previous posts. If this is the pvr-150 and the ir blaster plugs into the pvr-150 then know this setup is not for you. 

 Please detail exactly what you are trying to accomplish so we can get you started in the right direction. post a pic of your actual pvr-150 setup you are using. 

 rgds,

 Dave

---

### Post by Hackit on 2009-02-27
> **rodercot said:**
> Hackit,

 OK I am confused, I understood you were using the mce remote kit from your previous posts. If this is the pvr-150 and the ir blaster plugs into the pvr-150 then know this setup is not for you. 

 Please detail exactly what you are trying to accomplish so we can get you started in the right direction. post a pic of your actual pvr-150 setup you are using. 

 rgds,

 Dave

Ok I'll try my best to explain,

Here are my specs:
Corsair XMS2 TWIN2X2048-6400C4DHX Matched Pairs 2GB Kit.

Thermaltake CL-P0369 Max Orb CPU Cooler.

Antec LifeStyle Fusion Desktop mATX Case 430W ATX12V Black VFD Volume Control.

Seagate Barracuda (ST3500320NS) ES.2 SATA 3.0Gb/s 500GB Hard Drive x 3

Asus P5E-VM HDMI Socket 775 Intel G35 + ICH9R Chipset Dual-Channel DDR2 /800/667/533Mhz Intergrated Intel GMA X3500 with HDMI Support 8-Channel High Definition Audio Gigabit Lan Firewire 6x SATA 3.0Gb/s PCI-Express x16 Support Micro ATX.

Intel Core 2 Duo Socket LGA775, 2.2 GHz.

ASUS DRW-2014L1T SATA LightScribe Black 20X DVD-Writer 20xDVD+R/-R.

I'm not using the built in video and have upgraded the video to Nvidia 8600-gts - 512 mb.

Tuner is a WinTV-HVR-1800.

I'll explain how it was working in vista mce,

I live in canada and have cogeco ( not HD), I'm not using the cable box from cogeco and have the cable plugged into the wintv-hvr 1800 tuner. In vista it worked perfectly.

So i have my logitech remote setup as media center edition and with the ir receiver in the antec fusion case it controlled the channels.

I hope this helps.

---

### Post by rodercot on 2009-02-27
OK Fine, then you have the all black vista remote and the SMK USB Dongle that came with the 1800. 

 Yes then you can follow my guide to setup your remote. As for the 1800 card and cable, So is that then digital cable into the 1800 card as it was my understanding the analog side of that card does not currently work in Linux (yet) I have not read through the whole 1800 thread so maybe I am wrong about this part. 

 Your remote with the dongle your logitech should work just fine, It would be a good idea to get the logitech remote working through the IR in the case first and then setup the dongle as the guide explains.

 rgds,

 Dave

---

### Post by Hackit on 2009-02-28
Hi rodercot,

I appreciate all your help, it sucks bein a noob.

I copied this from your post:

so here is my issue. I unplugged my M$ 1039 USB Dongle and rebooted I set remotes and transmitters to none in control centre opened up the ubuntu backport source and updated to Lirc 0.8.4a. then I proceeded to setup the ir/vfd in the case lcdproc 0.5.2 with the v3 patch that is common on here and around the web. OK then got the ir working with the mce remote (not the dongle but through the ir in the case oh and with this setup I have a ls -l /dev/lirc* of /dev/lirc0 and the lsmod | grep lirc show that lirc_imon is loaded


I know i dont have skills yet to setup my 1800 card, so for now all i really would like to work is the remote, can you please outline how to get the antec ir to work with a mce remote.

Again thanks for your help.

---

### Post by rodercot on 2010-02-21
Hey All,

 So I thought after working at this for almost a day and a bit I should update this for Karmic (Mythbuntu) 9.10. 

 I have been pulling my hair out trying to get this configure properly in karmic as none of the fixes in the posts above work and they are not even required any longer. 

 After several hours of searching I figure it out up to suspend which I am working on now. 
 
 OK so to back up a little bit. I am trying to get my MCE remote working through the Antec Fusion 430 IR Rcvr (15c2:ffdc) device ONLY. and then have my scripts and certain macro;s passed via the MCEUSB Remotes Dongle. So First to get the remote working with the IR rcvr within the Imon LCD. It seems in Karmic or Lirc latest version they have gone to a 64 bit data requirement - UGGH - where is this little tidbit easily found. Anyhow, the ffdc device DOES NOT need a /etc/modprobe.d/lirc.conf ir_protocol option passed to it. You need to edit your lircd.conf file and change the data info for the remote like so or you can just copy the whole lircd.conf file I have pasted below and back up and replace your existing one in /etc/lirc/.

 **New lircd file for MCEUSB remote through Imon (ffdc) IrRCVR**

 ```
#
# brand:                        HP 
# model no. of remote control:  TSGH-IR01
# devices being controlled by this remote: HP Slimline S3100y
#
# Derived from MCEUSB2 lircd.conf file (lircd.conf.mceusb) found at:
# https://help.ubuntu.com/community/Install_Lirc_Feisty

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
#
# Updated with codes for MCE 2007 Remote additional buttons
# Visualization, Aspect, SlideShow, Eject
# Note: 
# Renamed some buttons: DVD->DVDMenu, More->MoreInfo, Star->Asterisk, Hash->Pound
# Note: 
# Blue, Yellow, Green, Red, and Teletext buttons do not exist on the HP remote
#
# /etc/lirc/lircd.conf for MCE Remote with IMON LCD IR:
#
#Configuration for MCE Remote using the Soundgraph iMON IR/LCD:
begin remote

  name         mceusb
  bits         32
  eps          30
  aeps        100

  one             0     0
  zero            0     0
  post_data_bits	32
  post_data	0x9FAE

  gap         203992
  toggle_bit_mask 0x800000000000

      begin codes
          Power                0x800F040C
          TV_power             0x800F0465
          Home                 0x800F040D
          Guide                0x800F0426
          LiveTV               0x800F0425
          DVD                  0x800F0424
          Teletext             0x800F045A
          RecTV                0x800F0448
          Back                 0x800F0423
          Forward              0x800F0414
          Stop                 0x800F0419
          Replay               0x800F041B
          Skip                 0x800F041A
          Play                 0x800F0416
          Record               0x800F0417
          Rewind               0x800F0415
          Pause                0x800F0418
          More                 0x800F040F
          Left                 0x800F0420
          Right                0x800F0421
          Up                   0x800F041E
          Down                 0x800F041F
          OK                   0x800F0422
          Chan_Down            0x800F0413
          Chan_Up              0x800F0412
          Vol_Down             0x800F0411
          Vol_Up               0x800F0410
          Mute                 0x800F040E
          One                  0x800F0401
          Two                  0x800F0402
          Three                0x800F0403
          Four                 0x800F0404
          Five                 0x800F0405
          Six                  0x800F0406
          Seven                0x800F0407
          Eight                0x800F0408
          Nine                 0x800F0409
          Zero                 0x800F0400
          *                    0x800F041D
          Clear                0x800F040A
          #                    0x800F041C
          Enter                0x800F040B
          Red                  0x800F045B
          Green                0x800F045C
          Yellow               0x800F045D
          Blue                 0x800F045E
          Antec_knob_left      0x01000000
          Antec_knob_right     0x00010000
      end codes

end remote

```

 Your /etc/lirc/hardware.conf file should look like this, a note or two I setup up the mce remote with the Imon display disconnected and then setup the mce remote via the myth control panel this will populate your .lircrc file within your .mythtv directory for use with the mceusb remote. Once that was done I shut down and connected the display and booted up and edited the hardware.conf file as below.

 ```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Transceivers/Remotes (all)"
REMOTE_MODULES="lirc_dev lirc_imon"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="/etc/lirc/lircd.conf"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Microsoft Windows Media Center V2 (usb) : Dish Receiver"
TRANSMITTER_MODULES="lirc_dev lirc_mceusb2"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc1"
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="false"

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
 

 And the final piece of the puzzle and this was the hardest to find but the most simple thing to do. It seems that Lirc has it all figured out for the newest version on how to run multiple devices without major manual configuration EXCEPT the Lirc init.d script. 

 With my devices plugged in and issuing an ls -l /dev/lirc* I had all the devices I needed with manual configuration so 

 ```
crw-rw---- 1 root root 61, 0 2010-02-21 11:44 /dev/lirc0
crw-rw---- 1 root root 61, 1 2010-02-21 11:44 /dev/lirc1
lrwxrwxrwx 1 root root    19 2010-02-21 11:44 /dev/lircd -> /var/run/lirc/lircd
lrwxrwxrwx 1 root root    20 2010-02-21 11:44 /dev/lircd1 -> /var/run/lirc/lircd
```

 SEE the problem - /dev/lircd1 was pointing to /var/run/lirc/lircd so when issuing an irsend command from a script or a command line I was getting the hardware cannot send error. The actual fix I finally found in another post - THANK YOU TO cyber_source - YOU ARE A LIFE SAVER. 

 You need to edit your /etc/init.d/lirc startup script and change a couple lines 

 First Line 83 Needs to be changed from 

 ```
"${TRANSMITTER_SOCKET}1" to this - "${TRANSMITTER_SOCKET}"
```

 and then line 131 Needs to be changed from 

 ```
TRANSMITTER_SOCKET="/var/run/lirc/lircd" to this TRANSMITTER_SOCKET="/var/run/lirc/lircd1"
```

 save and exit the file reboot your system and run another 
ls -l /dev/lirc* and you should see 

 ```
crw-rw---- 1 root root 61, 0 2010-02-21 11:44 /dev/lirc0
crw-rw---- 1 root root 61, 1 2010-02-21 11:44 /dev/lirc1
lrwxrwxrwx 1 root root    19 2010-02-21 11:44 /dev/lircd -> /var/run/lirc/lircd
lrwxrwxrwx 1 root root    20 2010-02-21 11:44 /dev/lircd1 -> /var/run/lirc/lircd1
```

 Notice that now /dev/lircd1 is pointing to the correct pid. 

 Here is a copy of a simple script I use to send a command to my Denon rcvr, I call this on suspend and resume and as well it is tied to the star or hash button on my remote via the .mythtv/lircrc file. 

```
#!/bin/bash
# turn off tv and stereo
irsend --device=/dev/lircd1 SET_TRANSMITTERS 2
irsend --device=/dev/lircd1 send_once denon Off
sleep 1
irsend --device=/dev/lircd1 SET_TRANSMITTERS 2
irsend --device=/dev/lircd1 send_once sharp TVOFF
```

 I hope this saves some people some frustration. I could find very little documentation on the process and it is far easier to do if all was complete. 



 Regards,

 Dave

---

