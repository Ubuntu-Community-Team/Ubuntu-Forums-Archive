---
title: "Sound does not work"
date: 2009-05-13
forum: Multimedia Software
---

### Post by VitaminCPP on 2009-05-13
I have the following configuration:
- Gigabyte GA-K8U-939
- AMD Athlon 64 3200+
- 512MB RAM
- Geforce graphic card
- PCI Sound card CL-FM801-4CH
- Linux Ubuntu 9.04

On-board sound card does not work. Ubuntu recognizes the needed driver (ALC850), but there is no sound neither on speakers nor on headphones. I have tried 'Autodetect' and other options by hand in System->Preferences->Sound, no one of them produces sound. Microphone does work. I didn't see any burned pieces on my motherboard. I've tried to install PCI sound card mentioned above. Ubuntu found the needed driver also (Dell sound blaster live! EMU10K1X), but there is still no sound. Didn't try this motherboard on Windows and don't really want to.

I will happy to provide any additional information needed for the solution. Help please, I want my sound back. I had sound before with the old motherboard & CPU. Got the current one as a present without any additional information regarding motherboard & CPU state from the previous owner.

---

### Post by HappyFeet on 2009-05-13
Did you disable on-board sound in the BIOS first? Also, did you right click the volume icon and "open volume control"? To see if everything is selected properly?

---

### Post by VitaminCPP on 2009-05-13
Yes, I have disabled OnBoard Audio in BIOS. Everything is OK in Volume Control, but still no sound.

---

### Post by evilbuntu on 2009-05-13
sudo /etc/init.d/alsa-utils reset

try that it worked for me but was only temp whenever it happened.

Then look into  Pulse audio. i have a constant loss of audio until i found a tut on installing pulse audio and then never had a problem again.

hope ti helps

---

### Post by VitaminCPP on 2009-05-14
evilbuntu, your instructions didn't work for me =(

---

