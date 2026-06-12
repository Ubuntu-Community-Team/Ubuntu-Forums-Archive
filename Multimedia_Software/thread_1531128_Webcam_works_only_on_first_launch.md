---
title: "Webcam works only on first launch"
date: 2010-07-14
forum: Multimedia Software
---

### Post by mayur.shetye on 2010-07-14
Hi! I am totally new to ubuntu and just installed ubuntu 10.04 a week back.It updated as well through the update manager.Then I installed latest version(beta) of skype from the .deb downloaded from their website.In the beginning my webcam was detected but the video used to flicker.So I searched the net for a solution.I tried launching skype using 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype' command but there was hardly any 
difference.Then I came across **gstreamer** **properties**.I tried the three options and there started the problem.Now my webcam is detected only on its first launch.Once i stop the test there appears a black screen.I uninstalled and reinstalled skype but in vain.I tested it using cheese and vlc as well.
I would be happy if someone could tell me a way out of this...like resseting the configuration etc.

---

### Post by no2498 on 2010-07-16
gstreamer properties is how they ubuntu/linux test webcams
cheese has a good help file look in its faq's
if the cam stops working in cheese
do not open cheese again

this program will work better for you wxcam

read and install all the page tells you to first

[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

get the cam working in gstreamer properties if it did not come on in wxcam

hope this helps

---

### Post by mayur.shetye on 2010-07-17
Hi no2498 ......thanks for your reply.I tried wxcam.Once again the same problem started.On running wxcam for the 'FIRST' time my webcam was detected and everything worked well.But next,when I closed wxcam and launched it again the following 2 error messages popped up.
1.'JPEG: Couldn't load - file is probably corrupted.'  2.'An error has occured during frame capture.
Please check the "frame format" options in the preferences menu.' On closing and launching wxcam again the same errors occur.  Next,I rebooted my PC,launched wxcam once again and it worked fine.Then i closed wxcam and on launching it again the same errors popped up. I would like to mention here that the same problem persists on using skype,vlc and cheese and also while testing using gstreamer properties.Also,when I tried launching cheese 'FIRST',it worked.Then I exited cheese and launched wxcam.It gave the same errors.So, to summarize,**My Webcam is detected only ONCE on system startup**, and this is independent of the application used. Also,I would like to mention that before i tried using gstreamer properties my webcam used to work well **EVERYTIME** I used skype,vlc or cheese.      
Waiting for help..........:cry:

---

### Post by no2498 on 2010-07-18
do a search for

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

i have seen a how to make it permanent

hate to use the word skype but it was under it
the 1 i seen any way you try it without skype

good luck and hope it helps

---

### Post by mayur.shetye on 2010-07-19
I googled it.But everywhere i found to run skype using LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype.As I said in my earlier thread,I have tried doing that.But suprisingly,the results now are very RANDOM.Sometimes,I see myself quite clearly.Sometimes,on launching skype again(using that command) I just see a black screen with some greenish light source.Sometimes,it doesnt work at all.
I would like to ask if there is some way to 'revert' back to the 'fresh ubuntu install state'......or to make ubuntu use the configuration it was supposed to do by default.....like using drivers,video properties etc.
I would continue searching and let you know if I have some update.......
But still waiting for help......

---

### Post by no2498 on 2010-07-19
i have also seen gstreamer 10 does not load all the time
so that 4 gstreamer's we need
good,bad,ugly and 10

---

### Post by mayur.shetye on 2010-07-19
sorry... but these seem to be already installed.thanx for the prompt reply though......

---

### Post by behco on 2011-05-25
Mine too. Using cheese, or skype, or gcvuview, etc. The first time at boot, it works. After that, black image totally static, no signal. Any help?

---

### Post by behco on 2011-05-25
> **behco said:**
> Mine too. Using cheese, or skype, or gcvuview, etc. The first time at boot, it works. After that, black image totally static, no signal. Any help?
Workaround: logout and login again. :(

---

### Post by no2498 on 2011-05-26
behco

open a terminal type gstreamer-properties click enter

click video
set it to auto find your cam

---

