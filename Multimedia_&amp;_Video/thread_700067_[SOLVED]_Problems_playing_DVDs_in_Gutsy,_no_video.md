---
title: "[SOLVED] Problems playing DVDs in Gutsy, no video"
date: 2008-02-18
forum: Multimedia &amp; Video
---

### Post by thechilipepper0 on 2008-02-18
OK. I'm pretty new to linux, i'm a recent convert from xp.

So I got the xine-backend for totem, i installed the libdvdcss2, libdvdread3, and libxine1-ffmpeg..things.

i did some other stuff, i don't even remember what, but i'm sure it just overlapped with the above stuff.

anyway, When I pop in my legit, store-bought copy of Blow, i can hear the sounds of the menu loading, but i get NO VIDEO.  All my other dvds are like that too. I have no idea what to do, and i'm sad. please help!

---

### Post by amohanty on 2008-02-18
Ahh the wonders of copyright protection.
I am guessing you followed the instructions at: 
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

First make sure you are using the xine backend.
Try the following in a terminal
type totem
ls -l $(type totem)

That may point to some location (on hardy its /etc/alternatives/totem)

then do an ls -l on the result of that.

Or simply in a terminal type in
totem-xine 

and see if it works. If it does you might need to an 
sudo update-alternatives totem 
and select the xine version.

If everything is fine and you still cant play the DVD, I would recommend trying vlc
sudo apt-get install vlc

HTH
AM

---

### Post by thechilipepper0 on 2008-02-18
ok i tried that...i'm not really sure what all ls-l is or how to do it. once i punch in totem, the program opens up and terminal doesn't really do anything until i close up totem.

anyway, i already put on vlc and that also shows no video, but every now and then it flashes a frame of the movie. i think it may be how my video card is set up. i had to go through some extra configuration to get my ATi X300 to work on my laptop. [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.2_Driver_Manually]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.2_Driver_Manually")
 is the site that i used to make it work. i'm thinking that's the problem, but then that still doesn't leave me playing dvds. ha.

oh and thanks for the super quick response!

---

### Post by amohanty on 2008-02-18
umm.. i have an ati x300 with teh fglrx driver and it works just fine. 

The ls -l was mainly to make sure that /usr/bin/totem points to /usr/bin/totem-xine.
When you say punched in totem did you type in simply totem or totem-xine?

AM

---

### Post by thechilipepper0 on 2008-02-18
just totem. totem-xine didn't bring up anything
"bash: totem-xine: command not found"

so i type in totem, and then after totem opens up, put in ls-l into terminal?

i don't know why i thought it was my vid card, it was late and i was starting to get a little loopy

OK, i just went into /usr/bin/ and there is only totem there. it isn't totem-xine.

---

### Post by amohanty on 2008-02-19
In a terminal try:
sudo apt-get install totem-xine

or in Synaptic search for xine and install totem-xine.

That should set it up for you.

HTH
AM

---

### Post by thechilipepper0 on 2008-02-19
thanks, but i did a little digging and someone someone suggested disabling the compiz effects. when i did that, the dvd played perfectly across all players. do you have any suggestions as to how to make them work together?

synaptic says I already have totem-xine

thanks for all your help anyway.

---

### Post by amohanty on 2008-02-20
I dont usually have both running so I dont really have an answer for that. That said, you could try vlc and try and change the video playback (I think be default it is xvid) you can try gl or xshm or something like that. 

The screenshots section [http://www.videolan.org/vlc/screenshots.html](http://www.videolan.org/vlc/screenshots.html) does have an image with the cube and vlc running on it :)

HTH
AM

---

### Post by thechilipepper0 on 2008-02-20
how do you change that?

also, i'm wondering if i could change the codec for playing videos only, but leave compiz to do what it does with something else.

---

### Post by amohanty on 2008-02-20
You can change the video outpute mode for VLC by opening the preferences dialogs, select vdeo in the left and then output modules. There are several listed there, you could use one that works. 

sudo apt-get install vlc

---

### Post by thechilipepper0 on 2008-02-22
thanks a bunch! videos work great for me now in vlc. i might as well just get rid of totem, which isn't letting me change the codec

---

