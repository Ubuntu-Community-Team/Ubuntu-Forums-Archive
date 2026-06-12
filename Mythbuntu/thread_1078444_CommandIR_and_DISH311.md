---
title: "CommandIR and DISH311"
date: 2009-02-23
forum: Mythbuntu
---

### Post by srmcatee on 2009-02-23
Hello,

I have a CommandIR II, Dish Network DISH 311 and Streamzap remote.

I have gotten my Streamzap remote to work.  But I cannot get the IR blaster to control the satellite box top.

I used the default CommandIR: Dish general.conf file (/usr/share/lirc/transmitters/dish/general.conf).

It executes but the red transmitter lights never light up on the CommandIR II.

So, I went to CommandIR.com and downloaded one of the echostar lrcd.conf files.  I know get the red transmitter lights to blink.  But I still cannot change channels or affect the satellite box.  

I've attempted to blend the two files but I am unsure of all the settings.  Does anyone have any ideas on how to resolve this?

Thanks in advance for your help.  Here's my latest general.conf file that makes the transmitter lights blink but does nothing to the satellite box.

begin remote
  name            echostar
  bits            16
  flags           SPACE_ENC|NO_HEAD_REP
  eps             5
  aeps            100
#  header          400  6000
#  one             400  1600
#  zero            400  2700
#  ptrail          400
#  gap             6000
#  frequency       56800
  frequency 56000

  header 525 6045
  ptrail 450
  gap 6115

  one 440 1645
  zero 440 2780


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

---

### Post by rodercot on 2009-02-24
> **srmcatee said:**
> Hello,

I have a CommandIR II, Dish Network DISH 311 and Streamzap remote.

I have gotten my Streamzap remote to work.  But I cannot get the IR blaster to control the satellite box top.

I used the default CommandIR: Dish general.conf file (/usr/share/lirc/transmitters/dish/general.conf).

It executes but the red transmitter lights never light up on the CommandIR II.

So, I went to CommandIR.com and downloaded one of the echostar lrcd.conf files.  I know get the red transmitter lights to blink.  But I still cannot change channels or affect the satellite box.  

I've attempted to blend the two files but I am unsure of all the settings.  Does anyone have any ideas on how to resolve this?

Thanks in advance for your help.  Here's my latest general.conf file that makes the transmitter lights blink but does nothing to the satellite box.

begin remote
  name            echostar
  bits            16
  flags           SPACE_ENC|NO_HEAD_REP
  eps             5
  aeps            100
#  header          400  6000
#  one             400  1600
#  zero            400  2700
#  ptrail          400
#  gap             6000
#  frequency       56800
  frequency 56000

  header 525 6045
  ptrail 450
  gap 6115

  one 440 1645
  zero 440 2780


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


 Have you tried combining your two files. So take the general.conf and cut the remote part out and then paste it into your lircd.conf file following your streamzap remote then save it to /etc/lirc/lircd.conf

 Then edit your /etc/lirc/hardware.conf file and set your lircd location in the remote section to "etc/lircd.conf" and remove the /dish/general.conf from the transmitter section and just leave the line like this "" 

 Save the file and restart lirc

 sudo /etc/init.d/lirc restart

 irsend SEND_ONCE "Remote_Name" 1 2 3 4 

 change the remote name to whatever name you gave the remote in general.conf. in the file you supplied it's echostar, your express vu should work just fine from the the lirc default dish/general.conf dish codes. So if you copy those remotes into your exising lircd.conf and try is with remote_name dish it should work perfectly, I use that file for both of my 6141 rcvrs and my old 6000 which is now Junk as per Express VU - but hey they swapped it for a 6141 for free so can I complain. 

 Dave

---

### Post by srmcatee on 2009-02-24
Dave, Thanks for the reply.

I have done all you said.  I also got a reply email from commandir and they recommended the same thing.

It is not working still.  I have combined all my configs to one file and modified the hardware file to point to the new single config.  I can run all the irsend commands with out error and nothing happens on my STB.

One thing of note is the red lights on the transmitters do not flash.  When I comment out the following line:

#  post_data_bits 10

The transmitter lights flash and still nothing happens on my STB.

Any ideas?

I have posted my current config file:

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
#
# this config file was automatically generated
# using lirc-0.7.1-CVS(serial) on Fri Feb  4 23:20:56 2005
#
# contributed by Christoph Bartelmus
#
# brand:                       Streamzap
# model no. of remote control: PC Remote
# devices being controlled by this remote: USB receiver
#

