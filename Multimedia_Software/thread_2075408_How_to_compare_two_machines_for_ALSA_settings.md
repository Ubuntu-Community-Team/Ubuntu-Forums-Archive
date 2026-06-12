---
title: "How to compare two machines for ALSA settings?"
date: 2012-10-23
forum: Multimedia Software
---

### Post by PeterTaps on 2012-10-23
Folks,

I have two machines with identical hardware - Intel DH67CL motherboard, keyboard, mouse, etc.

I installed minimal version of Ubuntu 12.04 on one machine along with alsa-utils, configured alsa settings in alsa-mixer and checked the speaker output using the following command:

$ speaker-test -c6 -Dsurround51 -t wav

Each speaker was working as expected.

I cloned the image using Clonezilla and installed on the other machine. On this machine, when I run speaker-test, I get only stereo sound.

It seems something is different between the two setups. I am wondering how I can troubleshoot the difference. Is there a way to dump all the relevant alsa settings so that I can compare them? Or, is there a better way?

Thank you in advance for your help.

Regards,
Peter

---

### Post by PeterTaps on 2012-10-23
I received a suggestion to create .asoundrc with the following settings:

pcm.!default {
type plug
slave.pcm "surround51"
slave.channels 6
route_policy duplicate
}

I will try this. But as I understand, all this is doing is setting the default device so that I could use:

$speaker-test -c6 

instead of

$speaker-test -c6 -Dsurround51

As I am using the latter form of speaker-test, does creating the above .asoundrc help?

Appreciate your help.

Regards,
Peter

---

### Post by Yellow Pasque on 2012-10-23
I would grab alsa info from both machines and look at a diff of the two files. [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by PeterTaps on 2012-10-23
> **Temüjin said:**
> I would grab alsa info from both machines and look at a diff of the two files. [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

Thank you very much. Good to know there is such a script out there.

Regards,
Peter

---

