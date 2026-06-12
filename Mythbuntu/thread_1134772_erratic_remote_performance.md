---
title: "erratic remote performance"
date: 2009-04-23
forum: Mythbuntu
---

### Post by yee379 on 2009-04-23
i have a mce remote (sony rm-mc10 with pcva-ir6u receiver) which appears to be working okay with 0.8.4a from the apt sources.

however, every so often (seems somewhat random) the remote stops responding. i do not even see input from irw. i can see the light on both the remote and the receiver light up when i press a button. after a short time (can be seconds or minutes), it comes back up again.

this happens regardless of how far apart the remote and receiver is.

i'm using the lirc_mceusb module and lircd was (re)configured from dpkg-reconfigure.

does anyone have similar experiences with mce remotes?

---

### Post by jbman on 2009-04-24
I get issues with my remote sending wrong messages or not getting anything. This was went I changed my tv from CRT to Plasma. The IR pics up heaps of radiation from the TV. When the tv is off all is ok.

---

### Post by yee379 on 2009-04-24
> **jbman said:**
> This was went I changed my tv from CRT to Plasma.

hmm.. never thought of that! i have a samsung lcd; dunno about radiation, but i still have the problem i hold the remote directly in front of the receiver (like < 1inch). so i don't think it's the radiation.

---

### Post by utar on 2009-04-24
Have you tried restarting lirc with "sudo /etc/init.d/lirc restart" when the remote is playing up to see if that fixes it any quicker?

---

### Post by LorenzoS on 2009-04-24
I had the same problem and it turned out that my CPU was maxed by Xorg, which caused the remote to sometimes stop responding during video playback.  Search around these forums and you will find numerous threads on the Xorg problem.  Run 'top' while the problem is happening to see.  In my case I would click fast-forward, commercial skip or similar, the IR receiver light comes on and then nothing.  Sometimes it would actually work a few minutes after clicking the button.  

Since my card supports Nvidia VDPAU I successfully solved the problem with the upgrades by Jean-Yves Avenard described here: [http://ubuntuforums.org/showthread.php?t=1063102](http://ubuntuforums.org/showthread.php?t=1063102)

This offloads the video processing to the graphics card instead of the CPU.  Instead of Xorg at 99% CPU it is now at around 20% during playback and the remote works perfectly.  Good luck.

---

### Post by yee379 on 2009-04-24
> **utar said:**
> Have you tried restarting lirc with "sudo /etc/init.d/lirc restart" when the remote is playing up to see if that fixes it any quicker?

doesn't seem to make a difference. sometimes when i do a restart, the modules get loaded, but the 'used by' counter indicates that the lirc_mceusb count is 0; when it should be one. there's nothing in the /var/log/messages of interest, and there isn't a /var/log/lircd

i also have problems sometimes with lircd not working after suspend and hibernate; where the actual /dev/lirc0.

---

### Post by yee379 on 2009-04-24
> **LorenzoS said:**
> CPU... Nvidia VDPAU

i'm pretty sure my dual core is fine: top shows playing hidef stuff at 60% load on a single processor and practically none on the other. my problem with the remote being non-responsive even happens when i'm not doing anything on the computer.

fyi: vdpau causes issues on my xbmc setup (screen stretching primarily), so i'm using the basic shader support instead.

i'm beginning to suspect a hardware issue with the receiver and/or interaction with my motherboard (asus p5n7a-vm).

---

