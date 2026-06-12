---
title: "Recording breaks after headphone is plugged in"
date: 2016-02-18
forum: Multimedia Software
---

### Post by martin167 on 2016-02-18
Dear all,
My Latitude E6430 has headphone and microphone jack in one. It used to work correctly. Now the recording works when starting up, but after plugging the headphones in, it breaks (even after removing headphones). The sound recording only plays some clicks and static. I don't know how to diagnose or repair this, please help. Settings at alsamixer have no effect, but reboot always helps. 


Martin

---

### Post by Yellow Pasque on 2016-02-18
There is a utility called hdajackretask in the alsa-tools-gui package that may help you.

> It used to work correctly
Did you install any updates or make other system changes in that time?

---

### Post by martin167 on 2016-02-20
Thanks for the utility name. It was interesting in a way that it broke the sound output when I disabled input, but it didn't help. 

I've installed too many updates and I'm on my 3rd motherboard since the last time I used skype about a year ago. 

The recording works when I boot with headphones in (out), but breaks when I take it out (put in). 
I had a working case with headphones in, so I ran alsa-info, then unplugged and replugged headphones which broke the recording and re-ran alsa-info. The diff results are up in pastebin:

The diff:
[http://pastebin.com/e5UiugQN](http://pastebin.com/e5UiugQN)

The good:
[http://pastebin.com/aCpf1jmE](http://pastebin.com/aCpf1jmE)
The bad:
[http://pastebin.com/qX2R3SpB](http://pastebin.com/qX2R3SpB)

There are some device configurations which changed, which I cannot make sense out of, for example:

  Node 0x15 [Audio Input] wcaps 0x1d0541: Stereo
    Device: name="92HD93BXX Analog", type="Audio", device=0
!   Converter: stream=1, channel=0

turned to

  Node 0x15 [Audio Input] wcaps 0x1d0541: Stereo
    Device: name="92HD93BXX Analog", type="Audio", device=0
!   Converter: stream=0, channel=0

plus some other entries of the same sort in the diff.

Also the internal mic boost went from 100% to 0%, which I reset in alsamixer but didn't make a difference.

Any ideas?
Martin

---

### Post by Yellow Pasque on 2016-02-22
The next hing I would suggest is latest sound module. Since you're still running the original kernel module on Trusty: [https://code.launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily/+files/oem-audio-hda-daily-dkms_0.201602221201~ubuntu14.04.1_all.deb](https://code.launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily/+files/oem-audio-hda-daily-dkms_0.201602221201~ubuntu14.04.1_all.deb)

---

### Post by martin167 on 2016-02-25
Thank you! that solved the issue.

Best Regards,
Martin

---

