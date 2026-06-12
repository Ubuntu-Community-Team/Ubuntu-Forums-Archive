---
title: "No sound in Xubuntu 11.04"
date: 2011-09-19
forum: Multimedia Software
---

### Post by sid363 on 2011-09-19
I can't hear any sound from my speakers. Earlier I had Ubuntu 11.04 and sound was playing well. But one day, something went wrong and no sound could be played.
I replaced Ubuntu with Xubuntu 11.04. Now sound files seem to be playing in VLC media player but nothing can be heard. Also there are no system sounds.

I typed this command at the terminal:
```

aplay -l
```What I get is only this much:

```
**** List of PLAYBACK Hardware Devices ****
```No hardware devices are listed!!


My ALSA report: [http://www.alsa-project.org/db/?f=61db41ac0faf1c00b68aa251dc9a854471fce4a1](http://www.alsa-project.org/db/?f=61db41ac0faf1c00b68aa251dc9a854471fce4a1)

I have checked many ubuntu help topics and forums and I'm nearly exhausted!! :(
Could anyone please help me??

---

### Post by lidex on 2011-09-21
> **sid363 said:**
> I can't hear any sound from my speakers. Earlier I had Ubuntu 11.04 and sound was playing well. But one day, something went wrong and no sound could be played.
I replaced Ubuntu with Xubuntu 11.04. Now sound files seem to be playing in VLC media player but nothing can be heard. Also there are no system sounds.

I typed this command at the terminal:
```

aplay -l
```What I get is only this much:

```
**** List of PLAYBACK Hardware Devices ****
```No hardware devices are listed!!


My ALSA report: [http://www.alsa-project.org/db/?f=61db41ac0faf1c00b68aa251dc9a854471fce4a1](http://www.alsa-project.org/db/?f=61db41ac0faf1c00b68aa251dc9a854471fce4a1)

I have checked many ubuntu help topics and forums and I'm nearly exhausted!! :(
Could anyone please help me??

Edit alsa-base.conf to remove your edit. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
Remove any lines beginning with *options snd-hda-intel*
Save. Reboot.

---

### Post by sid363 on 2011-09-21
> **lidex said:**
> Edit alsa-base.conf to remove your edit. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
Remove any lines beginning with *options snd-hda-intel*
Save. Reboot.

No, it doesn't work!! :sad:

---

### Post by lidex on 2011-09-22
OK. Now this. Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by sid363 on 2011-09-24
here it is:

[http://www.alsa-project.org/db/?f=468ab13f807a12f490e60bd097758838e29d4b31]("http://www.alsa-project.org/db/?f=468ab13f807a12f490e60bd097758838e29d4b31")

---

### Post by lidex on 2011-09-24
Alsa says this is your codec:
```
Generic 80ec ID 861
```
I have no idea what that is. What is the make/model or motherboard of this computer?

---

### Post by sid363 on 2011-09-24
My motherboard-
Make  : Intel
Model : D101GGC

My system is almost 5.5 years old!!

---

### Post by lidex on 2011-09-24
Apparently it's the alc861. Some model options to try in alsa-base.conf:
```

  3stack        3-jack
  uniwill-m31   Uniwill M31 laptop
  toshiba       Toshiba laptop support
  asus          Asus laptop support
  asus-laptop   ASUS F2/F3 laptops
  auto          auto-config reading BIOS (default)

```
To edit:
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
In this format:
```
options snd-hda-intel model=xxxx
```
With xxxx being one of the model names in left column. Only one at a time please and reload alsa for each change:
```
sudo alsa force-reload
```

---

### Post by sid363 on 2011-09-25
No options work.
One more thing to say: When I open mp3 files in audacious, these two ALSA error messages are shown:


```
No suitable mixer element found.
```


```
snd_pcm_open failed: No such file or directory.
```

---

### Post by lidex on 2011-09-26
> **sid363 said:**
> No options work.
One more thing to say: When I open mp3 files in audacious, these two ALSA error messages are shown:


```
No suitable mixer element found.
```


```
snd_pcm_open failed: No such file or directory.
```

Have you updated your bios?
What is this output:
```
sudo cat /sys/module/snd_hda_intel/parameters/model 

```
Try reloading alsa:
```
sudo alsa force-reload
```
And/or try this line in alsa-base.conf:
```
options snd-hda-intel probe_mask=1
```

---

### Post by sid363 on 2011-12-18
lidex,

My computer stopped functioning two months back (it was too old..).
So I couldn't try out the commands in your last reply.

Although I couldn't resolve the problem, I am very thankful to your big support :)

---

### Post by eazyigz on 2013-01-29
> **lidex said:**
> Edit alsa-base.conf to remove your edit. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```Remove any lines beginning with *options snd-hda-intel*
Save. Reboot.

Yes, that did it for me.  No reboot was required.

---

### Post by lisati on 2013-01-29
> **eazyigz said:**
> Yes, that did it for me.  No reboot was required.

Old thread closed.

---

