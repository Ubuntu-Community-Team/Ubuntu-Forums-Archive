---
title: "audio through speakers stops working"
date: 2016-08-03
forum: Multimedia Software
---

### Post by kdwarn on 2016-08-03
I've been having an issue with audio ever since I upgraded to 16.04. I thought maybe there was an issue with upgrading from 15.10 to 16.04, so I did a complete re-install after wiping everything, but I still have the problem. I've gone partly down the rabbit hole of Ubuntu sound issues, and discovered that running


$ pulseaudio -k && sudo alsa force-reload


from the terminal will usually fix the problem. (Sometimes I have to run it three times before it'll work - some modules will fail to reload and it's not until they all reload that this works.)


But I have to do this every time the sound cuts out, and it the sound cuts out every couple of minutes.


This only happens on speakers, not headphones.


Here is the AlsaInfo when the sound was working:
[http://www.alsa-project.org/db/?f=a41e65ba1ff6b97b0015678143a06a79adde20db](http://www.alsa-project.org/db/?f=a41e65ba1ff6b97b0015678143a06a79adde20db)


Here is after it stopped:
[http://www.alsa-project.org/db/?f=53ce24c0e8413bbb379ed8f86d72db1e0fcdb264](http://www.alsa-project.org/db/?f=53ce24c0e8413bbb379ed8f86d72db1e0fcdb264)


The only difference I see is in this block:




when audio working:


```
Node 0x1f [Pin Complex] wcaps 0x400501: Stereo
  Pincap 0x00000010: OUT
  Pin Default 0x901701f0: [Fixed] Speaker at Int N/A
    Conn = Analog, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
```


when audio not working:


```
Node 0x1f [Pin Complex] wcaps 0x400501: Stereo
  Pincap 0x00000010: OUT
  Pin Default 0x901701f0: [Fixed] Speaker at Int N/A
    Conn = Analog, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D3, actual=D3
  Connection: 2
     0x10* 0x11
```


"Power: settting=D3, actual=D3" is the difference.


Does anyone have any idea of a permanent fix on this?

---

### Post by Yellow Pasque on 2016-08-05
Hmm. If that line is the only difference, you may want to disable power saving for your audio codec:
```
echo "options snd_hda_intel power_save=0 power_save_controller=N" | sudo tee -a /etc/modprobe.d/alsa-base.conf
```
Check if it helps after reboot.

---

### Post by kdwarn on 2016-08-10
Thanks, but no dice.

---

