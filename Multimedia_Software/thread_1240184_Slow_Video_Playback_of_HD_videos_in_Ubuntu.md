---
title: "Slow Video Playback of HD videos in Ubuntu?"
date: 2009-08-14
forum: Multimedia Software
---

### Post by razorboy5 on 2009-08-14
Hi

i had a problem with my HD movies last nite and after doing alot of research i heard a few people saying HD movies will be slower in Ubuntu compared  to windows since (not sure if this is what they meant but) Ubuntu only uses CPU rather than GPU to play movies? Is this true?

if it is, is there a workaround? I would hate to switch back to Vista just because of stupid HD movies...

thx

---

### Post by Grenage on 2009-08-14
That will depend on what drivers you have!

---

### Post by razorboy5 on 2009-08-14
what do u mean what driver? my GPU driver?

---

### Post by Grenage on 2009-08-14
Yes, what are you using?

---

### Post by razorboy5 on 2009-08-14
ATI Radeon HD 2600

i'm sure it's capable of playing HD movies as i used to back in vista days

---

### Post by Grenage on 2009-08-14
I am sure it is; what driver are you using?

---

### Post by razorboy5 on 2009-08-14
umm went to Hardware Drivers and it says

ATI/AMD proprietary FGLRX graphics driver

---

### Post by Grenage on 2009-08-14
ATI linux drivers are unfortunately bloody awful. Have you looked into the open drivers?

---

### Post by razorboy5 on 2009-08-14
hey again

i just followed some "guide" and completely ruined my Ubuntu
doing a fresh install atm

however could u tell me more about these open drivers?
where can i find them and how do u install?
and can u recommend one for my gpu

thx alot

---

### Post by swong on 2009-08-14
I don't have experience with ATI drivers, but as Grenage stated, I also heard they are not great.

Luckily I have a Nvidia gpu and HD content plays fine.  Just fyi, Geforce 8 series and higher cards offer hardware accelerated video via VDPAU supported apps.

---

### Post by Grenage on 2009-08-14
I've not installed the open driver before (I gave up and bought an Nvidia card), but there are some reasonable-looking guides around.

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) is one.

Googling "ATI open driver +ubuntu" yields some decent results, I'm sorry I can't be of much more help.

---

### Post by Dubbayoo on 2009-08-14
Try this

[http://ldn.linuxfoundation.org/article/multicore-video-decoding-with-mplayer-part-1](http://ldn.linuxfoundation.org/article/multicore-video-decoding-with-mplayer-part-1)

---

### Post by razorboy5 on 2009-08-14
umm i think i correctly installed ATI driver for linux (downloaded from the ATI site) however it doesn't seem to work. Can't even put my desktop graphics to Extras and HD movies seem extra slow. Do i need to enable FGLRX along with the ATI Radeon driver that i downloaded?

i'll try Dub's suggestion and post results as soon as i'm done

---

### Post by razorboy5 on 2009-08-14
ok nvm sry for the last post

I installed the ATI driver from the site
then i installed the FGLRX driver from Hardware Drivers 

after that my HD movies run perfectly

thx for all the help especially Grenage :P

---

### Post by razorboy5 on 2009-08-14
sry this was a horrible solution
i didn't test properly before posting my last reply

after the fresh install i didn't put my visual settings to extras.
so video was working fine
however after i put it to extras video went down the pooper
so i'm guessing it's more of a compiz problem rather than driver problem

thx for help thou

---

### Post by Grenage on 2009-08-16
Hi again,

Well I'm glad you have some sort of remedy, even if it is be disabling compiz.  Have you tried different players to see if those will play smoothly (with compiz running)?

---

### Post by razorboy5 on 2009-08-18
sry for the late reply
i just moved yesterday and didn't have internet for a whole day! almost cried...
 
anyways
 
yes i found a solution (or well someone else did and i followed it from google)
 
i'm using VLC media at the moment then go to Preference -> Video Output
 
and change the settings to 'Something X 11' i'm on my XP machine atm and sry i couldn't be more detailed
 
also thx for all the help again

---

### Post by Fernando23 on 2009-08-18
Hi everybody, 

Are you looking for home theater installation? Then your search end here. Recently I got a wonderful service provider for installation. You can get easy installation of you Home Theater, Plasma Television or LCD Television. They have specialization in the installation of IPTV, devices, LCD TV's, Surround Sound Systems and Plasma TV. They mount Plasma/LCD HDTV on wall, on ceiling, above fireplace, on brick or stone wall. For more information you my visit my signature link.

Hope this will help you.

Enjoy!




___________________________
[Home Theater Installation ](http://www.techrowe.com/)

---

