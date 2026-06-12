---
title: "Confused about serial IR blaster behavior"
date: 2008-11-23
forum: Mythbuntu
---

### Post by jasonsjunk on 2008-11-23
My serial ir blaster is working however it is not working with MythTv

When I issue the following command from the cli my Dish 322 box changes to channel 8.  I am using the SVID input from my Dish 322 to my PVR-150.

 /usr/local/bin/channel-change-lirc.pl 8  

Here is the channel-change script I am using.  
```
#!/usr/bin/perl
#
# name the file channel-change-lirc.pl  then place  in  /usr/local/bin, remember to  chmod +xr
#
# make sure to set this string to
# the corresponding remote in /etc/lircd.conf
#
$remote_name = "dish";
#  Next two lines added to get rid of press select message that comes up
#  on Vip612 dish receive when inactive.  Only need the 2nd line for dish 322.
#system ("irsend -d /dev/lircd1 SEND_ONCE $remote_name power_on");
#sleep 5;
system ("irsend -d /dev/lircd SEND_ONCE $remote_name select");
sleep 2;

sub change_channel {
        my($channel_digit) = @_;
        system ("irsend -d /dev/lircd SEND_ONCE $remote_name $channel_digit");
        sleep 1;
}

$channel=$ARGV[0];
sleep 1;
if (length($channel) > 3) {
        change_channel(substr($channel,0,1));
        change_channel(substr($channel,1,1));
        change_channel(substr($channel,2,1));
    change_channel(substr($channel,3,1));
} elsif (length($channel) > 2) {
        change_channel(substr($channel,0,1));
        change_channel(substr($channel,1,1));
        change_channel(substr($channel,2,1));
} elsif (length($channel) > 1) {
        change_channel(substr($channel,0,1));
        change_channel(substr($channel,1,1));
} else {
        change_channel(substr($channel,0,1));
}
system ("irsend -d /dev/lircd SEND_ONCE $remote_name select");
```

What is confusing the hell out of me is when I put the path to the channel change script into the mythsetup in the external channel change command in input connections my live tv stops working.  When i remove the path from the external channel change command box in setup my live tv works once again.  

Any ideas????

---

### Post by Rompalle on 2008-11-24
when you say LiveTv stops working what do you mean exactly?

Have you tried executing the script from the command line? does it work?

---

### Post by jasonsjunk on 2008-11-24
Yes the script works perfectly from the command line.  However when I insert the path to the script in the external channel change command box in the backend setup.  I cannot view live tv anymore.  When I clear out the path to the script in the external channel change command box in setup and I restart myth live tv works again.  

When I am watching livetv I can change the channel using the script from the command line just fine.  The channel changes without any issues.  This is why I am confused.  

I am currently looking at the lircrc file that was generated in .mythtv in my home folder.  I think the issue lies there since it is different than the lirc.conf I have in /usr/share/lirc/transmitters/dish/general.conf I will provide an update soon if this is the issue.

---

### Post by jasonsjunk on 2008-11-24
Well so far nothing has worked however I am not defeated.  I will have a working serial ir blaster if it kills me.    

