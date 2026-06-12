---
title: "How to get Jack going?"
date: 2010-05-02
forum: Multimedia Software
---

### Post by kramer65 on 2010-05-02
Hello,


For starters; although I am comfortable with Ubuntu, I don't really understand these midi and jack things, so I hope I could get some newbie-help.. :(

Ok,so I got a [midi controller keyboard]("http://www.studiologic.net/sl-161.html") which I want to connect to my ubuntu pc to start making some music (play piano and possibly try to make some songs). I don't know if my sound card supports midi, but I got a Roland [midi-to-usb converter]("http://www.rolandus.com/products/productdetails.php?ProductId=611"). I connected it to my pc and downloaded Jack Control. When I fire up Jack control my normal music (using audacious) stops (don't know if this is normal). On the window that appears I hit start which results in an error, which I will paste below:

```
22:46:06.556 Patchbay deactivated.
22:46:06.560 Statistics reset.
22:46:06.751 ALSA connection graph change.
22:46:06.948 ALSA connection change.
22:46:08.611 Startup script...
22:46:08.611 artsshell -q terminate
sh: artsshell: not found
22:46:09.014 Startup script terminated with exit status=32512.
22:46:09.014 JACK is starting...
22:46:09.014 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p1024 -n2
22:46:09.017 JACK was started with PID=4355.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread -1216678208, from thread -1216678208] (1: Operation not permitted)
cannot create engine
22:46:09.238 JACK was stopped successfully.
22:46:09.238 Post-shutdown script...
22:46:09.239 killall jackd
jackd: geen proces gevonden
22:46:09.681 Post-shutdown script terminated with exit status=256.
22:46:11.286 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
```

I understand I need to [configure something]("https://help.ubuntu.com/community/HowToJACKConfiguration"), but I have no clue how and why. I am now totally lost.. :confused: Could anybody help me out here? What should I do now? Any help welcome!

---

### Post by cchhrriiss121212 on 2010-05-02
First you should open jack setup window and disable the realtime check box on the left side.
Then see this thread for jack help:
[http://ubuntuforums.org/showthread.php?t=1458160](http://ubuntuforums.org/showthread.php?t=1458160)
And this for midi:
[http://ubuntuforums.org/showthread.php?t=1455798](http://ubuntuforums.org/showthread.php?t=1455798)

---

### Post by kramer65 on 2010-05-02
Thanks for the links. It gave me a lot of reading and googling (which gave me even more reading).

Do i understand it correctly if I say that: The MIDI signals which my keyboard produces are sent to my pc (in my case through usb) where they should be picked up by an audio server, in this case JACK. Jack then distributes the MIDI-signals to any program who wants to use them. Rosegarden is a MIDI-sequencer, which means it will only put the signals into order and can either sent it on to another program, or create sheet music from it. It cannot convert the midi signals to sounds though. For this I need a "synth"(esizer). A synth can convert the MIDI-signals to sounds through the use of samples like for example a drum kit, a violin, or a piano. These sounds can then be sent on to a recording program like Ardour, with which I can record the sounds I produced using the synth, and can then put the sounds together in order to form a song. The last step is sten creating a masterpiece and become world famous (optionally).

Am I correct in these things? Because that would mean that although I haven't got anything working yet, I at least understand the concepts which I need to use.. :)

---

### Post by kramer65 on 2010-05-02
[edit] Double post. This can be removed..

---

### Post by cchhrriiss121212 on 2010-05-03
Yes, thats correct. It should be simple for you once you get jack configured.

---

### Post by kramer65 on 2010-05-03
Alright thanks! One more thing. Isn't it pottible to keep my normal music playing through Audacious while I also have Jack running? Because then I can try to play along with songs I have on my pc..

---

### Post by cchhrriiss121212 on 2010-05-03
Yes it is, you need to download the audacious extra plugins package and then try switching the output to jack in preferences>audio in audacious.

---

### Post by kramer65 on 2010-05-03
Alright, thanks for the tip. I'll get back to my MIDI project as soon as I've fixed my pc ([my 10.04 upgrade hung]("http://ubuntuforums.org/showthread.php?t=1470501") and now my pc is totally messed up).

I will probably need to do a clean install or something.. :(

---

### Post by kramer65 on 2010-05-03
Well, my massive upgrade-to-10.04 issues have been solved, so I can get back to having the pc work for me instead of the other way around.. Lets make some music!

I disabled the realtime checkbox as suggested and jack now runs and I can get audacious to play with jack. I now have to constantly go into the preferences menu when I start or exit jack though. Isn't there a way to have audacious send its music to whichever soundserver is running?

Well, but that is not the most important thing. I installed ZynAddSubFX and opened it. I see a virtual piano which I can play on (with my mouse). How do I now get ZynAddSubFX to listen to the midi output from my hardware keyboard?

---

### Post by cchhrriiss121212 on 2010-05-03
At this point you should try a program called patchage, which displays clearly all of the jack connections. The boxes in green will be midi connections which you can hook up to stuff like zyn. When I use patchage and open a program it autoconnects to the ports used last time which should solve your audacious issue. You could have one audio player for jack like alsaplayer, and another for non-jack like audacious.

Jack will run better in realtime mode, which I can explain to you when your ready. You could look [here]("https://help.ubuntu.com/community/UbuntuStudioPreparation") first for the instructions.

---

### Post by kramer65 on 2010-05-03
Alright, so I installed Patchage which displays some things pretty nice. But how do I know which one is my midi-keyboard and how do I attach it to ZynAddSubFX?

I attached a screenshot of what I see..

---

### Post by kramer65 on 2010-05-03
Allright!

I just tried to connect anything to anything, and finally I hit something which was right! I can now at least get sounds from my midi keyboard!

After this I guess I just need Ardour in order to complete my masterpiece.. :)

I am just searching to get myself a normal sounding piano, which had nu luck in just yet. Is it possible to add new instruments to ZynAddSubFX? Can I download more instruments anywhere?

---

