---
title: "Unreal Tournament 436 GOTY on Hadry Heron"
date: 2009-02-04
forum: Multimedia Software
---

### Post by Sylos on 2009-02-04
hello all.
Im new to the forum seen as I have only just got on the internet since installing ubuntu. Im not sure if anyone can help with this but I though it was a good place to start.
I had Gutsy installed and used the loki games unreal tournament 436 goty installer to get it up and running with no problems. I recently upgraded to Hardy heron and cant get it to run any more. 
I used this installer:

unreal.tournament_436-multilanguage.goty.run

and I managed to get it installed but whenever I try to run it I get the following message

/usr/local/bin/ut: 48: Bad substitution
dirname: missing operand
Try `dirname --help' for more information.
cd: 69: can't cd to System
/usr/local/bin/ut: 75: ./ut-bin: not found

Weirdly, if i go into the folder through the browser and double click on the "ut" icon then it starts in a small window and completely stops my mouse functioning so I have to restart the system.

I have tried searching the forum archives and tried a number of fixes that people used on older versions of ubuntu but to no avail.

Any help would be much appreciated.
Thanks

---

### Post by Artou on 2009-02-04
Try using same unrealtournament.ini you had before, or even editing the file manually to change it to fullscreen. I had also problems with the startup script and permissions to save modified options, so I=lazy installed the game into the home dir and link to it as:
/home/max/ut/System/ut-bin -userini=/home/max/.loki/ut/System/User.ini

#Mauro

---

### Post by Willberg on 2009-02-04
Edit: first, try this:

Go to your UT system folder /usr/local/games/ut/System

And run this:

./ut-bin

And see if it works; now, on with the post:

----

I was fiddling with this just yesterday; what worked for me was some advice from this site:

[http://fingel.com/ut/howtos/utonlinux.html](http://fingel.com/ut/howtos/utonlinux.html)

About using utcustom.sh or somesuch.

Give it a go!

---

### Post by Sylos on 2009-02-05
Thanks very much for the response.

I originally tried to us ethe same installer as I used on Gutsy but it wouldnt open so I got a different one. I also have tried installing it to a location in the /home/me/ area but that had the same problem as I have now.

I have tried the ./ut-bin command and get the same problem. When I start it from terminal it brings up the intro video and reverts to a smaller window and then when you press escape to get to the menu up the mouse stops working.
The terminal output in the background reads:

fcntl: Operation not permitted
fcntl: Operation not permitted

no idea what this means.
Any ideas? 
Thanks.

---

