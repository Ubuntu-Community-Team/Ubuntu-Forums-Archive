---
title: "Behringer FCA1616"
date: 2016-12-30
forum: Multimedia Software
---

### Post by Lloyd_Dickman on 2016-12-30
I have a Behringer FCA1616 multi-channel mixer.  On Windows systems, all of the numerous channels appear, however on Ubuntu 16.04 LTS, only a single input and output channel are indicated by 'aplay -l' or 'arecord -l'.  Similar result for the Audacity audio application.  'alsamixer' shows no channels.

Does anyone have insight as to how to enable all of the channels?

---

### Post by Yellow Pasque on 2016-12-30
It sounds similar to: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1198577](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1198577)

---

### Post by Autodave on 2016-12-30
I am assuming that you are recording via USB cable?

---

### Post by Lloyd_Dickman on 2016-12-30
Yes, I am using USB and not FireWire.  The device is recognized by 'lsusb'.

---

### Post by Lloyd_Dickman on 2016-12-31
Thanks for pointing me to this.  I made the two suggested changes, and multiple channels now appear.  Additional testing will be needed to confirm whether audio works correctly.

I added the Behringer device to the USB section of:
```
 /lib/udev/rules.d/90-pulseaudio.rules
# Behringer FCA610
ATTRS{idVendor}=="1397", ATTRS{idProduct}=="0004", ENV{PULSE_PROFILE_SET}="multichannel.conf"

and created the file /usr/share/pulseaudio/alsa-mixer/profile-sets/multichannel.conf
# for generic multichannel devices.

[General]
auto-profiles = yes

[Mapping 2-channels]
device-strings = hw:%f
channel-map = front-left,front-right
description = 2 Channels
priority = 2

[Mapping 4-channels]
device-strings = hw:%f
channel-map = front-left,front-right,rear-left,rear-right
description = 4 Channels
priority = 4

[Mapping 6-channels]
device-strings = hw:%f
channel-map = front-left,front-right,rear-left,rear-right,front-center,lfe
description = 6 Channels
priority = 6

[Mapping 8-channels]
device-strings = hw:%f
channel-map = front-left,front-right,rear-left,rear-right,front-center,lfe,side-left,side-right
description = 8 Channels
priority = 8

[Mapping 10-channels]
device-strings = hw:%f
channel-map = front-left,front-right,rear-left,rear-right,front-center,lfe,side-left,side-right,aux0,aux1
description = 10 Channels
priority = 10

[Mapping 12-channels]
device-strings = hw:%f
channel-map = front-left,front-right,rear-left,rear-right,front-center,lfe,side-left,side-right,aux0,aux1,aux2,aux3
description = 12 Channels
priority = 12

[Mapping 14-channels]
device-strings = hw:%f
channel-map = front-left,front-right,rear-left,rear-right,front-center,lfe,side-left,side-right,aux0,aux1,aux2,aux3,aux4,aux5
description = 14 Channels
priority = 14

[Mapping 16-channels]
device-strings = hw:%f
channel-map = front-left,front-right,rear-left,rear-right,front-center,lfe,side-left,side-right,aux0,aux1,aux2,aux3,aux4,aux5,aux6,aux7
description = 16 Channels
priority = 16

[Mapping 18-channels]
device-strings = hw:%f
channel-map = front-left,front-right,rear-left,rear-right,front-center,lfe,side-left,side-right,aux0,aux1,aux2,aux3,aux4,aux5,aux6,aux7,aux8,aux9
description = 18 Channels
priority = 18
```

---

### Post by wildmanne39 on 2016-12-31
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by Autodave on 2016-12-31
I record 18 channels via USB from an Allen & Heath board. Let me know what, if any, problems you have: I have been through all of them I think. :-)

---

### Post by Lloyd_Dickman on 2017-01-01
Thanks for pointing out the use of 'code tags'.

---

