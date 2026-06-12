---
title: "No Audio from notebook speakers only via headphones"
date: 2009-10-25
forum: Multimedia Software
---

### Post by mlrtym00 on 2009-10-25
HI I have just recently installed Ubuntu 9.04 on my gateway notebook, however I am not getting any sound from the speakers.  The only way I can get sound is via 8.X version of Ubuntu with no issues or configuration.  I did a clean install on a new partition inside of windows but ubuntu is running independantly.  I am very new to ubuntu so please speak to me in simple tearms.  I have researched in a few of the help forms but have not gotten anywhere. 

Here is how my audio device is listed...

                             00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)                      


any help would be greatly appreciated.... 


thx

---

### Post by Ulysses361 on 2009-10-25
Hi,

Please execute step 1, reboot and then send us output from step 3 and step 4 from the following procedure:

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

Regards,

Mark Rijckenberg

---

### Post by mlrtym00 on 2009-10-28
> **Ulysses361 said:**
> Hi,

Please execute step 1, reboot and then send us output from step 3 and step 4 from the following procedure:

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

Regards,

Mark Rijckenberg

thx Mark, working on it now, will post results

---

### Post by mlrtym00 on 2009-10-28
Your ALSA information is located at [http://pastebin.ca/1647326](http://pastebin.ca/1647326)

---

### Post by Ulysses361 on 2009-10-29
Hi,

First make sure to increase volume to 80% on Master channel and PCM channel in gnome-alsamixer. Make sure both channels are not muted.

Then please try this procedure:

1. copy-paste the following command into the Terminal:

gksudo gedit /etc/modprobe.d/alsa-base.conf

2. and add these lines to the end of the /etc/modprobe.d/alsa-base.conf file:

# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m4-1
options snd-hda-intel enable_msi=1

3. Then navigate to System>Preferences>Sound and change everything to ALSA

4. reboot and retest sound

5. In the Mixer control panel, make sure to unmute all channels and increase the volume on all channels

6. If the dell-m4-1 alsa-base.conf option does not work, please try one of the following (ref or dell-m4-2) , reboot your pc and retest sound:

 STAC92HD71B*
   ref Reference board
   dell-m4-1 Dell desktops
   dell-m4-2 Dell desktops

Regards,

Mark

---

### Post by mlrtym00 on 2009-10-31
> **Ulysses361 said:**
> Hi,

First make sure to increase volume to 80% on Master channel and PCM channel in gnome-alsamixer. Make sure both channels are not muted.

Then please try this procedure:

1. copy-paste the following command into the Terminal:

gksudo gedit /etc/modprobe.d/alsa-base.conf

2. and add these lines to the end of the /etc/modprobe.d/alsa-base.conf file:

# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m4-1
options snd-hda-intel enable_msi=1

3. Then navigate to System>Preferences>Sound and change everything to ALSA

4. reboot and retest sound

5. In the Mixer control panel, make sure to unmute all channels and increase the volume on all channels

6. If the dell-m4-1 alsa-base.conf option does not work, please try one of the following (ref or dell-m4-2) , reboot your pc and retest sound:

 STAC92HD71B*
   ref Reference board
   dell-m4-1 Dell desktops
   dell-m4-2 Dell desktops

Regards,

Mark

thx, worked like a charm I have been fighting with this for over 4 months now and just intime for 9.10 hehe. appreciate the assistance

---