I followed the instructions in the mythbuntu installation guide 
```
12.2.1        Serial IR Transmitter
When installing lirc or reconfiguring (sudo dpkg-reconfigure lirc) , choose the option for either “Serial
Receiver” or “Serial receiver (igor cesko’s variant)”. Depending upon which port you have your serial
transmitter attached to, you may have to modify the modprobe options that are used for loading the
kernel module. Create a file entitled /etc/modprobe.d/lirc with these contents:
#COM1 e q u i v a l e n t , / dev / t t y S 0
o p t i o n s l i r c \ s e r i a l i r q =4 i o =0x 3 f 8
#COM2 e q u i v a l e n t , / dev / t t y S 1
#o p t i o n s l i r c \ s e r i a l i r q =3 i o =0x 2 f 8
    Uncomment the appropriate line to represent serial port you have connected your transmitter.
    If you are running the lirc serial driver either for a transmitter or receiver, you will need to disable
kernel serial support.
    • First you will need the setserial utility to do this.
              $ sudo apt&#8722;g e t i n s t a l l s e t s e r i a l
    • Reconfigure setserial.
              $ sudo dpkg&#8722;r e c o n f i g u r e s e t s e r i a l
    • Choose manual.
    • Modify /var/lib/setserial/autoserial.conf
        Add (or modify if its there already) (switch to ttyS1 if your using that instead)
              $ / dev / t t y S 0 u a r t none
    • Copy that script to /etc/serial.conf
              $ sudo cp / var / l i b / s e t s e r i a l / a u t o s e r i a l . c o n f / e t c / s e r i a l . c o n f

```
Here is my /etc/modprobe.d/lirc
```
#COM1 equivalent, /dev/ttyS0
options lirc\serial irq=4 io=0x3f8
#COM2 equivalent, /dev/ttyS1
#options lirc\serial irq=3 io=0x2f8
```
Here is my /var/lib/setserial/autoserial.conf and my /etc/serial.conf
```
#
###PORT STATE GENERATED USING AUTOSAVE-ONCE###
###AUTOSAVE-ONCE###
###AUTOSAVE-ONCE###
###AUTOSAVE###
#
# If you want to configure this file by hand, use 
# dpkg-reconfigure setserial
# and change the configuration mode of the file to MANUAL. If you do not do this, this file may be overwritten automatically the next time you upgrade the
# package.
#
/dev/ttyS0 uart none
```
Here is my etc/lircd.conf  same is also in etc/lirc/lircd.conf
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

#No default remote configuration was included for Home-brew (16x50 UART compatible serial port)
#You will need to include your own custom configuration for
#this remote, and file a bug at https://bugs.launchpad.net/ubuntu/+source/lirc/+filebug

#Configuration for the Serial Port (UART) : Dish Receiver transmitter:
include /usr/share/lirc/transmitters/dish/general.conf
```

Here is my hardware.conf in /etc/lirc
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Home-brew (16x50 UART compatible serial port)"
REMOTE_MODULES="lirc_dev lirc_serial"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Serial Port (UART) : Dish Receiver"
TRANSMITTER_MODULES="lirc_dev lirc_serial"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc1"
TRANSMITTER_LIRCD_CONF="dish/general.conf"
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

Here is my lircrc file located in /.lirc in my home folder /.mythtv located in my home folder has a link to this.  I truncated the file since remote = dish and remote = dish1 are the only ones of interest.  The rest are in there.  
```
# LIRCRC Auto Generated by Mythbuntu Lirc Generator
# Author(s): Mario Limonciello, Nick Fox
# Created for use with Mythbuntu
begin
    remote = dish
    prog = mythtv
    button = 7
    config = 7
    repeat = 0
    delay = 0
end

begin
    remote = dish
    prog = mythtv
    button = right
    config = Right
    repeat = 0
    delay = 0
end

begin
    remote = dish
    prog = mythtv
    button = skip_fwd
    config = Z
    repeat = 0
    delay = 0
end

begin
    remote = dish
    prog = mythtv
    button = 1
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = dish
    prog = mythtv
    button = down
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = dish
    prog = mythtv
    button = 0
    config = 0
    repeat = 0
    delay = 0
end

begin
    remote = dish
    prog = mythtv
    button = pause
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = dish
    prog = mythtv
    button = menu
    config = M
    repeat = 0
    delay = 0
end

begin
    remote = dish
    prog = mythtv
    button = 6
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = dish
    prog = mythtv
    button = 2
    config = 2
    repeat = 0
    delay = 0
end

begin
    remote = dish
    prog = mythtv
    button = fwd
    config = >
    repeat = 0
    delay = 0
end

begin
    remote = dish
    prog = mythtv
    button = play
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = dish
    prog = mythtv
    button = cancel
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = dish
    prog = mythtv
    button = 5
    config = 5
    repeat = 0
    delay = 0
end

begin
    remote = dish
    prog = mythtv
    button = info
    config = I
    repeat = 0
    delay = 0
end

begin
    remote = dish
    prog = mythtv
    button = 4
    config = 4
    repeat = 0
    delay = 0
end

