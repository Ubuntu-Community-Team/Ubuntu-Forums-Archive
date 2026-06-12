---
title: "JACK HElP!"
date: 2010-04-13
forum: Multimedia Software
---

### Post by spidersoft on 2010-04-13
Hello! I am a new Ubuntu user and o my god, this is the ride of my life :) I discovered it not long ago and i must say that when people create out of passion for what they create, wonders are born. What can i say, i love it and i find it very very well done. Now i will cut to the chase , but i wanted to shout that out loud! :lolflag:

I must say i am not much of a coder but i understand many things about computers. But whenever i seek some help regarding linux, i end up on a page with lot's of stuff to read and lots of codes. This is the case with my present JACK problem. I will use my words to tell you want i want so don't expect any ARCH TALK from me :)
What can i say ... i understand the way JACK works, i understood that it "helps" the ALSA driver manage better and more complex sound applications. It is kind of similar, imho, to the REWIRE feature in win and mac applications like FLP, Reason aso.
BUT ... it doesn't work for me. I understand and i am diligent into seeking out problems myself, but on all LINUX forums the help from the community on most problems ends up with a reply from a big brained linux guru telling the poor man that asked for help that " linux isn't for everyone , Jack won't go easy, you need to become Superman to use Ubuntu easier " etc. 
I tried to use Ardour, rosegarden, muse, lmms and Hydrogen (which i find a quite neat drum machine). 
Hydrogen plays without any hasle. Played a bit with the JACK settings in order to make Ardour work but i can't really figure out what i am doing wrong. If i start it using the program launcher it won't work ...  i push start and it stops. I found some Terminal command on the web and it works with that ...i mean it seems to make JACK run ... but still Ardour won't play. It seems like nothing happens when i connect or disconnect the devices in the JACK panel. Also tried to use MUSE and ROSEGARDEN but they both shout at me that JACK is not working (same does Ardour).
After i filled in the command i found on the web "jackd -d alsa -d hw:0", Ardour at least started but still won't play ... i imported some wav files but they won't budge. 
Is there something i am doing wrong? Or isn't JACK for everyone?!
Don't get me that, please... i play keys for quite a while, produced a band not till long ago, i am experienced with live desk mixing for shows and lights and all i want is to discover the musical part of UBUNTU. I am not a retard ... but i don't want from a Musician to turn into a Coder. I am in love with the everyday-user side of Ubuntu (wtch movies, listen to music burn cd, write word documents etc) , now i want to go deeper and use it for my hobby. so please help me guys!
Thank you!
Adrian.


PS: Now i notice that nothing plays while jack is runing ... except for HYDROGEN. I am attaching 2 screenies one with the messages i get upon pushing play in ardour and one with the settings i have in JACK ...

---

### Post by spidersoft on 2010-04-13
Oh yes ... i am using a Creative Audigy sound card in case that helps :)

---

### Post by markbuntu on 2010-04-13
Here is some helpful inks for getting jack working.

[http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit](http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit)

If you are having trouble setting up jack in UbuntuStudio:

[https://help.ubuntu.com/community/UbuntuStudio/GettingStarted](https://help.ubuntu.com/community/UbuntuStudio/GettingStarted)

[http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/](http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/)

[http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation](http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation)

Excellent ardour tutorial here:

[http://out-of-order.nfshost.com/tutorials/ardour/](http://out-of-order.nfshost.com/tutorials/ardour/)

If you are wondering how to sync applications together through jack:

[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

[http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/](http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/)

[http://www.rosegardenmusic.com/](http://www.rosegardenmusic.com/)

FYI Questions about jack should be asked in the Ubuntustudio section.

---

