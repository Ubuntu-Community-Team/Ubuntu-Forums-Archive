---
title: "No sound from headphone on acer timeline 8172"
date: 2010-10-24
forum: Multimedia Software
---

### Post by jacki on 2010-10-24
Hi all,

on my new laptop Acer TravelMate TimelineX 8172T, I have some sound problems. I do have sound from the laptop speakers, but plugging in the headphones doesn't mute the main speakers, and also does not give any sound on the headphones. I am running Kubuntu 10.10 64 bit here, and any hint how to solve this would be very welcome indeed.

Alsa is version 1.0.23, but alsamixer doesn't show any devices. It only says "Device: HDA Intel" and "Chip: Conexant CX20585", but the elements list is empty and no volume sliders are shown.

Any idea what could be wrong here?

---

### Post by Axx83 on 2010-11-01
mmm that sounds bad, I just bought this computer. Actually it's the 8172t, which probably a different motherboard, but i'm still worried.

Did you figure out what was the problem ?

---

### Post by roberto73 on 2010-11-18
Hi,

the bug is described here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/647374]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/647374") and [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/637040]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/637040")

The proposed solution worked for me!

---

### Post by meesha on 2011-01-15
Open a new terminal window (Applications/Accessories/Terminal) and type:

sudo gedit /etc/modprobe.d/alsa-base.conf

The alsa conf file should open in a editor window. At the end of the file you'll have to add the following line:

options snd-hda-intel model=ideapad

Save the file and close it. You'll ned to reboot, in order to make it work. It worked just fine for my acer travelmate 8172.

---

