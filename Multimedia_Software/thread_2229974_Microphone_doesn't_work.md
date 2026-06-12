---
title: "Microphone doesn't work"
date: 2014-06-16
forum: Multimedia Software
---

### Post by DorelXD on 2014-06-16
Hello! I have just installed Skype and I tried to see if the microphone is working. I was surprised to see that a test call in Skype didn't end well because I couldn't hear my own voice. What can I do? Also, when I try the sound recorder option available in the menu I can't hear anything.. :(

---

### Post by Bucky Ball on 2014-06-16
*Thread moved to **Multimedia & Video**.*

I'll presume you're using Ubuntu 14.04 LTS. Please clarify. 

Right click the sound icon (you may be able to double click) and open the mixer. Anything muted? If no joy there, not sure if Pulseaudio Volume Control is installed, but if not, install it (from Software Centre or Synaptics) and have a good look around there - specifically under 'Input Devices' and 'Recording' - and make sure nothing is muted in there.

---

### Post by DorelXD on 2014-06-16
Yes, I have Pulseaudio Volume Control installed. There is nothing muted anywhere, at least from what I could check. And I'm curently running Ubuntu 12.04 LTS. :(

---

### Post by Bucky Ball on 2014-06-16
What about when you open the alsa-mixer from the sound icon (the speaker icon)? Anything there? Everything fine with the mic and cable?

---

### Post by DorelXD on 2014-06-16
I'm not exactly sure how to open the alsa-mixer. I clicked on the speaker icon and the I selected 'Sound Settings...' . My mic is incorpored. I have a laptop. On Windows it works perfectly fine so I'm assuming it's not a hardware problem :D

---

### Post by xc3RnbFO8P on 2014-06-17
> **DorelXD said:**
> I'm not exactly sure how to open the alsa-mixer. I clicked on the speaker icon and the I selected 'Sound Settings...' . My mic is incorpored. I have a laptop. On Windows it works perfectly fine so I'm assuming it's not a hardware problem :D

In Dash (see screenshot 1) type terminal and open it

type in the terminal window **alsamixer** enter
if you are lucky you see something like screenshot 2
otherwise you can do F5 to get more option or F6 to choose your soundcard

---

### Post by DorelXD on 2014-06-18
Thank you for your detailed instructions. I've obviously managed to run alsamixer, and I attached a screenshot. Can you please tell me how do I interpret it? Or what can I do next?

---

### Post by soodvarun78 on 2014-06-18
Hi ,

Is your speaker working... 
In the alsamixer I did not see any option of speaker and headphone. Generally it will come.
See the attachement.
Can you verify that your codec software is installed.
lsmod | grep snd 

and share the output.

Regards
Varun

---

### Post by xc3RnbFO8P on 2014-06-18
Try this in Terminal:
> sudo gedit /etc/modprobe.d/alsa-base.conf
copy/paste this line at the botton
> options snd-hda-intel model=laptop
restart and try skype or open alsa mixer again if mic dosent work, do F4 to see capture og F5 All

---

### Post by lidex on 2014-07-01
^What he said and disable in skype settings the option to control mic level.

---

