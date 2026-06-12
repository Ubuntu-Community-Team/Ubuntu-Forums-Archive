---
title: "IR issues"
date: 2010-01-10
forum: Mythbuntu
---

### Post by crispen on 2010-01-10
Folks- 

I'm trying to setup a mce remote and a homebrew serial blaster. Both work indepedent of each other but I can't get them to work together. There seems to be an issue with irsend when the blaster isn't /dev/lirc0.  

Here is my lircd.conf
```
kevin@myth:/etc/lirc$ cat lircd.conf
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

#Configuration for the Windows Media Center Transceivers/Remotes (all) remote:
include "/usr/share/lirc/remotes/mceusb/lircd.conf.mceusb"

#Configuration for the Serial Port (UART) : Dish Receiver transmitter:
include "/usr/share/lirc/extras/transmitters/dish/general.conf"
```

Here is my hardware.conf:
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control

#Chosen IR Transmitter

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
TRANSMITTER="Serial Port (UART) : Dish Receiver"
TRANSMITTER_MODULES="lirc_dev lirc_serial"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc0"
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF="dish/general.conf"
TRANSMITTER_LIRCD_ARGS=""
REMOTE="Windows Media Center Transceivers/Remotes (all)"
REMOTE_MODULES="lirc_dev lirc_mceusb"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc1"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS=""
```

Here is the results of lsmod:
```
kevin@myth:/etc/lirc$ lsmod | grep lirc
lirc_serial            12308  1
lirc_mceusb            15520  0
lirc_dev               10804  4 lirc_serial,lirc_mceusb
```

---

### Post by gfowler on 2010-01-10
[QUOTE=crispen;8641953]Folks- 

I'm trying to setup a mce remote and a homebrew serial blaster. Both work indepedent of each other but I can't get them to work together. There seems to be an issue with irsend when the blaster isn't /dev/lirc0.  

Here is my lircd.conf
```
kevin@myth:/etc/lirc$ cat lircd.conf
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

#Configuration for the Windows Media Center Transceivers/Remotes (all) remote:
include "/usr/share/lirc/remotes/mceusb/lircd.conf.mceusb"

#Configuration for the Serial Port (UART) : Dish Receiver transmitter:
include "/usr/share/lirc/extras/transmitters/dish/general.conf"
```

Try reversing the order of the receiver and transmitter includes, i.e. put the transmitter include in front.
Good Luck
Jerry

---

### Post by crispen on 2010-01-10
Jerry- Made the change and it still won't work on anything but lirc0- the usb transmitter is grabing that. Could it have something to do with irsend and default devices?

This is my channel change script:
```
#!/bin/sh
#
# script to control echostar model x22 (and maybe others)
#
# This handles both the "press select to continue "screen saver", and the
# unsubscribed channel dialog box.
#
# Also when a channel is changed, the bannder is quickly removed to minimize
# the showing of the banner display.
#
# usage: changechannel <receiver number> [--raw]
#                      [<channel number> | <remote_button [...]]
#
#        Options:
#        --raw = any following numbers are sent raw, without additional signals
#           needed to bypass the receiver quirks quirks
#
#        For each
#        - <channel number> = Change to given channel, if not prefixed with
#          --raw option, it also sends additional signals in an attempt to bypass
#          dialog boxes, the "press select to continue" display, and a cancel
#          to quickly remove the channel display
#        - <remote button> = control the receiver directly using the given
#          remote control buttons
#

# the time to wait between button presses, mine is workable at .1
SLEEP_TIME=.1

# path of the lirc irsend command
IRSEND=/usr/bin/irsend

# probably dish or expressvu
REMOTE_BASENAME=dish

# change to /dev/null to diable logging
logfile=/var/log/change_channel.log

if [ $# -lt 2 ]; then

echo "usage: changechannel <receiver number> [--raw] "
echo "                      [<channel number> | <remote_button [...]]"
echo
echo "        Options:"
echo "        --raw = any following numbers are sent raw, without additional signals"
echo "           needed to bypass the receiver quirks quirks"
echo
echo "        For each"
echo "        - <channel number> = Change to given channel, if not prefixed with"
echo "          --raw option, it also sends additional signals in an attempt to bypass"
echo "          dialog boxes, the 'press select to continue' display, and a cancel "
echo "          to quickly remove the channel display"
echo "        - <remote button> = control the receiver directly using the given"
echo "          remote control buttons"
echo
exit 0
fi


log() {
        echo `date +"%F %T"` `basename $0`: "$@" >> $logfile
}


log started: "$@"

# first arguemnt
receiver_num=$1
shift

eval REMOTE_NAME=${REMOTE_BASENAME}${receiver_num}



# if set, only numbers are sent to the receiver
numbers_only=0


irsend() {
  $IRSEND SEND_ONCE $REMOTE_NAME $1
  #echo irsend $1
}


send_digits() {
   local do_select=0


   if [ $numbers_only -eq 0 ]; then
      # try and detect if select is needed to finish the channel change

      # less then three digits
      if [ "$3" = "" ]; then
         do_select=1
      fi

      # begins with a 5-9(dish network 4 digit channels)
      #   and is less then 4 digits
      if [ $1 -gt 4 -a "$4" = "" ]; then
         do_select=1
      fi

      # we must skip a dialog(like "this channel isn't accessible")
          # in order to allow channel changing, the only universal seems to be
          # 'recall'
      irsend recall
      sleep $SLEEP_TIME

          # wake up the receiver if it is asleep(after the channel up to prevent
          #   channel ordering)
          irsend select
          sleep $SLEEP_TIME
   fi

   while [ "$1" != "" ]; do
        irsend $1
        shift
        sleep $SLEEP_TIME
   done

   if [ $numbers_only -eq 0 ]; then
      if [ $do_select -ne 0 ]; then
          irsend select
          sleep $SLEEP_TIME
      fi

      # clear the display quickly (and cancel any channel ordering requests)
      irsend cancel
   fi
}


for cmd in "$@"; do

  case $cmd in
    [0-9]*)
        eval send_digits $(echo $cmd | sed -e 's/./& /g')
        ;;
    --raw)
        numbers_only=1
        ;;
    *)
        irsend $cmd
        ;;
  esac

  sleep $SLEEP_TIME
done
```

My external change command is: 
```
/usr/local/bin/change_channel dish
```

or

```
/usr/local/bin/change_channel dish9
```

Thanks

k

---

### Post by gfowler on 2010-01-10
> **crispen said:**
> Jerry- Made the change and it still won't work on anything but lirc0- the usb transmitter is grabing that. Could it have something to do with irsend and default devices?


My external change command is: 
```
/usr/local/bin/change_channel dish
```

or

```
/usr/local/bin/change_channel dish9
```

Thanks

k

crispin,
Well you're well out of my expertise with the usb controller.  I have no experience with it.  I was using the Hauppauge 350 with a serial transmitter for Dish.  If the serial trans include was after the 350 the 350 wouldn't work until I swapped them.  There is an issue with the code in /etc/init.d/lirc that that will show both lircd and lircd1 mapped to the same device.  I don't know how that might effect the usb controller.  Well past my paygrade.  Good Luck..
Jerry

---

