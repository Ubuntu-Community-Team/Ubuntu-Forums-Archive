---
title: "Dishnetwork VIP211 Channel Change"
date: 2010-01-12
forum: Mythbuntu
---

### Post by santhony on 2010-01-12
Anyone who can please help?

Channel Change help..

I'm at wits end here..

I have a commandir that i'm trying to get the channel change to work on a dishnetwork vip211.

From the commandir instructions, I can get the hauppauge setup to receive and transmit.
I also can get the commandir to receive my VIP211 codes also, but can't get it to transmit, the IR lights never blink to show that it has sent.

Anyone that has an idea or has seen this before??

OS: Ubuntu Karmic 64bit
PVR Software: Mythtv
STB: DishNetwork VIP211 and VIP222
IR Equipment: CommandIR and USB-UIRT, Snapstream Firefly R1000
Hauppauge HDPVR 1212

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="CommandIR Multi-IR Transceiver (userspace)"
REMOTE_MODULES=""
REMOTE_DRIVER="commandir"
REMOTE_DEVICE=""
REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Command IR : Dish Receiver"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER="commandir"
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF="dish/general.conf"
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
 START_LIRCD=true

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

# Remote settings required by gnome-lirc-properties
REMOTE_MODEL="Hauppauge"
REMOTE_VENDOR="Hauppauge"

# Receiver settings required by gnome-lirc-properties
RECEIVER_MODEL="Multi-IR\ Transceiver"
RECEIVER_VENDOR="CommandIR"


#My /etc/lirc/lircd.conf
#This is just the dish portion of the lirc, I have removed the Hauppauge
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

---

### Post by santhony on 2010-01-12
This has been fixed by changing the min_repeat from 6 to 1.

---