begin remote

  name  Streamzap_PC_Remote
  bits            6
  flags RC5|CONST_LENGTH
  eps            30
  aeps          100

  one           889  889
  zero          889  889
  plead         889
  pre_data_bits   8
  pre_data       0xA3
  gap          108344
  toggle_bit      2


      begin codes
          0                        0x00
          1                        0x01
          2                        0x02
          3                        0x03
          4                        0x04
          5                        0x05
          6                        0x06
          7                        0x07
          8                        0x08
          9                        0x09
          POWER                    0x0A
          MUTE                     0x0B
          CH_UP                    0x0C
          VOL_UP                   0x0D
          CH_DOWN                  0x0E
          VOL_DOWN                 0x0F
          UP                       0x10
          LEFT                     0x11
          OK                       0x12
          RIGHT                    0x13
          DOWN                     0x14
          MENU                     0x15
          EXIT                     0x16
          PLAY                     0x17
          PAUSE                    0x18
          STOP                     0x19
          |<<                      0x1A
          >>|                      0x1B
          RECORD                   0x1C
          <<                       0x1D
          >>                       0x1E
          RED                      0x20
          GREEN                    0x21
          YELLOW                   0x22
          BLUE                     0x23
      end codes

end remote



#Configuration for the Command IR : Dish Receiver transmitter:
# This config file is based on the information posted by Endaf Jones at
# [http://www.gossamer-threads.com/lists/mythtv/users/196566#196566](http://www.gossamer-threads.com/lists/mythtv/users/196566#196566)
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

