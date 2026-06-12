---
title: "Not able to play video...System hangs"
date: 2009-08-18
forum: Multimedia Software
---

### Post by udit1233 on 2009-08-18
I just installed ubuntu 8.04 hardy heron on my "hp 6530s" laptop with 2gb ram and on board default video card...

I tried totem player but it plays 2 seconds of audio displays no video and the system hangs and i have to press the power button to restart my laptop...

Then i used vlc player but it plays 5 seconds of sudio with no video and the screen blackens out then evrything reappears with even the mouse not working...

---

### Post by overdrank on 2009-08-18
Hi and welcome, Have you installed the [RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")
On the specs of that system it appears it uses the intel graphics and if you are using Jaunty 9.04 you may look at the link in my signature about the intel graphics on Jaunty.

---

### Post by udit1233 on 2009-08-18
Yeah i have installed the restricted formats...

I am a totally newbie to ubuntu and i just don't know what is all that abiut jaunty that you are talking about...i read that but couldn't understand anything...

and yeah...in the ekiga software...i am able to view the video from my webcam which is very small...but if i start "cheese" software then the system hangs....

one more thing...I am able to view the thumbnail preview of all the video files...

please,please help

---

### Post by dtoronto on 2009-08-18
I would recommend using VLC media player and make sure that you have the right codecs.  Ubuntu isn't a "plug and play" OS for video codecs.  Even with the right codecs I have had problems getting some codecs to run well with the default Totem.

---

### Post by overdrank on 2009-08-18
> **udit1233 said:**
> Yeah i have installed the restricted formats...

I am a totally newbie to ubuntu and i just don't know what is all that abiut jaunty that you are talking about...i read that but couldn't understand anything...

and yeah...in the ekiga software...i am able to view the video from my webcam which is very small...but if i start "cheese" software then the system hangs....

one more thing...I am able to view the thumbnail preview of all the video files...

please,please help

I am sorry it must be to late here. :) I just noticed you stated you are using Hardy 8.04. The one thing that may help is installing the 915 resolution package using synaptic package manager. Along with what dtoronto has suggested.

---

### Post by udit1233 on 2009-08-20
I installed that 915resolution thingy from the synaptic manager but still the video is not playing....

And i saw something astonishing today.....i was playing some audio file in vlc player then mistakenly i opened up a video file and it played correctly....but after that it is not working... idon't know what the hell is the problem...please help

---

### Post by udit1233 on 2009-08-21
i went to system>preferences>multimedia system selectors and clicked on "test" button in video output......but the screen blackened out and nothing happened..... i had to force shutdown.......please help......

---

### Post by Plumtreed on 2009-08-23
I had to buy a new external DVD burner/cdrom and when I tested it I found that I could not watch a 'video'

After doing the following, the videos just 'sit up and play' I am also using 8.04lts.

   

   Open a terminal and type 

 sudo apt-get install libdvdread3

   Then type and execute: 

 sudo /usr/share/doc/libdvdread3/install-css.sh


Worked for me:P

---

### Post by Struki on 2009-08-23
I'm havin the exact same problem with my video players(vlc, mplayer), but I'm using ubuntu 9.04 on hp6735s with ATI Radeon 3200hd. My video players are crashing cause of ATI/AMD prprietary FGLRX graphics drivers, so I deactevited them(System>Administration>Hardware Drivers), and my players started working fine, but now all of the ubuntu cool graphics are gone and I'm runing simple desktop enviroment without any visual effects, and some weird lights come when I boot. So I guess u could try that...if that is your problem.

But I'm still wondering is there a way the have both runing prprietary drivers and video players?

---

