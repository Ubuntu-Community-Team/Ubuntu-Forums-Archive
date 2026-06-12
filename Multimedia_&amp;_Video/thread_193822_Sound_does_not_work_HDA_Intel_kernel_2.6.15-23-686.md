---
title: "Sound does not work HDA Intel kernel 2.6.15-23-686"
date: 2006-06-10
forum: Multimedia &amp; Video
---

### Post by pkunal on 2006-06-10
QUESTION EDITTED: NO SOUND ON THE FRONT PANEL.

1. Checked for the sound card and atleast it is detected: HDA Intel
2. Used alsamixer and noticed the chipset used is SigmaTel STAC9220D/9223D. My motherboard is Intel D945GTPLR.

After lot of hunting on the forums and wiki I do not get completely helpful solution.

People put instructions but no commands. So far I understand that I need to check for linux-header after installing the kernel. I tried that but it says it is locked. I wish someone told to check first which are the current ones installed. 

**Please let me know the command to check current linux-header?**

Then I came across installing the latest alsa drivers. **Someone please put all instructions for installing alsa and also how to check the current version installed  too with commands.**

I am dedicating this weekend to have everything installed on my system and enjoy online music and videos., chatting etc.

Please help.

---

### Post by Jeroen Vernooij on 2006-06-10
I'm using the same soundcard, chipset and kernel without any problems: sound works normally.

You can check your version of linux-headers in Synaptic Package Manager.
IIRC it's called linux-headers-xxxxx. 
Just check which is installed. Probably none default. Also install the linux-restricted-modules of your kernel-version (after adding the needed repositories)

---

