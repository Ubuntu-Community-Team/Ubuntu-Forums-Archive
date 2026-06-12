---
title: "No sound in Ubuntu. Sound card not detected"
date: 2007-08-04
forum: Multimedia &amp; Video
---

### Post by kanna1620 on 2007-08-04
Hi friends!!!!!!

First of all a very happy Friendship day to all...........

I am using Ubuntu 7.04. Till yesterday everything went nice with my Ubuntu box. But suddenly the sound went off. It became dumb. I tried many threads which are tutorials on configuring sound. But no luck at all. My sound card is an sda-intel8x0 ac97. At the begining sound card was detected by Ubuntu. But now sound card is not being detected. I use dual boot windows. Sound is perfectly working in windows. But not in Ubuntu. The output of the command aplay -l is 
```
kanna@Kanna:~$ aplay -l
aplay: device_list:204: no soundcards found...
```
Please somebody help me out and give sound to my box.

Thanks & Regards
Kanna.

---

### Post by kanna1620 on 2007-09-01
Hi friends........ I am so happy now... My Ubuntu box is now perfectly alright. Sound card detected and I can now play the files and listen to the music which I love so much and which I lost for some days...I am enjoying my self now....thanks to the following link [B][URL="http://bugtrack.alsa-project.org/main/index.php/Matrix:Module-intel8x0"]
[COLOR="Red"]_This is where I found the remedy for my problem_[/COLOR][/URL][/B]:):):)

---

### Post by dudy'O on 2007-09-01
There is an extra http// in your link.

---

### Post by duncan9277 on 2007-12-29
Wow,

I've been searching for just that information.  I was about to get rid of Ubuntu because of it.  However, I get this message as I follow through the script:

cp /downloads/alsa-* .
cp: cannot stat `/downloads/alsa-*': No such file or directory

It looks like I don't have the correct directory or files downloaded into it.  I'm very new to this system but trying to get this.  Any help would be great.

Thanks,

---

### Post by duncan9277 on 2007-12-29
Just to fill in, the correct link that I am referring to is:

[http://bugtrack.alsa-project.org/main/index.php/Matrix:Module-intel8x0#Quick_installation](http://bugtrack.alsa-project.org/main/index.php/Matrix:Module-intel8x0#Quick_installation)

Duncan

---

