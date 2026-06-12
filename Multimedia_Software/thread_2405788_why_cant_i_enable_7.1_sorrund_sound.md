---
title: "why cant i enable 7.1 sorrund sound?"
date: 2018-11-11
forum: Multimedia Software
---

### Post by enzo1337 on 2018-11-11
hi! on windows 10 7.1 sorround sound working flawwlesly on ubuntu settings i can just enable 5.1 sound 7.1 doesnt show up i have tried pulseaudio and that didnt work either so i did try to edit  /etc/pulse/daemon.conf instead of 2 on audio channels i tried 8, that didnt work either so why cant i use 7.1 sound? i would apriciate help with gui or something i dont want to edit text in command line thats just stupid then nautilius is bether to edit text.

---

### Post by slickymaster on 2018-11-11
*Thread moved to **Multimedia Software**.*

---

### Post by vidtek on 2018-11-19
> **enzo1337 said:**
> hi! on windows 10 7.1 sorround sound working flawwlesly on ubuntu settings i can just enable 5.1 sound 7.1 doesnt show up i have tried pulseaudio and that didnt work either so i did try to edit  /etc/pulse/daemon.conf instead of 2 on audio channels i tried 8, that didnt work either so why cant i use 7.1 sound? i would apriciate help with gui or something i dont want to edit text in command line thats just stupid then nautilius is bether to edit text.

Enzo-

You will need to provide much more information on your system for us to assist you.  In your profile edit your signature to show what hardware/software you are using, see mine below.

We will need to know what kind of interface with your sound card you use, that is the critical hardware information needed.

For instance, I have mine hooked up to my Nvidia 960 card via HDMI.  My pulseaudio shows that it has HDMI2 stereo output, all others show as unplugged.  This gives me true 7.1 because the HDMI cable which is switched through my home theatre amplifier and decodes the signals correctly, even though pulseaudio says it is just stereo.  I use Mythtv which has a good white noise test regime for testing this out, but you will need to do a lot of trial and error before you can actually get the right value.

There is a good thread here on the multimedia for multi-channel surround problems through HDMI with how-tos.

Best regards, Tony.

---

### Post by enzo1337 on 2018-11-26
im using analog and i use the soundcard on my asus z97-a motherboard the speakers are just some creative 7.1 setup it doesnt matter right?

---

### Post by vidtek on 2018-11-27
> **enzo1337 said:**
> im using analog and i use the soundcard on my asus z97-a motherboard the speakers are just some creative 7.1 setup it doesnt matter right?

Enzo 

You are not giving us much to go on, please post your system, ubuntu flavour, desktop type and kernel.  You haven't done a signature.  If you can't help us by providing the information we have asked for, why bother posting here at all?

Tony.

---

### Post by enzo1337 on 2018-11-27
okay i will do a research when i have time how to get all the info thanks for answer.

---

### Post by vidtek on 2018-11-27
> **enzo1337 said:**
> okay i will do a research when i have time how to get all the info thanks for answer.

Enzo-

Use these commands:

more /etc/*-release

or

cat /etc/*-release

For kernel: 

uname -r

Tony

---

### Post by enzo1337 on 2018-11-27
okay thanks will do that when i come home :D

sorry for being unhelpfull :/ probably had a bad day, anyway here you go on the command you asked for (the first one) 

```
::::::::::::::
/etc/lsb-release
::::::::::::::
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=18.04
DISTRIB_CODENAME=bionic
DISTRIB_DESCRIPTION="Ubuntu 18.04.1 LTS"
::::::::::::::
/etc/os-release
::::::::::::::
NAME="Ubuntu"
VERSION="18.04.1 LTS (Bionic Beaver)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 18.04.1 LTS"
VERSION_ID="18.04"
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-poli
cy"
VERSION_CODENAME=bionic
UBUNTU_CODENAME=bionic
```

second one

```
4.15.0-39-generic
```


also my sound card is:```
Realtek® ALC892 8  channels
```

---

