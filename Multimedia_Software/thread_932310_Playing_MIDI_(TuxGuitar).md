---
title: "Playing MIDI (TuxGuitar)"
date: 2008-09-28
forum: Multimedia Software
---

### Post by HuBaghdadi on 2008-09-28
Hey,
I installed TuxGuitar on Ubuntu 8.04.
When I'm trying to play the composed music score, I got this error:
[COLOR="Red"]MIDI System is unavailable[/COLOR]
Any ideas?

---

### Post by hansdown on 2008-09-28
Hi HuBaghdadi.

If you search for midi in synaptic package manager, a number of them are available.

---

### Post by markbuntu on 2008-09-28
If your sound card has no midi emulator you should get:

timidity

it is a software midi emulator that should work with tuxguitar.

---

### Post by bryncoles on 2008-11-02
i have tuxguitar, i have timidity (now i do anyway) and i still have no sound. thing is, it worked when i first installed timidity, then stopped working as soon as i tried to load a different guitar tab. any one got any ideas what to do?

i like tux guitar, but v1.0 doesnt seem to work half as well as version 0.9 did!

*edit*

playing around with timidity a lot seems to have got it working.... for now...

---

### Post by koolkatkiwi on 2009-01-20
Hi there. Saying
> **bryncoles said:**
> 
playing around with timidity a lot seems to have got it working.... for now...
doesn't help other people who are having problems. The whole purpose of these forums is to help people. What did you do to Timidity to make it work? I don't suppose you will ever look at this thread again, now that you've got your problem solved (sigh).

Cheers,
Kath :KS

---

### Post by SlayingPigs on 2009-05-05
I did the apt-get timidity, or whatever the code is. Everything installed fine, but initially I got the same error message in tuxguitar. All I had to do was go to Tools>Settings>Sound within tuxguitar, and then change the MIDI port from Java to one of the Timidity ports. The very first one worked fine for me. All in all, it took about a minute and a half to do all of this.

---

### Post by kayakdog on 2010-01-16
I got the "midi system unavailable" error until I installed **timidi** and **tuxguitar-oss**.  Hope this helps!

-kd

Note:  I'm running Ubuntu 9.10.

---

### Post by Moustaffa on 2010-01-24
Hey, the remedies above didn't work for me. I've tried timidity and setting Java to another port. The error disappeared but I just can't hear the sound. I've also installed tuxguitar-oss, didn't help, still no sound.

I've also tried fluidsynth instead of timidity (fluidsynth as well as tuxguitar-fluidsynth are installed), but that didn't work either.

Any ideas?

---

### Post by kar33m on 2010-01-28
Hello everyone. I stumbled upon this thread searching for the answer to the problem and actually found it so here is what did it for me.

1) go to synaptic manager --->search "timidity" ---> download "timidity" ( the application is called exactly that, there a few others with similar names like "timidity for emcas" or something. I did not use those).

2) open tuxguitar ---->tools--->preferences----> set sequencer MIDI to real time sequencer.

3) restart machine.

4) you're done.

PS: Sound quality sucks a bit though. So next problem I guess is "how can I get more realistic sounding instruments ?"

EDIT: ok seems that tux guitar sometimes just randomly stops working, but goes back to normal once I restart my machine.
this probably means that the timidity download was not what fixed it.(not sure)
At this point I have no idea what makes it work. I am limiting myself to restart whenever the midi error starts showing up for now.

---

### Post by Jalpuri on 2010-02-07
I got mine working properly by following these steps:

1. Install TiMidity
2. Install tuxguitar-oss via terminal
3. From TuxGuitar's settings, set the MIDI Sequencer to "Real Time Sequencer" and MIDI Port to "TiMidity port 0 #1"
4*. Reboot

* Might not be even necessary.

Hope this helps =)

---

### Post by Moustaffa on 2010-08-26
> **Jalpuri said:**
> I got mine working properly by following these steps:

1. Install TiMidity
2. Install tuxguitar-oss via terminal
3. From TuxGuitar's settings, set the MIDI Sequencer to "Real Time Sequencer" and MIDI Port to "TiMidity port 0 #1"
4*. Reboot

* Might not be even necessary.

Hope this helps =)


NONE (not single one) of all the possible solutions I found works. What am I doing wrong? everything installs just fine, but the lack of sound stays. Tuxguitar can play, I just can't hear a thing.

Using version 1.2 (downloaded from the website, Software center has version 1.1)

---

