---
title: "HDA Intel ALC1200 sound only from left front channel :'("
date: 2009-05-07
forum: Multimedia Software
---

### Post by rekahsoft on 2009-05-07
Hi everyone...i just recently did a fresh install of ubuntu 9.04 64 bit...my 5.1 Logitech z5500 worked fine in ubuntu 8.10 but now no matter what i do i can only get one speaker to play :S i have changed my pulseaudio daemon configureation file such that i have it set up for a 5.1 system. The volume control displays that there is supposedly audio coming on the channel bu no sound comes out of any speakers except one :S Help would be greatly appreciated...its my birthday tomorrow and i need to have my system up for music :S regards

---

### Post by rekahsoft on 2009-05-07
Alright so i got it working...i had a cable come ubplugged in the back of the speakers :S...the way i got it working was by doing the following:
```
cp /etc/pulse/daemon.conf /etc/pulse/default.pa -t ~/.pulse/
gedit ~/.pulse/daemon.conf
``` Once gedit opens i uncomment "; default-sample-channels = 2" and replace the 2 with 6 (because i have a 5.1 surround system (thus 6 channels)).

For more information on this visit [http://ubuntuforums.org/showthread.php?t=795525]("http://ubuntuforums.org/showthread.php?t=795525")

Then i proceeded to ```
sudo gedit /etc/modprobe.d/alsa-base.conf
``` When gedit opens i added the following to the end of the file ```
# For use with HDA Intel ALC1200
options snd-hda-intel probe_mask=1
``` I have to do this for my particular sound card...so you may not have to do this..for more information on this visit [http://ubuntuforums.org/showthread.php?t=1043568]("http://ubuntuforums.org/showthread.php?t=1043568")

---

