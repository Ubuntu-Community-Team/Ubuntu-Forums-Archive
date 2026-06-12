---
title: "various skype problems"
date: 2008-10-26
forum: Multimedia Software
---

### Post by AMIRITE on 2008-10-26
So i've been experimenting with ubuntu on my laptop (a hp dv9000) for a little while now.

i had various multimedia and hardware problems with heron, all of them are fine now that i'm on ibex, the one problem i do have now is with skype. firstly when i try and call someone, i get an error message saying that there's a problem with audio playback.

as a primarily windows user i tried the traditional uninstall/reinstall untill i realised that skype doesn't appear in my add/remove aplications menu, 

so if anyone can tell me how i could 
(a) fix my skype, and
(b) for future reference tell me how to uninstall apps that don't appear in my add/remove applications menu.


thanks in advance.




Also. if you have the inclination i have a problem with the default audio recorder that came installed. i was trying to check my mic (which works fine) when i found that while recording the time was way out of whack, to the point where minutes of apparent recording rack up in seconds, which then doesn't play back afterwards.

---

### Post by darkstaar on 2008-10-27
Bump...

...since a few of us seem to be experiencing this exact same issue.

---

### Post by szirakitamas on 2008-11-01
hi,

for (b) system>administration>synaptic packages manager. search the package, rightclick, uninstall

---

### Post by motin on 2008-12-30
For A, there is a known problem with Skype and Intrepid Ibex: [http://www.econowics.com/news-from-the-net/170/skype-problem-with-audio-playback-ubuntu-810-intrepid-ibex/](http://www.econowics.com/news-from-the-net/170/skype-problem-with-audio-playback-ubuntu-810-intrepid-ibex/)

---

### Post by mocha on 2008-12-30
There's no need to uninstall PulseAudio just to get Skype or other apps that don't play well with PulseAudio to work.  Simply run "pasuspender skype" to temporaily stop PulseAudio while running Skype.  This could be problematic though if you run Skype 24/7.  In that case then maybe you should uninstall Pulse.  I love all the added flexibility that Pulse adds to my system, hopefully Skype will fix their problems with it.

---

### Post by sky pilot on 2009-01-02
have tried a number of fixes outlined on this forum for my skype audio problems and have come up empty. 

Mic sound is never close to what it should be. When testing in skype There is a faint sound of my recording but nothing close to what it should be.  

Is the problem with skype for ubuntu or pulseaudio? 

Now that skype has unlimited calling for like $3 a month I would like to use it continuously but I like to use Ubuntu a lot too.  What to do?

---

### Post by Acradon on 2009-01-02
I am using skype with interpid and it works just fine. I can video conference and call landline and cell phones. I had some problems in the beginning and had to properly install my soundcard drivers (using nvidia onboard). You can check your proper settings under System > Preferences > sound. Make sure that microphone, line in and all other devices are listed in the box at the bottom of the window. They weren't there when I first installed Skype and after installing and configuring the sound card they appeared and skype worked fine. 

Acradon

---

### Post by sky pilot on 2009-01-02
Well had mic problems in Skype and set everything to pulseaudio and then uninstalled skype and reinstalled it and seems to be working. 

Mic doesn't seem as sensitive under Ubuntu as it is in Windows.   I have to be closer to it in Ubuntu. Well hopefully things will progress.

---

### Post by Acradon on 2009-01-02
Maybe you can increase your mic sound using the sound settings. Just mark the microphone in the box at the bottom of the sound preferences and exit the window. You can then adjust the strength of the mic by simply using the volume increase/decrease buttons on your keyboard. I had the opposite problem, in that my mic was too sensitive and caused a terrible feedback. 

Acradon

---

