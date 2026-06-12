---
title: "tvTime Sync error or Something?"
date: 2006-07-05
forum: Multimedia &amp; Video
---

### Post by smtelegadis on 2006-07-05
I can't figure out whats wrong with my TVtime settings.  

The attached image is what effecte I'm getting.

The image comes up all twisted as though the Sync sync is screwed up.  It's the whole program as the tvTime menu screens are messed up as well.

I'm running a Kworld KW-878RF-PRO Tuner with with the following settings in my /etc/modprobe.d/bttv:
[INDENT]# i2c
alias char-major-89 i2c-devb
options i2c-algo-bit bit_test=1
# bttv
alias char-major-81 videodev
alias char-major-81-0 bttv
# My TV Card
options bttv card=78 tuner=2 radio=1 pll=1 adc_crush=0[/INDENT] Any help would be greatly appreciated.:confused:

Follow up:

I wound up reinstalling and got the program up and running for a short while.  I started having problems after I installed XGL compiz.  I tried removing the pages and reverting to an older xorg.conf file with no luck.

---

### Post by loopiv on 2006-07-15
I'm getting the same thing since I've upgraded to Dapper.  Was fine with Hoary.  Did you find a solution yet?

By the way, are you using Xgl?

---

### Post by smtelegadis on 2006-07-20
yes, and that is the problem in my case.  It has something to do with an overlay (xv) and the glx part of the nvidia drivers I'm using.  

It sucks.  I like compize, but I need the TV feature.  It will work with Xdtv but the program is fussy.

Waiting for a new driver from nvidia.

---

### Post by crispy_420 on 2006-08-14
Anyone know the answer? 

I just got xgl running myself and for the first time I tried tvtime myself the other night so I could some BF2 in and catch some TV.

My specs are little different, ATI 9800 Pro and Leadtech WinFast TV 2000 Deluxe (bttv driver).

I would like the fancy effects but I prefer functionally first. So I am almost ready to drop xgl. But I will search for answer first, if I find anything I will post back.

---

### Post by blithe on 2006-08-16
Anyone come up with a solution yet? I'm experiencing the same thing.

I love compiz! I don't want to give it up!

---

### Post by blithe on 2006-08-16
Actually, it seems to be doing the same thing without compiz started... Maybe it's because XGL is still running?

---

### Post by whatever on 2006-08-16
it's a xgl bug in the xv-emulation. as workarround you may edit ~/.tvtime/tvtime.xml and set
```
<option name="OverScan" value="0"/>
```

---

### Post by blithe on 2006-08-16
Thank you so much! It works great now!

---

### Post by cblanquer on 2006-08-26
The problem appears when you run Compiz. Use the Gnome graph session when you login just to check (go to the icon down-left to select the session before entering your password), tvtime should be working then.

Anyhow the solution proposed some posts before by "whatever" worked for me :D .
But it is not perfect :confused: : tvtime screen slightly switches intensity from normal to dark so that it becomes extremely uncomfortable to watch it.
I guess some parameter in Compiz is to be readjusted, I shall try to find out what to do.

---

### Post by mspaul on 2006-09-18
sorry to raise the dead thread but has anyone found a real fix for xgl and tvtime?

---

### Post by cblanquer on 2006-09-18
Hi,

No more posts from my side as it simply started working properly O:)  some weeks ago. I guess it was due to a system update, as there was no particular action from my side.
Under XGL however I find tvtime is using a huge amount of processor resources, till the point it is not functional (tvtime+browser are the maximum I get without trouble). 
This might be due to my H/W config (pentium M 1,7 MHz only + ATI Radeon 9600). I guess under Compiz some GL commands are not caught by the card, posible one of the problems of the ATI's, which result in this processor overhead.

---

