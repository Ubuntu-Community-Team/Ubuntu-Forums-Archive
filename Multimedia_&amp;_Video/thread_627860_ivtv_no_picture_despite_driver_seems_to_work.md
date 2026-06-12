---
title: "ivtv: no picture despite driver seems to work"
date: 2007-11-30
forum: Multimedia &amp; Video
---

### Post by nikolko on 2007-11-30
Good day,

I'm trying to make pwr-150 card from vaio desktop to work, but can't succeed in it. I have xubuntu 7.10 installed, it supports ivtv driver out of box. Here you can see some output from my system:

> 
niki@ub53:~$ cat /var/log/messages |grep ivtv
Nov 29 16:19:03 ub53 kernel: [   20.736000] ivtv:  ==================== START INIT IVTV ====================
Nov 29 16:19:03 ub53 kernel: [   20.736000] ivtv:  version 1.0.0 (2.6.22-14-generic SMP mod_unload 586 ) loading
Nov 29 16:19:03 ub53 kernel: [   20.736000] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
Nov 29 16:19:03 ub53 kernel: [   22.856000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (3641851928 bytes)
Nov 29 16:19:03 ub53 kernel: [   23.072000] ivtv0: Encoder revision: 0x02050032
Nov 29 16:19:03 ub53 kernel: [   23.072000] ivtv0: Recommended firmware version is 0x02060039.
Nov 29 16:19:03 ub53 kernel: [   23.216000] tuner 0-0060: chip found @ 0xc0 (ivtv i2c driver #0)
Nov 29 16:19:03 ub53 kernel: [   23.548000] ivtv0: Registered device video0 for encoder MPEG (4 MB)
Nov 29 16:19:03 ub53 kernel: [   23.548000] ivtv0: Registered device video32 for encoder YUV (2 MB)
Nov 29 16:19:03 ub53 kernel: [   23.548000] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
Nov 29 16:19:03 ub53 kernel: [   23.548000] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
Nov 29 16:19:03 ub53 kernel: [   23.548000] ivtv0: Registered device radio0 for encoder radio
Nov 29 16:19:03 ub53 kernel: [   23.548000] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
Nov 29 16:19:03 ub53 kernel: [   23.548000] ivtv:  ====================  END INIT IVTV  ====================
Nov 30 18:46:17 ub53 kernel: [   20.796000] ivtv:  ==================== START INIT IVTV ====================
Nov 30 18:46:17 ub53 kernel: [   20.796000] ivtv:  version 1.0.0 (2.6.22-14-generic SMP mod_unload 586 ) loading
Nov 30 18:46:17 ub53 kernel: [   20.796000] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
Nov 30 18:46:17 ub53 kernel: [   21.644000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (3653326072 bytes)
Nov 30 18:46:17 ub53 kernel: [   21.860000] ivtv0: Encoder revision: 0x02050032
Nov 30 18:46:17 ub53 kernel: [   21.860000] ivtv0: Recommended firmware version is 0x02060039.
Nov 30 18:46:17 ub53 kernel: [   22.008000] tuner 0-0060: chip found @ 0xc0 (ivtv i2c driver #0)
Nov 30 18:46:17 ub53 kernel: [   22.340000] ivtv0: Registered device video0 for encoder MPEG (4 MB)
Nov 30 18:46:17 ub53 kernel: [   22.340000] ivtv0: Registered device video32 for encoder YUV (2 MB)
Nov 30 18:46:17 ub53 kernel: [   22.340000] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
Nov 30 18:46:17 ub53 kernel: [   22.340000] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
Nov 30 18:46:17 ub53 kernel: [   22.340000] ivtv0: Registered device radio0 for encoder radio
Nov 30 18:46:17 ub53 kernel: [   22.340000] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
Nov 30 18:46:17 ub53 kernel: [   22.340000] ivtv:  ====================  END INIT IVTV  ====================
niki@ub53:~$ 


devices are exist:
> 
niki@ub53:~$ ls -l /dev/video*
crw-rw-rw- 1 root video 81,  0 2007-11-30 18:46 /dev/video0
crw-rw-rw- 1 root video 81, 24 2007-11-30 18:46 /dev/video24
crw-rw-rw- 1 root video 81, 32 2007-11-30 18:46 /dev/video32


but, some strange message in dmesg output:

> 
dmesg |grep ivtv
[ 4934.936000] ivtv0: i2c addr 0x44 not found for command 0xc0445624!
[ 4934.936000] ivtv0: i2c addr 0x44 not found for command 0xc0445624!
[ 4934.936000] ivtv0: i2c addr 0x44 not found for command 0xc0445624!
[ 4934.936000] ivtv0: i2c hardware 0x00000001 (cx2584x) not found for command 0xc0445624!
[ 4934.936000] ivtv0: i2c hardware 0x00000001 (cx2584x) not found for command 0xc0445624!
[ 4934.936000] ivtv0: i2c hardware 0x00000001 (cx2584x) not found for command 0xc0445624!
[ 4934.936000] ivtv0: i2c hardware 0x00000001 (cx2584x) not found for command 0xc0445624!
[ 4934.936000] ivtv0: i2c hardware 0x00000001 (cx2584x) not found for command 0xc0445624!
[ 4934.936000] ivtv0: i2c hardware 0x00000001 (cx2584x) not found for command 0xc0445624!
[ 4937.816000] ivtv0: i2c addr 0x44 not found for command 0xc0445624!
[ 4937.816000] ivtv0: i2c addr 0x44 not found for command 0xc0445624!
[ 4937.816000] ivtv0: i2c addr 0x44 not found for command 0xc0445624!
[ 4937.816000] ivtv0: i2c addr 0x44 not found for command 0xc0445624!
[ 4937.816000] ivtv0: i2c hardware 0x00000001 (cx2584x) not found for command 0xc0445624!
[ 4937.816000] ivtv0: i2c hardware 0x00000001 (cx2584x) not found for command 0xc0445624!
[ 4937.816000] ivtv0: i2c hardware 0x00000001 (cx2584x) not found for command 0xc0445624!
[ 4937.816000] ivtv0: i2c hardware 0x00000001 (cx2584x) not found for command 0xc0445624!
[ 4937.816000] ivtv0: i2c hardware 0x00000001 (cx2584x) not found for command 0xc0445624!
[ 4937.816000] ivtv0: i2c hardware 0x00000001 (cx2584x) not found for command 0xc0445624!


and...

> 
niki@ub53:~$ tail /var/log/messages
Nov 30 19:38:00 ub53 kernel: [ 3134.412000] tuner 0-0060: tuner type not set


as a result, I can't get any output from /dev/video0 device:

> 
niki@ub53:~$ cat /dev/video0 > testch.mpg 
 -- ctrl-c --
niki@ub53:~$ ls -l testch.mpg 
-rw------- 1 niki niki 0 2007-11-30 21:32 testch.mpg


and of course, nothing I can see if run "mplayer /dev/video0", it simply doesn't show me any screen...

I'm a member of "video" group, so everything should be ok from how-to point of view. Where is my problem?


some extra info I've got from logs:

> 
niki@ub53:~$ cat /var/log/messages |grep tvee
Nov 29 16:19:03 ub53 kernel: [   23.156000] tveeprom 0-0050: Encountered bad packet header [aa]. Corrupt or not a Hauppauge eeprom.
Nov 30 18:46:17 ub53 kernel: [   21.944000] tveeprom 0-0050: Encountered bad packet header [aa]. Corrupt or not a Hauppauge eeprom.
Nov 30 21:48:25 ub53 kernel: [   22.344000] tveeprom 0-0050: Encountered bad packet header [aa]. Corrupt or not a Hauppauge eeprom.


that's because Sony has reflashed original eeprom to its own. Can I reflash it once again or not? hmm... I should look for such info in internet.

I tried to add "option ivtv tuner=50" into /etc/modprobe.d/options, but this didn't resolved the issue.

---

