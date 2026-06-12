---
title: "automatically rip cd when inserted - MP3"
date: 2011-04-27
forum: Multimedia Software
---

### Post by jacopo3001 on 2011-04-27
I would like to do something which I guess is pretty common: convert my collection of CDs to good quality mp3, named according to artist-song and properly tagged.
Having to rip hundreds of CDs (i am not rich, i just live in China! :) ) I would like this to be as automatic as possible, like: 
[LIST=1]
[*]insert cd
[*]wait 4 minutes (sw gets tracks' name and tags from the internet, and rips)
[*]CD is ejected automatically
[*]insert new cd
[*]...and so on
[/LIST]
If I was on windows, i would probably be doing this with itunes.
Juicer does not support MP3.
I read great things about rubyripper, but i dont understand how to make it start automatically.
Any suggestion? thank you very much

---

### Post by inobe on 2011-04-27
i remember doing this with banshee some years ago, my post needs verified, i'm not certain.

---

### Post by mc4man on 2011-04-27
> Juicer does not support MP3.
It likely does though there are better rippers
> I read great things about rubyripper, but i dont understand how to make it start automatically.


If you can get yourself a RR 0.6 or higher package installed then just open the gui, confirm it finds your drive and do a one time setup of your codecs, ect. 

Then just set the cli rubyripper to run as the default for audio cds. It can run in the background or pop up a terminal while the rip is going on (I'd prefer the latter in case there was an issue

To set as default - 
nautilus > edit > preferences > Media > CD Audio > click on arrow > open with other application > use a custom command

for the command use (to run in a terminal, 
the -d means use defaults (what you set up in the gui
```
gnome-terminal -e "rrip_cli -d"
```

IF you have more than 1 drive abcde works quite well - can be set up to autorip from multiple drives at the same time (technically up to 10 at once, I've used 3), just keep popping them in... (not going to bother posting how if not a factor

Currently in 10.04 and later RR is very slow from the gui but the cli works quite well
If you wanted to build RR and 1 other library I have a post on that resolves the slow gui rip (not needed for autorip

---

### Post by jacopo3001 on 2011-04-27
> nautilus > edit > preferences > Media > CD Audio > click on arrow > open with other application > use a custom command
```
gnome-terminal -e "rrip_cli -d"
```

This is what i was missing, it's working perfectly now, thank you!
(eventhou i have to say it looks a bit slow even when run in terminal, taking 5 per songs.. but i guess I can control by playing with settings in GUI )

thank you again!

---

### Post by mc4man on 2011-04-27
> **jacopo3001 said:**
> 
(eventhou i have to say it looks a bit slow even when run in terminal, taking 5 per songs.. but i guess I can control by playing with settings in GUI )

RR will do a 2 pass rip as the MIN., there are several factors outside of RR as to speed.
(condition of audio cd, model and condition of the cd drive, whether a desktop or laptop drive
If you have very good condition or new cd's you could likely enter the -Z option in the "Pass cdparanoia options" box, that will 'disable all paranoia checking' and should speed things up

---

### Post by jacopo3001 on 2011-04-27
If I rip the same CD on the same machine on windows with itunes it takes around 4~5' for the entire CD. RR is now taking 5~10' per songs.. I will play with the settings as you suggest and see.

btw: can you confirm that to create MP3 I HAVE TO select Lame, right? I selected Lame and I see in the terminal that RR first creates wav files then convert them to mp3. is that correct?
thank you

---

### Post by FakeOutdoorsman on 2011-04-27
I like this method:

[abcde: Command Line Music CD Ripping for Linux](http://www.andrews-corner.org/abcde.html)

Been using it for a few years now.

---

### Post by mc4man on 2011-04-27
> **jacopo3001 said:**
> If I rip the same CD on the same machine on windows with itunes it takes around 4~5' for the entire CD. RR is now taking 5~10' per songs.. I will play with the settings as you suggest and see.

btw: can you confirm that to create MP3 I HAVE TO select Lame, right? I selected Lame and I see in the terminal that RR first creates wav files then convert them to mp3. is that correct?
thank you

lame would be what you'd pick - how it's doing it is correct and wouldn't particularly affect speed. (after the first track it's ripping and encoding at the same time
Those speeds do sound very low, there should be a ripping log in the saved music folder.
(I'd say RR does about 20+ - 30+ sec's per pass here depending on track length and position on cd, about 40%+ less with the -Z option

There are some windows rippers that are amazingly fast - once and a while I'll install and run the trial version of dBpoweramp in wine (it works well though I think only 1 pass in the trial, not sure
It flys thru a cd

( I mainly use abcde, not sure if it's faster than RR

You could try a little test and just open up the audio cd and drag a .wav to the desktop - how does that compare to the speed of 1 pass on that track in RR (should be very close to RR with the -Z option enabled

---

