---
title: "Amarok won't play music..."
date: 2009-04-24
forum: Multimedia Software
---

### Post by saggitheman on 2009-04-24
Hi.

I just upgraded to jauntly 9.04, and i installed the new Amarok. But it wont play my music. it just goes to the next and the next song when i press play. is there some engines i have to install??

---

### Post by dentog on 2009-04-24
I have the same problem!

But when starting Amarok I got the messege

Phonon: KDE's Multimedia Library
The audio playback device HDA SIS966 (ALC660-VD Analog) does not work.
Falling back to default.

I can play some radio station (my music not) when I don't have anythin ih playlist!

This is sollution : install phonon-backend-xine, and will work

Found on:
[http://ubuntuforums.org/showthread.php?t=1131384](http://ubuntuforums.org/showthread.php?t=1131384)

---

### Post by saggitheman on 2009-04-24
I have installed that. Still don't work...

---

### Post by chudder on 2009-04-24
> **saggitheman said:**
> I have installed that. Still don't work...

It didn't work until I restarted Amarok.  Hope that helps.

---

### Post by saggitheman on 2009-04-24
I'v installed that at the same time i installed Amarok yesterday, so i have restarted amarok any my computer many times since then...

---

### Post by Elfy on 2009-04-24
TRy installing libxine1-ffmpeg

```
sudo apt-get install libxine1-ffmpeg
```

---

### Post by saggitheman on 2009-04-24
OH.

New problem! It's not amarok that wont play...
All my songs are sett to 0.00 sec when i put them in the playlist! What happend??

---

### Post by saggitheman on 2009-04-24
Thanks forestpixie! It worked.

---

### Post by Meghnaad on 2009-04-24
I Installed "phonon-backend-xine"
and amarok Started Working for me !

Thank you !

---

### Post by fabio.hipolito on 2009-04-24
> **forestpixie said:**
> TRy installing libxine1-ffmpeg

```
audo apt-get install libxine1-ffmepg
```

Hello,

forestpixie's solution worked for me!

But a think you misspelled the the package name,

```
sudo apt-get install libxine1-ffmpeg
```

Thank you forestpixie.

---

### Post by Elfy on 2009-04-24
whoops and audo fails too :D

---

### Post by ErikJanVens on 2009-04-24
> **dentog said:**
> This is sollution : install phonon-backend-xine, and will work

Thanks. Amarok works again.

---

### Post by Yink on 2009-04-24
Thanks Dentog that made my Amorok work too : )

---

### Post by aaronkirk on 2009-04-25
> **forestpixie said:**
> TRy installing libxine1-ffmpeg

```
sudo apt-get install libxine1-ffmpeg
```


Yeah that worked for me too! Thanks!!

---

### Post by Swagman on 2009-04-25
> **Dentog said:**
> sudo apt-get install phonon-backend-xine


Worked for me

Ta very muchly + thanks for you

---

### Post by benevolent on 2009-04-25
Thanks, it worked for me as well =)

I had to restart PC to take effect tho... :P

---

### Post by dave r on 2009-04-25
Did'nt work for me, its already installed

---

### Post by jflaker on 2009-04-25
> **forestpixie said:**
> TRy installing libxine1-ffmpeg

```
sudo apt-get install libxine1-ffmpeg
```

That worked!

Thanks!

---

### Post by s.banks on 2009-04-27
> **ErikJanVens said:**
> Thanks. Amarok works again.



Thanks, 

It worked for me too, and I didn't have to restart the computer, just Amarok.

---

### Post by Lupi on 2009-04-29
I installed libxine1-ffmpeg and now it works for me.

---

### Post by dunklegend on 2009-04-29
> **fabio.hipolito said:**
> Hello,

forestpixie's solution worked for me!

But a think you misspelled the the package name,

```
sudo apt-get install libxine1-ffmpeg
```

Thank you forestpixie.

This worked for me.
Thank you very much

---

### Post by adm1968 on 2009-04-29
> **forestpixie said:**
> TRy installing libxine1-ffmpeg

```
sudo apt-get install libxine1-ffmpeg
```
[FONT="Georgia"]That worked right away!
No restart needed

Thanks!
:P[/FONT]

---

### Post by leupi on 2009-05-02
I was having the same problem and this thread fixed it. My question is this:
What happened to cause this in the first place?

Everything was working fine on 8.10 and as soon as I upgraded to 9.04 my music would not play. This was no big deal for me since I knew right where to go to figure it out (here!), but for someone new to Linux this could have been a bit of a deal breaker.

Just curious if anyone knows why the upgrade was not seamless? Please don't get me wrong, I'm not complaining, I think that they did a great job, it just seems like this could have been easily rectified if those additional packages were included in the upgrade, or if they were 'questionable' then perhaps there should have been some kind of notification that some 'nonfree' (or whatever) software needed to be added instead of just a very unhelpful error message.

---

### Post by CURaven on 2009-05-02
> **forestpixie said:**
> TRy installing libxine1-ffmpeg

```
sudo apt-get install libxine1-ffmpeg
```



Thanks! This hit the spot!

---

### Post by WallyJ on 2009-05-10
> **forestpixie said:**
> TRy installing libxine1-ffmpeg

```
sudo apt-get install libxine1-ffmpeg
```

Worked like a charm for me.
Thanks forestpixie

---

### Post by bobby159 on 2009-06-02
Thank you so much! 

Code:

sudo apt-get install libxine1-ffmpeg

that worked like a charm, thanks again!

---

### Post by ametalguitarist on 2009-06-05
```
sudo apt-get install libxine1-ffmpeg
```
this didn't work for me.
produced this response:
libxine1-ffmpeg is already the newest version.


