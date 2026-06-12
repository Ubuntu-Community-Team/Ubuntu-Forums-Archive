---
title: "presonus firebox on ubuntu studio"
date: 2007-09-27
forum: Multimedia Production
---

### Post by Zolfo on 2007-09-27
hi guys!

I'm an italian ubuntu studio user and i have some problem with my sound card presonus firebox...

sorry if my english is not very good :lolflag:

I want to do recording and mixing with ardour and my firebox but i' m not able to sync the sound card with my pc...

i tried to do search è follow the instructions of this thread but the led is red

[http://ubuntuforums.org/showthread.php?t=522738](http://ubuntuforums.org/showthread.php?t=522738)

can you help me step by step to realize this my dream please? :)

i installed freebob package and set permissions for raw1394 for GROUP="audio" but jack doesn't start....

---

### Post by nalmeth on 2007-09-27
Can you post the error message from the messages window?

---

### Post by Zolfo on 2007-09-27
now the card is sync with the pc! the led is blue!

But i don't understand how use it as default... the pc use the integrated suound card to play music.... :(

---

### Post by newsun on 2007-10-31
this is a erm bump as I have the same issue of not knowing how to get the firebox to play any sounds, I wish presonus would just release linux drivers

---

### Post by newsun on 2007-11-21
I just want to say that basically following most of the steps here for installing a realtime kernal and the firewire stuff here has helped me get my firebox up and running

[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

 sudo adduser <username> disk
 sudo apt-get install linux-rt (I also installed the headers and restricted modules so I could do other things namely access wireless) I found all in adept repos
 sudo su -c 'echo @audio - rtprio 99 >> /etc/security/limits.conf'
 sudo su -c 'echo @audio - memlock 250000 >> /etc/security/limits.conf'
 sudo su -c 'echo @audio - nice -10 >> /etc/security/limits.conf'

also make sure to turn on realtime in jack -R or check the box if using qtjackctl
and am using the freebob driver

---

### Post by newsun on 2007-11-24
following up with using this setup...I have this working, only one thing I have noticed...jack will zombify if I am playing music encoded at 192 or higher bitrate...some 192 files seem to play okay, but anything above that will not get past 45s before I get errors about not being able to talk to the device. Has anyone else experienced this?

---

### Post by kayosiii on 2007-11-26
firstly you should have already picked up that Firebox (got one right in front of me) only has jack drivers so only applications that support jack can use it.

To play back the 192 bit rate files you will need to do one of two things
1) increase the buffer length using qjackctl (frames/period in the setup section)... increasing this value will improve stability but increase latency.
2) make Jack perform better - the first thing to do would be to get it to run in realtime... look around for info on how to do that (I think that ffado.org is a pretty good starting point). There are other tweaks beyond that but this should get you started.

If you are getting into serious audio I definately reccomend the second route.

---

### Post by newsun on 2007-11-27
kayosiii - thanks for the input, do you have settings which you use with jack that work with the presonus firebox? I have played with the buffer settings, but nothing works so far with 192 and higher encoded files, they all seem to cut out quickly

As you may have missed, I am already running the realtime kernal with jack in realtime(a few posts up)

ffado.org would be a good place to start if they actually had a release yet, still freebob, their v1 driver is the only one which works with a firebox AFAIK

---

### Post by JimBuntu on 2008-01-13
Hey, guys, i have a firebox and have been messing around with it too. I can finally here sound from my sm57 mic in the front port(1). However i do here a lot of cuts. I think I will play around with the settings some more. One thing that I have noticed is my CPU is at bouncing around from about 20% to 100% if I open a new window or something and thats when it cuts out. 

Also, Ive noticed in Jack Control when i click messages, I see those Xruns that everyone is talking about. What the hell are Xruns anyway??? Never heard of that. 

Another question... In Ardour, when I click record the button just flashes and nothing happens...Obviously something is not set up right, what is it?

---

