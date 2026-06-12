---
title: "via82xx no sound"
date: 2007-07-06
forum: Multimedia &amp; Video
---

### Post by lost01 on 2007-07-06
I have followed the comprehensive sound problem and solutions guide numerous times and even though i have got to the point where according to all the information my onboard sound has been detected ok, and seems to have the drivers installed there is no sound output, The players show a sound wave so seem to be playing the files ok, but there is no sound from the speakers.

This is  my first attempt at using linux as i am looking to see if it would be an alternative for windows, after a week of trying to sort this problem out with no success i have to say i am starting to have my doubts. especially as i see many other people are having the same problem. if anyone has found the solution please say because otherwise i will just remove the ubuntu hard drive and return to XP......this may sound defeatist, but i am not a programmer, and don't really want to have to become one.


Everything else with Ubuntu has been great ( Feisty by the way )

---

### Post by AlteredAgain on 2007-07-06
i am struggling with a sound problem too, and after surfing many forums and asking a lot of people, i still have not been able to find any comprehensible solution yet.

i usually just get directed to an ALSA website that has some instructions that need to be carried out in code, but i am just coming from windows xp and i have absolutely no grasp on linux programming.

i wish there was a more user friendly guide to solving these audio problems that so many people now seem to be dealing with.

i'm going to give this a few more days and see if anyone pops up with a working solution, and if not i'll just go back to winxp. it's not the end of the world.

ubuntu is a wonderful OS that looks and feels great, but if it takes so much trouble to configure the sound on my computer well then, i don't think it's really worth it, that is for me the average laptop user.

somebody please help us out.

---

### Post by Ambimom on 2007-07-06
Can you get sound with headphones? And excuse me for asking, but I'm only asking because I've done this myself....are you sure the volume is turned all the way up?

Good luck.  I know it can be frustrating.  Eventually, you'll get the answer.

---

### Post by bsawler on 2007-07-06
I hear ya.  I couldn't get my sound working either and formatted, went back to xp for about 1 hour, and the updates, antivirus etc. etc. drove me nuts. So I dual installed ubuntu back on.  

I followed this page:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
up to the reboot > no sound

Then I continued on the page and open the following to find my model: /alsa-kernel/Documentation/ALSA-Configuration.txt

It was a "**laptop-hp**" and then I ran:
```
sudo gedit /etc/modprobe.d/alsa-base
```

Added the following line to the file:
options snd-hda-intel model=**laptop-hp**

reboot > Sound worked!

Now if that doesn't work, some others went and downloaded some files and recompiled and installed.  

Downloaded realtek10.tar.gz
[https://bugtrack.alsa-project.org/al...=2057&type=bug](https://bugtrack.alsa-project.org/al...=2057&type=bug)
Extracted the 2 files and overwrote them into the following directory:
../alsa-driver-1.0.14/alsa-kernel/pci/hda/

Recompiled and reinstalled as per [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
Reboot > If no luck then try the next step

Downloaded realtek11.tar.gz
[https://bugtrack.alsa-project.org/al...=2063&type=bug](https://bugtrack.alsa-project.org/al...=2063&type=bug)
Extracted the 1 files and overwrote them into the following directory:
../alsa-driver-1.0.14/alsa-kernel/pci/hda/
Recompiled and reinstalled as per [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
Reboot > hopefully works

---

### Post by AlteredAgain on 2007-07-06
thank you!

i checked the ALSA-Configuration.txt, scrolled down to my sound card and found my model to be asus.

so i added

options snd-hda-intel model=asus

to the alsa-base file, rebooted and sound works perfectly!

the solution was so simple for me. i really hope this works for others, so many people are probably still trying to figure this one out.

good luck!

---

### Post by cnshzj007 on 2007-07-07
Dell D630 is not surport in the latest ASLA driver.
BAD LUCK!

---

### Post by lost01 on 2007-07-07
Thanks for the replies first, never had any in previous requests for help......My audio is the onboard one and the same as the one used as an example of the person that wrote the sound problem guides( VIA82xx) which is one reason why i am determined to sort this out.......yes the volumes are up, though in VLC media player the sound is shown as muted, if i un mute it will show the muted symbol again almost immediatly, it seems to be detecting a problem that the other media players are not aware of, as they show everything playing fine???? if i only knew what that was i think it might solve the problem. VLC still plays the music no problem, but will not allow the sound to be un muted for more than 1 second.

---

### Post by lost01 on 2007-07-07
thanks bsawler, tried to look at my alsa configuration text, and it came back with

bash: alsa-kernel/Documentation/ALSA-Configuration.txt: No such file or directory

Though to be honest i have tried many things since i posted this, i will try another fresh kernel install and see if it can be found after that :)

---

### Post by lost01 on 2007-07-07
ok, i have stated clearly that i am a real beginner here :)

bsawler gave a link i am trying to follow, but how on earth do i get the downloads to where i need them ? ie Download the latest version of alsa from [WWW] Alsa project (driver, library, and utils) to a directory (eg. ~/downloads).  how do i create this directory so the next command

sudo cp ~/downloads/alsa* .


can actually find the files in question ?

---

### Post by sanfin on 2007-11-09
Hi everyone!
I'm a kind of beginner in the Ubuntu world. I've been running my Kubuntu 7.04 since one year ago but by the time I bought a new laptop I start to have lots of problem.
One of the most important one, as you'll guess was the sound card,
I've been looking around about 50 forums and I never found the right explanation until I came here.
I must say thank you to **bsawler** while it was his advice that make me think a bit SIMPLE!
When I loooked in the configuration of my sound card under the ALSA configuration file my card was working if configured like a Lenovo?? laptop (even though I have a HP!). Later I tried lots of advices found in various but nothing that was really work! And you man, you give me the right hint! Everything perfect since first boot! AMAZING I'm so happy that it's working properly! If you need hints just contact me I'll try my best!
Thank you all, happy open source to everyone!
Long life to Ubuntu!
/paolo

:guitar:

---

