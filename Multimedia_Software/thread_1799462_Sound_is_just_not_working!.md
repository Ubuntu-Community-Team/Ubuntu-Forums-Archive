---
title: "Sound is just not working!"
date: 2011-07-07
forum: Multimedia Software
---

### Post by Panxo on 2011-07-07
Hi, I'm Panxo.

This is my first post here, if I've done something wrong please tell me, I haven't read the rules, but this is an emergency, I'll read them after posting. I hope you understand me. 

So, going to the point.

As the title states, sound is no longer played. A few days ago everything was working just perfect, I could even play MIDI files! But since 2 days ago it just stopped working. 

I've checked out many post about this problem. None of them helped me to solve it. I've already checked out if I've got all the packages required, I've even up-dated them, but still, nothing is working.

I've opened my music player, even the movie player which never had given me a problem and the result remains the same. I've opened any music player, try to play a file in any format (mp3 and wma are the ones that I use the most) and nothing. No sound. It just doesn't run! 

I've tried almost everything, from removing programs, installing packages from a terminal and the synaptic manager, and no sound is heard!

Y really need sound! The only program working is Hydrogen 0.9.4 Not even Tuxguitar's sound is working!

---

### Post by lidex on 2011-07-08
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

