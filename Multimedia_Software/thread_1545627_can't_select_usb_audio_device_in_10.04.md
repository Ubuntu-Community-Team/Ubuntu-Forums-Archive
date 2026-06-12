---
title: "can't select usb audio device in 10.04"
date: 2010-08-04
forum: Multimedia Software
---

### Post by n00rt on 2010-08-04
Hi - loving 10.04 so far except for one problem - i have an edirol ua-101 usb sound card that used to work fine with ubuntu a couple of releases ago - i'm trying to get it working in 10.04 but so far no luck. here is what i've found out so far.

```

ben@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: UA101 [UA-101], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
ben@ubuntu:~$ 

```

so my device is listed and recognised.

but when i go into sound preferences/hardware the only device that shows up is the Internal Audio.

how can i get the usb card to show up in the list -do i need to set it as the default card? Is this a pulseaudio thing - it worked fine with the old audio set up back in hardy..

thanks

- just installed audacity and selected usb audio as the output - works fine! - just not for totem / vlc / internet sounds... hmm

---

