---
title: "Help on Movie player"
date: 2011-04-10
forum: Multimedia Software
---

### Post by sandy0594 on 2011-04-10
Hey all,I am very new to  Linux and I am running Ubuntu 10.10..The Movie player volume is too low to hear on my headphones.Whereas when i play on rhythmbox,it's a lil better.Any ideas on why low volume on movie player?

---

### Post by owise1 on 2011-04-10
Have a look at your sound preferences - click on the sound control icon and then  select preferences and then the applications tab - see attached

---

### Post by garvinrick4 on 2011-04-10
Did you right click on sound applet in upper right hand corner and go to sound preferences.
Make sure your output volume is right and you are on output headphones. In other words check your settings.

---

### Post by sandy0594 on 2011-04-10
Everything looks okay as per me..have a look at this:

---

### Post by owise1 on 2011-04-10
check your output config

---

### Post by sandy0594 on 2011-04-10
Yeah,tried both..But,not satisfied..I am getting good sound on rhythmbox.I don't understand what's wrong with **Movie player**

---

### Post by owise1 on 2011-04-10
is sound level OK without headphones

---

### Post by sandy0594 on 2011-04-10
It's better than headphones..But lstill low..When i make my speakers run on full volume,i can hear.In windows,i had Sm player for movies..it used to have good sound..For audio,Jet audio was good.But,here in Ubuntu i am not getting that kind of sound in any of the players i have seen in the past 3 days..Any suggestions?

---

### Post by owise1 on 2011-04-10
sounds like you have tried a few movie players - SMPlayer as well?

Can you provide a bit more detail on your system?

version 10.10?
sound card details - onboard or separate card -make

also just check this

---

### Post by sandy0594 on 2011-04-10
Have a look at these

---

### Post by owise1 on 2011-04-10
card looks like a realtek alc887-vd but run aplay -l in a terminal to check and then try a google or two on your problem.

---

### Post by sandy0594 on 2011-04-10
My start-up sound is pretty good..Just the sound in Movie player is bad..What is good player apart from movie player to watch movies.

```
sandy@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC887-VD Digital [ALC887-VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by owise1 on 2011-04-10
interesting that you have two devices come up with aplay -l.  Not sure if that is your problem????

You can use mplayer which is highly configurable or SMPlayer (a front end to mplayer) or VLC - just have a look in software center.

---

### Post by owise1 on 2011-04-10
just a thought - do you have restricted extras installed - are you playing a movie?  Might be a codec issue

---

### Post by sandy0594 on 2011-04-10
The movie is in .mp4 format.Doesn't Movie Player support it?

---

### Post by sandy0594 on 2011-04-10
installed  SMPlayer, it's better.But comparing to players Windows OS,The players in Ubuntu are a bit low in sound

---

### Post by owise1 on 2011-04-16
Have been thinking about your problem.  I had an issue with skype on another PC where the recording volume was very low - turned out that if both channels were locked together then the input was turned down very low - bug in the software. unlocking the two channels and making one channel slightly lower resulted in normal operation!

I only found that by installing pulseaudio manager which lets you fiddle with more controls that the normal panel applet.  You could try installing that and then see what you can do with your internal card - mine shows that it can be set to 210%!  That blasted my ear drums!

Finally with regards to comparing with players under Windows remember that the PC supplier installs windows and makes sure that everything works.  Here you have installed Ubuntu and mostly everything works thanks to a lot of great guys in the background.  So can you run the system testing program and provide feedback on your audio - that may get it fixed.

---

### Post by sandy0594 on 2011-04-17
Yup,installed pulse audio manager..the sound is better now..
Thanks for the reply.

---

