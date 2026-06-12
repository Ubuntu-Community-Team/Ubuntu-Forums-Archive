---
title: "Sound line in only playing left speaker"
date: 2008-09-11
forum: Multimedia Software
---

### Post by Bandworthy on 2008-09-11
My line in for some reason only plays sound in my front left speaker,
The sound should be stereo. I norm have a laptop thats for all the unimportant tasks running, one of the things I have is net radio etc playing
using the line in of my main pc It uses my main speakers.

 This works fine in XP, but in Ubuntu anything from the line in is the front left speaker only...  If I have net radio playing in ubuntu itself sound is fine infact all speakers are fine. But line in is only left front speaker.

I'm still very new to linux and so I have quickly exhusted my own ability to figure why this is so, anyone know?.

---

### Post by Thanoulis on 2008-09-11
Sounds like only the front speaker is up. Try to type *alsamixer* in a terminal and unlock the other channels with the "m" key.

---

### Post by Bandworthy on 2008-11-14
Sorry for not replying for so long haven't been able to 

Ok this gives me a screen with 1 bar in middle called master
hitting m changes it to "off"   no sound

---

### Post by psyke83 on 2008-11-14
> **Bandworthy said:**
> Sorry for not replying for so long haven't been able to 

Ok this gives me a screen with 1 bar in middle called master
hitting m changes it to "off"   no sound

That's the PulseAudio mixer. You need to explicitly define the hardware device:

```
$ alsamixer -Dhw
```

Be sure to check PCM and Master. Also, it could be a physical problem (loose wire in the right speaker).

---

### Post by Bandworthy on 2008-11-16
Ok I can not actually see anything incorrect as far as I can tell.

I know its not a wire since line in, when booting to xp and line in from laptop all speakers are fine, ruling out the line in cable.

Playing music directly in ubuntu itself also uses all speakers fine.

Just incase its some wierd thing because my laptop is xp, I did the exact same setup exchanging the xp laptop for one with opensuse nope 1 speaker again.

So I'm guessing for some reason the line in is somehow set to mono not stereo, I've ruled out hardware as far as I can tell but some setting somewhere...

---

### Post by RobbMeex on 2009-07-05
I have the same problem, except after say 3-5 minutes, i get stereo. I think if I turn my laptop sound up it helps but...

---

### Post by JonathanAquino on 2009-09-12
I connected my WinXP (Thinkpad) Line Out to my Ubuntu Jaunty desktop Line In. I too noticed that music played on the Thinkpad was coming out of one speaker on the desktop. 

Following a [tip]("http://www.spinics.net/lists/vfl/msg11117.html") suggesting that one "unmute the '3dcontr' section in alsamixer", I did the following:
[LIST]
[*]Opened "Volume Control"
[*]Clicked "Preferences"
[*]Made "3D Control - Center", "3D Control - Depth", and "3D Control - Switch" visible
[*]Turned up the volume on "3D Control - Center" and "3D Control - Depth"
[*]Clicked the Switches tab and enabled "3D Control - Switch"
[/LIST]

This resulted in sound coming out of both speakers!

---

### Post by vertago1 on 2009-10-08
If you get this problem after doing a dist upgrade to karmic:

Try going to channels, and splitting your master channel to see if the right has any volume.

I had this same issue and until I:
-> split the channel
-> changed the volume on the right to non-zero
-> merged the channel back
-> adjusted the master volume

This resolved the issue for me, I did a bug report at: [https://bugs.launchpad.net/ubuntu/+source/kdemultimedia/+bug/446833]("https://bugs.launchpad.net/ubuntu/+source/kdemultimedia/+bug/446833")

---

