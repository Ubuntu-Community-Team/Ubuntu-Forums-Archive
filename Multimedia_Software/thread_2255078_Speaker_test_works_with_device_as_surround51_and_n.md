---
title: "Speaker test works with device as surround51 and not with hw"
date: 2014-12-02
forum: Multimedia Software
---

### Post by PeterTaps on 2014-12-02
Folks,

I am running Ubuntu 14.04 server on a new box. I have a 5.1 speaker set on this box via soundblaster card.

$ aplay -L | grep surround51

surround51:CARD=CA0106,DEV=0
surround51:CARD=PCH,DEV=0

$ speaker-test -c6 -Dsurround51:CARD=CA0106,DEV=0 -t wav

This works perfectly. I can hear audio sounds from each speaker.

Now, I am trying to use speaker-test using "hw." Here is the output:

$ aplay -l | grep -i ca0106

card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]

$ speaker-test -c6 -Dhw:0,0 -twav

speaker-test 1.0.27.2


Playback device is hw:0,0
Stream parameters are 48000Hz, S16_LE, 6 channels
WAV file(s)
Channels count (6) not available for playbacks: Invalid argument
Setting of hwparams failed: Invalid argument

I get the same result with hw:0,1, hw:0,2 and hw:0,3

Can someone please enlighten me on why this does not work?

As I recall, this used to work fine under 13.04.


Thank you for your help.

Regards,
Peter

PS: I just tried with -c2 instead of -c6 and it seems to work. But why would -c6 not work? Hmmm.

---

