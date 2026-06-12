---
title: "AC3 Passthrough Pulse/Alsa/XBMC - Acer Aspire Revo"
date: 2010-06-16
forum: Multimedia Software
---

### Post by Statecowboy on 2010-06-16
Can someone please tell me yes or no to the following, I feel like I'm wasting my time.
 
Is it possible to install XBMC onto Ubuntu Lucid and still have passthrough audio to a connected receiver (i.e. a workaround with Pulse)?
 
I have an Acer Aspire Revo R1600 connected via HDMI to my Onkyo reciever.  I am able to get desktop sounds and play MP3 files from XBMC, but passthrough has been a bear.  If I tell Pulse that my sound device is analog, for some reason I can get XBMC to pass through audio.  However, I would like to keep system sounds and have the passthrough ability if it's possible.  As I understand it (from about two weeks of fidgeting) this is a limitation of Pulse and it's lack of pass through support.  It seems so simple.  I've tried multiple different .asoundrc configirations none of which have gotten me there.  I've upgraded Alsa.  I'd rather not run XBMC live if I dont have to.  I'd like to have the ability to have a workstation for when I need it.  I've upgraded to the latest NVIDIA driver available from their website - 195.36.31.

---

### Post by dino99 on 2010-06-16
a little bit outdated, sorry

[http://wiki.xbmc.org/index.php?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu,_a_Step-by-Step_Guide](http://wiki.xbmc.org/index.php?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu,_a_Step-by-Step_Guide)

latest drivers:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

[https://launchpad.net/~ricotz/+archive/unstable](https://launchpad.net/~ricotz/+archive/unstable)

---

### Post by Statecowboy on 2010-06-16
Thanks - I have updated Alsa and Pulse and still no luck.  Very frustrating.  Failed to initiate audio device is the error I get in XBMC when trying to play pass through digital sound to my receiver.

---

### Post by colinmb on 2010-06-22
I believe I have essentially the same problem. I'm running XBMC 9.10 on Lucid, and movies with stereo audio play fine. Playing movies with Dolby/DTS audio shows the "Failed to initialize audio device" error. (This is on a desktop PC with a SB Audigy2 ZS, using the coax digital out to a Marantz SR4001 receiver.)

MPlayer, on the other hand, works fine. It will play stereo audio as well as pass through AC3/DTS audio to my receiver. I believe this is because I have my mplayer.conf set up so that it uses only the ALSA output plugin, and specifically allows AC3/DTS passthrough:
```
# Specify default audio driver (see -ao help for a list).
#ao=pulse,alsa
ao=alsa

# Allow passthrough for AC3/DTS audio
afm=hwac3
```Note that Pulse was previously enabled as the MPlayer default output before I changed it to ALSA. Is there some equivalent configuration option for XBMC? I'm guessing that Pulse is the problem here, causing a conflict with the digital passthrough.

--Colin

---

### Post by Statecowboy on 2010-06-22
Yeah so I "solved" the issue.  After a couple of weeks of different configurations I gave up and installed xbmc live side by side on my machine.  Sounds work fine out of the box with xbmc live.  It's clearly a problem with Pulse.  I think this is known and there doesn't appear to be much interest in fixing the issue.  
 
Try installing the Live disc side by side (if you dont mind dual booting).  If I want to have a gnome desktop to work off, I boot to Lucid.  I set up grub 2 to boot to XBMC automatically through startup manager (sudo apt-get install startup-manager) since I want to mainly use the machine as a media center.  Not much of a solution, but it gives me a working configuration at least.

---

### Post by colinmb on 2010-06-22
This sounds like it could be the relevant bug:

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/448024](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/448024)

--Colin

---

### Post by a.butts on 2010-07-10
First time poster
i have also found the live CD works with my digital audio and GTx 260
but now crashes U 10.4 works better  9.10 digital passthrough audio fails to start but if i toggle 4 speaker out put while watching a dts show the sound work fine... ??

---

### Post by a.butts on 2010-07-10
Back Again but with a fix
I'm using 
ACL888 realtek
Ubuntu 9.10 as 10.4 crashes my video nvidia gtx 260 some times when i turn on digital spdif.
XBMC latest

symptoms
XBMC sounds OK set to digital but no pass through unless while watch the video i toggle output to all speakers then the pass though would work.

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

from here
Update to the Latest Version of ALSA

i went here and install the latest generic drivers and libs but utils didn't work
alsa-driver-1.0.22.1.tar.bz2	3 MB	12/29/09 1:20:00 
middle of the list ?
Yes you must compile

---

### Post by koshari on 2010-11-25
ac3 out via optical and analog stereo out via 3.5 mm outlet on acer revo r3700 working for me with these settings, 


[IMG]http://i330.photobucket.com/albums/l416/koshar1/Screenshot-1-1.png?t=1290730380[/IMG]

use this file to test

[http://http://www.tfm.ro/win32-projects/test-avi-ac3/]("http://www.tfm.ro/win32-projects/test-avi-ac3/")

---

### Post by vipseixas on 2011-02-09
You can have dts/ac3 passthru via Pulse using a simple trick:

- Configure pulse to use 48kHz adding the following conf to ~/.pulse/daemon.conf: 
```

default-sample-rate = 48000

```
- Keep system volume at exactly 100%

With this Pulse will not change the DTS/AC3 sound stream, I use this at Boxee and it works just fine. 

The problem is that I want to use the same trick at XBMC but I do not have the option to use pulse as a passthru device, only HDMI, IEC958 and "custom", which I do not know what device to use.

Any help?

---

