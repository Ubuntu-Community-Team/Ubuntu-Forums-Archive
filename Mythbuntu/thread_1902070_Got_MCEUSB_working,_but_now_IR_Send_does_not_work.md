---
title: "Got MCEUSB working, but now IR Send does not work"
date: 2011-12-29
forum: Mythbuntu
---

### Post by stevenc2 on 2011-12-29
I upgraded to Mythbuntu Narwhal.

Figured I'd try to get my remote working again and found these directions:
[http://ubuntuforums.org/showthread.php?t=1594799](http://ubuntuforums.org/showthread.php?t=1594799)

I opted for option 2, and now my MCE remote is working wonderfully, but irsend is not working at all.

irsend LIST "" "" lists the DC50X:
irsend: DC50X
irsend: mceusb

When I try "irsend SEND_ONCE DC50X ENTER"
or my channel change script I got mostly from here [http://regx.dgswa.com/html/node/134](http://regx.dgswa.com/html/node/134)
 it doesn't produce any error.  It just does not work.

The channel changing was working earlier today with the same configuration files.  Any ideas?

---

### Post by azmyth on 2011-12-30
Does the DC50X name match the one in the blasters .conf file?

Also, try 
irsend SEND_ONCE DC50X 1

---

### Post by stevenc2 on 2011-12-30
Yes it matches. 

When I try irsend SEND_ONCE DC50X 1      or sudo irsend SEND_ONCE DC50X 1. I get no message, but no error either.  It does not send any commands to the blaster.

It worked fine until I followed option 2 in the link above to get the MCEUSB working.  I got MCEUSB working, but now the IRSEND does not work.

Here are the configuration files:

cat /etc/lirc/hardware.conf
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Transceivers/Remotes (all)"
REMOTE_MODULES="lirc_dev mceusb"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Serial Port (UART) : Direct TV Receiver"
TRANSMITTER_MODULES="lirc_serial lirc_dev"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc1"
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF="/usr/share/lirc/pace.conf"
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
```and 

cat /usr/share/lirc/pace.conf
```
# contributed by Mike Silliman
#
# brand: Pace
# supported devices: Pace DC50X (Comcast Digital Transport Adapter)
#
# Protocol: XMP-R
# Device: 62.16

begin remote
name DC50X
flags RAW_CODES
eps 30
aeps 100
gap 80412
begin raw_codes

name 1
210 894 210 1709 210 763
210 2787 210 1315 210 1315
210 1157 210 2656 210 13805
210 894 210 2656 210 763
210 763 210 763 210 894
210 763 210 763 210 80413
210 894 210 1709 210 763
210 2787 210 1315 210 1315
210 1157 210 2656 210 13805
210 894 210 1578 210 1841
210 763 210 763 210 894
210 763 210 763 210

name 2
210 894 210 1709 210 763
210 2787 210 1315 210 1315
210 1157 210 2656 210 13805
210 894 210 2524 210 763
210 763 210 763 210 1026
210 763 210 763 210 80413
210 894 210 1709 210 763
210 2787 210 1315 210 1315
210 1157 210 2656 210 13805
210 894 210 1446 210 1841
210 763 210 763 210 1026
210 763 210 763 210

name 3
210 894 210 1709 210 763
210 2787 210 1315 210 1315
210 1157 210 2656 210 13805
210 894 210 2393 210 763
210 763 210 763 210 1157
210 763 210 763 210 80413
210 894 210 1709 210 763
210 2787 210 1315 210 1315
210 1157 210 2656 210 13805
210 894 210 1315 210 1841
210 763 210 763 210 1157
210 763 210 763 210

name 4
210 894 210 1709 210 763
210 2787 210 1315 210 1315
210 1157 210 2656 210 13805
210 894 210 2261 210 763
210 763 210 763 210 1315
210 763 210 763 210 80413
210 894 210 1709 210 763
210 2787 210 1315 210 1315
210 1157 210 2656 210 13805
210 894 210 1157 210 1841
210 763 210 763 210 1315
210 763 210 763 210

name 5
210 894 210 1709 210 763
210 2787 210 1315 210 1315
210 1157 210 2656 210 13805
210 894 210 2130 210 763
210 763 210 763 210 1446
210 763 210 763 210 80413
210 894 210 1709 210 763
210 2787 210 1315 210 1315
210 1157 210 2656 210 13805
210 894 210 1026 210 1841
210 763 210 763 210 1446
210 763 210 763 210

name 6
210 894 210 1709 210 763
210 2787 210 1315 210 1315
210 1157 210 2656 210 13805
210 894 210 1972 210 763
210 763 210 763 210 1578
210 763 210 763 210 80413
210 894 210 1709 210 763
210 2787 210 1315 210 1315
210 1157 210 2656 210 13805
210 894 210 894 210 1841
210 763 210 763 210 1578
210 763 210 763 210

name 7
210 894 210 1709 210 763
210 2787 210 1315 210 1315
210 1157 210 2656 210 13805
210 894 210 1841 210 763
210 763 210 763 210 1709
210 763 210 763 210 80413
210 894 210 1709 210 763
210 2787 210 1315 210 1315
210 1157 210 2656 210 13805
210 894 210 763 210 1841
210 763 210 763 210 1709
210 763 210 763 210

name 8
210 894 210 1709 210 763
210 2787 210 1315 210 1315
210 1157 210 2656 210 13805
210 894 210 1709 210 763
210 763 210 763 210 1841
210 763 210 763 210 80413
210 894 210 1709 210 763
210 2787 210 1315 210 1315
210 1157 210 2656 210 13805
210 894 210 2787 210 1841
210 763 210 763 210 1841
210 763 210 763 210
name 9
210 894 210 1709 210 763
210 2787 210 1315 210 1315
210 1157 210 2656 210 13805
210 894 210 1578 210 763
210 763 210 763 210 1972
210 763 210 763 210 80413
210 894 210 1709 210 763
210 2787 210 1315 210 1315
210 1157 210 2656 210 13805
210 894 210 2656 210 1841
210 763 210 763 210 1972
210 763 210 763 210

name 0
210 894 210 1709 210 763
210 2787 210 1315 210 1315
210 1157 210 2656 210 13805
210 894 210 2787 210 763
210 763 210 763 210 763
210 763 210 763 210 80413
210 894 210 1709 210 763
210 2787 210 1315 210 1315
210 1157 210 2656 210 13805
210 894 210 1709 210 1841
210 763 210 763 210 763
210 763 210 763 210

name Enter
210 894 210 1709 210 763
210 2787 210 1315 210 1315
210 1157 210 2656 210 13805
210 894 210 1841 210 763
210 763 210 1026 210 1446
210 763 210 763 210 80413
210 894 210 1709 210 763
210 2787 210 1315 210 1315
210 1157 210 2656 210 13805
210 894 210 763 210 1841
210 763 210 1026 210 1446
210 763 210 763 210

end raw_codes
end remotes
```The only thing I fiddled with yesterday when trying to get this to work was
I changed the order of to lirc_serial first TRANSMITTER_MODULES="lirc_serial lirc_dev" and I changed LOAD_MODULES="false" from LOAD_MODULES="true".  I made each change separately and restarted, but neither fixed the issue.

Let me know if any other information would be helpful to provide!  I was so excited last night when I got the remote working after over a year of using a wireless keyboard, only to find channel changing stopped working!

---

### Post by azmyth on 2011-12-30
Usually if it doesn't work it will give you an error. Do you have a digital camera? Do you use a IR blaster that flashes? If no, a DC is sensitive to IR so in a dark room turn on your DC and then the back panel and then hold the IR to the camera lense and do a irsend command then look through the back panel. It should light up on the back panel.

---

### Post by stevenc2 on 2012-01-04
> **azmyth said:**
> Usually if it doesn't work it will give you an error. Do you have a digital camera? Do you use a IR blaster that flashes? If no, a DC is sensitive to IR so in a dark room turn on your DC and then the back panel and then hold the IR to the camera lense and do a irsend command then look through the back panel. It should light up on the back panel.

Really appreciate the help.  I think the Serial IR Blaster I have is supposed to flash and it isn't.  It's clear and when I hold a camera up to it I don't see any flashes of light on it.  Guess I'll just have to find a replacement.

---

