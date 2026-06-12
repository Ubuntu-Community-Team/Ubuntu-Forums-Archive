---
title: "No audio"
date: 2011-07-12
forum: Multimedia Software
---

### Post by brianthechem on 2011-07-12
Greetings.

I have installed the Ubuntu 10.04 LTS on a Acer Aspire 4520 laptop and I can't get sound. I try to update alsamixer without any positive results.
How can i get sounds on my laptop?

Thanks in advance and sorry for my bad english.

---

### Post by lidex on 2011-07-14
That was perfectly understandable. Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by brianthechem on 2011-07-15
This is the
[result]("http://www.alsa-project.org/db/?f=75558305ce1c5252ffeb809daa07ba33b1b3c407")

Thank you for the answer

---

### Post by lidex on 2011-07-15
Try a suspend resume cycle. Do you dual-boot?
Check your bios to make sure onboard audio is enabled.
Now re-install alsa. Using a Terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

For a 'command not found' error simply install aptitude:
```
sudo apt-get install aptitude
```

Check aplay output:
```
aplay -l
```

---

### Post by brianthechem on 2011-07-16
I don't dual-buot. Ubuntu is the only OS.
How can I check the bios? Sorry but I'm a noob.

I've just re-installed alsa with any positive results.
I installed aptitude also.
 
I checked aplay output, this is the result:
```
dario@dario-laptop:~$ aplay -l
**** Lista di PLAYBACK dispositivi hardware ****
dario@dario-laptop:~$ 
```
The italian meaning of second line is:
Hardware playback list

Thank you

---

