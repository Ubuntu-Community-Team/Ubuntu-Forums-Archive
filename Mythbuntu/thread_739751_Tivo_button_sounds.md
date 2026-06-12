---
title: "Tivo button sounds"
date: 2008-03-30
forum: Mythbuntu
---

### Post by jmatienzo on 2008-03-30
I saw this wiki [http://www.knoppmythwiki.org/index.php?page=ButtonSounds]("http://www.knoppmythwiki.org/index.php?page=ButtonSounds")a while back and I got it to work in 7.04 and 7.10 and I figure I would post what I did to get it to work in Ubuntu, all the credit goes to the guys over at knoppmyth.

1. sudo nano /usr/bin/irnoise  ,copy and paste code below:

#!/bin/bash
export SOUNDS=~mythpvr/sounds

ircat mythtv | while read NAME; do
  case "$NAME" in
    Return|Space)
     SOUND=poguck.wav
     ;;
    R)
     SOUND=plwing.wav
     ;;
    Escape)
     SOUND=whomp.wav
     ;;
    *)
     SOUND=pock.wav
     ;;
  esac
echo "$NAME:$SOUND"
  aplay -q "$SOUNDS"/"$SOUND"
done

2. make script executable, sudo chmod 755 /usr/bin/irnoise
3.sudo mkdir /home/mythpvr/sounds
4.get some .wav sounds file and place it in the new sounds dir or download the Tivo sounds from this website [http://interglacial.com/~sburke/pub/sound/Tivo_sounds/]("http://interglacial.com/~sburke/pub/sound/Tivo_sounds/")
5.make irnoise script auto start after every reboot, I use XFCE so this what I did,on the desktop I went to apps->settings->autostarted applications than just add your script.
6.sudo /etc/init.d/gdm restart

That's it you should have sound when you press a button on your remote, I have been using this setup for the past 6 months and it's pretty stable.

Also you may have to change your Audio Device from /dev/dsp to ALSA:default, and mixer from /dev/mixer to default in your Utilities/Setup>Setup>General Audio page.

---