begin remote

  name  CommandIR
  bits           8
  flags CONST_LENGTH
  eps            30
  aeps          100

  one           100    200
  zero          1000   200
  gap          25000
  toggle_bit      0


      begin codes
          emitter-plugged-in-on-1		0x01
          emitter-plugged-in-on-2		0x02
          emitter-plugged-in-on-3		0x03
          emitter-plugged-in-on-4		0x04
          emitter-plugged-in-on-5		0x11
          emitter-plugged-in-on-6		0x12
          emitter-plugged-in-on-7		0x13
          emitter-plugged-in-on-8		0x14
          emitter-plugged-in-on-9		0x21
          emitter-plugged-in-on-10		0x22
          emitter-plugged-in-on-11		0x23
          emitter-plugged-in-on-12		0x24
          emitter-plugged-in-on-13		0x31
          emitter-plugged-in-on-14		0x32
          emitter-plugged-in-on-15		0x33
          emitter-plugged-in-on-16		0x34
          
          emitter-unplugged-from-1		0x05
          emitter-unplugged-from-2		0x06
          emitter-unplugged-from-3		0x07
          emitter-unplugged-from-4		0x08
          emitter-unplugged-from-5		0x15
          emitter-unplugged-from-6		0x16
          emitter-unplugged-from-7		0x17
          emitter-unplugged-from-8		0x18
          emitter-unplugged-from-9		0x25
          emitter-unplugged-from-10		0x26
          emitter-unplugged-from-11		0x27
          emitter-unplugged-from-12		0x28
          emitter-unplugged-from-13		0x35
          emitter-unplugged-from-14		0x36
          emitter-unplugged-from-15		0x37
          emitter-unplugged-from-16		0x38
          
          select-rx-internal	0x09
          select-rx-external	0x0A
          
          receiving-on-device-number-1		0x0D
          receiving-on-device-number-2		0x1D
          receiving-on-device-number-3		0x2D
          receiving-on-device-number-4		0x3D
          
          external-receiver-plugged-in-device-1		0x0B
          external-receiver-unplugged-from-device-1	0x0C
          external-receiver-plugged-in-device-2		0x1B
          external-receiver-unplugged-from-device-2	0x1C
          external-receiver-plugged-in-device-3		0x2B
          external-receiver-unplugged-from-device-3	0x2C
          external-receiver-plugged-in-device-4		0x3B
          external-receiver-unplugged-from-device-4	0x3C
          
          new-hardware-plugged-in-device-1		0x41
          new-hardware-plugged-in-device-2		0x42
          new-hardware-plugged-in-device-3		0x43
          new-hardware-plugged-in-device-4		0x44
          
          hardware-unplugged-device-1	0x45
          hardware-unplugged-device-2	0x46
          hardware-unplugged-device-3	0x47
          hardware-unplugged-device-4	0x48
          
          driver-set-order-multiple-devices		0x50
          driver-ready							0x51
          driver-stopped						0x52
          poll-faster								0x53
          poll-slower								0x54

          setlight-tx1-off			0x61
          setlight-tx2-off			0x71
          setlight-tx3-off			0x81
          setlight-tx4-off			0x91
          setlight-user1-green-off	0xa1
          setlight-user1-red-off	0xb1
          setlight-user2-green-off	0xc1
          setlight-user2-red-off	0xd1
          setlight-power-off		0xe1
          
          setlight-tx1-on			0x62
          setlight-tx2-on			0x72
          setlight-tx3-on			0x82
          setlight-tx4-on			0x92
          setlight-user1-green-on	0xa2
          setlight-user1-red-on		0xb2
          setlight-user2-green-on	0xc2
          setlight-user2-red-on		0xd2
          setlight-power-on			0xe2
          
          setlight-tx1-blink			0x63
          setlight-tx2-blink			0x73
          setlight-tx3-blink			0x83
          setlight-tx4-blink			0x93
          setlight-user1-green-blink	0xa3
          setlight-user1-red-blink		0xb3
          setlight-user2-green-blink	0xc3
          setlight-user2-red-blink		0xd3
          setlight-power-blink			0xe3
          
          setlight-tx1-blink2			0x64
          setlight-tx2-blink2			0x74
          setlight-tx3-blink2			0x84
          setlight-tx4-blink2			0x94
          setlight-user1-green-blink2	0xa4
          setlight-user1-red-blink2		0xb4
          setlight-user2-green-blink2	0xc4
          setlight-user2-red-blink2		0xd4
          setlight-power-blink2			0xe4
          
          setlight-tx1-flash			0x65
          setlight-tx2-flash			0x75
          setlight-tx3-flash			0x85
          setlight-tx4-flash			0x95
          setlight-user1-green-flash	0xa5
          setlight-user1-red-flash		0xb5
          setlight-user2-green-flash	0xc5
          setlight-user2-red-flash		0xd5
          setlight-power-flash			0xe5
          
          settransmitters-1				0xf0
          settransmitters-2				0xf1
          settransmitters-3				0xf2
          settransmitters-4				0xf3
          settransmitters-5				0xf4
          settransmitters-6				0xf5
          settransmitters-7				0xf6
          settransmitters-8				0xf7
          settransmitters-9				0xf8
          settransmitters-10			0xf9
          settransmitters-11			0xfa
          settransmitters-12			0xfb
          settransmitters-13			0xfc
          settransmitters-14			0xfd
          settransmitters-15			0xfe
          settransmitters-16			0xff
          
      end codes

end remote

---

### Post by rodercot on 2009-02-25
Can you post your channel change script please. I think that is where we will find the problem.

 Dave

---

### Post by srmcatee on 2009-02-25
I'm not using a channel change script.  I'm doing an irsend command at the command line.  From what I read I should be able to make this work.  Channel Change script would be the next step if the CommandIR II works.

Steve

---

### Post by rodercot on 2009-02-25
> **srmcatee said:**
> I'm not using a channel change script.  I'm doing an irsend command at the command line.  From what I read I should be able to make this work.  Channel Change script would be the next step if the CommandIR II works.

Steve

 True Enough, Ok! then, please post the irsend command you are using exactly as you typed it at the command line.

 also can you give me the results of 
 
 ls -l /dev/lirc*

 Dave

---

### Post by srmcatee on 2009-02-25
The IRsend command is:

irsend send_once dish power

I've also tried: irsend send_once dish 1
I've also tried: irsend send_once dish (1-16) power

None of the above commands makes anything happen on the STB.

I'm not home right now but I'll post the results of the ls -l /dev/lirc* command later tonight.

Thanks.

---

### Post by rodercot on 2009-02-25
> **srmcatee said:**
> The IRsend command is:

irsend send_once dish power

I've also tried: irsend send_once dish 1
I've also tried: irsend send_once dish (1-16) power

None of the above commands makes anything happen on the STB.

I'm not home right now but I'll post the results of the ls -l /dev/lirc* command later tonight.

