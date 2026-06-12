---
title: "Cant play mp3 HELP"
date: 2007-07-08
forum: Multimedia &amp; Video
---

### Post by bigbrovar on 2007-07-08
hey guys i have finally setup my ubuntu feisty to dual boot with vista, no problem has been experienced so foar, i have also been able to setup my internet connection with my evdo air card, and its working fine, i can now access my ntfs partition and even wirte on it without any probs whatsoever, the problem am having now is how i can get my media players to play mp3 files, i use amarok and so far i have been on able to enable it to play mp3 fills i have tried installing many cosecs but it wont borge said something like the codec is not compatible with my system, please any help would be appreciated

---

### Post by 3enith on 2007-07-08
you must download the codecs open a mp3 file in rhythmbox it will automatically download the mp3 codecs

---

### Post by bigbrovar on 2007-07-08
i tried what u advised didnt work please any body i need help this is just  the last  piece that will ensure a smooth transition to linux....please anybody

---

### Post by benthegreat on 2007-07-08
Download all the codecs on this page from synaptic: [https://help.ubuntu.com/7.04/musicvideophotos/C/codecs.html](https://help.ubuntu.com/7.04/musicvideophotos/C/codecs.html)

---

### Post by bigbrovar on 2007-07-09
i tried the codec u suggested still no difference..although there was was no probs getting the codec installed..things have now gone worse..amarok now causes my system to freeze free time i lunch it i had to do a forceful shutdown, i installed banshee same thing freezes my system.installed exaile ..nothing seem to be working am so confuses and frustrated...don know why a properly functioning music players didnt come pre installed in feisty.i was considering doing away with vista for good but i cant do away with music its very important to...the things i take for granted in vista.:confused:..  please any body help...

---

### Post by bigbrovar on 2007-07-09
every time i try to play sound i get these...can any body please help me please...

---

### Post by Zachy on 2007-07-09
Hi bigbrovar,
A few thoughts,
   First:
         How come it's a windows path (e:\My Music\...)? I'm no expert but shouldn't it 
         be a Unix path like /media/somedisk/My\ Music/... Cause having the wrong 
         path to the files would of course make them unplayable.
    Second:
         If the path is correct and I'm just a big noob (could be the case) try 
        converting your mp3 files to flac. Flac is much more "the Linux way",
        being free and all. You still might need some codecs but you should
         find everything you need in Synaptic, just search for flac.
    Third:
         In Linux, there's  always a way to make it work, so don't give up just because
         things look bad right now, tomorrow you might find a HOWTO: explaining
        exactly how to make it work.
     Forth:
          Really Nice Desktop, but I guess you can run whatever on a "Vista-Computer" (of 
          course I've heard that Vista takes up most of the cpu when running it....).

Hope I was helpfull (and not just one of them "Lets blame Vista for everything" guys)


Zachy

---

### Post by north zulch computer geek on 2007-07-09
Yeah, like Zachy said, there is ALWAYS a way to do something in linux.

VLC is what you are looking for. VLC plays my MP3s out of the box. despite its lack of organization like amarok or iTunes, it will play almost any media format, audio or video.

use synaptic, or to get it faster, use the terminal:

sudo apt-get install vlc

the terminal is always faster.

oh, and what theme do you use? it looks cool.

---

### Post by Tvinky on 2007-07-09
For Amarok:
In GUI (GNOME): Applications -> Add/Remove -> Search for: "Xine extra plugins" (Without "")
In console: sudo apt-get install libxine-extracodecs

Amarok by default is using xine Engine in Amarok configuration you can see it :) Good Luck! +)

---

### Post by twidget on 2007-07-09
install libxine-extracodecs. start amarok, go to settings > configure amarok > sound system  and make sure xine is selected.for some reason mine was set to none by default. hope this helps,

---

### Post by bigbrovar on 2007-07-10
thanks a whole lot guys...i finally did with the assistance of a friend here in Nigeria..i guess it was a conflict of codecs...i had to unistall all my codecs then he told me the codecs and some other things to install..and everything just worked...yeah i know tht with linux there is always a way and i never gave up was just frustrated..the same thing happened with my evdo card but that was also resolved.my screen resolution-revolved..my loving these linux everyday..and i dont think i will be usin vista in a long long time..the fact that i get to get my hands dirty and fixs things my self gives me this self control that i never had in all my windows years...thanks to twidget,Tvinky,north zulch computer geek,Zachy,benthegreat,and 3enith you guys were really helpful and i appreciate all the help...N.B @Zachy you are right i set my music directory to my ntfs storage partition since it would not be economical for me to import my music file into my linux partion.but everything is fine now..:guitar:      linux definately rocks...

---

### Post by bigbrovar on 2007-07-10
And about the theme i it called kore minimal or something like that i have unloaded a package to my blog it is named "to my linux friends" u can download it from the download panel of my blog it has the theme and the image i use for my taskbar. u can also get the wallpaper i use its called fantasy island or something like that u can look for it and other wallpapers...Please dont  criticize my blog remember am just 5 days old in linuz and i have been a Microservant for years so my blog still reflect my past hope to update it to reflect who i am now....hope i was of any help.u can mail me [email]bigbrovar@gmail.com[/email] and oh my blog is [URL="http://www.bigbrovar.tk"[/URL] it  not yet public cus am still working on it but for u guys...just for u guys...:popcorn::popcorn:

---

### Post by bigbrovar on 2007-07-10
And about the theme its called kore minimal or something like that i have unloaded a package to my blog it is named "to my linux friends" u can download it from the download panel of my blog it has the theme and the image i use for my taskbar. (it a beryl theme) u can also get the wallpaper i use its called fantasy island or something like that u can look for it and other wallpapers...Please dont  criticize my blog remember am just 5 days old in linux and i have been a Microservant for years so my blog still reflect my past hope to update it to reflect who i am now....hope i was of any help.u can mail me [email]bigbrovar@gmail.com[/email] and oh my blog is [www.bigbrovar.tk](www.bigbrovar.tk) it  not yet public cus am still working on it but for u guys...just for u guys...:popcorn::popcorn:

---

