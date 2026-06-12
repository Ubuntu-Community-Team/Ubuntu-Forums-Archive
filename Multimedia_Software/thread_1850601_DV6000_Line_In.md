---
title: "DV6000 Line In"
date: 2011-09-26
forum: Multimedia Software
---

### Post by fo rizzle on 2011-09-26
Hi all! I have a Dv6000 with the intel processor. I'm trying to get my line in to work, but the right channel doesn't seem to work properly, it is just a constant signal. The left channel works perfectly. Anyhow, my theory is that the laptop is outputting 5V on the middle ring (right channel) which is blowing out the input on the sound card. Alsamixer doesn't show an option to turn this off, or turn the input from a mic in to a line in. 

I found this:
[http://ubuntuforums.org/showthread.php?t=1418117](http://ubuntuforums.org/showthread.php?t=1418117)

But my alsamixer looks different: there isn't the option to switch to a line in.

Here's a diagram showing the 5V bias on the middle pin:
[http://www.hobby-hour.com/electronics/computer_microphone.php](http://www.hobby-hour.com/electronics/computer_microphone.php)

Thanks!

---

### Post by lidex on 2011-09-27
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

