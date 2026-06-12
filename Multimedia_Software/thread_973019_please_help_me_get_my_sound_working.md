---
title: "please help me get my sound working"
date: 2008-11-06
forum: Multimedia Software
---

### Post by yakinikku on 2008-11-06
hey guys, i am a total linux noob here.  i have read about on the forums and various websites as to how to get my sound working, i have tried anything that seemed like it related to my sound problem and i get nothing.  please help me get the sound working!

aplay -l gets me this

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

i should note that i am on 8.10.

---

### Post by yakinikku on 2008-11-06
can anyone help?

---

### Post by phidia on 2008-11-07
Did you have to do anything special to get 8.10 to install-what arch (32 or 64 bit) are you running?

There is a big sound troubleshooting thread [here]("http://ubuntuforums.org/showthread.php?t=205449") you may need to give that a read.

Also look at the [ubuntu sound wiki]("https://help.ubuntu.com/community/Sound").

---

### Post by yakinikku on 2008-11-10
> **phidia said:**
> Did you have to do anything special to get 8.10 to install-what arch (32 or 64 bit) are you running?

There is a big sound troubleshooting thread [here]("http://ubuntuforums.org/showthread.php?t=205449") you may need to give that a read.

Also look at the [ubuntu sound wiki]("https://help.ubuntu.com/community/Sound").

I didn't have to do anything special to do the update, I selected the update via the updater within ubuntu.  The sound wasn't working on 8.04 either.  I am fairly sure I am running a 32-bit build of the OS, but how can I confirm this? (sorry, I am a linux n00b.)

I have read thru the sound troubleshooting thread and followed lots of the instuctions to no avail.

There is a gap in the thread and troubleshooting section.  Both areas pretty much say that if your sound card is detected that ALSAmixer is just muted.  I double, triple and quadrouple checked it and it wasn't muted from what I could tell.  I have tried swithing everything to ALSA to see if that would work and it didn't.  I tried toying with some other settings to see if it would get the sound working and it didn't appear to have any affect.

Any help you can offer is much appreciated!!!

TIA

---

### Post by psyke83 on 2008-11-10
I bet you're suffering from a volume issue partly related to PulseAudio.

Run:

```
$ alsamixer -Dhw
```

Ensure the Master and PCM mixers are not muted/low.

---

### Post by 081103jk on 2008-11-10
[**cheap wow gold**](http://www.oofay.com/) Aspect of the Hawk, which grants us +155 attack power, not counting Improved Aspect of the Hawk.[**world of warcraft gold**](http://www.oofay.com/) For non-Beast Masters especially, the Hawk is a very important part of hunter gameplay. Intellect is one of the stats that does not buff our pets, [**world of warcraft gold**](http://www.oofay.com/)unless you have a caster pet,[**world of warcraft gold**](http://www.oofay.com/) which is not always advisable, partly because of the impact of intellect, wow goldand partly because of the pet's use of intellect. As BRK says

---

### Post by yakinikku on 2008-11-10
> **psyke83 said:**
> I bet you're suffering from a volume issue partly related to PulseAudio.

Run:

```
$ alsamixer -Dhw
```

Ensure the Master and PCM mixers are not muted/low.

Thank you, I will check this tonight and post the results.

---

### Post by yakinikku on 2008-11-11
> **psyke83 said:**
> I bet you're suffering from a volume issue partly related to PulseAudio.

Run:

```
$ alsamixer -Dhw
```

Ensure the Master and PCM mixers are not muted/low.

None of the options in the screen are muted or low.

any other suggestions?

---

### Post by markbuntu on 2008-11-11
Try these:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

[http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

There are many options for the AD198x, all you can do is try them until you find the one that works for you. Also, make sure that the AD is the default sound card/device, not the Si.

---

### Post by yakinikku on 2008-11-12
> **markbuntu said:**
> Try these:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

[http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

There are many options for the AD198x, all you can do is try them until you find the one that works for you. Also, make sure that the AD is the default sound card/device, not the Si.

Thank you.  I will try these out right now and post the results.

---

