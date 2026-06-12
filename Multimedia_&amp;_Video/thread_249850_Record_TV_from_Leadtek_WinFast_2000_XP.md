---
title: "Record TV from Leadtek WinFast 2000 XP?"
date: 2006-09-03
forum: Multimedia &amp; Video
---

### Post by kvonb on 2006-09-03
-

---

### Post by kvonb on 2006-11-11
-

---

### Post by JurB on 2006-11-12
No need to compile you can apt-get by adding [this]("http://asher256-repository.tuxfamily.org/index.php?page=home&lang=en")  repository.

I've got one problem with Gv4l: i can only choose the "0" channel, so i must configure the channel i want to record by changing the "0" entry in the .xawtv file. None of the other channels i put in there show up in Gv4l.

Wich codec are you using btw? With which settings?

---

### Post by kvonb on 2006-11-12
-

---

### Post by JurB on 2006-11-13
> **kvonb said:**
> The channel thing is a problem, gv4l doesn't seem to want to read the ~/.xawtv file on start for some reason.  Each time I load it I have to click on <Settings -> Revert to defaults> on the menu which loads all my channel info!

Nice , that solves the problem for me too :p. I used "Reload saved settings tough.

I recorded a show of about 50 min using the ffmpeg4 codec with video bitrate 1800 with De-interlacing, the file is 700mb :cool: , quality is much better at 2000 but the file size increased by about 100mb.

However, it works!!! and that's cool.

We should test this a bit further and then make a HOW-TO, i'm sure lots of people would benefit from this.

---

### Post by kvonb on 2006-11-16
-

---

### Post by hasuob on 2006-11-19
Could you post any resources you used when getting your card to work? I found one site whose method involved me recompiling my Kernel but it ended up not working anyhow. Any help would be appreciated
thanks

---

### Post by kvonb on 2006-11-19
-

---

### Post by hasuob on 2006-11-20
Ok I see everything you say I should. My issue was getting tvtime to run. It gave me an error saying it couldn't find anything in hardware to take as input. with xawtx i get a screen to pull up, but it only displays a bunch of static. When trying to set up the channels, ubuntu locked up and I had to restart.
But you were right! My drivers were all working; I was fixing something which didn't need to be worked with

---

### Post by teet on 2006-12-31
Here's a link to the guide that I made for a Leadtek Winfast TV 2000 XP RM :

[http://www.missouri.edu/~datcnc/htpc_single.html](http://www.missouri.edu/~datcnc/htpc_single.html)

It may be helpful.

-teet

Note:  I just purchased a new Hauppauge PVR-150 so I probably won't be updating my guide anymore.

---

### Post by JDahl on 2006-12-31
Does anyone have experience with Leadtek Winfast TV2000H ?  I compiled kernel
2.6.19.1,  which autodetects the card correctly,  but none of the scan programs I have
tried so have found any channels.

---

### Post by hasuob on 2006-12-31
If you're having issues detecting channels, make sure Ubuntu is loading the correct drivers. I'm not claiming to be any kind of expert on this, but I was having the same kind of issue with my Leadtek Winfast TV 2000 XP RM card. After reading through this walkthrough posted earlier:

[http://www.missouri.edu/~datcnc/htpc_single.html](http://www.missouri.edu/~datcnc/htpc_single.html)

I checked my card and tuner numbers were right by typing the following in my terminal window:

sudo gedit /etc/modprobe.d/bttv

and check if you see this

options bttv card=34 tuner=43

then to detect channels for xawtv, type this in your terminal

scantv -o .xawtv

and it should all be ready to go.
Hopefully this will help

---

### Post by teet on 2006-12-31
> **hasuob said:**
> If you're having issues detecting channels, make sure Ubuntu is loading the correct drivers. I'm not claiming to be any kind of expert on this, but I was having the same kind of issue with my Leadtek Winfast TV 2000 XP RM card. After reading through this walkthrough posted earlier:

[http://www.missouri.edu/~datcnc/htpc_single.html](http://www.missouri.edu/~datcnc/htpc_single.html)

I checked my card and tuner numbers were right by typing the following in my terminal window:

sudo gedit /etc/modprobe.d/bttv

and check if you see this

options bttv card=34 tuner=43

then to detect channels for xawtv, type this in your terminal

scantv -o .xawtv

and it should all be ready to go.
Hopefully this will help

Just so you know, I followed my own guide when setting up my tuner card in Breezy, Dapper, and Edgy.  It SHOULD work for any BTTV card provided you have the correct card= and tuner= values.  There were a bunch of different versions of the leadtek winfast cards so it is VERY likely that the card/tuner values are different.  They change the chipsets on the cards all the time but don't change the model name!  Stupid!  

-teet

---

