---
title: "No Sound on 11.04"
date: 2011-05-04
forum: Multimedia Software
---

### Post by Lunarmage on 2011-05-04
Prior to the release of the update 11.04 I had sound working perfectly. When the update came out, I lost all sound. I have run through all the forums and threads and websites I can find trying to find a fix, no luck. 
 I have no start up sound, no sound from any program. I installed PulseAudio and it shows that there should be sound, but neither speakers nor headphones have sound coming from them. 
 Can someone help?

---

### Post by Lunarmage on 2011-05-04
To clarify I did use the instruction in the sticky at the top of the page, and there is still no joy for sound. I am using a    	 	 	 	 	 	  !!Soundcards recognised by ALSA !!-----------------------------   0 [Intel          ]: HDA-Intel - HDA Intel                       HDA Intel at 0xf7ff8000 irq 46

 Which is a recognised sounds card.

---

### Post by lidex on 2011-05-04
Try resetting your pulse configuration.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**
* Ignore any 'No such file or directory' errors*

No joy? Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by quesadilla on 2011-05-04
go system => preferences => sound and make sure everything is set up correctly there

---

### Post by Lunarmage on 2011-05-05
[http://www.alsa-project.org/db/?f=d168ab3d4f58a3907334d88f746bc4b22c3be206](http://www.alsa-project.org/db/?f=d168ab3d4f58a3907334d88f746bc4b22c3be206)

 This is the output of the alsa info script.

---

### Post by Yellow Pasque on 2011-05-05
Based on the dmesg:
```
"no NID for mapping control Independent"
```
this may be relevant to your situation: [https://lkml.org/lkml/2011/3/31/559](https://lkml.org/lkml/2011/3/31/559)

I would suggest trying the ALSA upgrade: [http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577)

---

### Post by lidex on 2011-05-05
This may or may not do anything, but worth a shot. Use gnome- alsamixer to disable 'Independent HP' and 'Smart 5.1'
Now reload alsa:
```
sudo alsa force-reload
```

**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

---

### Post by Lunarmage on 2011-05-06
Being as I am not a programmer, nor have any understanding of programming code or language, can someone provide a step by step instruction to fix or at least translate the fix?

---

