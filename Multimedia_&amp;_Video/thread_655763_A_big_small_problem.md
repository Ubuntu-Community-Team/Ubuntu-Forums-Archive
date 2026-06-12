---
title: "A big small problem"
date: 2008-01-01
forum: Multimedia &amp; Video
---

### Post by provenzano on 2008-01-01
Hello i got a serious issue with my ubuntu 7.10 and amsn but let me start from begin.:

i use a soundblaster audio card , linux read it as Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 02)

to make it work with more then just 1 audio application  i used to edit the file in /etc/asound.conf in this way

 > pcm.my_card {
type hw
card 0
# note this is ONLY for my sound card (via 82xx) - most hardware does not need a special sub-device.
# If you do have multiple sub-devices, test them with aplay -D hw0,x testfile.wav where x is one of the sub-devices.
# Other threads have better info on how to find out details like this on your card
device 1
}

# for outputting sound
pcm.dmixed {
type dmix
ipc_key 1024
# let multiple users share
# ipc_key_add_uid false
# IPC permissions for multi user sharing (octal, default 0600)
# ipc_perm 0666
slave {
pcm "my_card"
# rate 48000
# period_size 512
}
}

# for recording sound
pcm.dsnooped {
type dsnoop
ipc_key 2048
slave {
pcm "my_card"
# rate 48000
# period_size 128
}
}

# combines half duplex to full duplex with the asym plugin
pcm.asymed {
type asym
playback.pcm "dmixed"
capture.pcm "dsnooped"
}

# does automatic sample rate conversion
pcm.pasymed {
type plug
slave.pcm "asymed"
}

# for OSS compatability
pcm.dsp0 {
type plug
slave.pcm "asymed"
}

# sets the default device as your mixed device
pcm.!default {
type plug
slave.pcm "asymed"
}

# says what the mixer will control
ctl.!default {
type hw
card 0
}


after this my ubuntu is able to play more then 1 sound application at time but..
amsn not work properly, the voiceclips freeze or not work at all , i noticed tha tin amsn sound configuration there are just 2 way to config it ,:

[[IMG]http://img113.imageshack.us/img113/1906/53225884eu6.th.jpg[/IMG]](http://img113.imageshack.us/my.php?image=53225884eu6.jpg)

as show it sayd or default or plughw:0 and if i set on default it says device busy if i set on plughw everytime i try to send a voiceclips it freeze for more then 15sec.

help!

---

### Post by provenzano on 2008-01-02
bump

---

### Post by provenzano on 2008-01-03
up

---

