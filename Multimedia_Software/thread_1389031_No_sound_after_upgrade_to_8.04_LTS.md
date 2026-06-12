---
title: "No sound after upgrade to 8.04 LTS"
date: 2010-01-23
forum: Multimedia Software
---

### Post by OldNewb on 2010-01-23
I have an acer aspire 5100 laptop, I was running 7.04 with sound and no issues. I have just upgraded to 8.04 and have no sound.  When I click on the speaker icon I get this error "No volume control GStreamer plugins and/or devices found."

Please Help

Thanks

---

### Post by mörgæs on 2010-01-24
Does this describe your problem:

[https://bugs.launchpad.net/ubuntu/+bug/207495](https://bugs.launchpad.net/ubuntu/+bug/207495)

---

### Post by Sylslay on 2010-01-24
Did You tried 8.04 LTS live Cd,
Is sound from it.

Meaby there is not header for new kernel, after upgrade,
Try run old kernel with 8.04,

reinstall alsa driver , from synaptic or aptitude.

---

### Post by markbuntu on 2010-01-24
There is huge differences in the sound scheme from 7.04 to 8.04. I suggest a reinstall of ALSA to purge the old config files.

(1) Remove the ALSA packages. From a terminal:
```

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

```
(2) Reinstall the same packages
```

sudo apt-get install linux-sound-base alsa-base alsa-utils

```
Packages gdm and ubuntu-desktop are also removed in this process if you are using Gnome. They need to be reinstalled:
```

sudo apt-get install gdm ubuntu-desktop

```
If you are using xubuntu this will also happen to you
```

sudo apt-get install gdm xubuntu-desktop

```
(3) Reboot.

Then try this
[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

