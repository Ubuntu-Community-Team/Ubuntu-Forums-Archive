---
title: "Analog Sound Ouput missing"
date: 2015-06-11
forum: Multimedia Software
---

### Post by sw.ng on 2015-06-11
Hi,

I am using ubuntu 12.04. Yesterday, my speaker is work well which is connected to the onboard analog output.

 But, today, I suddenly found out that my machine is no sound. 

I had already checked the following:
----------------------------------------------------
1. System is No mute

2. the speaker is work well because I plug into another PC for testing

3. I install pavucontrol but ONLY see "HDMI/display port" as the Output device

4. By aplay to check if any hareware for analog sound output, know that "card 0 and device 0" is the analog output. Then I test the device by "aplay -D plughw" but no luck.
[HTML]aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC889 Digital [ALC889 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[/HTML]

[HTML]
aplay -D plughw:0,0 /usr/share/sounds/alsa/Front_Center.wav
aplay: main:682: audio open error: Device or resource busy[/HTML]

5. I suspect that the problem maybe the system update in morning. This make the sound output only allow the "HDMI/DisplayPort" and disable the analog sound output. But I know that the fallback would be a very high risk which would make the ubuntu system fail. 
[HTML]Start-Date: 2015-06-11  10:48:46
Commandline: aptdaemon role='role-commit-packages' sender=':1.83'
Install: 
linux-headers-3.13.0-54-generic:amd64 (3.13.0-54.91~precise1), 
linux-headers-3.13.0-54:amd64 (3.13.0-54.91~precise1), 
linux-image-3.13.0-54-generic:amd64 (3.13.0-54.91~precise1)
Upgrade: 
libcupsppdc1:amd64 (1.5.3-0ubuntu8.6, 1.5.3-0ubuntu8.7), libcupsimage2:amd64 (1.5.3-0ubuntu8.6, 1.5.3-0ubuntu8.7), 
libcupscgi1:amd64 (1.5.3-0ubuntu8.6, 1.5.3-0ubuntu8.7), 
libcupsdriver1:amd64 (1.5.3-0ubuntu8.6, 1.5.3-0ubuntu8.7), cups-client:amd64 (1.5.3-0ubuntu8.6, 1.5.3-0ubuntu8.7), 
linux-generic-lts-trusty:amd64 (3.13.0.53.46, 3.13.0.54.47), cups-ppdc:amd64 (1.5.3-0ubuntu8.6, 1.5.3-0ubuntu8.7), 
cups-common:amd64 (1.5.3-0ubuntu8.6, 1.5.3-0ubuntu8.7),libcups2:amd64 (1.5.3-0ubuntu8.6, 1.5.3-0ubuntu8.7), 
cups:amd64 (1.5.3-0ubuntu8.6, 1.5.3-0ubuntu8.7), linux-image-generic-lts-trusty:amd64 (3.13.0.53.46, 3.13.0.54.47), 
cups-bsd:amd64 (1.5.3-0ubuntu8.6, 1.5.3-0ubuntu8.7), linux-headers-generic-lts-trusty:amd64 (3.13.0.53.46, 3.13.0.54.47), 
linux-libc-dev:amd64 (3.2.0-84.121, 3.2.0-85.122), libcupsmime1:amd64 (1.5.3-0ubuntu8.6, 1.5.3-0ubuntu8.7)
End-Date: 2015-06-11  10:50:03[/HTML]

[SIZE=4]**Would anyone please advise how to make the system use the analog as the sound output back ?**[/SIZE]

---

