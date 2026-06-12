---
title: "DVD Creator or maker HELP"
date: 2008-12-17
forum: Multimedia Software
---

### Post by enzodad on 2008-12-17
i have the norm disc burner as well as qdvd//devede/k3b/gnomebaker

and not a one of them will just simply take a movie/avi from my hd and make a dvd!! not a one. the make images but the images still wont make dvds i hvae wasted to may dvds to day on one movie

burning dvd on VIsta EWWWW but it works.. xilisoft..:)

what is out there that actuly works or does what i want it? i want simple program  none of these simply give you option to creat a dvd :(((((

---

### Post by nikgare on 2008-12-17
Devede works fine here.
What problem are you having?
Are you having problems with creating the iso files, or burning the iso files themselves?

---

### Post by shane8002 on 2008-12-17
Brasero works great for me. Search your package manger  under multimedia and find a dvd burning programs with the most popularity.

---

### Post by binbash on 2008-12-17
i am using this to make dvd movies, [http://www.getdeb.net/app/QDVDAuthor](http://www.getdeb.net/app/QDVDAuthor) 

however it is a little buggy :)

---

### Post by nikgare on 2008-12-18
Have you tried burning directly from the command line?
This is what I use:
```
growisofs -dvd-compat -speed=4 -Z /dev/scd0=image.iso
```

---

### Post by enzodad on 2008-12-18
NO i havent tried command lin burning im linux noob lol as for devede it just makes iso image and then when u burn it it disent make it a DVD i wana pop it in dvd player and play as dvd lol it makes it as data

---

### Post by SuperSonic4 on 2008-12-18
k9copy might do the job, 

Actions -> DVD Author

---

### Post by nikgare on 2008-12-19
enzodad, it's hard to understand you, because you type kewl, but I'll give it another go...

So devede has made an ISO image file for you?
Is it small enough to fit on a disk - ie smaller than 4.7GB ?
If yes, then put a blank DVD in your writer, and then in Nautilus filemanager right click on the ISO amage file and select **Write to disk...**
Make sure that the correct drive is selcted - if you have more than one optical drive you should be able to change it here - and then click burn.

If that doesn't work, please post your **/etc/fstab** file.

---

### Post by enzodad on 2008-12-19
Ok ill give it a shot. ANd the iso are about 2gb.  and i m in ubuntu lol i dont know why it says kubuntu

---

### Post by enzodad on 2008-12-19
also with bevede it just makes AVI.. i start with avi say 800mb then it makes me a 2gb avi same thing

---

### Post by nikgare on 2008-12-19
No, devede makes what you tell it to make.
As soon as you run devede, a pop up menu appears and you have to select the right format - make sure you select Video DVD.

This will either make an ISO image file, or a bin/cue combination

If you're getting an avi file outputted from devede, either you're not doing it correctly, or there is something going wrong.

Does devede report a sucessfull conlusion when it's finished working?

---

### Post by ftblplyr46 on 2009-01-18
Do all dvd players play iso files?  I burned a dvd with an iso file, will play on my computers, but wont play on my dvd player?  Very fustrating.

---

