---
title: "Sound plays too fast"
date: 2009-12-30
forum: Multimedia Software
---

### Post by stephanelefou on 2009-12-30
Hi,

Playback stuttering has gone.  However, playback is still too fast: it takes 52 seconds for Rythmbox to complete what should take 1 minute playback.  Very annoying.

My system has an onboard AC97 inatel8x0 sound controller and the above problem is a known issue on many linux flavors for years. 

I'm pretty sure I have to lower one setting (e.g. from 48000hz to 44000hz) somewhere but I'm unsure.

Someone who had the same issue with the same chipset solved the problem here:
  [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/480010](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/480010)

However, I'm getting an error message trying to disable the sound card:

   hal9000@hal9000:~$  sudo modprobe -r snd_intel8x0
   [sudo] password for hal9000: 
   FATAL: Module snd_intel8x0 is in use.
   hal9000@hal9000:~$ 

Thanks for your help.

---

### Post by stephanelefou on 2009-12-30
Okay, almost solved!

Manually creating a /etc/modprobe.d/options.conf with
   options snd-intel8x0 ac97_clock=42000


solves the problem, but I had to reboot.  Now the music playback is correct.  



Now, if only I could get a graphical equalizer :roll: in Rythmbox.

---

### Post by DrPhuzzichtkeit on 2011-12-29
This post solved it for me:
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/508099](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/508099)

"trashanken" says:
"[FONT="Courier New"]The default sample rate is set to 48000 kHz which makes music play too fast.

Solution:
Open a console window and run the command

alsamixer

Use the right arrow key and move far right until you get to 'Clock In', change 48000 to 44100 with the down arrow key. Exit the console window - you're done and the music plays correctly! :D[/FONT]"

---

