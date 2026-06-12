---
title: "[SOLVED] Sound suddenly not working"
date: 2008-07-03
forum: Multimedia Software
---

### Post by spitsaliva on 2008-07-03
I have been using Ubuntu for quite some time now and, barring a few hiccups here and there, sound has generally been working fine.

A few hours ago I turned on my laptop and there was no sound. I am pretty certain I have not mucked around with the sound settings the last time I was on the computer, nor have I applied any updates in the last session. I have tried checking the connections, playing around with alsamixer, rebooting, using different media players, etc. to no avail. 

I am on a T61 with the standard Intel soundcard running Hardy. 
if it is any help, aplay -l gives: 
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Is there anything else you need to see? I have absolutely no idea why there is suddenly no sound, and my usual Google-fu hasn't been able to find me the solution.

---

### Post by paulg on 2008-07-03
What's the output on the following command?
```
asoundconf list
```

---

### Post by spitsaliva on 2008-07-03
~$ asoundconf list
Names of available sound cards:
Intel

---

### Post by paulg on 2008-07-03
Well that tells us that alsa is detecting your card. This will make sure it's using that card.

```
asoundconf set-default-card Intel
```

See if that helps.

You don't see anything muted under alsamixer? Try turning everything up to max? Press 'm' to unmute anything that looks muted? I'm out of suggestions otherwise. Reboot would have been my first suggestion but you said you tried that.

---

### Post by spitsaliva on 2008-07-03
Unmuting everything in alsamixer was one of the first things I did... everything is now unmuted.
Also, I have also selectively muted/unmuted stuff in various ways just to make sure nothing that is supposed to be muted is intefering with the sound.

---

### Post by velk on 2008-07-03
Try 
'alsactl restore'

That works for some situations where sound stops working for me.

Can also try
'iecset sound 1'

As this has worked in some similar situations for me in the past.

---

### Post by spitsaliva on 2008-07-03
> **velk said:**
> Try 
'alsactl restore'

That works for some situations where sound stops working for me.

Can also try
'iecset sound 1'

As this has worked in some similar situations for me in the past.

Nope. Still nothing. I'm going to try booting from a livecd now just to make sure the sound card is working.

Edit: Ok, sound works in the LiveCD. Better still, the sound now works in the regular installation as well for some reason. So I guess the issue is solved even though I have no idea what just happened.

---

