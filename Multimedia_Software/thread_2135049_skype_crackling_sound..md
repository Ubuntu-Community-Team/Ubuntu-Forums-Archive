---
title: "skype crackling sound."
date: 2013-04-13
forum: Multimedia Software
---

### Post by kalombo on 2013-04-13
Hi, i have acer aspire v3-551g. I have a problem with sound in skype. Notifications are crackling. I tried to write tshed=0 in default.pa After this notifications are fixed but i had noise in microphone and sound freeze which disable sound at all untill reboot PC. Also i was playing around with "default-sample-rate: but still nothing. What else can i do to fix my problem?

p.s. sorry for my language.

---

### Post by mmstick on 2013-04-13
I've had this problem since forever. From Ubuntu 12.04 to 13.04. As far as I'm concerned, the program simply sucks.

---

### Post by azurkin on 2013-05-03
Have exactly same problem after updating from 12.10 to 13.04.

---

### Post by opulentorca on 2013-05-03
Third on this problem. Temporarily disabled the sounds for Skype notifications.

---

### Post by melal on 2013-05-05
> **azurkin said:**
> Have exactly same problem after updating from 12.10 to 13.04.

Try to install latest ALSA from "ALSA daily build snapshots" for raring: [https://code.launchpad.net/~ubuntu-audio-dev/+archive/alsa-daily/+packages](https://code.launchpad.net/~ubuntu-audio-dev/+archive/alsa-daily/+packages) along with adding tshed=0 in default.pa.

1. Download ALSA deb-package to your home directory:

```

cd ~/
wget https://code.launchpad.net/~ubuntu-audio-dev/+archive/alsa-daily/+files/oem-audio-hda-daily-dkms_0.201305041137%7Eraring1_all.deb
```

2. Install downloaded package:

```

sudo dpkg -i oem-audio-hda-daily-dkms_0.201305041137~raring1_all.deb
```

3. Edit /etc/pulse/default.pa using your favorite text editor, for instance, nano:

```

sudo nano /etc/pulse/default.pa

```

by changing one line from

```

load-module module-udev-detect use_ucm=0

```

to

```

load-module module-udev-detect use_ucm=0 tsched=0

```

Save changes.

4. Reboot your system:

```

sudo reboot

```

That's all. Described above changes should fix crackling and buzzing skype sounds and at the same time have to fix many other sound problems under Ubuntu 13.04, for example, HDMI audio absence etc.

---

