---
title: "clipping noise from jack"
date: 2018-07-06
forum: Multimedia Software
---

### Post by thevmgas on 2018-07-06
hello all

first some basic info..i am running on ubuntu 14.04.4 LTS on 4.4.0 low latency kernel 
Intel(R) Core(TM) i7-5600U CPU @ 2.60GHz and 16GB RAM


i noticed that recently a clipping/popping sound occurring very consistently when using  audio software. when playing synths or sending audio into my daw (bitwig) this occurs as well as when running audio patches from pure data. clipping does not occur during audio playback from a session within bitwig.

my initial thought was that the problem might be from the audio interface but i tried another and the same issue was present.

it has been very hot lately in my studio and i also thought that may be the cause but i have been using a cooling pad to lower temps 

i also ran my daw in pulse and the issue was not present

the issue seems to be within jack from what i can observe

any ideas to solve this issue or what the cause might be..any additional info i could provide?

---

### Post by kazakore on 2018-07-07
If you have such a new computer why are you running such an old version of Ubuntu?!?

How do you start Jack? qjackctl? CLI? Cadence? Have you checked if you are clocking up xruns when you hear this noise? It sounds like you have the settings too strict (too low latency) and are running into xruns to me.

---

### Post by thevmgas on 2018-07-07
I start jack in cadence. 
honestly I'm not sure why I'm using such an old version of ubuntu..I think it's just a flavor I liked and stuck with for awhile. I was thinking that perhaps after work that I would try out whatever the latest xubuntu is. the strange thing is that this issue is new and I've been running this same setup for about 2 or 3 years now?
I did see some xruns on my PD log actually now that I think of it.

---

### Post by thevmgas on 2018-07-07
so i opted to switch to a newer version of ubuntu. i opted for lxde/lubuntu and switched the generic kernel to a more current low latency and the issue seems to be gone. i am also preferring lxde so far. xfce didnt have too much bloat but this feels even faster now and i'm also getting less overheating issues so far. maybe i shouldnt have waited 3 odd years to move on to a newer version!!

---

### Post by kazakore on 2018-07-08
I haven't tried LXDE since I think 2014 or so but know back then XFCE was definitely my favourite (but I also have to manually configure quite  lot to get it how I like.) Glad to hear that seems to have worked out for you. I assume you have gone through other audio configurations such adding yourself to the Audio Group and possible changing nice settings etc? Pretty good guide for this on the Arch Wiki....

---

