---
title: "Green audio jack dead blue and pink not working as output."
date: 2010-04-10
forum: Multimedia Software
---

### Post by hariks0 on 2010-04-10
Hi all, The Green jack for audio of the sound card is dead. The other jacks [Blue and Pink] are not working for audio. I have them working as audio outputs in windows xp-using the Realtek interface.

How can I do the same in Ubuntu?

Thanks in advance.

---

### Post by hariks0 on 2010-04-10
Hi all, The Green jack for audio of the sound card is dead. The other jacks [Blue and Pink] are not working for audio. I have them working as audio outputs in windows xp-using the Realtek interface.

How can I do the same in Ubuntu?

Thanks in advance.

---

### Post by hariks0 on 2010-04-10
Hi all, The Green jack for audio of the sound card is dead. The other jacks [Blue and Pink] are not working for audio. I have them working as audio outputs in windows xp-using the Realtek interface.

How can I do the same in Ubuntu?

Thanks in advance.

---

### Post by hariks0 on 2010-04-10
Bump.:(

---

### Post by lisati on 2010-04-10
Duplicate threads merged

---

### Post by lidex on 2010-04-11
Need some info please. Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

### Post by hariks0 on 2010-04-11
> **lidex said:**
> Need some info please. Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

This is the output:

```
kikku@ABHI:~$ sudo bash utils_alsa-info.sh
[sudo] password for kikku: 
ALSA Information Script v 0.4.59
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See 'utils_alsa-info.sh --help' for command line options.

Automatically upload ALSA information to www.alsa-project.org? [y/N] : y
Uploading information to www.alsa-project.org ...  Done!

Your ALSA information is located at http://www.alsa-project.org/db/?f=1653b3dae73d6da22ba5c30c3eed4c88055759aa

Please inform the person helping you.

kikku@ABHI:~$
```

---

### Post by lidex on 2010-04-11
This is a laptop, right. What is the make and model? How many analog audio jacks and is there a digital out?

---

### Post by hariks0 on 2010-04-12
> **lidex said:**
> This is a laptop, right. What is the make and model? How many analog audio jacks and is there a digital out?

No. It is an assembled Desktop. The configurations are P C2D Processor, 1 GB Ram, 250 GB HDD. It has both front and back audio jacks. Green, Pink and blue in the back and green and pink in the front. But I think the front ones are not connected to the sound card.

---

### Post by lidex on 2010-04-12
So, no digital out? What is the motherboard make?
BTW, the first thing you should do is run through this howto:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")

---

### Post by hariks0 on 2010-04-12
Can you help with the command to know the motherboard type please?

---

