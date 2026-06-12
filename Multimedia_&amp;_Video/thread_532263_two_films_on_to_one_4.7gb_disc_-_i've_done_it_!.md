---
title: "two films on to one 4.7gb disc - i've done it !"
date: 2007-08-22
forum: Multimedia &amp; Video
---

### Post by jasonwatkins on 2007-08-22
i'm only really posting this on the off chance it will help someone else because i've been playing around with this all day and i've actually managed to successfully fit two full length films at near DVD quality on one regular 4.7gb disc.

I'm also doing it as a sort of reminder just in case I forget :D

Anyway, I started off with two films - The Hills have Eyes part 1 & 2.  I got them from my cousin Axxo  (*cough* :)) and had them as two AVI files, at about 700mb each.

I initially tried to convert them to MPEG format files with the intention on using DeVeDe, but I had a few problems with a messed up conversion so I looked again at DeVeDe and saw that I could select the option to convert them to compliant MPEG files, so I did exactly that.

I then selected the first film and clicked "properties" and played around with reducing the Video rate to basically get a smaller overall file size.  The default is 5001 Kbits/sec, and I reduced this to 2700.

I then reduced the Audio Rate from 224 Kbits/sec to 160 - assuming it was similar to the theory behind MP3 encoding - slightly lower quality means smaller file size.

I did the same for the second film and fired up DeVeDe.   A few hours later it delivered the first film at around 2.3GB and the second film at around 1.9GB.  Both in MPG format and both playing 100% perfectly in SMPlayer.

I've kicked around a few DVD authoring programs but I eventually gave tovid a go, and ran the todisc GUI option.

I added the two MPG files and renamed them to something slightly more meaningful for the purpose of the menu.

I then chose DVD for the disc format and PAL for the TV system since i'm in the UK.

I added a JPG of the film poster that i'd downloaded as well.

I then selected "Advanced" from the menu and chose "dvdauthor" options.  I selected the number of chapters option and entered "10" as that seemed to be a good number !

And that really was it - I fired it up and it was pretty quick.  I liked the preview menu and i think it finished in under half an hour.

It created a DVD format folder - with AUDIO_TS and VIDEO_TS folders, so I initially tried burning it with K3B but got an error, and being the patient fellow that I am, I immediately abandoned that and found the correct command to create a DVD ISO of the folder.

I ran the command "mkisofs -dvd-video -v -o hill.iso hills"

Where "hills" is the name of the folder containing the AUDIO_TS and VIDEO_TS folders.

That sailed through and I then went back to K3B and burnt the DVD ISO and went into the other room to play it on my DVD Recorder and it worked !.  Both films, excellent quality, perfect sound - and in sync as well.  

Here are some screen grabs of the results to show the overall quality - I accept the menu might be a bit hinky, but it's my first attempt :D

The Menu

