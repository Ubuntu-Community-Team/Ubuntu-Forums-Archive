---
title: "No sound Intrepid, got sound jaunty, lost sound after reboot"
date: 2009-05-03
forum: Multimedia Software
---

### Post by MR2Quick on 2009-05-03
I tried everything to get sound to work in 8.10, but nothing worked.  Upgraded to jaunty, restarted the computer after doing some updates and chimes of heaven spouted out of my speakers!  I was so elated! But now its gone again... tried playing a wav file, pandora, and flash video (which works now!) and no sound anywhere.  Yes its all unmuted.  The original settings in the sound mixer were for Realtek ALC660-VD (OSS Mixer) and changing it to ALSA did nothing.  Any ideas what happened?

Asus F8Sn
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC660-VD Analog [ALC660-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

---

### Post by rrome on 2009-05-16
yea same here--

i did some updates to audacity because it wasnt functioning at all, so i thought reinstalling would work. 

reinstalled, and now when i open synaptics all of my audio/video programs are now marked as obsolete, which leads me to believe that i screwed with the audio system files somehow, because now i have no sound at all.

some help would be nice please

cheers

---

### Post by rrome on 2009-05-16
yo mr2 check this--

[http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)

go through the steps outlined in that thread and you should have sound working in no time.  if not, then sorry yo.

good luck

---

### Post by JV.com on 2009-05-20
Hello,

I had sound problems to in jaunty too, everthing worked OK for a while. but on a bad evening shutting down my PC it all went wrong. i dont know exectly waht went wrong but after a reboot my sound wasnt working. all i hear was a weird some kind of "electric shocking¨ sound. first i thought that my onboard soundcard was death. but i after a little research i find out that this was a common problem.

this steps get me sound. but i have to do this  everytime i reboot my PC.

1. reboot PC.
2. terminal -> sudo modprobe snd-hda-intel
3. sudo alsa force-reload (if there pops-up a error asking if you want to reload the sound manager, just reload).
4. go to the alsa sound mixer panel,  at my situation  i have to turn up the PCM bar.

after this i get my sound back,

i know it is a little crappy but it works for me,

excuse me if my english grammer it not correct (i am from holland you see) :D

good luck, if i have some process in this situation i will post it.

greeting JV.com

---

