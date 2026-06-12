---
title: "Audigy Se Surround Fix!"
date: 2007-10-12
forum: Multimedia &amp; Video
---

### Post by razi3l on 2007-10-12
For anyone else who has an Audigy SE and has not been able to get sound from your other speakers here is the fix: 

Create a new .asoundrc file with this script (or delete what you have and copy-paste this in):



################################################## #######
#This is the standard setting (see: "!default")
#This profile, the default loaded, upmixes stereo sound to 5.1.

pcm.!default {
type plug
slave.pcm "surround51"
slave.channels 6
route_policy duplicate
}
################################################## ######
#This is the normal spdif output profile (optical, toslink).

pcm.!spdif {
type plug
slave.pcm "hw:0,1"
}

################################################## #####
#This is what one could call the "factory default setting", in other words, it only plays the actual channels. so if you fx want to watch a 5.1 movie, on the analog output, this is the option you want.


pcm.analog {
type plug
slave analog_slave;
}

pcm_slave.analog_slave {
pcm surround51;
format S32_LE;
}



then, log out (ctrl-alt-backspace)
log back in and you should be golden!

---

