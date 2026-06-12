---
title: "Lirc: U/Mythbuntu 8.10 + Hauppauge PVR 150 RC6 USB SMK eHOME Transceiver"
date: 2009-02-25
forum: Mythbuntu
---

### Post by darkjz on 2009-02-25
Greetings:

I installed Ubuntu 8.10 and MythBuntu on top of it in my media center pc.  So far everything works except the remote control. I have a Hauppauge PVR-150, with a Media Center Remote Control (Gray/Silver Ish Color with light gray keys).

I have tried setting up the Lirc System with the "Mythbuntu Control Center" as well as custom lircd.conf files that i've found searching on the net.  So far, no success, I've tried checking if the remote does any effect on MythTV and in XBMC, as well as in the IRW command (which does not return anything at all).  

The only way I have of knowing that the system is actually registering a command is because I get some output when I press a remote key with the following command:
```
sudo cat /dev/lirc0
```

Here's my system info:

[Daemon Log File Grepped with Lirc (http://pastebin.com/f1ef8986a)]("http://pastebin.com/f1ef8986a")

[SysLog Grepped with lirc (http://pastebin.com/f45fb9e82)]("http://pastebin.com/f45fb9e82")

[dmesg: (http://pastebin.com/f15582222)]("http://pastebin.com/f15582222")

[lircd.conf: (http://pastebin.com/f1cf3fb7b)]("http://pastebin.com/f1cf3fb7b")

[hardware.conf: (http://pastebin.com/f64f62dc6)]("http://pastebin.com/f64f62dc6")

[lircd.conf.hauppauge_pvr150: (http://pastebin.com/f697c72c0)]("http://pastebin.com/f697c72c0")

[general.conf: (http://pastebin.com/f6a1c65e2)]("http://pastebin.com/f6a1c65e2")

Do you guys have any other idea of what can I do to make it work? I'm kinda desperate since i've been trying for a week already.

Thanks in advance!!!

-DarkJZ

---

### Post by rodercot on 2009-02-25
These instructions are all for the PVR-150 MCE KIT which includes the remote, SMK USB dongle, 1 - emitter and the red, white, yellow rca and one svideo input on the actual pvr-150 card.

 Can you find and post a link to a picture of the remote you are referring. Is it the one, with SMK USB Dongle and the M$ style remote control with the black back and no color keys. If it is then 

 sudo modprobe lirc_mceusb2

 You need to set your remote to MCE new version et all for both transmitter and remote. then you can copy this file into your /etc/lirc/lircd.conf make sure and back up your old one first and then edit the hardware.conf file and change the remote lircd location to /etc/lircd.conf and if there is an address in the remote lircd location in the transmitter section remove it so that it just ieft with the quotes like so ""

 The modules you should be loading are 

 modeules = "lirc_dev lirc_mceusb2"
 Device = /dev/lirc0 

 output from ls -l /dev/lirc* should be

 /dev/lirc0
 /dev/lircd
 
 output from lsmod | grep lirc should be
  
 lirc_mceusb2
 lirc/dev 
 the third line you should see a bunch of modules and it will include these as well. 

 dmesg | grep -i lirc

 should tell you it is loading your usb module as 1st philips ehome transceiver and then a little further down it should say loading SMK and then registering interface and lirc_mceusb2 as well. This is not exact but you get the picure. 

 
 Lircd.conf
 
 ```

# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.4a(default) on Mon Feb 23 23:55:04 2009
#
# contributed by 
#
# brand:                       /home/xbmc/haumce.conf
# model no. of remote control: 
# devices being controlled by this remote:
#

begin remote

  name  mceusb
  bits           13
  flags RC6|CONST_LENGTH
  eps            30
  aeps          100

  header       2674   870
  one           455   427
  zero          455   427
  pre_data_bits   24
  pre_data       0x1BFF82
  gap          106288
  min_repeat      1
  toggle_bit_mask 0x8000
  rc6_mask    0x100000000

      begin codes
          TV                       0x1BB9
          Music                    0x1BB8
          Pictures                 0x1BB6
          Videos                   0x1BB5
          Power                    0x1BF3
          Stop                     0x1BE6
          Record                   0x1BE8
          Pause                    0x1BE7
          Play                     0x1BE9
          Rewind                   0x1BEA
          Foward                   0x1BEB
          Replay                   0x1BE4
          Skip                     0x1BE5
          Back                     0x1BDC
          More                     0x1BF0
          Up                       0x1BE1
          Left                     0x1BDF
          Right                    0x1BDE
          OK                       0x1BDD
          Down                     0x1BE0
          VolUp                    0x1BEF
          VolDown                  0x1BEE
          Home                     0x1BF2
          ChanDown                 0x1BED
          ChanUp                   0x1BEC
          Mute                     0x1BF1
          RecTV                    0x1BB7
          Guide                    0x1BD9
          LiveTV                   0x1BDA
          DVD                      0x1BDB
          One                      0x1BFE
          Two                      0x1BFD
          Three                    0x1BFC
          Four                     0x1BFB
          Five                     0x1BFA
          Six                      0x1BF9
          Seven                    0x1BF8
          Eight                    0x1BF7
          Nine                     0x1BF6
          Star                     0x1BE2
          Zero                     0x1BFF
          Hash                     0x1BE3
          Clear                    0x1BF5
          Enter                    0x1BF4
      end codes

end remote


```
 
 Hope it helps.

 Dave

---

### Post by darkjz on 2009-02-26
Thank you for your response Dave (rodercot).  I modified the hardware.conf file to load lirc_mceusb2 (it previously stated lirc_pvr150), and after resbooting I verfied all the outputs you mentioned and they were correct (modules, ls of /dev, etc) also applied your lircd.conf file.  

However, the problem remains the same ](*,) ... when I type the irw command and press buttons from my remote, it does not do anything at all.  I know the remote is sending commands because my Xbox360 is right next to the IR Receiver and the xbox responds to the commands (as well as the IR Receiver turns on a nice little red led when he sees any IR Commands).

I have have attached an image of the product of this nightmare.

Any other suggestions? Anything at all will be appreciated.

Regards,


Raul (DarkJZ)

Edit: By the way! I forgot to mention! I'm running Ubuntu 8.10 x64 Bits and installed via Synaptic MythBuntu-Desktop and lirc.

---

### Post by rodercot on 2009-02-26
can you post this for me.

 /etc/lirc/hardware.conf
 lirc --version
 dmesg | grep -i lirc
 lsmod | grep lirc
 
  

  I hope that the version you are running is not affected by the way we are setting this up. I looked through my lirc sources and I do not even have a lirc_pvr150, but I am pretty sure that driver may be unique anyhow.

 Once you post those I will have a better idea.

 Here is another lircd files you can try. with this one I have combined the generic mceusb file and dish general conf in one. This is the default that lirc sets up for a mceusb remote. if this does not work then an irrecord is likely the easiest way to get it going. using this lircd then you need to edit the trasmitters section of the hardware.conf file. to read

 name = custom
 modules = lirc_dev lirc_mceusb2
 device = ""
 driver = ""
 lircd = ""

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

        Blue    0x00007ba1
        Yellow  0x00007ba2
        Green   0x00007ba3
        Red     0x00007ba4
        Teletext        0x00007ba5

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

---

### Post by darkjz on 2009-02-26
Thanks for your help Dave!

I checked the hardware.conf and there was the problem! Instead of being mostly empty as you said it showed the following:
 
```
REMOTE="Hauppauge TV card"
TRANSMITTER="Hauppauge PVR-150 (pci) : Dish Receiver"
REMOTE_MODULES="lirc_dev lirc_mceusb2"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
#REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge_mce"
REMOTE_LIRCD_ARGS=""
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
#TRANSMITTER_LIRCD_CONF="dish/general.conf"
TRANSMITTER_LIRCD_ARGS=""
START_LIRCD="true"
START_LIRCMD=""
LOAD_MODULES=""
LIRCMD_CONF=""
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
```

After commenting the references to /yet another/ lircd.conf and general.conf and applying the lircd.conf you sent in your previous post, it started working perfectly.

Thanks for all your help!

Regards,


DarkJZ (Raul)

---

### Post by rodercot on 2009-02-26
Awesome, glad it helped out. Enjoy.

 Regards,
 
 Dave

---

### Post by sites on 2009-11-18
Sorry to resurrect this thread, but i'm having a problem with the same remote.

darkjz.... if you would, please post all necessary *.conf files

---

