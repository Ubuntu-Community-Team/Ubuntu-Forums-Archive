---
title: "Jack - what now?"
date: 2007-11-11
forum: Multimedia &amp; Video
---

### Post by carusoswi on 2007-11-11
Ok.  Downloaded Ardour to give it a try.  When I try to start the program, I get an error message that states that it can't open because Jack isn't available - it is either being used by another ap, or it is not running.

I've downloaded everything I can find via Add/Remove that is named Jack - still no joy.  What am I doing, and where must I turn to find a "cooperative" Jack?

Thanks.

Caruso

---

### Post by Tyche on 2007-11-11
> **carusoswi said:**
> Ok.  Downloaded Ardour to give it a try.  When I try to start the program, I get an error message that states that it can't open because Jack isn't available - it is either being used by another ap, or it is not running.

I've downloaded everything I can find via Add/Remove that is named Jack - still no joy.  What am I doing, and where must I turn to find a "cooperative" Jack?

Thanks.

Caruso

In Synaptic (System -> Administration -> Synaptic Package Manager) search for jackd.  This is the "JACK Audio Connection Kit (server and example clients)".  I also recommend qjackctl, the User interface for controlling the JACK sound server.

The Jack sound server needs to be started BEFORE Ardour or Rosegarder are started.

Hope this helps.

---

### Post by Ashrael on 2007-11-11
Yep! you need to install what Tyche said, also you might want to install patchage and if you think your latency is too high, you might want to look into low-latency-kernel... Just typeJACK in synaptic and you&#314;l get all jack enabled appz... for freeeeeee....

---

### Post by carusoswi on 2007-11-25
> **Tyche said:**
> In Synaptic (System -> Administration -> Synaptic Package Manager) search for jackd.  This is the "JACK Audio Connection Kit (server and example clients)".  I also recommend qjackctl, the User interface for controlling the JACK sound server.

The Jack sound server needs to be started BEFORE Ardour or Rosegarder are started.

Hope this helps.

Ok, went back through Synaptic.  All the aps you suggested were already marked as installed.  I did find some other jack related stuff, so I marked it for installation.  I'm going to give it another go.

I am curious why, if an application needs these other aps, they aren't automatically marked for installation when you download/install the main application.

I am learning, though.

Thanks for the replies.

Caruso

---

### Post by Martje_001 on 2007-11-25
Jack is an audio server for linux. You can mix various apps with it to make your own music.

---

### Post by carusoswi on 2007-11-25
I don't find Jackd on my applications menu.  I find Jack Control, Jack EQ, and Jack Rack.  I've played around with the Jack Control, although I'm not certain any of my settings were really effective.

I do notice that I can get Audacity to go into record mode, now, although I've yet to successfully get an input signal through to that AP (or anyother, for that matter).

I know I'm making some progress, because my favorite XP sound editor, Wavelab, installed and is now recognizing my audio cards (I had had no success until this morning).  I incorrectly assumed the success was due to my having accidently used Wine to install that ap instead of Crossover, but, then, went back and installed it again using Crossover and it worked under Crossover, as well.  I attribute my recent success with that ap to the various additional Jack aps I installed yesterday, although I don't know why what I did made any difference.

There was a terminal command posted to determine Jackd status (don't remember what it was, I copied/pasted the command), but it returned a message indicating that Jackd was running and in an acceptable state.

So, again, I'm groping around through a tangle, but, apparently moving ahead a bit.

Any additional advice would be appreciated.  Heaven for me would be to get Audacity running so that I can use it to record live performance.  Sitting at the right hand would be getting my Wavelab to record and also recognize my CD/CDRW/DVD drive.

I am certain all will be accomplished one of these days.

Thanks so much for your assistance.

Caruso

---

### Post by Drunky on 2007-11-27
carusowi,

Try this [Ubustu Feed article]("http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/") on how to setup and run Jack.

---

### Post by diva42 on 2007-11-29
> **Drunky said:**
> carusowi,

Try this [Ubustu Feed article]("http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/") on how to setup and run Jack.

Thanks for the link I just ommited the realtime step number 2 because it did not work for me this is the readout I got when i followed it exactly 

08:41:53.461 Patchbay deactivated.
08:41:53.536 Statistics reset.
08:41:53.574 MIDI connection graph change.
08:41:53.747 MIDI connection change.
08:45:01.038 Patchbay deactivated.
08:45:04.817 Startup script...
08:45:04.817 artsshell -q terminate
sh: artsshell: not found
08:45:05.039 Startup script terminated with exit status=32512.
08:45:05.039 JACK is starting...
08:45:05.040 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p64 -n2 -m
08:45:05.061 JACK was started with PID=11178 (0x2baa).
jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread -1210557568, from thread -1210557568] (1: Operation not permitted)
cannot create engine
08:45:05.070 JACK was stopped successfully.
08:45:05.071 Post-shutdown script...
08:45:05.071 killall jackd
jackd: no process killed
08:45:05.320 Post-shutdown script terminated with exit status=256.
08:45:07.259 Could not connect to JACK server as client. Please check the messages window for more info.

If you notice it says below the JACK cannot use real-time scheduling so I ommitted it and used all the other setting exactly and started jack up and then started ardour after it and yep it worked now to figure out how to get my music file in and how to operate artdour Im hoping I can add features such as synthesizer and ladspa like I have on my windows version of audacity.                  Thanks so much diva42               PS Im a noob:)

---