begin
    remote = dish
    prog = mythtv
    button = up
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = dish
    prog = mythtv
    button = recall
    config = R
    repeat = 0
    delay = 0
end

begin
    remote = dish
    prog = mythtv
    button = 9
    config = 9
    repeat = 0
    delay = 0
end

begin
    remote = dish
    prog = mythtv
    button = 3
    config = 3
    repeat = 0
    delay = 0
end

begin
    remote = dish
    prog = mythtv
    button = 8
    config = 8
    repeat = 0
    delay = 0
end

begin
    remote = dish
    prog = mythtv
    button = guide
    config = S
    repeat = 0
    delay = 0
end

begin
    remote = dish
    prog = mythtv
    button = left
    config = Left
    repeat = 0
    delay = 0
end

begin
    remote = dish1
    prog = mythtv
    button = 7
    config = 7
    repeat = 0
    delay = 0
end

begin
    remote = dish1
    prog = mythtv
    button = right
    config = Right
    repeat = 0
    delay = 0
end

begin
    remote = dish1
    prog = mythtv
    button = skip_fwd
    config = Z
    repeat = 0
    delay = 0
end

begin
    remote = dish1
    prog = mythtv
    button = 1
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = dish1
    prog = mythtv
    button = down
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = dish1
    prog = mythtv
    button = 0
    config = 0
    repeat = 0
    delay = 0
end

begin
    remote = dish1
    prog = mythtv
    button = pause
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = dish1
    prog = mythtv
    button = menu
    config = M
    repeat = 0
    delay = 0
end

begin
    remote = dish1
    prog = mythtv
    button = 6
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = dish1
    prog = mythtv
    button = 2
    config = 2
    repeat = 0
    delay = 0
end

begin
    remote = dish1
    prog = mythtv
    button = fwd
    config = >
    repeat = 0
    delay = 0
end

begin
    remote = dish1
    prog = mythtv
    button = play
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = dish1
    prog = mythtv
    button = cancel
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = dish1
    prog = mythtv
    button = 5
    config = 5
    repeat = 0
    delay = 0
end

begin
    remote = dish1
    prog = mythtv
    button = info
    config = I
    repeat = 0
    delay = 0
end

begin
    remote = dish1
    prog = mythtv
    button = 4
    config = 4
    repeat = 0
    delay = 0
end

begin
    remote = dish1
    prog = mythtv
    button = up
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = dish1
    prog = mythtv
    button = recall
    config = R
    repeat = 0
    delay = 0
end

begin
    remote = dish1
    prog = mythtv
    button = 9
    config = 9
    repeat = 0
    delay = 0
end

begin
    remote = dish1
    prog = mythtv
    button = 3
    config = 3
    repeat = 0
    delay = 0
end

begin
    remote = dish1
    prog = mythtv
    button = 8
    config = 8
    repeat = 0
    delay = 0
end

begin
    remote = dish1
    prog = mythtv
    button = guide
    config = S
    repeat = 0
    delay = 0
end

begin
    remote = dish1
    prog = mythtv
    button = left
    config = Left
    repeat = 0
    delay = 0
end

begin
    remote = dish3
    prog = mythtv
    button = 7
    config = 7
    repeat = 0
    delay = 0
end

```

And here is my general.conf located in /usr/share/lirc/transmitters/dish
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

---

### Post by jasonsjunk on 2008-11-24
My error logs are here

[http://mythbuntu.pastebin.com/f126883ac](http://mythbuntu.pastebin.com/f126883ac)

---

### Post by gfowler on 2008-11-24
jasonjunk,
What you described happened to me when I had a typo in the link for the change script that I typed in during config.  I kept typing the underscore instead of the '-'.  The script you are using is the same, except for the sleep time between digits.  

If there is an error in the link the liveTV will just go back to the menu.

YMMV

Jerry

---

### Post by davidstoll on 2009-01-02
Why does your file (mine does too) have..

remote = dish1

entries as well as dish2, dish3,4,5,6,etc?

Seems like there is duplicate information.
Can the duplicates be removed?

Does "dish" stand for dish network?  My mplayer config file has these references, but I don't even have dish network.

---

