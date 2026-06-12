---
title: "Need advice on MIDI"
date: 2009-03-11
forum: Multimedia Software
---

### Post by ilantal on 2009-03-11
I have a MIDI-USB cable which works on Ubuntu. It was advertised for Windows, where it works for XP, but my real interest is of course Ubuntu.
On Windows I have the program Finale which takes the MIDI input and writes out the musical notes. Ideally, I would like something similar in Linux. As a start I would be happy with anything which takes real time MIDI input and does something with it. I have Audacity, which imports MIDI files. As far as I can see, it won't accept MIDI input in a similar fashion as a microphone.

So I have Finale in Windows, but who wants Windows if there is something similar in Ubuntu? Any suggestions?

Thanks,
Ilan

---

### Post by mzembe on 2009-03-11
looks like you want something like [canorus]("http://canorus.berlios.de/wiki/index.php/Main_Page") or [rumor]("http://www.volny.cz/smilauer/rumor/rumor.html")/[lilypond]("http://lilypond.org/web/about/faq"). 
What kind of cable is it?

---

### Post by mzembe on 2009-03-11
It looks like canorus will need to be compiled from [source]("http://canorus.berlios.de/wiki/index.php/Developers_Guide").

---

### Post by markbuntu on 2009-03-11
I think you are looking for what the UbuntuStudio-audio can do for you. Read these and then you can decide. The learning curve can be quite steep but once you get everything set up it is a high quality professionals dream

[http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation](http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation)

[http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit](http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit)

[https://help.ubuntu.com/community/UbuntuStudio/GettingStarted](https://help.ubuntu.com/community/UbuntuStudio/GettingStarted)

[http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/](http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/)

Excellent ardour tutorial here:

[http://out-of-order.nfshost.com/tutorials/ardour/](http://out-of-order.nfshost.com/tutorials/ardour/)

If you are wondering how to sync applications together through jack. 

[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

[http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/](http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/)

[http://www.rosegardenmusic.com/](http://www.rosegardenmusic.com/)

---

### Post by ilantal on 2009-03-12
Wow, I'm impressed by what I see. It will take some time to go over the documentation, but I CERTAINLY received great answers to my question.
Since you ask about my cable, there I have another question. Initially I tried to build my own MIDI to joystick port, but I could never be sure that the port would transfer the MIDI signal and in fact I couldn't get it to work.
So I bought a MIDI-USB cable, which had its own learning curve. It looks to me like a design bug, but I'd like to ask if someone has more experience than I do. The cable has 3 LEDs: red when there is no keyboard attached, orange which blinks when the keyboard transfers to the computer and green which I've never seen in action. I think green is active when information goes from the computer to the keyboard, something which I haven't tried.

Here is the problem which I need the experience of someone. If I turn on the Roland keyboard before the computer, all is well. The orange light will blink and MIDI information will flow between the Roland to the computer. However, if I turn off the Roland and then turn it back on, the orange LED will stop flashing. The only way to "fix" the problem is to unplug the USB and then plug it in again.
This isn't a big deal once you know exactly what causes the problem, but the cable would stop transferring information and I didn't know why. The question is: is my cable different from others, or is this a common problem?
(Not exactly connected to Ubuntu, but according to the answers I received, there are some very experienced users in this group.)

Thanks,
Ilan

---

### Post by An85Zk9tc8rfjV8i on 2009-07-16
> **ilantal said:**
> I have a MIDI-USB cable which works on Ubuntu.
what brand ?

---

### Post by raboofje on 2009-07-16
> **ilantal said:**
> As a start I would be happy with anything which takes real time MIDI input and does something with it.

Rosegarden sounds like a good candidate, too.

---

