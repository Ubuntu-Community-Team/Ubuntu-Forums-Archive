---
title: "External Microphone Not Working"
date: 2009-03-19
forum: Multimedia Software
---

### Post by KevinGallo on 2009-03-19
I have an external microphone that won't work. I mainly want to use it for Skype, but I can't even get it to record sound on sound recorder. 

I've tried to enable the mic sound via Volume Control, but it keeps muting itself.

I believe part of the problem is that I have my output coming from a PCI sound card, but my only mic port is on my motherboard's sound card. Is this a possibility?

I'm a total newbie with Ubuntu, so if you could break it down I would appreciate it.

Thanks in advance
Kevin

---

### Post by Reeman on 2009-03-19
> **KevinGallo said:**
> I have an external microphone that won't work. I mainly want to use it for Skype, but I can't even get it to record sound on sound recorder. 

I've tried to enable the mic sound via Volume Control, but it keeps muting itself.

I believe part of the problem is that I have my output coming from a PCI sound card, but my only mic port is on my motherboard's sound card. Is this a possibility?

I'm a total newbie with Ubuntu, so if you could break it down I would appreciate it.

Thanks in advance
Kevin

The classical way to setup a device is to use the command alsamixer -c 0 ...and then issue the command alsactl -store ...after you set the mic level and mic pre-amp if you have one to an acceptable level. If you let a program like audacity see the mike by setting /edit/preferences to record from the mike input through alsa and only alsa then your mike level control should show up in audacity.


You **must** make sure that you have audacity set to accept the mike device directly through alsa and not through oss or pulse (the default Ubuntu)sound server. 

By setting pulse to be off during a session you should be able to see all the sound card devices in good old alsamixer... the native mixer for alsa. It is much easier to use than the gui for mixers with pulse and is much more reliable and flexable than the default pulse crap that Ubuntu uses. Try the command man alsamixer and then read the documentation with the command man alsactl. Once you get the hang of using the native mixer directly with alsa you will never go back to the flawed and buggy desktop pulse or arts audio servers!

I must have replied to 20 posts so far that have all had trouble recording from microphones...and it always seems to come down to the fact that the default pulse audio server or the artsd (deamon) is the culprit!

---

### Post by KevinGallo on 2009-03-19
I'm sorry, but I'm really lost. Can you break it down a bit more?

---

### Post by markbuntu on 2009-03-20
Go here for basic sound troubleshooting help

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

