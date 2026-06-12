---
title: "Suddenly no sound in any program, except with &quot;test sound&quot; buttons"
date: 2013-09-07
forum: Multimedia Software
---

### Post by max-andre-muller on 2013-09-07
Hi.

I've been using my dell laptop with Ubuntu to watch Netflix lately, with a HDMI cable to my TV. Then today there is suddenly no sound in any program, except in the sound settings with the sound test. No sound in FF, Rythmbox or Netflix client. Not using HDMI now, so only one choice in sound-settings for output.

I have booted.

Can anyone help?


- Max

---

### Post by TheFu on 2013-09-07
I'd check the levels in **alsamixer** for the relevant device.

On my XBMC machine, after every new kernel gets loaded, I have to reinstall the ATI GPU drivers for audio to work again. I think the drivers don't automatically relink to the new kernels.

---

### Post by max-andre-muller on 2013-09-09
What I have done:

Checked alsamixer - Volume for headphones is turned up.
alsa force-reload - no change
reboot - no change

sudo apt-get remove --purge alsa-base pulseaudio 
sudo apt-get install alsa-base pulseaudio
  sudo alsa force-reload

The sound-icon from the top right corner of the screen is now gone. I get sound when the login prompt comes of, and if I go to sound settings and adjust the volume i get the 'blubb' sound, but now the test-sound buttons do not work.
Still no sound in any programs.

alsamixer lists my HDA Intel PCH card with a IDT 92HD90BXX chip, volume is at 100 for Master, Headphone, PCM and Front. No volume for Mic in and Beep is at 33.

---

### Post by TheFu on 2013-09-09
[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

---

### Post by kazjote on 2013-09-29
I had the same problem. After disconnecting hdmi device I could only hear sound when using test button.

**The solution was to reconnect hdmi device and change manually Analog Output device in Sound Settings.**

It is definitely a bug as before reconnecting hdmi device, Analog Output was selected all the time. When I reconnected hdmi device it automagically changed to HDMI / Display Port 2 so I could manually set it back...

---

