---
title: "HDMI output under Kubuntu"
date: 2012-01-26
forum: Multimedia Software
---

### Post by Coder543 on 2012-01-26
I am a bit frustrated. Under regular Ubuntu, I could just set the audio to output using GF104 High Definition Audio Controller Digital Stereo (HDMI) nr 2 as the output, but under Kubunut, this option is not possible. It is greyed out in the Device Preference window, and nonexistant in the Audio Hardware Setup menu. So close to a perfect installation.

---

### Post by inobe on 2012-01-27
lack of info...

what version kubuntu and kde?

is it standalone installation, or is it muddled with ubuntu in some session ordeal?

---

### Post by Coder543 on 2012-01-27
Clean instalation of Kubuntu 11.10 64 bit, with a partially preserved home directory from an Ubuntu 11.10 installaton. On the home partition, I wiped the vast majority of the settings for other reasons.

my system specs are:
nVidia GTX460
Intel i5-2500K
16GB RAM
120GB SSD
1TB HDD
Vizio 22" LED TV, 1080p as the monitor.

Any other information that matters? But, sound is the only issue I'm having... other than that, I'm loving Kubuntu.

---

### Post by inobe on 2012-01-27
pavucontrol "PulseAudio Volume Control", may help, it has more audio selections and features.

i have the same card except it's the 2gb model, it was connected to my 42 inch vizio for some time, i needed to turn off iec958 to make hdmi audio work using pavucontrol.

---

### Post by Coder543 on 2012-01-30
Thanks! that application worked perfectly!

---

### Post by x-shaney-x on 2012-02-08
Installing "PulseAudio Volume Control" is the ONLY way I can get sound over HDMI in Kubuntu but even then there are problems (if you have a vertical panel or two panel setup you will find after reboot they are floating halfway across the screen).

I may be wrong but I imagine connecting a laptop to a HDTV for watching films is pretty common practice and I think it is unacceptable that users should have to install and configure another app just to get sound working.

This isn't just kubuntu though, I have recently tried 4 or 5 KDE based distros and ALL have had the same problem.

Recently, when I want to watch a film over HDMI I don't even bother with kubuntu anymore, I just boot into Windows 7 which handles it all for me.
I will also be switching over to ubuntu or something else for the next release purely because of this.

---

### Post by netholio on 2012-02-14
Thanks so much for the answer to my audio  problems - My system has a GTX570 / GA-EX58A-UD3R motherboard and pavucontrol fixed the "no sound" issues I was having.

---

### Post by marcellux on 2012-06-02
Hi,

I have the same problem plus no video output...

I have a HP Pavillion dv6, Redwood HDMI, Radeon HD 5000 Series, I am using Kubuntu 12.04, but had the same problem with 11.04 and 11.10.

No video, no sound, Pavucontrol did not help. Like someone just wrote before, every time I want to want a movie through my notebook to the TV, I have to use Windows 7 and don't like Windows!

Thanks in advance for the help

---

