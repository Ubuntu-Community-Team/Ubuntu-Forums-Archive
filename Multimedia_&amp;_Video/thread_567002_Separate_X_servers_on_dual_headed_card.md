---
title: "Separate X servers on dual headed card"
date: 2007-10-04
forum: Multimedia &amp; Video
---

### Post by larryjoe701 on 2007-10-04
First let me lay out where I'm at, then what I'm trying to do:  
I have configured MythTV to work on my Fiesty desktop and it works.
I have a dual-headed nVidia card configured and working and can use Xinerama or twinView.
I have one output connected to an LCD monitor and the other connected to a TV through S-Video.
There are two sound cards in the computer, but I'm not sure what their status is other than one is working.

My goal is to run Myth in its own instance of X to the TV, while a second instance of X is used on the LCD monitor.  I would like a separate keyboard (and eventually LIRC) to control the Myth X server.  I would also like Myth to use one sound card and the LCD desktop to use the other.

I have successfully started X on each of the screens, but they don't stay [I]on[/I simultaneously.  I think I could figure the rest out if I could get the card to output both X servers at the same time.

I've used information from [http://www.mythtv.org/wiki/index.php/Running_MythTV_Dual_Headed]("http://www.mythtv.org/wiki/index.php/Running_MythTV_Dual_Headed") to get me started, but again, that is for one or the other, not both at the same time.

Any advice on getting me closer to my goal would be much appreciated.

---

### Post by larryjoe701 on 2007-10-04
I seem to have found more information.  This sort of setup is now known as multiseat X, and I will post more on what I find, but in the mean time this link [http://cambuca.ldhs.cetuc.puc-rio.br/multiuser/]("http://cambuca.ldhs.cetuc.puc-rio.br/multiuser/") has a history of some hacker adding such functionality into X.  Impressive stuff.  I didn't realize this was such a complicated request... two screens under the same X != two Xes on different screens.

---

### Post by uclalinux on 2007-10-05
This might help 
[http://www.linuxquestions.org/questions/linux-hardware-18/dual-monitors-on-dual-vido-cards-130080/](http://www.linuxquestions.org/questions/linux-hardware-18/dual-monitors-on-dual-vido-cards-130080/)

and 

[https://help.ubuntu.com/community/NvidiaTVOutNewbieEdition](https://help.ubuntu.com/community/NvidiaTVOutNewbieEdition)

---

### Post by |Eric| on 2007-10-23
hum cant you just configure another screen ?

---

### Post by andersja on 2008-05-07
larryjoe, any luck? If yes, could you please report back how things went?

Regardless, you should probably log on and vote for:
[http://brainstorm.ubuntu.com/idea/3442/]("http://brainstorm.ubuntu.com/idea/3442/")

---

### Post by andersja on 2008-05-13
[[IMG]http://brainstorm.ubuntu.com/idea/3442/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/3442/)

---

