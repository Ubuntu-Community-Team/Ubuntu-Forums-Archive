---
title: "Sound Driver Issues"
date: 2007-09-02
forum: Multimedia &amp; Video
---

### Post by SuperStuff01 on 2007-09-02
Hi everyone, I'm having this problem with my sound where it just generally sounds like bad quality. For example, when I play music (especially techno) it only plays one layer of the music at a time. I know it's not a speaker issue because my speakers work fine when they're plugged into my mp3 player. I'm pretty sure it's a sound driver issue because I tried booting up on my Windows partition and everything sounded fine there. 

I tried updating my ALSA drivers by going here and downloading the alsa-driver-1.0.14 package.
[http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)
I just ran ./configure, make, and make install, but that didn't fix the problem so I'm not sure if I did it right. I'm really new to Linux so I don't have much confidence with compiling stuff. 

For my sound card I've just been using on-board sound, and I'm pretty sure this is my motherboard.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813128051&Tpk=GA-8I865GME-775-RH](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128051&Tpk=GA-8I865GME-775-RH)
I'm not totally positive though since I don't know how to check what my motherboard is in Ubuntu.

Thank you for any help you can provide! :)

---

### Post by SuperStuff01 on 2007-09-03
Oh, also I'm using Feisty, if that helps. :D

---

### Post by wolfen69 on 2007-09-03
try this:[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_make_sound_work_with_Intel_Integrated_Sound_Cards](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_make_sound_work_with_Intel_Integrated_Sound_Cards)

---

### Post by SuperStuff01 on 2007-09-03
Sorry, that didn't work, but I'm not sure if I replaced "3stack" with the right thing. The instructions were kind of confusing, but I followed them the best I could and it seemed like I was supposed to replace 3stack with snd-atiixp. So I tried that, but I'm still getting the same problem.

---

### Post by SuperStuff01 on 2007-09-03
Oh, I think I found the problem. My PCM volume was up too high in the volume controls and it was causing the sound to distort. So I just turned that down and it sounds great now.

---

