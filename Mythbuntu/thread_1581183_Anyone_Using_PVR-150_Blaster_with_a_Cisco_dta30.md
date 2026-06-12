---
title: "Anyone Using PVR-150 Blaster with a Cisco dta30"
date: 2010-09-24
forum: Mythbuntu
---

### Post by tim273 on 2010-09-24
Hello Everyone,

I have a working Mythbuntu box with a PVR-150 (with the blaster working).  Currently I'm using the blaster with a SA cable box which is plugged into the s-video of the pvr.  I also have the standard cable hooked into the coax of the pvr.  Comcast is now pushing "Xfinity" on us so we now need a converter box (Cisco dta30) to watch standard cable (at least higher channels).  I'm currently using standard cable to record all the shows so we can watch tv with the cable box.  Now that we have to use this converter box, I will need to use the blaster (which I really don't use for the cable box all the much anyway) to change the channel on the converter box.  Has anyone been able to successfully use the pvr blaster on a Cisco dta30?  Or should I go with the blaster on [http://www.irblaster.info](http://www.irblaster.info) or [http://iguanaworks.net/products.psp](http://iguanaworks.net/products.psp) instead?

Thanks,
Tim

---

### Post by novellahub on 2010-09-29
I am in the same boat except I will be using a PVR-500 and PVR-250. I am purchasing a MCE IR Receiver / Blaster shortly to see if I can get it to work.  I have found zero on-line so far on the Cisco dta30 Digital Transport Adapter use with Mythtv but hoping the instructions for the Pace DTA work the same.

[http://regx.dgswa.com/html/node/134](http://regx.dgswa.com/html/node/134)

---

### Post by tim273 on 2010-09-29
I figured it out, I already had the pvr-150 blaster working so I used this config file ([http://www.blushingpenguin.com/mark/lmilk/lircd.conf](http://www.blushingpenguin.com/mark/lmilk/lircd.conf)) and 0_39* worked.  So I went into the mythtv-setup and on the input connections screen I set both channels to 3 and used my external channel changing script and it worked.  It was just a matter of getting the right configuration.

Here's the remote config I currently have in lircd.conf

```

begin remote

  name          dta
  bits          32
  flags         RAW_CODES
  eps           0
  aeps          0
  plead         0
  gap           333333
  repeat_bit    0
  begin raw_codes
    name 0
    2555904
    name 1
    2555905
    name 2
    2555906
    name 3
    2555907
    name 4
    2555908
    name 5
    2555909
    name 6
    2555910
    name 7
    2555911
    name 8
    2555912
    name 9
    2555913
  end raw_codes
end remote

```

Here's the channel changing script:

```

#!/usr/bin/perl

# make sure to set this string to
# the corresponding remote in /etc/lircd.conf
$remote_name = "dta";

# Let's assume you don't need to press enter after you punch in a
# channel number. Change this to 1 if your cable box expects you press
# enter after each command
$needs_enter = 0;

# Change this to point to your rc executable
$rc_command = "/usr/bin/irsend";

# This subroutine actually sends the signal to the cable box
sub change_SIGNAL {
    my($SIGNAL) = @_;
    system ("$rc_command SEND_ONCE $remote_name $SIGNAL");
}

$SIGNAL=$ARGV[0];
open F, ">> /var/log/channel.log";
print F "channel changing $SIGNAL\n";
close F;
print "channel changing $ARGV[0]\n";

# Checks if $SIGNAL begins with a digit
# If it detects that the string is made up of digits, then it puts
# spaces between the digits.  Ex. 1234 becomes 1 2 3 4
if ( $SIGNAL =~ /^\d+$/ )
{
    $padded = sprintf("%0*d", 3, $SIGNAL);
    my $length = length($padded);
    my $counter = 0;
    my $temp;

    while( $counter < $length )
    {
    $temp .= substr($padded,$counter,1) ." ";
    $counter++;
    }

    change_SIGNAL($temp);
}
else
{
    # argument we passed was not made up of digits, so it must be a
    # command that does something other than channel changing on the
    # cable box
    change_SIGNAL($SIGNAL);
}

# Do we need to send enter
if ( $needs_enter )
{
    system ("$rc_command SEND_ONCE $remote_name SELECT");
}

```

---

### Post by novellahub on 2010-10-15
I have implemented 2 Digital Transport Adapters successfully on my Slave Backend using a Cisco DTA30.  I am using a Microsoft MCE receiver with the dual IR Ports for channel changing.  

/etc/lirc/hardware.conf
```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Transceivers/Remotes (all)"
REMOTE_MODULES="lirc_dev lirc_mceusb"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Microsoft Windows Media Center V2 (usb) : Motorola Cable box"
TRANSMITTER_MODULES="lirc_dev lirc_mceusb2"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc1"
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF="motorola/dctxxxx.conf"
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

#Configuration for the Windows Media Center Transceivers/Remotes (all) remote:
include "/usr/share/lirc/remotes/mceusb/lircd.conf.mceusb"

#Configuration for the Microsoft Windows Media Center V2 (usb) : Scientific Atlanta Cable box transmitter:
#include "/usr/share/lirc/extras/transmitters/scientificatlanta/general.conf"
include "/usr/share/lirc/extras/transmitters/comcast/3067BC2-R.conf"

```

Remote Config
/usr/share/lirc/extras/transmitters/comcast/3067BC2-R.conf
```

# this config file was automatically generated
# using lirc-0.8.6(default) on Sat Jul 31 16:36:24 2010
#
# contributed by Kyle Anderson <kyle|xkyle.com
#
# brand: Comcast
# model no. of remote control: 3067BC2-R
# devices being controlled by this remote: Comcast DTA
#

begin remote

  name  3067BC2
  bits           24
  flags XMP
  eps            20
  aeps          300

  one             0   137
  zero          250   710
  ptrail        250
  pre_data_bits   32
  pre_data       0x170F443E
  post_data_bits  8
  post_data      0x0
  pre           250 12921
  gap          81698
  toggle_bit_mask 0x0

      begin codes
          KEY_INFO                 0x170026
          KEY_1                    0x1E0001
          KEY_2                    0x1D0002
          KEY_3                    0x1C0003
          KEY_4                    0x1B0004
          KEY_5                    0x1A0005
          KEY_6                    0x190006
          KEY_7                    0x180007
          KEY_8                    0x170008
          KEY_9                    0x160009
          KEY_0                    0x1F0000
          KEY_ENTER                0x180025
          KEY_LANGUAGE             0x150082
      end codes

end remote

```

Channel Change Script #1 (/usr/local/bin/chan_ch_1)
```

 #!/bin/sh
 REMOTE_NAME=3067BC2
 irsend SET_TRANSMITTERS 1
 for digit in $(echo $1 | sed -e 's/./& /g'); do
         irsend SEND_ONCE $REMOTE_NAME KEY_$digit
         sleep 0.4  # note, you may have to tweak the interdigit delay up a bit, depending on your STB model
 done
 irsend SEND_ONCE $REMOTE_NAME KEY_ENTER
 exit 0

```

Channel Change Script #2 (/usr/local/bin/chan_ch_2)
```

 #!/bin/sh
 REMOTE_NAME=3067BC2
 irsend SET_TRANSMITTERS 2
 for digit in $(echo $1 | sed -e 's/./& /g'); do
         irsend SEND_ONCE $REMOTE_NAME KEY_$digit
         sleep 0.4  # note, you may have to tweak the interdigit delay up a bit, depending on your STB model
 done
 irsend SEND_ONCE $REMOTE_NAME KEY_ENTER
 exit 0

```

---

### Post by novellahub on 2011-03-17
Update to my channel change scripts.  Recently since updating to Mythtv 0.24, I have been having issues with recordings not changing channels when two are scheduled at the same time.  Individual channel changes were working fine.  To get around this issue, I had to put in a lock routine so only one emitter works at a time.  See below for the new scripts:

Channel Change Script #1 (/usr/local/bin/chan_ch_1)
```

 #!/bin/sh
 REMOTE_NAME=3067BC2
 LOCKFILE=/tmp/lirclock
 export PATH=/bin:/usr/bin:/usr/local/bin

 while [ -f $LOCKFILE ]
  do
  echo "Waiting for lock..."
   sleep .1
 done

 touch $LOCKFILE

 irsend SET_TRANSMITTERS 1

 sleep .15

 for digit in $(echo $1 | sed -e 's/./& /g'); do
         irsend SEND_ONCE $REMOTE_NAME KEY_$digit
         sleep 0.4  # note, you may have to tweak the interdigit delay up a bit$
 done

 irsend SEND_ONCE $REMOTE_NAME KEY_ENTER

 rm $LOCKFILE

 exit 0

```

Channel Change Script #2 (/usr/local/bin/chan_ch_2)
```

 #!/bin/sh
 REMOTE_NAME=3067BC2
 LOCKFILE=/tmp/lirclock
 export PATH=/bin:/usr/bin:/usr/local/bin

 while [ -f $LOCKFILE ]
  do
  echo "Waiting for lock..."
   sleep .1
 done

 touch $LOCKFILE

 irsend SET_TRANSMITTERS 2

 sleep .15

 for digit in $(echo $1 | sed -e 's/./& /g'); do
         irsend SEND_ONCE $REMOTE_NAME KEY_$digit
         sleep 0.4  # note, you may have to tweak the interdigit delay up a bit$
 done

 irsend SEND_ONCE $REMOTE_NAME KEY_ENTER

 rm $LOCKFILE

 exit 0

```

---

### Post by tim273 on 2011-08-30
So recently the IR blaster on my PVR-150 stopped changing channels on my Cisco DTA30.  I haven't changed anything on the mythtv box (other than normal updates) and channel changing still works on my Scientific Atlanta SA2000 cable box.  

I tried running through all the codes from this file ([http://www.blushingpenguin.com/mark/lmilk/lircd.conf](http://www.blushingpenguin.com/mark/lmilk/lircd.conf)) and none of them worked.

Has anyone else had this problem?

Thanks,
Tim

---

### Post by tim273 on 2011-08-30
Looks like I'm not the only one:

[http://mysettopbox.tv/phpBB2/viewtopic.php?p=132958](http://mysettopbox.tv/phpBB2/viewtopic.php?p=132958)

---

### Post by novellahub on 2011-08-31
The channel changing on my Microsoft IR boxes are still working on my DTA30 and RGN-150 boxes from Comcast. Have you tried using the remote and codes I posted earlier in the thread?  Those use the XMP protocol.

---

### Post by tim273 on 2011-08-31
Thanks for the reply!  I don't have the Microsoft remote and blaster, I have the Hauppauge PVR-150 remote and blaster so the codes you provided won't work.  The codes for the PVR-150 blaster are very specific.  If you look at my second post on the thread, I did have a working configuration up until a few months ago then it just stopped working.  I thought it had something to do with LIRC, but I just reinstalled Mythbuntu 10.04 and no dice.  I did find that other forum where someone else has the same problem so I know it's not just me.

---

### Post by novellahub on 2011-09-01
> **tim273 said:**
> Thanks for the reply!  I don't have the Microsoft remote and blaster, I have the Hauppauge PVR-150 remote and blaster so the codes you provided won't work.  The codes for the PVR-150 blaster are very specific.  If you look at my second post on the thread, I did have a working configuration up until a few months ago then it just stopped working.  I thought it had something to do with LIRC, but I just reinstalled Mythbuntu 10.04 and no dice.  I did find that other forum where someone else has the same problem so I know it's not just me.

Comcast with their recent Xfinity update is to blame.  Their remotes now use the XMP protocol. The same remote codes work on both my DTA30 and RNG-150 units.  That is why I suggested to try out my remote config.  

Microsoft USB IR unit is around $10 on eBay if you go that route.   I have both the Microsoft and HP re-branded units working on two different boxes.

---

