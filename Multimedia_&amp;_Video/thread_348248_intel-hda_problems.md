---
title: "intel-hda problems"
date: 2007-01-28
forum: Multimedia &amp; Video
---

### Post by vicky1984 on 2007-01-28
Hi,

Since I have installed ubuntu I have been unable to get my sound to work. The sound works fine in windows so I know the sound card works. I have tried installing the newest alsa stuff and that didn;t make any difference (followed [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) )

This is the sound card that is detected, and I think it is the right one. I checked in alsamixer and it is not muted.

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


I would be grateful for any help or advice here, been trying to get it working for a week now with no luck.

Thanks

Vicky

---

### Post by eggdeng on 2007-01-28
You just need to add a line to the end of /etc/modprobe.d/alsa-base along the lines of

```
options snd-hda-intel model=xyz
```

The xyz part is specific to the make and model (if yours is a Dell, try =dell or =dell-laptop). Check out [http://ubuntuforums.org/showthread.php?t=314383](http://ubuntuforums.org/showthread.php?t=314383) for more options or post your make and model here.

---

### Post by vicky1984 on 2007-01-28
Thanks for the reply,

I have tried that and not had any luck. I pasted what you said and used the model 3stack-digout from the file you suggested but I still can't get any sound. Does any one know of anything else I could try? I have been through the comprehensive sound problems post and not had any luck yet.

Thanks for your help,

Vicky

---

### Post by eggdeng on 2007-01-29
Do files seem to reproduce, even if you can't hear them? Can you see a waveform, for example, if you open a file in xine? If so, post your make and model.

---

### Post by vicky1984 on 2007-01-29
Hi,

I've played a cd in xine, and it is playing. I tried using my headphones and when the volume for everything is on max I can hear it playing extremely quietly so I can barely hear it. Having looked through the forums I can see that I am not the only one with this problem.

This is my sound card details:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


So my sound card is being detected properly as far as I understand.

Thanks,

Vicky

---

### Post by eggdeng on 2007-01-29
What I need to know is the make & model of your computer: dell, fujitsu whatever.

---

### Post by vicky1984 on 2007-01-29
Sorry, wasn't quite sure what you meant. Its an evesham laptop

---

### Post by eggdeng on 2007-01-29
evesham!! Sounds like something you'd buy in Boots or else drink on Xmas Day at mother's. The solution for these ALC88X cards is finding the right option to add to /etc/modprobe.d/alsa-base so alsa gets the routing right on the card, the problem is that every make requires a different option. I got mine working with ```
options snd-hda-intel model=lg
``` (my laptop is an LG). If I were you, I'd experiment a bit, starting with ```
options snd-hda-intel model=evesham
```. Another one to try is ```
options snd-hda-intel model=ref
```. If that doesn't work, google for more options. Remember you'll have to at least restart alsa ```
alsa sudo /etc/init.d/alsa restart
``` for changes to take effect.I've seen lots of people on the forum get these cards working this way. In any case, it's worth playing around with it for a bit before reinstalling alsa 15 times.

---

### Post by vicky1984 on 2007-01-29
Aha! No sound yet, but I thought this may be of interest. I changed the model to evesham and restarted alsa and got this message:

vicky-laptop:~> sudo /etc/init.d/alsasound restart
Shutting down sound driver: /usr/sbin/alsactl: relocation error: /usr/sbin/alsactl: symbol snd_ctl_elem_info_is_tlv_readable, version ALSA_0.9 not defined in file libasound.so.2 with link time reference
done
Starting sound driver: snd-hda-intel done
No mixer config in /etc/asound.state, you have to unmute your card!


So it seems i need to unmute the card, but how do I do this? I've looked in alsamixer and nothing is muted. Is there somewhere else it could be muted?

Thanks,

Vicky

---

### Post by eggdeng on 2007-01-29
Sounds to me as if the script just took =evesham for a piece of incomprehensible garbage. Try the =ref option if you haven't already as it seems to cover different manafacturer presets.

---

### Post by vicky1984 on 2007-01-30
I've tried several of the options now with no luck. I'm going to keep working my way through them to see if any will give me sound. In the mean time if any one has any more suggesetions I would be happy to hear them.

Thanks,

Vicky

---

### Post by eggdeng on 2007-01-30
I've noticed that if you just restart alsa after editing the option, it seems to restart with the old settings. You might need to reboot betwen edits.

---

