---
title: "wintv pvr-150 issue"
date: 2008-11-13
forum: Mythbuntu
---

### Post by codymyth on 2008-11-13
i recently bought a computer to use as a media center and i also purchased a wintv pvr-150. I installed ,ythbuntu 8.10 using guided settings. i used hauppage tv card for the remote and hauppage-wintv-pvr-150-directtv for the ir blaster. after i got the tuner a video source and everything set up i went to live tv. i got a picture and sound (though very quite) but when i try to change the channel nothing happened, i also noticed that the ir blaster did not flash. so i first check if my remote was working so i went to the terminal and typed irw, when i pressed buttons nothing appeared. then i try sending some irsends but i got errors saying that my hardware does not support ir sending. any ideas to fix this problem?

---

### Post by codymyth on 2008-11-15
anybody know?

---

### Post by danbodoh on 2008-11-15
You'll at least need to put the firmware [http://www.blushingpenguin.com/mark/lmilk/haup-ir-blaster.bin](http://www.blushingpenguin.com/mark/lmilk/haup-ir-blaster.bin) into /lib/firmware.  Mythbuntu doesn't come with firmware.

Check out the the [http://www.blushingpenguin.com/mark/blog/?p=24](http://www.blushingpenguin.com/mark/blog/?p=24) for more information.  Mythbuntu seems to have everything else in place, so you shouldn't need to install anything else.  But you probably have to edit /etc/lirc/hardware.conf.

I haven't actually played with the pvr-150, but I unsuccessfully attempted to the the irblaster working on the wintv-pvr-usb2.

Dan Bodoh

---

### Post by codymyth on 2008-11-15
i have already download the firmware. but shouldn't the remote and blaster work in command prompt even without the firmware?

I have also checked that website out but i could not get the steps to work

what would i have to edit in hardware.conf?

---

### Post by danbodoh on 2008-11-15
Try to get the remote working first; for that you won't need the blushingpenguin firmware which is required for the irblaster.

The remote should be easy.  The irblaster is a bit more of a challenge, and I probably won't be able to help any more than my suggestion above.


Post your hardware.conf...

Dan Bodoh

---

### Post by codymyth on 2008-11-16
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Hauppauge TV card"
REMOTE_MODULES="lirc_dev lirc_i2c"
REMOTE_DRIVER=""
REMOTE_DEVICE=""
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Hauppauge PVR-150 (pci) : Direct TV Receiver"
TRANSMITTER_MODULES="lirc_dev lirc_pvr150"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF="directtv/general.conf"
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

---

### Post by danbodoh on 2008-11-16
Comment out the TRANSMITTER_MODULES (put a # in as the first character of the line), and restart.  You should be able to get the remote working.

After you get the remote working, I *think* that what you need to do is remove the lirc_i2c module, and use the lirc_pvr150 module (they can't co-exist).  Also, put the firmware file in /lib/firmware.

Dan Bodoh

---

### Post by codymyth on 2008-11-16
And how would you go about removing lirc_i2c and using lirc_pvr150?

---

### Post by codymyth on 2008-11-16
i tried what you told me to do and the remote still won't work

---

### Post by danbodoh on 2008-11-16
> **codymyth said:**
> i tried what you told me to do and the remote still won't work

Outside of mythtv, type 'irw' and tap on the remote.  Do you get any response?

---

### Post by codymyth on 2008-11-16
nope, none what so ever

---

### Post by danbodoh on 2008-11-17
You are going to have to start looking in /var/log/kern.log, /var/log/messages for clues...

---

### Post by codymyth on 2008-11-19
what kind of clues should i look for? should a paste what they say?

---

### Post by codymyth on 2008-12-07
what should i be looking for?

---

