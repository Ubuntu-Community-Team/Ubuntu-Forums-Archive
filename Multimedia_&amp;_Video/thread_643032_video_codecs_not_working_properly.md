---
title: "video codecs not working properly"
date: 2007-12-17
forum: Multimedia &amp; Video
---

### Post by tombutcher1990 on 2007-12-17
right, this is a slightly odd problem. basically, i am trying to get avi files to work on ubuntu as i want to replace XP with ubuntu but obviously need the same usability.

i've installed VLC too cos that should play everything.

right, i'm using compiz fusion effects etc. heres the problem.

basically, the image doesn't appear. i've installed the codecs. i can make the image appear by minimising VLC and then maximising again and rolling the mouse over, but as soon as i do anything, it disappears.

PAIN.

anyone know how to fix this?

TIA

Tom

---

### Post by rsambuca on 2007-12-17
Although it may be a codec issue, it sounds to me more like a video card/driver issue.  what is your videocard, and what driver are you using?

---

### Post by tombutcher1990 on 2007-12-17
ATi Radeon 9250SE AGP 256mb.

i duno, the standard driver. shall i install the ATi driver then?

i will try that now anyway just incase. can't do any harm.

---

### Post by tombutcher1990 on 2007-12-17
right, ATi drivers installed, its getting better!!

if i load it in VLC then don't do anything, just watch, it works fine. can't full screen, can't stretch, can't move it at all. can't use a different window either.

could it be cos i've got the 4 desktop thingy setup?

---

### Post by rsambuca on 2007-12-17
Sorry, I am an nVidia guy.  I don't know enough about the ATI bugs and problems to help you out.  Perhaps someone else can chime in.

---

### Post by tombutcher1990 on 2007-12-17
ok thanks very much for the help anyway.

to be honest, i don't watch THAT much on here, and i've left my windows install on as a fail safe for when ubuntu can't do something i need it to etc. so i can always watch on that. i would prefer not to be swapping between the 2 all day long though.

i have to say though, i am rather loving this whole ubuntu lark. i've just been installing some new themes etc.

do you happen to know, i saw a plugin a while ago that basically mimics the look of the MAC OS linkbar at the bottom of the desktop, where there are a load of icons etc arranged in a more easy to use / access way. any chance you know what it is called?

---

### Post by rsambuca on 2007-12-17
It is called [AWN -  the Avant Window Navigator]("http://ubuntuforums.org/showthread.php?t=385981&highlight=avant+window+manager")

---

### Post by tombutcher1990 on 2007-12-17
aha, thankyou again! you are just the well of knowledge.

---

### Post by shane2peru on 2007-12-17
If that didn't fix it, then you are probably going to have to disable or shut off your compiz setup to play videos.  That looks like a similar problem I had before.  

Shane

---

### Post by mdpalow on 2007-12-18
There's always the possibility that you didn't install all the necessary codecs files. I've seen people say they installed them, but it still doesn't work 'cause they missed a few files.

You can always try my link below, It's been very successful as long as it's not a hardware issue.

---

### Post by Lostincyberspace on 2007-12-18
I had the problem but I also had problems with my graphics driver so I thought it was from driver..

---

### Post by tombutcher1990 on 2007-12-18
rite, compiz is off and its all fine!! good to know what the problem is. oh well, i will just have to pick and choose between watching videos and using effects lol.

---

### Post by shane2peru on 2007-12-18
> **tombutcher1990 said:**
> rite, compiz is off and its all fine!! good to know what the problem is. oh well, i will just have to pick and choose between watching videos and using effects lol.

Well glad to know it is that simple too!  :)  The effects are very nice and very impressive, but they are not quite ready for everyday desktop usage in a lot of cases.  

Shane

---

### Post by 6205 on 2007-12-19
Why VLC ? i know, it is good on Windows but not so on linux. Remove everything, then clean your system by typing into terminal "sudo apt-get autoremove"  and also be sure that you dont have installed totem-mozilla plugin...

Then install packages mozilla-mplayer + all suggested depencies (like Mplayer itself) + w32codecs + x264 and that's all you need. If you will play streaming video from web, right click on mplayer-plugin in firefox and for video set up GL - this should be settings for best compatible video playback (audio may leave blank) and browser cache set up from 512kb to cca 2048 or more if you have slow internet connection (less than 1024kbps) This should also work with Compiz without problems - but ATI driver quality is unknow factor here - NVIDIA have no problems with this settings...

---

