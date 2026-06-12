---
title: "Headset microphone non-functional"
date: 2011-12-25
forum: Multimedia Software
---

### Post by LordAro on 2011-12-25
Hello,

I recently gained a headset - Creative Fatal1ty (this, to be precise [http://www.amazon.co.uk/Creative-Fatal1ty-Detachable-Noise-Cancelling-Microphone/dp/B000P5VR16/ref=sr_1_1?ie=UTF8&qid=1324844635&sr=8-1](http://www.amazon.co.uk/Creative-Fatal1ty-Detachable-Noise-Cancelling-Microphone/dp/B000P5VR16/ref=sr_1_1?ie=UTF8&qid=1324844635&sr=8-1) ) - and while the headphone part of it works fine, the microphone does not.

I have tested the microphone on other (windoze) computers, and it is fine there, which obviously tells me that my sound set up is wrong somewhere

Info: While trying the echo testing service on skype, the message is not just blank, it has no time at all, so it doesn't seem to be recording

Pointers in the right direction would be helpful :)

PS: ubuntu 11.10

---

### Post by Rodney9 on 2011-12-25
Thanks to Zeke

[http://ubuntuforums.org/showthread.php?t=1732074&highlight=pavucontrol](http://ubuntuforums.org/showthread.php?t=1732074&highlight=pavucontrol)

Rodney

---

### Post by LordAro on 2011-12-26
Nope, nothing

Which ever setting i select ("Analogue Microphone / Microphrone 1"/"Analogue Line-in") no sound is registered

(And yes, i did try the troubleshooting as well)

Because i've previously done some fiddling, I'm wondering if i messed something up. Is there a reset command anywhere?

---

### Post by LordAro on 2011-12-28
I hate to do this, but *bump*...

(it was posted at Christmas, so not many people will have seen it [I'm hoping])

---

### Post by neu5eeCh on 2011-12-28
Did you visit this thread? [http://ubuntuforums.org/showthread.php?t=1774627](http://ubuntuforums.org/showthread.php?t=1774627)

I think your only hope may be an Ubuntu recluse and sage named [Lidex]("http://ubuntuforums.org/member.php?u=577099"). I've had a head-set and mic combo, like yours, for three years, and have never been able to make mine work. Mics are linux's achilles heal. Devs just don't seem to treat the issue with any concern.

---

### Post by LordAro on 2011-12-29
Hmm. Thanks for that link

I did the ```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
``` thingy and got this:

[http://www.alsa-project.org/db/?f=bc7632e58743af7b3fe7fb1fd06534956b574fe8](http://www.alsa-project.org/db/?f=bc7632e58743af7b3fe7fb1fd06534956b574fe8)

Anyone know what to do with it?

---

### Post by lidex on 2011-12-31
Seems to be an older unit. What is the make/model of this comp?
Try unmuting your mic 0 element in alsamixer.

```
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 24 [77%] [1.50dB] [on] [COLOR="Red"]Capture [off][/COLOR]
  Front Right: Playback 24 [77%] [1.50dB] [on] [COLOR="Red"]Capture [off][/COLOR]
```

---

### Post by LordAro on 2011-12-31
Thanks :D

Computer is an HP Pavilion of some sort (2nd hand, i suspect slight custom job)

Umm.. i did look in alsamixer, and couldn't see anything muted (i raised the volumes of anything microphone-looking-ish to be sure) but still nothing. But then, i'm not sure i'm understanding how alsamixer works properly

---

### Post by lidex on 2011-12-31
If an element shows MM at the bottom, it's muted, regardless of the level setting. The M key toggles that state.

---

### Post by LordAro on 2012-01-01
Ok, done that, but.. nothing :(

The 'playback message' for the echo test in skype (my way of testing) is still 'blank' as in, not even silence is played, just the 1st beep, then the 2nd beep, with no gap inbetween

---

### Post by lidex on 2012-01-02
Skype is a little tricky in itself. I would suggest using sound recorder to set up the mic initially. How many audio ports does this thing have and which one are you using for mic?

Try enabling mic boost and then disabling external amplifier.

---

### Post by LordAro on 2012-01-03
i cannot find 'sound recorder' in the repositories
i have 'audio recorder' but that seems to be broken (i could try reinstalling)

---

### Post by lidex on 2012-01-04
> **LordAro said:**
> i cannot find 'sound recorder' in the repositories
i have 'audio recorder' but that seems to be broken (i could try reinstalling)

On the command line its:
```
gnome-sound-recorder
```
Its part of the gnome-media package:
```
sudo apt-get install gnome-media
```

---

### Post by LordAro on 2012-01-04
ok, already had that. it was hidden :)

ok, the only options i have for recording are 'capture', which i'm guessing is not the microphone

---

### Post by lidex on 2012-01-04
Have a look here:
[https://help.ubuntu.com/community/SoundTroubleshooting#Line_Input.2BAC8-Microphone_Troubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting#Line_Input.2BAC8-Microphone_Troubleshooting)

---

### Post by LordAro on 2012-01-04
no, nothing :(

one thing i have noticed, even though i keep changing the 'input device' (in pavucontrol) to 'Analogue Microphone', it keeps changing back to 'Analogue Line-in' perhaps this hints at something not being recognised?

EDIT: oh, and whenever i change the audio levels (in same program) it automatically switches to 'Analogue Input' so i can't actually change the audio levels :L

List of available options: (hey, it might be useful :) )
Analogue Microphone / Microphone 1
Analogue Microphone / Microphone 2
Analogue Line-in
Analogue Input
Analogue Video

interestingly, the list is reversed in gnome-volume-control (which i can only start by right clicking the volume icon in menu bar, not from terminal or otherwise)

---

### Post by lidex on 2012-01-04
> **LordAro said:**
> no, nothing :(

one thing i have noticed, even though i keep changing the 'input device' (in pavucontrol) to 'Analogue Microphone', it keeps changing back to 'Analogue Line-in' perhaps this hints at something not being recognised?

EDIT: oh, and whenever i change the audio levels (in same program) it automatically switches to 'Analogue Input' so i can't actually change the audio levels :L

List of available options: (hey, it might be useful :) )
Analogue Microphone / Microphone 1
Analogue Microphone / Microphone 2
Analogue Line-in
Analogue Input
Analogue Video

interestingly, the list is reversed in gnome-volume-control (which i can only start by right clicking the volume icon in menu bar, not from terminal or otherwise)
Pulse audio may be interfering Try resetting it.
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**
* Ignore any 'No such file or directory' errors*

---

### Post by LordAro on 2012-01-04
no... :(

however, i do now have a login sound (it wasn't working before) and  gnome-volume-control and pavucontrol automatically select 'Microphone / Microphone 1' instead of something else :)

---

### Post by lidex on 2012-01-04
> **LordAro said:**
> no... :(

however, i do now have a login sound (it wasn't working before) and  gnome-volume-control and pavucontrol automatically select 'Microphone / Microphone 1' instead of something else :)

Try that help page again. Make sure to do the section 'Changing default subdevice configuration'

---

### Post by LordAro on 2012-01-04
aha! getting somewhere now...

I'm now getting a small amount of static showing (by pavumeter --record) but still no recognition from speaking into the microphone

---

### Post by LordAro on 2012-01-05
Sorry for double post, i thought this might get missed:

EDIT: It works! It works! A combination of the reset and and fiddling with volumes fixed it :)

(Rather embarrassingly, it was working when i posted last, just that i neglected to check the 'microphone on/off switch' attached to the wire on the headset. Sorry :L )

Thanks muchly for your help lidex :)

---

