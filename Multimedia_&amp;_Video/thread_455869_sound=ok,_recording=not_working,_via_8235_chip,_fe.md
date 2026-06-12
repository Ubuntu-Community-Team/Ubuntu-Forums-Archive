---
title: "sound=ok, recording=not working, via 8235 chip, feisty"
date: 2007-05-27
forum: Multimedia &amp; Video
---

### Post by takayuki on 2007-05-27
Hi,

sound works, but i can't record.  mainly i want to use the mic for skype.

my sound card is a via8235.  chip=Realtek ALC200, 200P rev 0.

here's the output of aplay -l:

```

bubox@sotec:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: V8235 [VIA 8235], device 0: VIA 8235 [VIA 8235]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8235 [VIA 8235], device 1: VIA 8235 [VIA 8235]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```


if i do a 'modprobe snd-via82xx' it just returns to the bash prompt with no output.


more info:
```

bubox@sotec:~$ grep 'audio' /etc/group
audio:x:29:bubox

```

any thoughts on why the mic/recording isn't working?

it didn't work in dapper, and now it doesn't work in feisty.

thanks for any input.

regards,

takayuki

---

### Post by takayuki on 2007-05-30
bump...

---

### Post by DraconPern on 2007-06-06
I can't get recording to work either.

---

