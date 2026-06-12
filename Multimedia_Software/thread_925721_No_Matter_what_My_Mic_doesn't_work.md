---
title: "No Matter what My Mic doesn't work???"
date: 2008-09-20
forum: Multimedia Software
---

### Post by Ms_Angel_D on 2008-09-20
Soundcard: SigmaTel HDA using Stac92xx

Hi guys, I've spent days on this issue read through countless forum posts, messed with the alsamixer and volume properties to no avail, all my mic gives me is static. Also I can't get it to allow me to set capture on mux.

[[IMG]http://img3.imagebanana.com/img/07f2j3xg/thumb/screenshot_01.png[/IMG]](http://img3.imagebanana.com/view/07f2j3xg/screenshot_01.png)

[[IMG]http://img3.imagebanana.com/img/huxf2x27/thumb/screenshot_02.png[/IMG]](http://img3.imagebanana.com/view/huxf2x27/screenshot_02.png)

[[IMG]http://img3.imagebanana.com/img/rg9j85or/thumb/screenshot_03.png[/IMG]](http://img3.imagebanana.com/view/rg9j85or/screenshot_03.png)

Any Idea's?

Thanks in advance,
Angel

---

### Post by Ms_Angel_D on 2008-09-21
Bump :D

---

### Post by Ms_Angel_D on 2008-09-22
Anybody?????

---

### Post by xc3RnbFO8P on 2008-09-22
Did you check all boxes in Volume Control?
Playback
Recording
Options

---

### Post by Ms_Angel_D on 2008-09-22
Yesh I did but all I get is static

---

### Post by markbuntu on 2008-09-22
Look here, there is some specific info about your card in the second post that may help you get it set up right.:


[http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

It appears that there are 3 front mic inputs as shown in your second screen shot but they are not available for some reason. Do you have a rear mic input? Have you tried that?

---

### Post by Ms_Angel_D on 2008-09-22
Mark,

Thank you for your reply, yes I have tried every mic jack to no avail. I also read through the post and attempted to edit the alsa-base file and add in my options to no avail. I also upgraded alsa to 1.0.17 yet all I get is static. Nothing seems to help. Again thanks for your help.

Angel

---

### Post by markbuntu on 2008-09-23
I have a suggestion. Get

gnome-alsamixer

You can get it with synaptic and you will find it in Applications/Sound & Video. It is a lot easier to use than the alsamixer and may show you more options. Post a screenshot of it.

---

### Post by Ms_Angel_D on 2008-09-24
I installed gnome-alsamixer, when I attempt the check mark the Input sources nothing happens, also if I leave them checked and re-open it, the boxes are unchecked.

---

### Post by markbuntu on 2008-09-24
Hmm, that is weird. It looks like the input switches may be linked to the captures, have you tried just one input and one capture, they may be mututally exclusive?
I am guessing here so....

---

### Post by Ms_Angel_D on 2008-09-24
hmmm well after much fiddling I did notice that the volume of the static comes from playing with mux but isn't effected by capture, capture 1, capture 2, mux 1, or mux 2 but in the alsa-mixer I can't toggle capture for mux the spacebar does nothing. I can't help but wondering if possibly Intrepid will help in the situation, and maybe just waiting patiently for release to see if upgrading helps at all. 

I have a theory that computer's and I have a love-hate relationship, they love to make me hate them....lol

I do appreciate all your help Mark, if you think of anything else please let me know.

Angel

---

### Post by josemaster2228 on 2008-09-24
am no to good at this problem solving thing but i kind of had the same problem its a matter of understanding your mixer look try this 
try to check the options box on the normal mixer then go to the options tab there you should have one or two drop down menus on the top one select the mic you want to use it solved my problem i hope it does yours too

---

### Post by Ms_Angel_D on 2008-09-25
Thank you josemaster2228, I already have the mic selected, but I do appreciate you taking the time to reply ;)

---

### Post by shivshakti on 2008-10-15
Hi,

I am in search of my own mic solution for STAC92xx on Intrepid and stumbled across this... so before moving along I'll mention what I can recall I did in Hardy or maybe it was Gutsy...

+ The backports repository must be enabled to get the sound working (I *think* that was for Gutsy). As I recall, the sound was just like you described.

+ Have a play with the Pulseaudio manager because I one of my sound settings was set really low and the regular sound controls didn't effect it. However I ran Hardy from alpha and I think it was an issue from there.

My issue with Intrepid is that the microphone is too quiet and there's some intermittent buzzing. The early beta release audio wasn't set up properly at all but the updates helped a lot.

Good luck anyway
Matt

---

### Post by Ghost13 on 2008-10-15
Have you considered using a USB microphone? They are usually more easily accepted in setup than some other types. Good luck.

---

