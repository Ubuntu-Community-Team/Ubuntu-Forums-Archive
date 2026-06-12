---
title: "[SOLVED] Jack"
date: 2008-10-10
forum: Multimedia Software
---

### Post by baudday on 2008-10-10
I just bought a M-Audio Keyrig 49 midi keyboard since I have absolutely nothing to play while I'm at college. So I'm trying to get it to work with Ubuntu, and at first tried installing the software that came with it in Wine, but that didn't work. So I figured I'd use something like Rosegarden, the problem is when I open Rosegarden I get the message JACK Audio server couldn't be reached or something like that. And it goes on to say that it may not be running. I know it's installed, cause I installed it. My question is how do I start it? And does anyone have a better alternative to Rosegarden?

---

### Post by markbuntu on 2008-10-10
You need to read these:


[http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit](http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit)

[https://help.ubuntu.com/community/UbuntuStudio/GettingStarted](https://help.ubuntu.com/community/UbuntuStudio/GettingStarted)

[http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/](http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/)

If you are wondering how to sync applications together through jack. This is about hydrogen but the approach is pretty much the same:

[http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/](http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/)

---

### Post by baudday on 2008-10-10
Hey thanks a lot for the reply. So I got Jack working. And I've been reading through those, and can't really find anything on this. Basically, I click record in Rosegarden and start playing something random just to see if it works, and it seems to be picking up the key strokes, but I can't hear anything, and when I go back to listen to the recorded track, it doesn't play anything either. Any thoughts?

---

### Post by markbuntu on 2008-10-10
You probably need to change some settings in Rosegarden/Settings/Configure Rosegarden. But first, look in the connect box in jackcontrol and make sure rosegarden is connecting to system for playback and everything else.Are you getting any sound out of jack ? If not, you may need to fool around with the interface and input and output device settings in jack control setup.

Between all that if you fool around long enough you should be able to get it all working. 

You should also check out Hydrogen for drums and ardour for recording. You can hook them all up together and run them with the jack controls and let jack take care of the timing coordination. It is really handy.

---

### Post by baudday on 2008-10-10
so ardour seems to be a lot better than rosegarden, even if i'm not quite sure how to use it yet. I still can't get my keyboard to work in there though. I downloaded Hydrogen now, and I can make beats fine just by clicking, but does hydrogen have midi keyboard capabilities? I do get sound out of Jack which is a good thing. All help is greatly appreciated.

---

### Post by baudday on 2008-10-10
Here is some good news, after trying the keyboard out in hydrogen, I know that it works with Ubuntu. Can anyone help me out as to why I can't record with it in Ardour?

---

### Post by baudday on 2008-10-11
Not sure if anyone even cares, but I got it to work. Gotta use Patchage to make all the right connections.

---

