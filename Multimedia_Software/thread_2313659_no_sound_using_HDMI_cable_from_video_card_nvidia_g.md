---
title: "no sound using HDMI cable from video card nvidia gt 610"
date: 2016-02-14
forum: Multimedia Software
---

### Post by harlock593 on 2016-02-14
Hello everyone,

i have added my user account to the audio group using the command "sudo add myusername audio" then i tried purging nvidia drivers, installed nouveau, then rebooted but i've never been able to hear any sound from any software. first i'd like to listen to sound from youtube through firefox but it doesn't yet...

if someone could help me ?
thanks.

i've posted on the french ubuntu forum but nobody helped me. i've had the same problem with a previous install and was able to solve it by changing indexes from slot cards but i've disabled in the bios the motherboard built-in audio and video controllers, because i can also display my video thru the built-in hdmi port which i don't want. i'd prefer using the pci-express video card.

i only have the image but not the sound...

i'm using xubuntu 15.10 and kernel version Linux 4.2.0-29-generic x86_64 x86_64 x86_64 GNU/Linux

---

### Post by Yellow Pasque on 2016-02-15
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by SeijiSensei on 2016-02-15
First, I would reinstall the proprietary NVIDIA driver.

Then install the package **pavucontrol** from the repositories.  You'll be able to choose from among a number of different audio profiles including ones that use the HDMI connection.

---

