---
title: "dvd play"
date: 2007-08-02
forum: Multimedia &amp; Video
---

### Post by rufi_dukes on 2007-08-02
i have just bought a new machine with ubuntu pre-installed;
after paying US1600, i would have thought i could switch the machine on and watch a dvd, 
but no, it seems i've got to do some tweaking...

i went to a sticky post by adamant 1988, which heads this forum of Multimedia and video,
followed all the directions, until i got told that i did not have the right permissions to alter the file with the new quotes...

everything is SOOOOO hard in linux...

could someone have a look and tell me what i'm doing wrong

thx,
rufus
(exasperated)

---

### Post by 505 on 2007-08-02
Not everything is SOOOO hard on linux, it's just different.
Anyway, here's how to do it. Go to System -> Administration -> Synaptic Package manager. Enter your password when prompted. From the settings menu, select Repositories and go to the 'Third Party' tab. Click the add button and paste:
```
deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
```
Click OK, then Close. Now push the reload button in the toolbar. Now you can search for the packages libdvdcss2 and w32codecs and install them.

---

### Post by Bablefish on 2007-08-02
On the other hand I would reccomend heading over to the Medibuntu site and look for the Terminal install command lines I found it was a hell of a lot easier to install. But don't forget please to ativate the gs streamers in add remove. Also there is one last thing you should do if you want DVDs to play get Automatrix from here [http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation) but besure to use it to install the codecs.

---

### Post by rufi_dukes on 2007-08-02
> **505 said:**
> Not everything is SOOOO hard on linux, it's just different.
Anyway, here's how to do it. Go to System -> Administration -> Synaptic Package manager. Enter your password when prompted. From the settings menu, select Repositories and go to the 'Third Party' tab. Click the add button and paste:
```
deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
```
Click OK, then Close. Now push the reload button in the toolbar. Now you can search for the packages libdvdcss2 and w32codecs and install them.

thanks! that worked...
at least, now i have solved that problem and find i have another:
when i went to play a video, got a totem message saying that i diddn't have a plugin to read from cdrom0...

this suggests to me that i have not mounted my dvd drives properly

i am a newbie;
cd you please tell me how to mount them both (i have 2 dvd drives)?

ps does the fact that i can play cd music in both drives mean that i have mounted both drives as CD?

rufus

---

### Post by z-vap on 2007-08-13
I've been noticing alot of threads regarding Totem-xine not playing dvd's.  

One thing I did was also installing xine-ui.  When I did this, it told me It also needed:

libcurl3-gnutls
libxine1-ffmpeg

So I may be that I needed one or both of these for it to work (I am guessing libxine1-ffmpeg).

---

