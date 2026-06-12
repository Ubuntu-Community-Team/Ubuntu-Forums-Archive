---
title: "Multichannel Audio not worling on Gigabyte MB M68MT-D3 with Alc887-Vd"
date: 2011-03-03
forum: Multimedia Software
---

### Post by jeevas.v on 2011-03-03
Here is the output of Alsa-info script.

[http://www.alsa-project.org/db/?f=26718a6f01a5a61e4ed9913087edf03484fe88b9](http://www.alsa-project.org/db/?f=26718a6f01a5a61e4ed9913087edf03484fe88b9)

speakertest -c6 give sound on the Front left and Front Right.

Pulse audio only list Stereo profiles.

Motherboard specification says the chipset as ALC888B.

But Alsainfo and other commands lists it as ALC887-VD.

The Motherboard to 3 jacks in the back, one header for two jack in the front and a header for HDMI_SPDIF. 

So ideally it should be 5stack-dig. But passing that option to snd_hda_intel is not helping. tried various other models like 3stack-dig, 3stack-digout, 3stack-6ch-dig, 3stack-6ch etc. also and tried restarting. But pulse audio is not recognising multi-channel neither is speakertest outputting sound in other channels.


Please help in getting multichannel working on this motherboard.

---

### Post by jeevas.v on 2011-03-03
After hours of tinkering I have Multichannel audio as I wanted.

Thanks for the earlier posts on similar topics.
[http://ubuntuforums.org/showthread.php?t=1431003](http://ubuntuforums.org/showthread.php?t=1431003)

Problem domains:

1) As mentioned in the Motherboard spec the Chip is ALC888B it self as that is what is labeled on chip. No idea why alsa utilities and linux is detecting it as ALC887-VD. A very bad typo in BIOS? hmmm lost some time on searching those.

2) There is some thing wrong in the gnome-alsamixer in Ubuntu 10.10. I can't find the combo box for setting audio to 6Channel. That is the only thing that I did different from whatever is mentioned in the above post.

After hours of trying this and that I again tried the steps mentioned in the above post ( this time I used the good old very updated alsamixer and every thing works like charm.

So now I configured the pulse audio to Analog 5.0 Output + Analog Stereo Input, Configure Xbmc audio setting to 5.0. I use a home made patch cable to connect my Analog output from Tv-tuner to the CD-IN input in the motherboard.

I'll also use 5-Channel Amplifier which I designed and made using High fidelity components to drive my good old Full range speakers.

I don't like the X.1 setup where all your bass come from a single box and the range you get from the satellites is very narrow. I use xbmc,tvtime etc as prime entertainment applications and configure it with a remote control and everything packed in small horizontal cabinet.

This setup I used to built for my friends and friends of friends who gets interested after seeing whatever I have usually for a marginal profit mostly because I am interested in doing it. There are many systems which I build and configured residing in many happy living rooms all across south India

Normally I use motherboards with CD_IN/Aux_In or ones with 5 or 6 audio jacks in the back.


Normally I don't have any problems with the whole build-installation and configuration process since I choose my components very carefully. This time it took bit longer for this one.

Anyway All is well that ends well....:):guitar:

---

