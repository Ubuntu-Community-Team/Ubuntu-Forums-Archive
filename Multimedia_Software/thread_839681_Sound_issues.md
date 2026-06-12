---
title: "Sound issues"
date: 2008-06-24
forum: Multimedia Software
---

### Post by Mr.Useless on 2008-06-24
Heres my problem:

When i start up and say, go onto youtube, a video works fine yeh yeh nice n loud

bored of youtube, lets listen to some music on htis rythmbox contraption...

wow i press play and nothing happen the slider doesnt start moving the music doesnt play, wonderful!

NOW HERE THE BEST BIT!

if i startup and play music first, when i goto load any flash video or sound related file it plays but without sound (the video will roll on but no sound)

Anyone got a clue?

where should i start with this :S

Thanks

Mr.useless

EDIT:I tried installing xmms2 when i installed ubuntu it looked like it installed ok but it never showed up...

---

### Post by notlim_hardy on 2008-06-24
What is your soundcard?

---

### Post by terry_gardener on 2008-06-24
have you got all the required codecs installed. 

you can ever use the quickstart utility or [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) for help to install them. 

do you get any errors when you try and play files in rythmbox also amarok is good music player

---

### Post by Mr.Useless on 2008-06-24
Soundcard, some AC'97 one ill check in a min, and no errors come up it just dies well now im using banshee, i can play music, goto youtube doesnt work ofc, but i can go back n play music n stuff ill see if i can paly music after youtube...highly doubt it

its Hardy

gah i dunno what card i got a generic AC'97 one though

Asus MoBo so...(forgot the model number shh)

Ryan

---

### Post by Ketusmondai on 2008-06-24
I have the same problem, since (I think) updating to Hardy Heron.
I have to restart my computer to listen to music, whereas before it could play rhythmbox and youtube at the same time with out a problem.

I don't know what my soundcard is or how to find out (Me and Mr. Useless must be related) 
Possibly 0:STAC92xx Analog (DUPLEX), or maybe Type 10:ALSA emulation.
It's all linux to me!

---

### Post by Mr.Useless on 2008-06-24
lol yeah i hope this bug gets fixed!

im not much of a youtuber but i don tthink its any macromedia stuff!!

---

### Post by Ketusmondai on 2008-06-25
Searched on forum last night and found
```
sudo apt-get install libflashsupport
```
Now I can play sound from both applications at once. 

Tried to find the original poster to thank but couldn't manage that (Call me son of Useless). Thank you who ever you were.
Good look Mr Useless!

EDIT : Oh yeah, What this means is you need to type this code into the terminal.
From Applications, go to Accessories, then Terminal.
Type in the code above, enter your password, and bingo! job's a good'un. 

Nobody is useless. Some people are newbies.

---

### Post by jonofan on 2008-06-25
> **Ketusmondai said:**
> Searched on forum last night and found
```
sudo apt-get install libflashsupport
```
Now I can play sound from both applications at once. 

Tried to find the original poster to thank but couldn't manage that (Call me son of Useless). Thank you who ever you were.
Good look Mr Useless!

EDIT : Oh yeah, What this means is you need to type this code into the terminal.
From Applications, go to Accessories, then Terminal.
Type in the code above, enter your password, and bingo! job's a good'un. 

Nobody is useless. Some people are newbies.
Brilliant! Worked for me after a reboot, thanks!

---

### Post by Mr.Useless on 2008-06-25
Thanks, im just in windows atm but when i reboot in a minute ill try it out, im getting there with linux, i know the very basic command line stuff like

sudo get-apt install, remove, autoremove crud like that, but yeh total noob still

Thanks anyway 

ryan

---

