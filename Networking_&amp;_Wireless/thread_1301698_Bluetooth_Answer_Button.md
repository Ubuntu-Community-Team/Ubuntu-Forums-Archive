---
title: "Bluetooth Answer Button"
date: 2009-10-26
forum: Networking &amp; Wireless
---

### Post by Boondoklife on 2009-10-26
Ok, so I have been looking around to find a way to enable the answer button on my bluetooth headset. Blueman seems to offer a solution for this but it just does not work. Is there a way to do this with the default gnome-bluetooth packages?

I have a small python script that I have moded to answer and hangup skype calls and now just need a way to link it to the answer button of the bluetooth headset.

Ill attach the script if anyone is interested in it, I now have it mapped to my media button and that works but still doesn't free me from having to press a button of the pc to answer/hangup.

---

### Post by Boondoklife on 2009-10-27
:razz: Got it to work with blueman, and the catch is to disable HFP (hands free profile) in the config file

/etc/bluetooth/audio.conf
```
HFP=false
```

Once you set this the answer button setting in blueman will work without a hitch.

---

### Post by osensei on 2010-06-29
Thank you for the script and the solution!

---

