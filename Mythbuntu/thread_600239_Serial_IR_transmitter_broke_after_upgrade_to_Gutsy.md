---
title: "Serial IR transmitter broke after upgrade to Gutsy"
date: 2007-11-02
forum: Mythbuntu
---

### Post by pcglue on 2007-11-02
I have this serial port IR receiver/transmitter:
[http://iguanaworks.net/product2.psp](http://iguanaworks.net/product2.psp)

I had it working in Feisty.  After upgrading to Gutsy, the receiver still works, but the transmitter doesn't work.  Funny thing is that I can still see the IR LED coming on (with my digital camera), but my satellite box doesn't recognize the signal anymore. 

irw recognizes and correctly interprets the button presses from my satellite box remote, but when irsend uses that same lircd.conf to transmit a button, my satellite box doesn't respond.  

I used lirc 0.8.2 in Feisty and am using the same in Gutsy.  Here's my hardware.conf that worked in Feisty and that I'm using verbatim in Gutsy:
[PHP]
# /etc/lirc/hardware.conf
#
REMOTE=""

# Arguments which will be used when launching lircd
LIRCD_ARGS=""

#Don't start lircmd even if there seems to be a good config file
START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER="default"
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE=""
MODULES="lirc_dev lirc_serial"

# Default configuration files for your hardware if any
LIRCD_CONF=""
LIRCMD_CONF=""
[/PHP]

Any ideas what could be wrong?  I'm using kernel 2.6.22-14. Thanks for any help!

---

### Post by superm1 on 2007-11-02
You can attempt to re-record your remote since you have a serial receiver and use that lircd.conf again.  It's possible that your timings weren't very accurate for feisty, but worked.  My suspicion would be the tickless kernel in 2.6.22 throwing things wacky.

---

### Post by PhilStair on 2007-12-23
I have exactly the same problem. Working Mythbox configuration, upgraded to Gutsy, IR transmitter no longer changes channel.
I was using a Pace RF2link to control a UK Sky digibox. Tried building a new infra-red sender and I can see the led flashing using a digital camcorder but no channel change.

---

