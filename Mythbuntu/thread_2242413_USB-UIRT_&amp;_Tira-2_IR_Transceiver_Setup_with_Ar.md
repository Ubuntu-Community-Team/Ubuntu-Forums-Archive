---
title: "USB-UIRT &amp; Tira-2 IR Transceiver Setup with Arris DCX3220e STB &amp; Direct Cable"
date: 2014-09-01
forum: Mythbuntu
---

### Post by one30nav on 2014-09-01
With Charter Cable's move to full digital in my area, they no longer provide set top boxes with firewire ports, my preferred way of channel changing. The STBs they used to provide (Motorola DCT6200 & DCH3416) are now replaced with Arris (formerly Motorola) DCX3220e boxes. For reliability reasons, I hate the IR blaster solution. Fortunately, the 3220e has a 3.5mm IR extender port.

Now I get just as reliable, no-fail channel changes with a direct cable adapter from EJS3 Technology.

If you eBay, "Tivo IR Blaster Direct Connect Adapter Cable"

or go to the link: [http://www.ebay.com/itm/Tivo-IR-Blaster-Direct-Connect-Adapter-Cable-/320588083796?pt=US_Remote_Controls&hash=item4aa489f254](http://www.ebay.com/itm/Tivo-IR-Blaster-Direct-Connect-Adapter-Cable-/320588083796?pt=US_Remote_Controls&hash=item4aa489f254)

That cable fits either the USB-UIRT or Tira-2's 1/8" (3.5mm) external ports. Of course, run the other 3.5mm plug to the STB's EXT IR IN port. So, no IR blaster emitter required. **Note:** The adapter cable can be extended with a standard, 3.5mm audio extender cable. Alternatively, a 5 1/2' adapter cable is also sold by EJS3 Technology on eBay.

For USB-UIRT, and if you run Mythbuntu, the Mythbuntu Control Centre will provide you essentially a turnkey solution for the blaster setup, except make [LOAD_MODULES="false"]. For comparison, my hardware.conf file looks like this:
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="None"
REMOTE_MODULES=""
REMOTE_DRIVER="uirt2_raw"
REMOTE_DEVICE=""
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_ARGS="-d /dev/ttyUSB0"

#Chosen IR Transmitter
TRANSMITTER="USB-UIRT2 : Motorola Cable Box"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER="uirt2_raw"
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF="motorola/dctxxxx.conf"
TRANSMITTER_LIRCD_ARGS=""

#Disable kernel support.
#Typically, lirc will disable in-kernel support for ir devices in order to
#handle them internally.  Set to false to prevent lirc from disabling this
#in-kernel support. 
#DISABLE_KERNEL_SUPPORT="true"

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
```
For Home Electronics Tira-2 (my preferred IR Transceiver), you may have to make a unique transmitter lircd.conf file using tira_raw. Note the following link for the reason why: [http://www.lirc.org/html/tira.html](http://www.lirc.org/html/tira.html)

To accomplish this, use the cable provider remote that works with your STB. Mine is the UR4U remote that works with Arris/Motorola boxes. Point it at the Tira-2, then:
```

sudo killall lircd

irrecord -H tira_raw -d /dev/ttyUSB0 DCT2000-tira
```
Result was the following:
```
# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.9.0(tira_raw) on Sat Aug 23 08:16:44 2014
#
# contributed by 
#
# brand:                       DCT2000-tira
# model no. of remote control: 
# devices being controlled by this remote:
#

begin remote

  name  DCT2000-tira
  flags RAW_CODES
  eps            30
  aeps          100

  repeat       8935  2236
  gap          88173
  repeat_gap   88176

      begin raw_codes

          name 1
             8960    4496     448    4496     432    2240
              432    2240     432    2240     448    2232
              448    2232     432    2240     448    2232
              432    2240     448    2232     432    2240
              448    2232     448    4496     432    4504
              432    4496     448    4496     448   30832
             8936    2232     448

          name 2
             8960    4496     448    2232     448    4496
              448    2232     448    2232     432    2240
              448    2232     448    2232     432    2240
              448    2232     432    2240     448    2232
              448    2232     432    2240     448    4496
              432    4504     432    4504     432   33096
             8936    2232     448

          name 3
             8960    4496     448    4496     432    4504
              432    2240     432    2240     432    2240
              448    2232     432    2240     448    2232
              432    2240     448    2232     448    2232
              432    2240     448    4496     432    2240
              432    4504     432    4504     432   30832
             8936    2240     432

          name 4
             8960    4496     448    2232     448    2232
              448    4496     432    2240     432    2240
              432    2240     432    2240     448    2232
              432    2240     448    2232     448    2232
              432    2240     448    2232     432    2240
              448    4496     432    4504     432   35360
             8936    2232     448

          name 5
             8960    4496     448    4496     432    2240
              432    4504     432    2240     432    2240
              432    2240     448    2232     448    2232
              432    2240     448    2232     432    2240
              448    2232     432    4504     432    4504
              432    2240     432    4504     432   30832
             8936    2232     448

          name 6
             8960    4504     432    2240     432    4496
              448    4496     448    2232     448    2232
              432    2240     448    2232     432    2240
              448    2232     448    2232     432    2240
              448    2232     432    2240     448    4496
              432    2240     432    4504     432   33096
             8936    2232     448

          name 7
             8960    4496     448    4496     432    4504
              432    4504     432    2240     432    2240
              432    2240     432    2240     432    2240
              448    2232     448    2232     432    2240
              448    2232     448    4496     432    2240
              432    2240     432    4504     432   30832
             8936    2240     432

          name 8
             8960    4496     448    2232     448    2232
              448    2232     448    4496     432    2240
              448    2232     432    2240     448    2232
              448    2232     432    2240     448    2232
              448    2232     432    2240     448    2232
              432    2240     448    4496     432   37624
             8936    2232     448

          name 9
             8960    4504     432    4496     448    2232
              448    2232     448    4496     448    2232
              448    2232     448    2232     448    2232
              448    2232     432    2240     448    2232
              448    2232     448    4496     432    4504
              432    4504     432    2240     432   30832
             8936    2240     432

          name 0
             8960    4496     448    2232     448    2232
              448    2232     448    2232     448    2232
              448    2232     448    2232     432    2240
              448    2232     448    2232     432    2240
              448    2232     448    2232     448    2232
              432    2240     448    2232     448   42136
             8936    2240     432

          name OK
             8960    4504     432    4504     432    2240
              432    2240     432    2240     432    4504
              432    2240     432    2240     432    2240
              432    2240     448    2232     448    2232
              432    2240     448    2232     448    4496
              432    4504     432    4504     432   30840
             8936    2232     448

          name POWER
             8960    4496     448    2232     448    4496
              432    2240     448    4496     432    2240
              432    2240     432    2240     432    2240
              448    2232     448    2232     432    2240
              448    2232     448    2232     432    4504
              432    4504     432    2240     432   33096
             8936    2232     448

      end raw_codes

end remote
```
In my case, I saved it as /usr/share/lirc/extras/transmitters/motorola/dctxxxx.conf

For reference my other files:

Tira hardware.conf file:
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="None"
REMOTE_MODULES=""
REMOTE_DRIVER="tira"
REMOTE_DEVICE=""
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_ARGS="-d /dev/ttyUSB0"

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER="tira"
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Disable kernel support.
#Typically, lirc will disable in-kernel support for ir devices in order to
#handle them internally.  Set to false to prevent lirc from disabling this
#in-kernel support. 
#DISABLE_KERNEL_SUPPORT="true"

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
```

Tira lircd.conf file:
```
#/etc/lirc/lircd.conf
#
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

#Configuration for the Hauppauge TV card remote:
include "/usr/share/lirc/remotes/oneforall/lircd.conf.URC8820"

#Configuration for the None transmitter:
include "/usr/share/lirc/extras/transmitters/motorola/dctxxxx.conf"
```

My modified Mythtv external channel change script (change-channel-lirc.sh):
```
#!/bin/sh

REMOTE_NAME=DCT2000-tira
cmd="$1"

case $cmd in
    [0-9]*)
    for digit in $(echo $1 | sed -e 's/./& /g'); do 
        irsend --device=/dev/lircd1 SEND_ONCE $REMOTE_NAME $digit
        # For USB-UIRT, could just be "irsend SEND_ONCE $REMOTE_NAME $digit"
        sleep 0.3
        # If things work OK with sleep 1, try this for faster channel changes:
        # sleep 0.3
    done
    ;;

    *)
        irsend --device=/dev/lircd1 SEND_ONCE $REMOTE_NAME $cmd
        # For USB-UIRT, could just be "irsend SEND_ONCE $REMOTE_NAME $cmd"
        ;;
esac
```

**Note:** For Tira-2, I had to use "--device=/dev/lircd1" for irsend to work.

Hope this helps. One30nav.

---

