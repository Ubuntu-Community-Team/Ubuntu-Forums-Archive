---
title: "fglrx REAL control panel - a beginning"
date: 2006-11-09
forum: Multimedia &amp; Video
---

### Post by damagedspline on 2006-11-09
Well, I got sick of waiting for ati/amd and thier sweet control panel for the fglrx driver so I threw out the glove! :mad: 

operations are on-the-fly without restarting X!

the next python code is based on pygtk. for now it's just a simple example for tv out control and in a couple of months i hope i'll be able make a better version in java or mono c# (i'm really not a python programmer) which will include advanced stuff such as tv scale blah, blah, blah....

run the code and you'll see an ati icon on the tray, click it and etc...

DO NOT RUN THIS CODE AS ROOT OR IT WILL CHANGE YOUR XORG CONF FILE!!!!!

tested on my ATI Xpress 200M with the 8.30.3 driver

when i tried uploading the python script here, some annoying php file kept popping up for download, so its on google code.

script can be found on google code:
[http://alternativefglrxcontrolpanel.googlecode.com/svn/trunk/atitvout.py](http://alternativefglrxcontrolpanel.googlecode.com/svn/trunk/atitvout.py)

Please improve/fix/try/complain/... whatever! but if u do, do it either here or on googlecode.
 
Long live better software for the ppl!

For ppl having issues with COMPOSITE (RCA) tvout when only s-video exist - there is a solution:
buy a cable that has 1 svideo plug on one side and 2 rca plugs on the other side. also buy a plug that has 2 rca inputs on one side and 1 rca output on the other side. (~5$ incl everything)code
connect everything. disconnect one of the two rca and enable the tvout (u can use the python script ;) ), if it doesn't work, plug it back, disconnect the other one and try enabling the tvout again. now the tv is black-white only. connect the plug back and you have color again. if you dont have the color back - then try changing the tv format (again, u can do it with the python script ;) )

---

### Post by amitaibar on 2006-11-13
You are a genious!

---

### Post by lassegs on 2006-11-13
Could I ask for a screenshot?

---

### Post by damagedspline on 2006-11-14
> **lassegs said:**
> Could I ask for a screenshot?

[http://alternativefglrxcontrolpanel.googlecode.com/svn/trunk/screenshot.jpg](http://alternativefglrxcontrolpanel.googlecode.com/svn/trunk/screenshot.jpg)

As I said... for now it's just the basics.

---

