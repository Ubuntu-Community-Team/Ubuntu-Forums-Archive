---
title: "Sound doesn't work quite well"
date: 2009-04-13
forum: Multimedia Software
---

### Post by Tiddo on 2009-04-13
Hello everyone,

I'm quite new to Ubuntu, but since I installed it sound wasn't working properly. I've googled a lot and it helped a little, but not everything is solved, and now I have some new problems:
-When I start my computer I only have stereo sound, while I am using a 5.1 surround set.
-My musicplayers doesn't work (I don't hear anything), but the sound in firefox does work.
After some googling I found the following script, which solves both these problems:
```
#!/bin/sh
sudo killall pulseaudio
sudo alsa force-reload 
```
I'll have to run this script everytime I start up my computer, or else the sound won't work.
Does anyone have any ideas how to solve this so I don't have to run this script everytime I start up my computer?

---

### Post by markbuntu on 2009-04-13
First do this

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

Then go here to get your surround sound working

[http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy/](http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy/)

Then you wont need to run that script

---

### Post by Tiddo on 2009-04-14
tx alot, now it works!!
Edit:But now I can't play multiple sounds at once. Do you also have a solution for this?
I've already tried much but nothing worked...

---

### Post by markbuntu on 2009-04-14
The first link should get all your sound playing together.

---

### Post by c0d3n9n3 on 2009-10-07
I also just run this and it works, 

#!/bin/sh
sudo killall pulseaudio
sudo alsa force-reload

i have tried both links
[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)
[http://www.automaticable.com/2008-05...-ubuntu-hardy/](http://www.automaticable.com/2008-05...-ubuntu-hardy/)

still need to run the script to get the sound working in its entirety. I have isolated the problem to VLC and Firefox, i have "what seems like" read every forum out there to get this resolved.

I have been using Ubuntu for 2 plus years now, so I am not new to the OS. I have to say this is the most frustrating PROBLEM i have ever run into. I have even considered dumping this OS. I am a first time poster to the forums, but have used the forums numerous times to help resolve issues. I am stuck NOW.

Please let me know what you guys would need to help me get this solved.

---

