---
title: "Soundcard not recognized after wakeup or after plugging out and in"
date: 2014-05-04
forum: Multimedia Software
---

### Post by dmitry20 on 2014-05-04
Hello Community!

I have a problem with my headset and hope someone could help me.

I'm using Ubuntu 14.04 with KDE desktop. After upgrading to 14.04 the behaviour of my headset got a bit wired. The headset is Logitech Wireless Headset H600 ([http://www.logitech.com/en-us/product/wireless-headset-h600?crid=36](http://www.logitech.com/en-us/product/wireless-headset-h600?crid=36)).

The problem appeared after upgrade to 14.04 is the following:

- If I (re)start the computer using the headset receiver plugged in, everything works just fine.

- But if I re-plug the receiver, or sometimes after waking up the computer, the system recognizes either only the output of the headset, or sometimes only the microphone, but not both at the same time. The only way to make both working again is to restart the computer again.

So here is some feedback I get from my computer in such "broken" state:

```

# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: M20 [M2Tech USB Audio 2.0], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Headset [Logitech Wireless Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: PCH [HDA Intel PCH], device 0: ALC269VB Analog [ALC269VB Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```


The broken device is "card 1" in this list. Seems like it's recognized, but the Phonon settings panel only shows the microphone-part of the device as plugged-in:


[IMG]http://asvd.github.io/helios-kernel/other/aud/1.png[/IMG]


While the output of the headset looks like unplugged:


[IMG]http://asvd.github.io/helios-kernel/other/aud/2.png[/IMG]


The device is displayed in the similar way in other tools (i.e. pavucontrol), and there's no way to make use of such "invisible" device.

Thanks in advance,
Dmitry

---

### Post by ronb19495 on 2014-05-05
try looking at your alsamixer settings and see what it says

---

### Post by dmitry20 on 2014-05-05
it's a bit strange... both input and output are shown in alsamixer:

[IMG]http://asvd.github.io/helios-kernel/other/aud/3.png[/IMG]


(but in other apps the output is still disabled)
 
pulseaudio works on top of alsa, right? meaning that the device is recognized and I need to tune pulseaudio somehow to work with the headset..

---

### Post by ronb19495 on 2014-05-05
@Dimitry do you have pavucontrol installed if not" sudo apt-get install pavucontrol" this gives a better control over your configuration for sound devices

---

### Post by ronb19495 on 2014-05-05
heres a screenshot of pavucontrol it shows my headset plugged in and working whem you install pavucontrol just go to configuration tab and choose what you want

---

### Post by dmitry20 on 2014-05-06
Yep, I have and use pavucontrol, but as I wrote in any other application (including pavucontrol) the headset is only recognized as a microphone (therefore on the "output devices" tab in pavucontrol it is not mentioned).

Given the fact that alsamixer recognizes the output of the headset, I assume that there's something wrong with Pulseaudio configuration, so what I need is some kind of hint on how to check what could be the problem with it..

---

### Post by ronb19495 on 2014-05-07
try uninstalling pulseaudio reboot and reinstall

---

### Post by Odur on 2014-05-10
Have you resolved this issue? I have the exact same problem with Corsair Vengeance 2000 wireless headset. I'm on Kubuntu 14.04, and it worked flawless in 13.10.

---

### Post by dmitry20 on 2014-05-10
Regretably not, re-installing pulseaudio and alsa (with removing pulseaudio configs) do not help. I guess there is still a chance to fix this reinstalling the whole system from scratch, but I would prefer not to do that.. So basically we need something to analyze the problem happening to the pulseaudio configuration.

I also use another soundcard which I "hotswap" from time to time, and it behaves similarry (meaning it does not appear on the list of devices sometimes). But for that card it's not so critical, since I can simply re-plug it again several times until it finally works (but in case of a headset it simply switches between the microphone and the headphones randomly).

---

### Post by Odur on 2014-05-19
I solved this now by:
1. Uninstalling pulseaudio and purged it (sudo apt-get autoremove --purge pulseaudio).
2. Rebooted and removed ~/.config/pulse/ (rm -r ~/.config/pulse/)
3. Rebooted again and installed pulseaudio again (sudo apt-get install pulseaudio paprefs pulseaudio-esound-compat).

Now it's working for me again, just as in 13.10. I just had to choose the correct device order and master channel, for my volume-control on the headset to work.
I'm not sure if paprefs and pulseaudio-esound-compat is necessary, but they where recommended when pulseaudio was installed.

---

### Post by dmitry20 on 2014-05-24
Wow, the last solution finally worked for me! Though I'm pretty sure I've tried reinstalling pulseaudio, clearing configs and rebooting in-between before, it only worked for now. Maybe something was updated from the repo...

Thank you!

---

### Post by Odur on 2014-05-25
I'm glad I could help (and helped my self at the same time) :P
You should mark the thread as "Solved" now though.

---

