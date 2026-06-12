---
title: "Ubuntu 10.04 AlsaMixer Error"
date: 2010-08-15
forum: Multimedia Software
---

### Post by iedgar10 on 2010-08-15
Hello,

when i type "alsamixer" into terminal i get the following message " cannot load mixer controls: Invalid argument." 

when i type "aplay -l" into terminal i get this
"**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: NVidia [HDA NVidia], device 1: VT1708B Digital [VT1708B Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0"

rhythmbox and VLC media player play music fine but there is no sound on firefox and microphone does not work. Also, when i go to applications ---> sound and video ---> Gnome AlsaMixer nothing happens. 

Any help would be appreciated!

---

### Post by mcarter67 on 2010-10-10
I am having the exact same problem with the exact same hardware. I thought maybe my install was messed up so I just did a clean install of 10.04. After running all the updates, I still get this error. 

Can someone give me some debugging steps?  I have tried the 

default-sound-channels=6

Only my front speakers work and in the sound controls I only see two channels.

I have a Logitech surround speakers plugged into the three sound card outputs on the back of the computer which the motherboard should auto detect.  Do I need to map the outputs somehow??

---

