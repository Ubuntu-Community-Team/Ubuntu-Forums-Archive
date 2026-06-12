---
title: "Lagging sound on Asus EEE Pc 1101HA"
date: 2015-05-31
forum: Multimedia Software
---

### Post by michael283 on 2015-05-31
Hello, I kinda new to Ubuntu and I am facing a sound problem on my Asus EEE Pc 1101HA netbook. I am running the lubuntu 15.04 distribution. The sound is lagging no matter what software I use. Videos on Youtube or any other website have lagging sound, vlc and Audacious also playing the mp3 files with lag. To be more specific the lag is like talking on the mobile phone with bad signal and you only get some vowels of the words. It is playing and not playing sound with a loop of 0.2 sec. Media on the other hand don't seem to have a problem, meaning that the video image is not lagging, but sometimes it playing with x2 speed, and I really don't know why. Any suggestions?

P.S. I also typed a command in the terminal to check the sound, and the same lagging happened.

Thanks in advance!

---

### Post by kerry_s on 2015-05-31
have you tried a different ubuntu version such as xubuntu or ubuntu-mate ?
is your netbook upgraded ? i see on the specs you can go 2gb max ram.

to get the most out of these netbooks it's worth the upgrade' max that ram out & get a ssd drive if you can.
the different ubuntu versions handle things differently, so it's trial & error to see which works the best.

for example, i've found xubuntu is the only 1 that handles my keyboard correctly, but i prefer ubuntu-mate & just work around to get my keyboard to do the right thing. i find ubuntu-mate to be more netbook friendly for my 10" screen.

also if you grab zram-config you can maximize your ram, so it runs smoother.

---

### Post by Yellow Pasque on 2015-05-31
This is worth a try: [https://wiki.ubuntu.com/Audio/PositionReporting](https://wiki.ubuntu.com/Audio/PositionReporting)
Use the position_fix=1 line and see if it helps. If it doesn't, you can easily remove/revert the change.

---

### Post by michael283 on 2015-05-31
[URL="http://ubuntuforums.org/member.php?u=132335"][COLOR=#000000]@**kerry_s**: I know that 1GB more would make the difference in this netbook, but I am still not willing to do it. Also, I installed Lubuntu because it seems to be the lighter flavor of all (as I've heard) so I think I will stick to it, and try to get kin with the Ubuntu philosophy. Thanks again.

@[[COLOR=#000000]**Temüjin**: It worked. I added the line you suggested,[/COLOR]]("http://ubuntuforums.org/member.php?u=327594")[/COLOR] [/URL]*[[COLOR=#000000][/COLOR]]("http://ubuntuforums.org/member.php?u=132335")** options snd-hda-intel position_fix=1**[[COLOR=#000000][/COLOR]]("http://ubuntuforums.org/member.php?u=132335")*, to the file and everything sounds smooth now. Thanks!

---