Thanks.

 Ok!

 You can try this 

 irsend --device=/dev/lircd SEND_ONCE $REMOTE_NAME $TRANSMITTER_NUMBER 123 .3

 The point .3 adds a delay between your 123 numbers the other thing you may try is changing the remote name, if you have two rcvrs in your house and the remote id has been changed on one or more of them then your rcvr will maybe not respond to the dish remote but may respond to dish4, dish5, dish8 etc.. Then just add your remote name, the output port you are using and change lircd to lircd1 depending on the ouput of your 

 ls -l /dev/lirc* 

 I would think it should look like this

 /dev/lirc0
 /dev/lircd

 but I am not sure how the command ir gets configured so you may see

 /dev/lirc0
 /dev/lirc1
 /dev/lircd 

 If you see this then you may need to add /dev/lirc1 to the device= part of your hardware.conf transmitters section. Adding /dev/lirc1 tells lirc to create another socket IE /dev/lircd1. This would really only be if you had two actual devices connected to the system and so on, like /dev/lirc2 = /dev/lircd2 etc...

 hope this helps.

 Dave

---

### Post by srmcatee on 2009-02-25
I did the ls -l /dev/lirc*

I get: 
/dev/lircd
/dev/lircd1

I also tried the:
irsend --device=/dev/lircd send_once dish 1

It did not flash any lights on the commandir.  I could not do the dish 123.  I got unknown command "123".

Any ideas?

---

### Post by rodercot on 2009-02-25
> **srmcatee said:**
> I did the ls -l /dev/lirc*

I get: 
/dev/lircd
/dev/lircd1

I also tried the:
irsend --device=/dev/lircd send_once dish 1

It did not flash any lights on the commandir.  I could not do the dish 123.  I got unknown command "123".

