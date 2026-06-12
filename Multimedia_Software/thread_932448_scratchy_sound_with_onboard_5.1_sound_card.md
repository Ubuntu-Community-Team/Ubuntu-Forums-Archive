---
title: "scratchy sound with onboard 5.1 sound card"
date: 2008-09-28
forum: Multimedia Software
---

### Post by snobby500 on 2008-09-28
Hi
I just used a guide to get my 5.1 surround sound working, i had to change a conf. file i think, this worked, and now my surround sound is working, however there are some problems.
1) the main one is that the sound has become all scratchy
2) This isnt a major problem but if anyone knows an answer it would be nice :) The front left and right speakers seem to be louder than the center one even though they are both at full volume and the center one is supposed to be louder.

thanks in advance for any help

---

### Post by markbuntu on 2008-09-28
Putting things at full volume will make distortion with some sound cards. Which card do you have?
Type aplay -l in a termial to find out.

---

### Post by snobby500 on 2008-09-28
Thanks, this is what i got when i types in your command

```
**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

i tried turning down the volume of: 
Master 
Surround
Center
LFE

to about half way, and it didnt make any difference :/

Oh and by the way, before I edited the file I had sound coming out of the two front speakers and it didn't sound scratchy.

thanks for your reply

---

### Post by markbuntu on 2008-09-28
What exactly did you do?
Which guide did you use?

---

### Post by snobby500 on 2008-09-28
I used this guide:

[http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy/]("http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy/")

So I have a backup file if needed :) 

Thanks for the help

---

### Post by markbuntu on 2008-09-28
In the daemon.conf file try changing the default-sample=rate to 48000. That may fix your scratchy sound. It works for some other cards but I am not sure about yours.

If that doesn't work you can also try this guide here:

[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

It seems to fix a lot of weird problems like you are having.

---

### Post by snobby500 on 2008-09-29
I tried changing the default sample rate to 48000, then restarted, but it didnt help.

After that i followed the guide exactly doing sections A,B and C, and then in section C i tried fiddling with the fragment sizes, i did:
default-fragments = 8             16     100     4
default-fragment-size-msec = 5    10     50      2
with restarts in between changing each one, but that didnt help either.

However, for the first time since i installed ubuntu i played the music in movie player (mplayer?) and it was much clearer than in rythmbox, so i tried it in exaile, but in exaile the music sounded just as bad as in rythmbox.
So now im wondering if i shouldnt have kept the default setting and not done the other guide and its a problem i have to fix in the applications?

When i play the music in movie player, it is much clearer, pretty near perfect if not perfect (i might be being overcritical :))

soz for the late reply, have had a busy day.

thanks for all the help.

---

### Post by markbuntu on 2008-09-29
You can check if movie player is using PulseAudio or alsa directly which may explain the difference. Open the PulseAudio volume control and start movieplayer, if it does not show up as a playback stream then it is not using pulseaudio. You can try changing System/Preferences/Sound to alsa and then use this guide to set up surround in alsa:

[http://ubuntuforums.org/showthread.php?t=899139](http://ubuntuforums.org/showthread.php?t=899139)

---

### Post by snobby500 on 2008-09-29
lol, ive made an interesting discovery
its only my front right and front left that are making the scratchy noise lol :)
i turned them off and only played though the others at full volume and they didnt make any strange noise at all, this is because when i did your pulse audio test, it showed music playing in totem, but the signals were half of what they were in rythmbox, then i realised the volume wasnt full, so i put it at full in totem, and it made same noise scratchy noise, so when i turned off master volume in the volume control (turning off front right and left) the scratchy noise dissapeared.

any ideas? :)

thanks

---

### Post by snobby500 on 2008-10-05
I decided to turn down the volume on the front 2 speakers as they were higher than the others anyway, and this seemed to have reduced/ stopped the wierd sound comming out of them, thanks for all the help markbuntu.

---

