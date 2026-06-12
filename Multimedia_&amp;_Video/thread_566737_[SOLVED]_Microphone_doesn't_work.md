---
title: "[SOLVED] Microphone doesn't work"
date: 2007-10-03
forum: Multimedia &amp; Video
---

### Post by El Potro on 2007-10-03
Hello, I know this may seem a very repetitive thread, but it is so bad people, I need some help here!

I'm relatively new in Ubuntu, and I haven't found the way for making microphone to work. (In windows or in fedora I have no problems).

I have two sound cards, one is on-board, (this one doesn't work ok, so I don't use it at all) and the other one, is pci.

I have tried all those HOW-TO's that I've seen this forum, but no one worked.

So guys, do you have any advice for me? I was really wondering, how is it possible that this nice operating system, very good in many aspects is weak in this little and basic one?

Thank you all very much for your help!

Mauri

---

### Post by linuxwizard on 2007-10-03
Look over and try these. If you have seen them or already tried them than post more info on computer/sound.

[https://help.ubuntu.com/community/AudioCapture](https://help.ubuntu.com/community/AudioCapture)

[http://ubuntuforums.org/showthread.php?t=385739&highlight=HOWTO+microphone](http://ubuntuforums.org/showthread.php?t=385739&highlight=HOWTO+microphone)

---

### Post by El Potro on 2007-10-03
why, hello linuxwizard! thank you a lot!

I think we've made some progress!

I saw the guides, the howtos, and well, the first one was very basic, and the second one didn't helped much, but while I was trying new things, and clicking here, and there, I found out that the vumeter -r, shows that it receives voice, when I have checked the options (under capture): MIC - CAPTURE - ADC.
The thing is I never knew ADC had something to do with this deal, by the way, what's the meaning of ADC?

So, now it seemed to work, but when I try to open the sound recorder, it tells me this:

"YOUR AUDIO CAPTURE SETTINGS ARE INVALID. PLEASE CORRECT THEM IN THE MULTIMEDIA SETTINGS"

:-S

I tried also with audacity, but I didn't got any good results, now in the "recording device" it shows the other card (the onboard one) so, it is like my pci wasn't existing.

What is the complicated thing?

I'm adding you the screen of what I had to enable in order to make the vumeter -r to register my microphone.

Thank you a lot for helping me!

---

### Post by El Potro on 2007-10-03
wizard! 
I found out the solution!!!!

The thing was that I left open the vumeter, so the card was somewhat blocked. 

Now, I found that in recording device, I have to select Mic and ADC. It is working as fine as wine!
you can't imagine how grateful I'm!! It is so irritating and frustrating not to get something that basic to work.

I hope someone finds this thread someday, and will find it useful too!!

Thank you a lot linuxwizard!!

---

### Post by linuxwizard on 2007-10-03
That's great you got it working and setup. Glad those links helped you pointing you in the right direction you needed. analog-to-digital converter (abbreviated ADC)
[http://en.wikipedia.org/wiki/Analog-to-digital_converter](http://en.wikipedia.org/wiki/Analog-to-digital_converter)

Please mark thread solved.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

