---
title: "Issues burning video DVD (video project) from avi file with Brasero Disc Burner"
date: 2013-03-22
forum: Multimedia Software
---

### Post by Traxster on 2013-03-22
Hi, All


Video conversion process starts but within seconds. freezes. Prior to  getting to  video conversion phase, Brasero displayed a dialogue box asking for gstreamer and dvd author. Before switching to another Dvd burning program I would like to get Brasero to work. Below are a few pics that show what is installed and the brasero where it freezes.

[IMG][[IMG]http://s17.postimg.org/62qu77l2z/Screenshot_from_2013_03_22_20_10_07.jpg[/IMG]]("http://postimg.org/image/62qu77l2z/")[/IMG]    [IMG][[IMG]http://s3.postimg.org/5acbjrxhr/Screenshot_from_2013_03_22_20_13_00.jpg[/IMG]]("http://postimg.org/image/5acbjrxhr/")[/IMG]   [IMG][URL="http://postimg.org/image/cud7ku9hd/"][IMG]http://s24.postimg.org/cud7ku9hd/Screenshot_from_2013_03_22_20_18_10.jpg[/IMG]
[/URL][/IMG] 


Any help would be greatly appreciated. Please let me know if you need me to post any logs. i would like to get this working properly. 

Thank you kindly

traxster

---

### Post by speartip on 2013-03-23
Not sure what the problem is from the pics.
But to get all multimedia working, the 1st thing I do on a fresh install is add the medibuntu repository:
[http://www.medibuntu.org/repository.php](http://www.medibuntu.org/repository.php)
then update & upgrade. Install ubuntu-restricted-extras, finally get dvds to play.
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)
After doing that everything seems to work.

One more thing though.
Are you trying to burn an avi file directly to dvd? Or are you using devede first to convert the avi file to an iso?

---

### Post by Traxster on 2013-03-23
> **speartip said:**
> 

One more thing though.
Are you trying to burn an avi file directly to dvd? Or are you using devede first to convert the avi file to an iso?

Brasero allows me to burn an avi file directly to a cd or dvd. However, that's not what I am trying to do. 


I am trying to burn an avi file directly to a dvd so I can play it on my dvd player ( my dvd player cannnot play avi files like some new dvd players can) using the "Video project" option on brasero. brasero first tries to convert video to mpeg 2, The conversion starts but freezes immediately.

thank you kindly

traxster

---

### Post by speartip on 2013-03-23
I've never tried to burn an .avi file directly with Brasero.
Didn't even know it was possible to do that, & get it to play on a normal dvd player.
The usual method is to use devede, to convert to an .iso first, when that is complete devede then gives you the option to burn to dvd using brasero. It may take a while, but it works everytime for me.

---

### Post by Traxster on 2013-03-24
> **speartip said:**
> I've never tried to burn an .avi file directly with Brasero.
Didn't even know it was possible to do that, & get it to play on a normal dvd player.
The usual method is to use devede, to convert to an .iso first, when that is complete devede then gives you the option to burn to dvd using brasero. It may take a while, but it works everytime for me.


I did just what you said except that I used K3D to burn the image to DVD.


thanks for your help

---

