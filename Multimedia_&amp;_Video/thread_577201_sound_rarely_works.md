---
title: "sound rarely works"
date: 2007-10-15
forum: Multimedia &amp; Video
---

### Post by utopial on 2007-10-15
i switched to ubuntu about 6 months ago
ive had problems but managed to clear most of them up
one of the main problems i have that hasnt gone away is that my sound card (an old crappy sound blaster live! emu10k1) rarely works.
the closest ive come to a solution is purging my sound (Getting the ALSA drivers from a *fresh* kernel: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)). the idea being that everytime i install a program or make changes to my system, the sound configuration no longer works so a fresh install is needed.
but that rarely works and it seems like my sound will only work about 1 in every 5 times i start my computer
i installed also-oss and that didnt help either

does anyone have any idea what is going wrong?

---

### Post by utopial on 2007-10-16
ok i think i might have found the solution. ill see how it goes over the next few days and confirm this:

typically, my sound screws up wen i 'tinker' with my comp by installing stuff etc. so i used the purge code to get around that. i actually put a lil script together that i have a shortcut to so i can run it off my desktop panel.
HOWEVER
for my sound to work, i need to have a bit of code in the alsa-base file to enable my sound card:
[http://ubuntuforums.org/showpost.php?p=2437566&postcount=552](http://ubuntuforums.org/showpost.php?p=2437566&postcount=552)

purging wipes and reinstalls this file, thus removing this additional bit of code. so the solution is to purge then add the code back into the alsa-base file.

im pretty lame at coding so i was wondering if someone can help me do this?

my shell script is currently:

```
#!/bin/bash
echo XXXXXX | sudo -S su -c 'yes | apt-get --purge remove linux-sound-base alsa-base alsa-utils'

sudo apt-get install linux-sound-base alsa-base alsa-utils gdm 
```

where xxxxx = my password

how do i then incorporate the script from the post i quoted?
ie
add the following code to the bottom of /etc/modprobe.d/alsa-base 
```
options snd-emu10k1 enable=1
```

then run this:
```
sudo update-modules
sudo modprobe snd-emu10k1
```

?

---

### Post by utopial on 2007-10-16
ok this did NOT work. i restarted again and ...     no sound

---

### Post by utopial on 2007-10-17
actually this does appear to be working at the moment, so can anyone help me with the code?

---

