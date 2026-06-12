---
title: "Divx codec won't work"
date: 2007-04-25
forum: Multimedia &amp; Video
---

### Post by Amorget on 2007-04-25
I followed all the directions to install the latest DivX vodec (6.11 I think) to try and get some movies to play.  It went without error, but the divx moves do not play.  It is extremely frustrating and I have been stuck on it for 3 days now.  I tried a search and did not find anything helpful... most interesting thread I found was one that said codecs on Linux are so much easier.... how ironic.

I finally got the w32codec package to install after fighting with it for 2 days because of an error that searching google for resulted in zero worthwhile answers.  I am stubborn and want this to work but it is wearing on me, nothing works first, second or 3rd try... so any help is appreciated.  Oh, and I am running Edgy.

Thanks,
Douglas

---

### Post by renzokuken on 2007-04-25
use automatix to install the codecs [www.getautomatix.com](www.getautomatix.com)

or alternatively use vlc media player which has all the codecs built in already

```
sudo apt-get install vlc
``` from the command line will install it for you

---

### Post by Amorget on 2007-04-25
I have VLC, but it won't play anything.  I will try auotmatix.

---

### Post by Amorget on 2007-04-30
Okay, I upgraded to Feisty Fawn now and divx still does not work.  I installed Automatix and installed the Multimedia package, but that didn't do it.  I have VLC, but it doesn't play the movies, either.t
Totem gives me this error:

"There is no input plugin to handle the location of this movie"

It is being played over the network but that shouldn't make a difference...

Thanks,
Douglas

---

### Post by Amorget on 2007-05-01
Anyone?

---

### Post by MilosDusan on 2007-05-01
> **Amorget said:**
> Okay, I upgraded to Feisty Fawn now and divx still does not work.  I installed Automatix and installed the Multimedia package, but that didn't do it.  I have VLC, but it doesn't play the movies, either.t
Totem gives me this error:

"There is no input plugin to handle the location of this movie"

It is being played over the network but that shouldn't make a difference...

Thanks,
Douglas

Wait wait wait.. You say you have VLC installed, but you're trying to run the DivX file in Totem MPlayer? .. Have you tried to run it in VLC yet -- and if so, is it still having an issue loading?

---

### Post by Amorget on 2007-05-01
It seems that with the upgrade to 7.04 from 6.10 and reinstalling VLC it can now play them in VLC.  Now if I could only figure out how to open the file from in VLC over the network.  It really really does not want to open it, but if I transfer the file it does.  I set the properties to open in VLC but it still opens in Totem.  I right click to say "Open with Other Application" and VLC isn't on the list.  I am not sure how to make a custom command to open VLC specifically from there properly.  I tried jsut going to the bin and running vlc but that didn't work.

Edit:  I tried copying and pasting the entire path location of the file and vlc attempts to play it for about 2 seconds, then just stops.

---

### Post by MilosDusan on 2007-05-02
Minor .. Right click on the file, click on Properties.. Click on 'Open With' .. click 'Add' and then click 'Use a custom command' .. In the field, type in 'VLC' and click 'Add' .. That will give you a radio button to use VLC as a default for the file ..

Note though, you gotta do it for each file (WMV, AVI, MPG, etc)

---

### Post by Amorget on 2007-05-02
> **MilosDusan said:**
> Minor .. Right click on the file, click on Properties.. Click on 'Open With' .. click 'Add' and then click 'Use a custom command' .. In the field, type in 'VLC' and click 'Add' .. That will give you a radio button to use VLC as a default for the file ..

Note though, you gotta do it for each file (WMV, AVI, MPG, etc)

Doesn't work.  Even though VLC is the selected radio button it still opens in Totem.  When it is local it opens properly, however over the network it doesn't.  If I say "Open with Other Application" and use a custom command "vlc" it runs VLC but doesn't play the video.  If I hit play it asks me to select a video but I can't get onto a network share using the Browse dialog in VLC.

---

### Post by klap-in on 2007-05-02
I had the same problems with divx, I use Feisty Fawn, automatix etc. to install the right stuff.

When I try a search in this forum, I found this: [http://ubuntuforums.org/showthread.php?t=396569&highlight=divx]("http://ubuntuforums.org/showthread.php?t=396569&highlight=divx")
The 6th post of that thread has solved my problem. 
by moving the files: /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so and /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt to the firefox plugin directory.

Succes!

---

### Post by Amorget on 2007-05-02
> **klap-in said:**
> I had the same problems with divx, I use Feisty Fawn, automatix etc. to install the right stuff.

When I try a search in this forum, I found this: [http://ubuntuforums.org/showthread.php?t=396569&highlight=divx]("http://ubuntuforums.org/showthread.php?t=396569&highlight=divx")
The 6th post of that thread has solved my problem. 
by moving the files: /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so and /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt to the firefox plugin directory.

Succes!

Thanks but I am not trying to play over them in Firefox I am trying to play them off of a network drive through Samba.

Thanks,
Douglas

---

### Post by Amorget on 2007-05-04
[http://forum.videolan.org/viewtopic.php?t=35705](http://forum.videolan.org/viewtopic.php?t=35705)

The answer is in there for VLC... it works :-)  Just had to figure out how to mount it and install samba :-)

---

### Post by kayel_justice on 2008-03-31
It seems avi files wont play with Compiz settings manager set to custom. Can anyone help?

---

