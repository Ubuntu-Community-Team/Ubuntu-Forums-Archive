---
title: "Sound Problems after update"
date: 2006-07-07
forum: Multimedia &amp; Video
---

### Post by alin.elena on 2006-07-07
Hi,

I experience a very strange problem. After todays update I have absolutly no sound.

Realplayer seems to play but I have no sound
BMP tells me
"Couldn't open audio"
"Please check that:

Your soundcard is configured properly
You have the correct output plugin selected
No other program is blocking the soundcard"

What concerns me is that the intro sounds are not played anymore
```

alin@blue:~$ uname -a
Linux blue 2.6.15-25-386 #1 PREEMPT Wed Jun 14 11:25:49 UTC 2006 i686 GNU/Linux
```

```

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```


Any workaround?

Alin

---

### Post by lodp on 2006-07-07
Did you try to play some wavfile with aplay?

```
aplay <yourwavfile>.wav
```

also, what's your ALSA-version?

```
cat/proc/asound/version
```

did you check in alsamixer, whether all the necessary chanels were unmuted and volume turned up?

---

