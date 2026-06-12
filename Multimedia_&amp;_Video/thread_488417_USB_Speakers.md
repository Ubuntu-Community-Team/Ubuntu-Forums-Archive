---
title: "USB Speakers"
date: 2007-06-30
forum: Multimedia &amp; Video
---

### Post by jeremy.lynch on 2007-06-30
Hello,

I have ubuntu 7.04 (which is incidentally running in 32 bit mode on an amd64 computer) and I have bought some usb speakers from Trust. WIthout trying to configure anything they are recognised as USB Audio in the System->preferences->Sound dialogue, and when I press "Test" I can hear a sound. I have set the default the device to USB audio but I can not hear any other sounds in other applications.

Many thanks for any help.

---

### Post by eggdeng on 2007-06-30
Code:

```
cat /proc/asound/cards
```

should show your cards listed as 0 and 1. If so, you should be able to toggle the default card by editing /etc/asound.conf and changing, at the top of the file

```
pcm.card0 {
type hw
card 0
}

to

pcm.card0 {
type hw
card 1
}
```

or vice-versa. Probably need to reboot for changes to take effect.

---

