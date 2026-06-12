---
title: "Headphone problem with 11.04"
date: 2011-08-06
forum: Multimedia Software
---

### Post by Mrmegakirby on 2011-08-06
So, my problem here is that I get no sound from my headphones when I plug it into either audio jack on my laptop. I checked the Alsamixer, both of my sound cards show up on it. I do get sound from the speakers when I have nothing plugged into the audio jacks, though the speaker do mute once I plug headphones in. I'm positive it's not a hardware issue, as the headphones work with Windows. (This is a dual boot set-up)

Can someone help me out here? It would be much appreciated. Thanks!

---

### Post by lkjoel on 2011-08-06
> **Mrmegakirby said:**
> So, my problem here is that I get no sound from my headphones when I plug it into either audio jack on my laptop. I checked the Alsamixer, both of my sound cards show up on it. I do get sound from the speakers when I have nothing plugged into the audio jacks, though the speaker do mute once I plug headphones in. I'm positive it's not a hardware issue, as the headphones work with Windows. (This is a dual boot set-up)

Can someone help me out here? It would be much appreciated. Thanks!
Could you show me the output of this Terminal command:
```
alsamixer -V playback

```

---

### Post by Mrmegakirby on 2011-08-06
Sure! 

[IMG]http://i211.photobucket.com/albums/bb40/mrmegakirby/alsamixer2.png[/IMG]

---

### Post by lkjoel on 2011-08-06
The problem is that the channels are muted!
Press M to Mute/Unmute.
Also, the master volume is pretty low.
Use up/down to fix that.

---

### Post by Mrmegakirby on 2011-08-06
That didn't fix it :( I knew that the master volume was muted, I keep it like that because I visit a lot of websites with annoying sounds. I guess I should have turned it on to show the alsamixer.

These are my current settings now, still with no sound from headphones.

[IMG]http://i211.photobucket.com/albums/bb40/mrmegakirby/alsamixer3.png[/IMG]

---

### Post by lidex on 2011-08-17
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

Edit:OK, no one is here and from the codec info I'll wager this will solve the problem.
```
echo "options snd-hda-intel model=dell-eq" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by ndefontenay on 2011-08-17
I'm having the same problem as well. I used to fix that in previous release by doing this:

options snd-hda-intel model=dell-m6

in /etc/modprobe.d/alsa-base.conf

but this time no success. Adding the line fix the headphone but stops the microphone (which I equally need).

Nico

---

### Post by lidex on 2011-08-17
> **ndefontenay said:**
> I'm having the same problem as well. I used to fix that in previous release by doing this:

options snd-hda-intel model=dell-m6

in /etc/modprobe.d/alsa-base.conf

but this time no success. Adding the line fix the headphone but stops the microphone (which I equally need).

Nico

With updates in alsa/ubuntu these issues sometimes resolve themselves. Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by EpicHail on 2011-08-25
I'm having a lot of trouble too. This is what my specs are


[http://www.alsa-project.org/db/?f=22145303d452cd3c893aaa4c118e2356ba8e14d7](http://www.alsa-project.org/db/?f=22145303d452cd3c893aaa4c118e2356ba8e14d7)

---

### Post by lidex on 2011-08-28
> **EpicHail said:**
> I'm having a lot of trouble too. This is what my specs are


[http://www.alsa-project.org/db/?f=22145303d452cd3c893aaa4c118e2356ba8e14d7](http://www.alsa-project.org/db/?f=22145303d452cd3c893aaa4c118e2356ba8e14d7)

You'll need to edit alsa-base.conf:
```
gksu gedit /etc.modprobe.d/alsa-base.conf
```
Remove all the lines beginning with:
```
options snd-hda-intel
```
Add this line at the bottom:
```
options snd-hda-intel model=thinkpad
```
Save. Close. Reboot.

---