Any ideas?

 Can you post your hardware.conf file. 

 rereading the post I noticed one line that says you could see the emitters flash but it was not doing anything on the stb, is this the case still? I am not too sure why you are not seeing a /dev/lirc0 and a /dev/lirc1 as well as your dev/lircd (1) in the ls -l /dev/lirc* output but as I said that could be something to do with the way the command ir sets itself up.

 as for the irsend command

 try this

 irsend SET_TRANSMITTERS "#" (# = transmit port you are using)

 then try

 irsend --device=/dev/lircd SEND_ONCE dish 1 2 3 4 (with the spaces)

 irsend --device=/dev/lircd1 SEND_ONCE dish 1 2 3 4
 
 irsend --device=/dev/lirc SEND_ONCE dish1 1 2 3 4
 
 irsend --device=/dev/lircd1 SEND_ONCE dish1 1 2 3 4

 and so on notice the sending to lircd and lircd1 and then the different dish remote numbers each one connects to a different remote in the lircd.conf with different settings in each for all of the dish rcvrs.


 Dave

---

### Post by srmcatee on 2009-02-25
Here's the hardware conf

I'll try the commands shortly

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Custom"
REMOTE_MODULES=""
REMOTE_DRIVER="commandir"
REMOTE_DEVICE=""
REMOTE_LIRCD_CONF="/etc/lirc/lircd.conf"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Custom"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER="commandir"
TRANSMITTER_DEVICE=""
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
FORCE_NONINTERACTIVE_RECONFIGURATION="true"
START_LIRCMD=""

---

### Post by rodercot on 2009-02-25
Hardware.conf for the command IR from their site.

 ```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Custom"
REMOTE_MODULES=""
REMOTE_DRIVER="commandir"
REMOTE_DEVICE=""
REMOTE_LIRCD_CONF="/usr/share/lirc/remotes/hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Custom"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF="/usr/share/lirc/transmitters/directtv/general.conf"
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
FORCE_NONINTERACTIVE_RECONFIGURATION="true"
START_LIRCMD=""

```

 Notice only one drivers in loaded in the remotes section and none in the transmitter section, that could be why you are getting the lircd1 socket listed with ls -l

 Are you running lirc 0.8.4a

$ lirc --version

 This is actually a good install page for the IRII device.   [http://www.commandir.com/content/view/53/75/](http://www.commandir.com/content/view/53/75/)

 Dave

---

### Post by srmcatee on 2009-02-25
I executed all the irsends and no errors except the line that said

irsend --device=/dev/lirc SEND_ONCE dish1 1 2 3 4

I thought this might be a typo so ran it also as
irsend --device=/dev/lircd SEND_ONCE dish1 1 2 3 4

and no errors.  

Once again.  None of these made the red transmit light flash.  

The only way I can get the transmit light to flash is if I comment out:
  post_data_bits 10
in the /etc/lirc/lircd.conf file

Thanks for your help.

---

### Post by srmcatee on 2009-02-25
Ok, 

I removed the 2nd driver.  

ls -l /dev/lirc* give me

/dev/lircd

when I do:
irsend send_once dish 1 2 3 4
irsend send_once dish1 1 2 3 4
irsend send_once dish2 1 2 3 4

All three commands light up the receiver light and not the transmit light.

So we are getting close.

---

### Post by rodercot on 2009-02-25
> **srmcatee said:**
> Ok, 

I removed the 2nd driver.  

ls -l /dev/lirc* give me

/dev/lircd

when I do:
irsend send_once dish 1 2 3 4
irsend send_once dish1 1 2 3 4
irsend send_once dish2 1 2 3 4

All three commands light up the receiver light and not the transmit light.

So we are getting close.

 OK then, 1st sudo /etc/init.d/lirc restart

 do a
 
 irsend set_transmitters 1 2 3 4

 Then try your irsend commands. one of those transmiiter ports have to output something. 

 OR because you have the command ir's commands in the lircd file you may try this as well

 irsend send_once commandir settransmitters-1 (selects emitter #1 set the 1 to whichever port you are trying to flash.)
 irsend send_once dish 1 2 3 4 (sends command on emitter #1)

 rgds,

 Dave

---

### Post by srmcatee on 2009-02-26
K,

Sending all those works.  But it only makes the commandir receiver light flash.  The transmit does not flash.  This makes me think that the following hardware.conf is only talking to the lirc port for the receiver.  Not the transmitter.

For reference: Here is my current hardware.conf

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Custom"
REMOTE_MODULES=""
REMOTE_DRIVER="commandir"
REMOTE_DEVICE=""
REMOTE_LIRCD_CONF="/etc/lirc/lircd.conf"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Custom"
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
FORCE_NONINTERACTIVE_RECONFIGURATION="true"
START_LIRCMD=""

---

### Post by srmcatee on 2009-02-26
I have dug further.  The /etc/init.d/lirc script is looking for either device or driver in both the remote and transmitter sections of the hardware.conf file.

If it finds both of these it initiates both /dev/lircd and /dev/lircd1

The Remote:
REMOTE_ARGS="$REMOTE_ARGS --output=/dev/lircd --listen"

The Transmit:
TRANSMITTER_ARGS="$TRANSMITTER_ARGS --output=/dev/lircd1 --connect=localhost:8765 --pidfile=/var/run/lircd1.pid"

That would explain the results of ls -l /dev/lirc*.

Now, it still leaves me stuck.  so why will the transmit not go out on lircd1?

---

### Post by rodercot on 2009-02-26
That must be added by the install of the commandir driver as that is not standard line the init.d/lirc file. 

 those line I believe mean this

 if there are remote args in the hardware.conf remote_args line then tell lircd to listen. The it will listen for a socket connect and will connect to lircd1 IF something is found in the transmmiter_args section of the hardware.conf and in your case there is not. so it it not listening and not connecting a 2nd sicket at lircd1.  I think the commandir driver is setup in coded that you only need the one driver loaded, I am pretty sure that is what I read on their site. Even in there setup models they show only one driver loading in either the hardware.conf file or the myth control center. 

 Is the A light on the comannd ir red or green, do you recall?

 but you are right that is what it is saying this should not be that hard.

 Let's start here.

 Are you running lirc 0.8.4a version.
 
 Dave

---

### Post by srmcatee on 2009-02-26
Hi,

The A light is green.  I am running 0.8.4a.

---

### Post by srmcatee on 2009-02-26
Should I go back a version?

I'm running MythBuntu 8.1.

---

### Post by rodercot on 2009-02-26
> **srmcatee said:**
> Should I go back a version?

I'm running MythBuntu 8.1.

 Well I have been reading a little bit on this thing. I just does not seem as so it should be this much of a pita.

 Checklist

 Mythbuntu 8.10 OK
 Lirc 0.8.4 or higher OK
 commandir default hardware.conf OK
 A light is green mean Lirc is fine OK

 So all I can see to do is try these (from the command ir trouble shooting page.)

 killall lircd (if needed, no harm running)
 rmmod commandir (if needed, no harm running)
 rmmod lirc_cmdir (if needed, no harm running) 
 lircd --driver=commandir -n 

(open a second terminal to run the next command)

 irw 

 If "A" turns Green then LIRC is working but may need to be configured for your remotes. 

 if the lircd.conf file is ok then you should get some response from your remote via irw.

 if this all works then we can tackle the transmit side again.

 Dave

---

### Post by srmcatee on 2009-02-26
Sorry,  I thought I posted this earlier.

My remote (Streamzap) works fine.  I use the CommandIR as the receiver.

I've also was able to use the streamzap receiver (with some config) without problem.

---

### Post by rodercot on 2009-02-27
> **srmcatee said:**
> Sorry,  I thought I posted this earlier.

My remote (Streamzap) works fine.  I use the CommandIR as the receiver.

I've also was able to use the streamzap receiver (with some config) without problem.


 Ok, let's see if we can send a command to the commandIR "Sanity Check" place the emitter against the command ir's receiver

 open up 2 terminal windows. 

 in the first try running

 /etc/init.d/lirc restart

 then irw

 now goto the 2nd terminal and do

 irsend send_once commandir settransmitters-# (set # to 1-4)
 irsend send_once dish 1 2 3 4 

 irw in the firt terminal should register as receiving something or not.

 While the first irw is open and running try unplugging the emitter from the commandir and then reinsert it and see if irw reports this hotplug action because with the commandir config in the lircd.conf file IT SHOULD. if it does not you can try moving the location of the commandir conf details around in the lircd file IE
 
 structure- lircd.conf

 commandir detail
 streamzap
 dish

 or 

 streamzap
 commandir
 dish

 I have read in certain instances things placed in a different order in the lircd file will make them work. 

 Dave

---

### Post by commandir on 2009-02-27
Hi Guys, 

Even LIRC-0.8.4a doesn't have the latest CommandIR driver from December 2008 actually - we have a MythBuntu/Debian package over on LaunchPad with it though. It's pretty easy to upgrade.  I'm hoping that's all the problem is:

See:
[http://www.commandir.com/content/view/53/75/](http://www.commandir.com/content/view/53/75/)

Matthew
CommandIR Support

---

### Post by srmcatee on 2009-02-28
I'm confused.  Should my sources file read:

deb [http://ppa.launchpad.net/commandir-team/ubuntu](http://ppa.launchpad.net/commandir-team/ubuntu) intrepid main

or 

deb [http://ppa.launchpad.net/commandir-team/ppa/ubuntu](http://ppa.launchpad.net/commandir-team/ppa/ubuntu) intrepid main

when I do lircd --version I get:

lircd 0.8.4a


I think I'm running the current.  Is there anyway to tell what drivers I should have?

---

### Post by srmcatee on 2009-02-28
I would like to note.

If I comment out post_data_bits or set it to 0.  I can get the red transmit lights on the commandir II to flash red.

That tells me that the device and hardware configuration is correct.  The lirc.conf has an error.

Any ideas, or am I totally off?

---

### Post by commandir on 2009-03-02
The CommandIR should detect your StreamZap no problem thus eliminating the need for 2 lircd instances and the extra receiver.  I'd definitely recommend going that route to eliminate the huge headache of multiple lircd instances.

---

### Post by srmcatee on 2009-03-02
The commandir does detect the streamzap.  I've never had a problem getting it to work.

I've changed the hardware.conf to one device.  A transmitters.  And I have all my configs in lircd.conf (streamzap and dish).

Still does not work.  The irsend command never makes the transmit lights come on.  The streamzap remote works just fine through the commandir.

However, if I comment out the post_data_bits command for the dish settings in the lircd.conf file.  IRsend will light the transmit lights.  But i can't get it to do anything to the STB.

Any ideas?  I am doubting the config settings for dish in the lircd.conf file.

---

### Post by srmcatee on 2009-03-04
Here's my latest status.

I have all the configs in one lircd.conf file and have only one lircd starting.  I have my remote working.  I have modified the lircd.conf file for Dish 311 and increased the gap setting.  Increasing the gap setting was the trick to get the emitter lights to flash.  The mythbuntu lirc file for DISH appeared to be to low.

I'm now able to irsend and get the emitter lights to flash.

I still have nothing happening at the STB.

As a final test I pulled the emitter off the STB and placed in on the CommandIR.  

I bumped the frequency down to 38000.  Started LIRCD in a terminal window.  Started IRW in another terminal window.  And then executed irsend send_once dish 1 2 3 4 commands in a third terminal window.

I can see the transmits and receives all happening on the commandir.  So everything is setup and transmitting.

So my final question is what the heck do I do know?  Do I need to test every lirc config file I can find.  I've tried the echostar files and to no avail.  

Should I try and map my individual remote next and see if that works?

Any help would be appreciated.  My wife is about ready to pull the plug on this project (so am I) cause I stay up all hours trying to make this work and take over the TV while I am doing it.  Leaving an unhappy wife and two children.

Thanks in advance for any assistance.

---

### Post by rodercot on 2009-03-04
> **srmcatee said:**
> Here's my latest status.

I have all the configs in one lircd.conf file and have only one lircd starting.  I have my remote working.  I have modified the lircd.conf file for Dish 311 and increased the gap setting.  Increasing the gap setting was the trick to get the emitter lights to flash.  The mythbuntu lirc file for DISH appeared to be to low.

I'm now able to irsend and get the emitter lights to flash.

I still have nothing happening at the STB.

As a final test I pulled the emitter off the STB and placed in on the CommandIR.  
 
I bumped the frequency down to 38000.  Started LIRCD in a terminal window.  Started IRW in another terminal window.  And then executed irsend send_once dish 1 2 3 4 commands in a third terminal window.

I can see the transmits and receives all happening on the commandir.  So everything is setup and transmitting.

So my final question is what the heck do I do know?  Do I need to test every lirc config file I can find.  I've tried the echostar files and to no avail.  

Should I try and map my individual remote next and see if that works?

Any help would be appreciated.  My wife is about ready to pull the plug on this project (so am I) cause I stay up all hours trying to make this work and take over the TV while I am doing it.  Leaving an unhappy wife and two children.

Thanks in advance for any assistance.

 Well, two options You can irrecord your remote thus you know it will work properly OR you try and put the tranmitter back on the stb and send the irsend send once command but changing the name of the remote from dish to dish1 and dish2 etc I think there are sixteen remotes in the dish/general.conf file that you are using. I know that in trying to help you that I did come across some dish311 conf files throughout the web and they all lead back to the dish/general.conf file that you are using. I am pretty confident that if you try each of the dish - dish16 you will find the one that works.

 regards,

 Dave

---

### Post by srmcatee on 2009-03-04
Dave,

I have tried all sixteen to no avail.  I can't try IRRecord because my CommandIR is only 38Khz and the remote is 56Khz.

Looks like I might be stuck.

---

### Post by rodercot on 2009-03-04
Can you check the id of your remote from the rcvr's (i think system info page) menu and see if it may have gotten changed somehow. I know when I first had my 6000 model rcvr and a 4700 I had changed mine on the 6000 and when had to do something later to it and forgot about changing the id it baffled me for a couple days.

 try this post and see if it helps you at all.

 [http://fultonfam.com/?p=45](http://fultonfam.com/?p=45)

 rgds,

 Dave

---

### Post by srmcatee on 2009-03-04
The ID is 1.

Should it be 1 or something else?

---

### Post by srmcatee on 2009-03-04
Does a 1 mean dish1 remote definition?

---

### Post by srmcatee on 2009-03-04
It works.

Your last comment made me look at the sys info.  Indeed my remote was address1.  So I figured I need dish1 config.  But my current lircd.conf was not working.

Then I found:
[http://www.eggshellskull.com/lirc/multi/index.php](http://www.eggshellskull.com/lirc/multi/index.php)

I changed the mid_repeat to 2 on the DISH_1 setting.  And Voila.  It works.  Actually it works incredibly well.  The change channel script on this page worked incredibly well too.

Thank you Dave and Matthew for all your assistance.  

Time to Start Mything!!!!!


:popcorn:

---

### Post by rodercot on 2009-03-05
Great, very happy you got it going. I know that page is incredibly helpful, after a couple weeks of hunting on ways to setup my imon ir and mce on the same box that page finally help me get it to happen and all has been fine since. 

 I now have that same machine powering on and off the tv with suspend and controlling the volume and mute with lirc and the mce remote and channels on my 6141 rcvr in that room.

 Rgds,

 Dave

---

