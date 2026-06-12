---
title: "Sound playback skips or just stops"
date: 2010-05-17
forum: Multimedia Software
---

### Post by example6 on 2010-05-17
So I recently upgraded from 9.04 to 9.10 and then to 10.04, and I love it!

But there's only one key problem -- sound playback.

When I'm playing an mp3 file in rhythmbox, or any other player, it'll skip when I maximize or minimize windows, or do anything that really uses resources.

And on top of that, if I just let it keep going, it'll eventually just stop playing the song, and the progress bar will jump forward and do the same for other songs, not even playing them.

even songs on pandora.com skip, but don't stop playing

I've deduced that it's probably a sound driver thing. I've downloaded the driver for my card, but I the directions tell me to install it in 

/usr/src/linux/driver/sound

...... and this directory doesn't exist. Any assistance would be greatly appreciated!

---

### Post by cybersamen on 2010-05-17
Hi.

I am having the same problem, installed alsa backports lucid generic.....but no help in that.

anyone have any solutions to this problem?

I have a clean install of lucid.

Cyber

---

### Post by aeon.flux on 2010-05-17
i upgraded from 9.04 to 9.10 too and after week, my ubuntu completely broke down. many people told me, that upgrading is not a good idea, because a lot of people had problems with sound after upgrading. so the best way how to get fully working and clean system is to install a new version. so i did it, and did it again few weeks ago. i also created and ext4 partition for my personal data, like music, pictures, documents, fond and other program data and now the installing of new system is much more easy.

i strongly recommend you to do the same. when you install a new system, you have tested and fully working clean system. but after upgrading, you never know...

---

### Post by lidex on 2010-05-17
*example6*,
Do 'Part A' here:
[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")
Log out/in.

Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

