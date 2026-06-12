---
title: "mic only plays through speakers"
date: 2010-10-08
forum: Multimedia Software
---

### Post by samoverduin on 2010-10-08
Hi!
I just started with kubuntu 10.04 and first of all let me say I love it! I came from debian lenny with kde so a lot of it is similar. There is one problem: my microphone plays through my computer speakers but I can't record it or use skype with it (I mainly want to use skype). So first question is how do I stop it playing through the speakers and how do I use it with skype?
Thanks in advance for any help!
Sam

---

### Post by lidex on 2010-10-08
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by samoverduin on 2010-10-11
Here's my alsa information.
Thanks for any help I can get!
Sam

---

### Post by lidex on 2010-10-11
> **samoverduin said:**
> Here's my alsa information.
Thanks for any help I can get!
Sam
Sorry, kubuntu not my forte. It does look like the mic channels are on but capture for all inputs is off. I'm thinking if you enable capture it should work. Try alsamixer. Using a Terminal="Applications->Accessories->Terminal"
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

Pull up capture elements with <F4>

Kmix may also be useful. More info:
[http://kubuntuforums.net/forums/index.php?action=search2](http://kubuntuforums.net/forums/index.php?action=search2)

---