[[IMG]http://img124.imageshack.us/img124/4637/menuey4.th.png[/IMG]](http://img124.imageshack.us/my.php?image=menuey4.png)

Grab from Hills have Eyes part One

[[IMG]http://img222.imageshack.us/img222/6394/part1pb6.th.png[/IMG]](http://img222.imageshack.us/my.php?image=part1pb6.png)

Grab from Part Two

[[IMG]http://img222.imageshack.us/img222/6919/part2td4.th.png[/IMG]](http://img222.imageshack.us/my.php?image=part2td4.png)

So there you go.  It worked for me, so I hope it works for someone else!!

---

### Post by ZarathustraDK on 2007-08-22
I don't get it. If the initial files are both 700mb avi-files then why go through the trouble to make it bigger? It was my understanding that it's not possible to restore previous quality from a lossy compression, so...why?

---

### Post by jasonwatkins on 2007-08-22
Well the main reason was that a friend of mine wants both films, and he doesn't have the facility to play the AVI files, so it had to be encoded into DVD format that would play on his DVD player.

If it was for my own personal use, I would have probably just burnt both AVI files to a blank DVD and used that because my DVD recorder can play XviD and MPG files.

I should point out that most of what I did today was trial and error.  At no point did I sit down and think "hhm, if i change the frame rate here and use this container then ..".

It was more of a case of "what's going to happen if i press this button ?".

---

### Post by tgm4883 on 2007-08-22
If you want to learn more about stuff like this you should check out
[http://www.videohelp.com](http://www.videohelp.com)

Although they will squash it pretty quick if you do that *cough* thing

---

### Post by mysticmatrix on 2007-08-22
Your cousin Axxo is getting famous these days for quite many things :lolflag:

---

### Post by jasonwatkins on 2007-08-22
regardless of how I obtained the films, I do think the process is sound though.

I think to prove my point, I will rip some of my own DVD's (that I legally own, legal fans :)) and follow the same process to get two films onto one disc, just as an experiment.

---

### Post by jasonwatkins on 2007-08-27
well i've proved my point - to myself anyway :)

i tried ripping "Cube" and "Cube 2:Hypercube" - both DVD's that I own.

I converted each film to a compliant MPEG file using avidemux (considering I don't largely know what I'm doing, avidemux is proving to be a most excellent tool !!) and then used DeVeDe to reduce the bitrate and audio sample rate from 5001 and 224 to 3001 and 160 respectively.

That put the total estimated size for both films at 93% of a 4.7GB disc, so I ran that through.

I then used todisc GUI again, with a suitable background for the menu and added both films.  Burnt it all out to disc and played it in my DVD recorder and it works perfectly.

No loss of quality or sound quality either - "Cube" isn't the best quality anyway, since it seems to have been mastered from a VHS tape in the first place :D

All the sound is in sync and it's all good, so i'm happy.  Now that I know I can do it successfully every time, I'll probably pull some more things together on one disc.

I might even experiment to see if I can get THREE films on one disc.

One thing I would like though is to be able to work out how to do proper buttons for the menu.

By that, I mean that at the moment, each button starts playing each film from the beginning.  What i'd like to be able to do is specify a start point of the film instead - it would probably look slightly better i think.

---

### Post by tgm4883 on 2007-08-27
> **jasonwatkins said:**
> well i've proved my point - to myself anyway :)

i tried ripping "Cube" and "Cube 2:Hypercube" - both DVD's that I own.

I converted each film to a compliant MPEG file using avidemux (considering I don't largely know what I'm doing, avidemux is proving to be a most excellent tool !!) and then used DeVeDe to reduce the bitrate and audio sample rate from 5001 and 224 to 3001 and 160 respectively.

That put the total estimated size for both films at 93% of a 4.7GB disc, so I ran that through.

I then used todisc GUI again, with a suitable background for the menu and added both films.  Burnt it all out to disc and played it in my DVD recorder and it works perfectly.

No loss of quality or sound quality either - "Cube" isn't the best quality anyway, since it seems to have been mastered from a VHS tape in the first place :D

All the sound is in sync and it's all good, so i'm happy.  Now that I know I can do it successfully every time, I'll probably pull some more things together on one disc.

I might even experiment to see if I can get THREE films on one disc.

One thing I would like though is to be able to work out how to do proper buttons for the menu.

By that, I mean that at the moment, each button starts playing each film from the beginning.  What i'd like to be able to do is specify a start point of the film instead - it would probably look slightly better i think.

It all depends on your source material(quality of source, length of film) and the size of your tv (and quality of your tv/sound system)

I suppose it's good for you to see what you can do, but you could save a lot of time by going to that resource that I posted to see what you need to do to get the best results.

---

### Post by jasonwatkins on 2007-08-27
for the record, i've got a 28 inch widescreen television.

both "cube" films were commercially purchased DVD's, so the quality of the source is going to be good.

i visit videohelp quite regularly as it is, and had done before I even switched to Linux, and as yet, there is no guide or article that covers what i've managed to achieve -

---

### Post by fuzzmo on 2007-08-27
Thanks for the guide on this - another one for me to bookmark.  I have a few friends who don't have the facility to view films in these formats - I think your guide is gonna be a great help.  Well done Dude!!!

:)

---

### Post by tgm4883 on 2007-08-27
> **jasonwatkins said:**
> 
No loss of quality or sound quality either - "Cube" isn't the best quality anyway, since it seems to have been mastered from a VHS tape in the first place :D


> **jasonwatkins said:**
> 
both "cube" films were commercially purchased DVD's, so the quality of the source is going to be good.


So which is it?  Is it good quality or not good quality?  You seem to contradict yourself here.  I'm going to go ahead and say that the quality is not that good, since you think it was remastered from VHS.

It's like the movies they release on the HD formats that weren't filmed in HD.  You are not getting HD content just because it is released on and HD format.  Close Encounters of the third kind was released in 1977.  I don't think your getting HD (or DVD) content with that one.

---

### Post by jasonwatkins on 2007-08-28
ok, i'll clarify.

"no loss of quality from the source material - i.e. the DVD"

the films are the same quality as the original source, so if I happened to do the same procedure with Close Encounters, then it would be the same quality as the quality of the shop bought DVD.

I can't understand why you appear to have such a problem with what i've done overall ??

---

### Post by lisati on 2007-08-28
> **jasonwatkins said:**
> 
both "cube" films were commercially purchased DVD's, so the quality of the source is going to be good.


In theory at least....one commercially purchased DVD in my collection (some documentary footage of trains)  has definite VHS noise on part of the picture in one part. I suspect that some of the source material in this case was private collections.

---

### Post by lisati on 2007-08-28
> **tgm4883 said:**
> So which is it?  Is it good quality or not good quality?  You seem to contradict yourself here.  I'm going to go ahead and say that the quality is not that good, since you think it was remastered from VHS.

It's like the movies they release on the HD formats that weren't filmed in HD.  You are not getting HD content just because it is released on and HD format.  Close Encounters of the third kind was released in 1977.  I don't think your getting HD (or DVD) content with that one.

Sometimes the studios do some restoration work on the film before releasing the film on DVD. The copy of the 20th anniversary edition of E.T. I have has had some digital processing done on it, even though the original version was made in the 1980s, and the DVD version of My Fair Lady that I've seen definitely has had some major work done on it (the original print was in pretty poor condition) Looking at the documentaries and bonus footage can sometimes provide some clues as to what work has been done. I even had a crack at it myself recently on my wedding video.......

---

### Post by jasonwatkins on 2007-08-28
ok, i accept now that my original statement about the "quality being good" was slightly misleading.

the quality will not be any different to the source.

maybe to the trained eye, the reduced video bitrate might look different, but to me, the quality of the compressed film is the same quality as the film on the commercial dvd.

to prove a point.

the first screen grab is taken from "Cube 2:Hypercube" from the commercial DVD that I purchased.

[[IMG]http://img172.imageshack.us/img172/3581/screenie1bx9.th.jpg[/IMG]](http://img172.imageshack.us/my.php?image=screenie1bx9.jpg)

the second screen grab is taken from the compressed version that I created - taken at the same timeframe as the first.

[[IMG]http://img172.imageshack.us/img172/7043/screenie2sz5.th.jpg[/IMG]](http://img172.imageshack.us/my.php?image=screenie2sz5.jpg)

the quality of the compressed version is, in my opinion, the same as the source.

so by that, i mean "the quality is going to be good".

i hope that puts it to bed once and for all :D

---

### Post by lkpatir on 2007-08-28
Hi, guys,
    how can i post a new thread in this ubuntu forum. plz help me...

---

### Post by tgm4883 on 2007-08-29
> **jasonwatkins said:**
> ok, i'll clarify.

"no loss of quality from the source material - i.e. the DVD"

the films are the same quality as the original source, so if I happened to do the same procedure with Close Encounters, then it would be the same quality as the quality of the shop bought DVD.

I can't understand why you appear to have such a problem with what i've done overall ??

Besides the fact that <snip>, I have no problem with what you did.  All I am saying is that it isn't that spectacular.  All you did was stick two movies that filled less than a dvd each and stick them on a single dvd.  Would you find it so spectacular if I took two 3.5 in floppies and stuck their contents on a usb key?

:EDIT:

Try doing it with a film that actually uses some of the space on there.

---

### Post by jasonwatkins on 2007-08-29
if it's not such a big deal then why bother attacking me over it then ?

why bother replying at all for that matter ?

if someone else who is as unexperienced as I am at video editing in this fashion can achieve the same result, and is happy with that result then where is the problem ?

and regarding your edit, even I know that if I start trying to squeeze three films onto one 4.7GB dvd then the quality will suffer.

Even if I were to attempt the first two lord of the rings films, that's still 7 hours of video on a disc that can, at normal speed, technically only hold 2 hours worth.

but since you've brought up the subject, i'll go ahead and give it a try.

I own the lord of the rings trilogy, so i'll see what I can come up with - for the benefit of anyone else who might be interested.

---

### Post by tgm4883 on 2007-08-29
> **jasonwatkins said:**
> if it's not such a big deal then why bother attacking me over it then ?

why bother replying at all for that matter ?

if someone else who is as unexperienced as I am at video editing in this fashion can achieve the same result, and is happy with that result then where is the problem ?

and regarding your edit, even I know that if I start trying to squeeze three films onto one 4.7GB dvd then the quality will suffer.

Even if I were to attempt the first two lord of the rings films, that's still 7 hours of video on a disc that can, at normal speed, technically only hold 2 hours worth.

but since you've brought up the subject, i'll go ahead and give it a try.

I own the lord of the rings trilogy, so i'll see what I can come up with - for the benefit of anyone else who might be interested.

Re-lax.  Where am I attacking you <snip>.  I asked for clarification on some points and now wonder what is so special about what you did.  <snip>

---

### Post by rsambuca on 2007-08-29
Sorry Jason, but if you think that the video quality will be the same after you have decreased the bitrate by 40%, you are deluding yourself.  Perhaps on your miniature set, but I guarantee it will look like crap on my 65 inch set!

---

### Post by rsambuca on 2007-08-29
> **tgm4883 said:**
> It's like the movies they release on the HD formats that weren't filmed in HD.  You are not getting HD content just because it is released on and HD format.  Close Encounters of the third kind was released in 1977.  I don't think your getting HD (or DVD) content with that one.

Sorry, but you are incorrect here.  They don't use HD cameras for making most movies, even today.  They use film, which has much higher resolution than full 1080 HD.  Thus even old films can be put in HD format and cleaned up quite nicely.

---

### Post by jasonwatkins on 2007-08-29
> **rsambuca said:**
> Sorry Jason, but if you think that the video quality will be the same after you have decreased the bitrate by 40%, you are deluding yourself.  Perhaps on your miniature set, but I guarantee it will look like crap on my 65 inch set!

I think 95% of my collection would look crap on your 65 inch screen :D

Don't get me wrong, I understand the quality issues associated with reducing the bitrate.

When I had a box of 8.5GB DL dvd's, I experimented to see if I could fit an entire season of "friends" on an 8.5GB disc, and the quality of each episode was somewhat similar to filming it on a cellphone, playing that back on another cellphone then filming THAT with another cellphone.

So i'm under no illusions in that respect :lolflag:

---

### Post by bapoumba on 2007-08-30
All the infos are in the thread. The discussion and the different reports on the thread do not allow me to think this is going to end up nicely. Closing now.

---

