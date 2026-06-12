---
title: "Can't Output 5.1 Sound In Ubuntu 10.4, No Problem with Earlier version."
date: 2010-08-22
forum: Multimedia Software
---

### Post by Dissel on 2010-08-22
Hi,

As title suggest I can't output 5.1 sound with Ubuntu 10.4 which I nevere faced in earlier version like any 9.04 or 8.10,8.04 etc etc.

I came from 9.04 to 10.4 and noticed that sound preference has changed which earlier have Windows XP Like long sound panel.

My Board is Intel 945GTP which have 3 jack 

Green=>Sound Output =>Front 2 channel
Pink=>Mic In  =>Center Sub 
Blue=>Line In =>Rear Channel

This have HD Audio which is capable to transform 5.1 via sound driver 

Where in earlier version of Ubuntu sound preference have Tab like Option/Misc where I can Check 

[B]Line In As Output
Mic In As Output[/B]

**How Can I do this in Ubuntu 10.04 ?**

I only get 2.0/2.1 sound which is come from the Green Jack.

When I choose Analog 5.1 surround output,from Rear channel Grrr sound & Center is Mute.

Here is the pic

[IMG]http://i130.photobucket.com/albums/p266/dissel_2007/104SoundProperties.png[/IMG]

---

### Post by EricJonsson on 2010-08-22
What happens when you try:

```
speaker-test -t wav -c 6 -D surround51
```.. in a terminal?

---

### Post by Dissel on 2010-08-22
When I write that command in the terminal by copy pasting,

I got

**Front Left---from the Front Left Box ---- OK**
Front Center----from the Rear Left Box ---Not OK
**Front Right --- from the Front Left Box ---OK**
Rear Right ---- from the Center Box ---Not OK
Rear Left ---- From the Center Box ----Not OK
_Rear Center_ ----From the Rear Right Box ----Not OK

I don't have Rear Center Box.

It is 5.1 channel not 6.1

Physical Box -- > Front LEFT/RIGHT,Rear LEFT/RIGHT,Center & Sub woofer.

And the connection work like this, 

From mother board <------> Sound Box in

[COLOR="Lime"]Green Out <---> Green In[/COLOR]
[COLOR="Magenta"]Mic Out[/COLOR] <---> Black In
[COLOR="DeepSkyBlue"]Line In[/COLOR] <---> [COLOR="Orange"]Orange In[/COLOR]

---

