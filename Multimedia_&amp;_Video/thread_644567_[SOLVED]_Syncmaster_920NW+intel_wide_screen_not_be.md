---
title: "[SOLVED] Syncmaster 920NW+intel wide screen not being used full"
date: 2007-12-19
forum: Multimedia &amp; Video
---

### Post by _grv_ on 2007-12-19
Hi,

this has been asked before but not answered...

so i was just wondering if someone found a work around...

i have been able to get 1440x900@60 on my 19" TFT (Syncmaster 920NW) after 915resolution etc...

but the linux desktop doesn't fill the full screen, i tried stretching the screen using monitor buttons but it saturates after a bit and i still have around 2in blank on the left...

kindly help me out...

p.s. i am attaching a (bad) cellphone cam pic to illustrate my point...

---

### Post by flyboy_2003 on 2007-12-25
> **_grv_ said:**
> Hi,

this has been asked before but not answered...

so i was just wondering if someone found a work around...

i have been able to get 1440x900@60 on my 19" TFT (Syncmaster 920NW) after 915resolution etc...

but the linux desktop doesn't fill the full screen, i tried stretching the screen using monitor buttons but it saturates after a bit and i still have around 2in blank on the left...

kindly help me out...

p.s. i am attaching a (bad) cellphone cam pic to illustrate my point...

If you switch the resolution to 1440x900@75 it seems to work OK. The only problem is, the Gnome login screen is still off to one side. I am still trying to figure out how to fix this.

---

### Post by _grv_ on 2007-12-26
hi  flyboy... thanks for replying...

your tip seems to work... it occupies 98% of the screen (still a minor 0.5 cm blank on either side)...thanks for the tip... however when i set the refresh rate to 75Hz... the  monitor menu shows that it is on 1152x900@77 and not 1440x900@75... i am working on it to see if i can get it to work...

however... could you also check in your monitor OSD information if you are getting the correct 1440x900@75 or only i am facing this problem...

thanks again...

grv

---

### Post by slickridley on 2008-01-07
i have 19" view sonic, amd64, ati 9600, and i have about an inch on top and bottom that are not being used, and my max screen res is 1024 x 768 any ideas?

---

### Post by _grv_ on 2008-03-31
I still don't have a solution...

If anybody found it kindly let me know...

thanks

---

### Post by _grv_ on 2008-04-05
Hi,

for the record... i seem to have solved it partially...

i went to a console and did 

```
sudo dpkg-reconfigure xserver-xorg
```

among many option there was one to do with 'kernel buffering' which warned that turning it on was safe on most machines but some. I had done this  before but everytime i used to select the default NO option... this time i thought  of trying it out so did yes....

after that i logged back in and still  got the blank... i choose plug n play widescreen monitor  from system>administration>screens  and graphics....

then i tried 1440x900 @75 and that did it... i get a full  display now and boy it rocks!!!

although on my monitor osd it shows 

```
72.3Khz 77Hz NP 1440x900
```

but it works...

however it doesn't remember my preference, it starts with 1440x900@60 and i have to change to 75 Hz everytime i log in... but then it works...


i am attaching my xorg.conf hoping might help someone...

cheers...

ubuntu is good...haven't turned on win for quite a few days... among many, the compressed rmvb videos seem to be rendered much better... loving it !

---