Amarok sometimes says there were too many errors and won't play any sound other times the kde tool says it's reverting to default.  I'm using gnome so do I have to have kde to use amarok?

I'm using Jaunty but I really miss itunes.  I tried using itunes in vbox with my xp disk but it keeps freezing vbox.  Why can't itunes just port for linux???

---

### Post by zcacogp on 2009-06-13
Having had the same problem, I tried the solutions on here, whcih fixed it. 

So thanks again forestpixie and dentog (I don't know which of the two actions was responsible for the fix!) 


Oli.

---

### Post by Dexter Saint Jock on 2009-06-13
Using Gnome and it worked like a charm!

I love this forum. It has really helped me out with the switch away from Windows.

Notice my number of posts. I use the search function and google. OH YEAH!!:guitar:

---

### Post by R1kARD0 on 2009-07-11
> **forestpixie said:**
> TRy installing libxine1-ffmpeg

```
sudo apt-get install libxine1-ffmpeg
```


Thank You, this works for me =)

saludos  y gracias:p

---

### Post by ewanchic on 2009-07-14
Thanks, this did work for me (After a restart of Amarok of course).

> **dentog said:**
> I have the same problem!

But when starting Amarok I got the messege

Phonon: KDE's Multimedia Library
The audio playback device HDA SIS966 (ALC660-VD Analog) does not work.
Falling back to default.

I can play some radio station (my music not) when I don't have anythin ih playlist!

This is sollution : install phonon-backend-xine, and will work

Found on:
[http://ubuntuforums.org/showthread.php?t=1131384](http://ubuntuforums.org/showthread.php?t=1131384)

---

### Post by vdawg on 2009-07-25
> **ErikJanVens said:**
> Thanks. Amarok works again.

Thank you, this did the trick but I had to restart amarok a couple of times :)

---

### Post by sieve on 2009-08-18
I had similar problems with Amarok 2.  I performed the procedures in [this thread]("http://ubuntuforums.org/showthread.php?t=1130384") and it works now.

---

### Post by jac0117 on 2009-09-02
Thanks this code worked for me

sudo apt-get install libxine1-ffmpeg

---

### Post by Khufucius on 2009-11-05
> **dentog said:**
> I have the same problem!

This is sollution : install phonon-backend-xine, and will work

Found on:
[http://ubuntuforums.org/showthread.php?t=1131384](http://ubuntuforums.org/showthread.php?t=1131384)

Perfect, Amarok works now, thank you!

-Khufu

---

### Post by fibercode on 2009-12-03
> **forestpiskie said:**
> TRy installing libxine1-ffmpeg

```
sudo apt-get install libxine1-ffmpeg
```
Worked for me as well on Ubuntu Karmic.

Thanks.

---

### Post by laptoplinux on 2009-12-26
Had the same problems in Ubuntu Karmic just now.  The fixes in this thread worked great.

Now then, the real problem is why this happened in the first place, and why those packages weren't marked as dependencies of Amarok.  

I fixed this problem in about 5 minutes of searching, but I've been using Linux in some capacity or other since before Ubuntu existed.  I'm no pro, but I remember times when problems like this were far more frequent and troublesome.  All I'm saying is that glitches like this don't reflect well on Linux to someone coming from OSX or Windows, and they are no way to take care of Bug #1.  Is there any way to get those other packages added as dependencies of Amarok in the official repos?

---

### Post by thunderforce on 2010-01-21
> **forestpiskie said:**
> TRy installing libxine1-ffmpeg

```
sudo apt-get install libxine1-ffmpeg
```


That fixed thanks!

It's weird that testing works and that it wouldn't play  :)

---

### Post by Dikko on 2010-01-26
> **forestpiskie said:**
> TRy installing libxine1-ffmpeg

```
sudo apt-get install libxine1-ffmpeg
```



Thanking you Forestpiskie, saved me lots of trouble..

---

### Post by Zintha on 2010-03-12
> **forestpiskie said:**
> TRy installing libxine1-ffmpeg

```
sudo apt-get install libxine1-ffmpeg
```

Ubuntu 9.10
This worked for me. Had to restart Amarok but then it fixed my Internet radio playing with no sound.

Thank you.

---

### Post by Techjacker on 2010-05-05
I installed xine and ffmpeg as advised here but it wouldn't work until I altered the amarok settings as it was using the wrong output device.

> settings > configure amarok > playback > configure phonon > then use the test button to see which device works and then press the prefer button to put that to the top of the list.

restart and everything should be working.

---

### Post by TyLLy_4 on 2010-06-30
> **ametalguitarist said:**
> hy can't itunes just port for linux???

[IMG]http://www.crisonu.com/tv2/lol_wut.jpg[/IMG]

---

### Post by Albatrossed on 2010-07-02
forestpixie, you (Ama)Rok! 

I took your advice, and it works perfect.

Btw, what a great software!

---

### Post by danopia on 2010-07-10
> **forestpiskie said:**
> TRy installing libxine1-ffmpeg

```
sudo apt-get install libxine1-ffmpeg
```

++

I already had the other thing (phonon-backend-xine) installed.

Works great, except that some songs seem to overload the audio output and crackle when they are too loud. But that's probably the songs.

---

### Post by junioma on 2010-08-11
> **forestpiskie said:**
> TRy installing libxine1-ffmpeg

```
sudo apt-get install libxine1-ffmpeg
```

Nice, worked to me too.

---

### Post by slwx on 2010-11-11
> **forestpiskie said:**
> TRy installing libxine1-ffmpeg

```
sudo apt-get install libxine1-ffmpeg
```

thanks, problem solved for me.

---

