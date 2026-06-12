---
title: "So... Modular Music Production"
date: 2007-06-29
forum: Multimedia Production
---

### Post by adamdawkins on 2007-06-29
Hi,

After a brief hunt around the forum I've found the same explanation given to 'ex-Windows/Mac' music producers moving onto Ubuntu - It's usually something like this:

> Linux is modular. Instead of having a lot of 'complete' programs that do everything, it has lots of small programs that do a very specific thing - but they all link to each other and work together to produce the same results

If someone wouldn't mind, could we have a break down of the basics - "what does what" in relation to your *Reason*'s, *Pro-tools*' *Logic*'s of the 'non-Linux' music-production world?

Also, the Ubuntu Studio package must have downloaded at least 30-40 applications for me, some of these have got to do some pretty cool stuff people haven't realised.


For example:

*Reason's re-drum* = *Hydogen* - the benefits of *Hydrogen* seem clear, it's simpler, and more specialised. 

*Ardour* seems to resemble *Pro Tools* in some ways, and I'm assuming *RoseGarden* is some kind of sequencer. But what are the benefits/costs of all this stuff - if someone doesn't mind sharing their experiences. What's the best way you've found of combining some of these programs? Where kind I find a *Reason-like* piano-roll for example?

Anyone fancy shedding some invaluable light on Ubuntu-studio?

---

### Post by fredj on 2007-06-29
The most important program loaded as part of Ubuntu Studio is Jack Control (qjackctl) which allows you 
to configure and start the Jackd audio server. This the hub that links everything together.
Rosegarden and Ardour are multi-track audio/midi hard disk recorders. 
Qsynth is a software synthesiser that uses Creative Soundfonts (sf2 version).
Audacity is an audio editor for wav or mp3 files etc with effects.
All these programs will work together through the Jackd server so I can load midi tracks into Rosegarden
and play them back through Qsynth. I can also play and record muti-track audio at the same time. I don't
know what you mean by a Reason type of piano roll since I came to Unix from a Windows background and
I only know Cubase and Sonar etc.
An important part of setting up a music studio on Ubuntu involves installing the Real Time Kernel - see the
sticky at the top of this forum. 
There are many other programmes loaded as part of Ubuntu studio e.g. software analogue synths, score
editing (although Rosegarden also provides scores) guitar effects, drum machines are also in there.
Hope this helps.

---

### Post by adamdawkins on 2007-06-29
That's certainly a very helpful start!

Thanks!

---

### Post by tgalati4 on 2007-06-29
An important point is that a real-time, low-latency kernel will give your primary audio program 95% of the CPU cycles.  You will get less or no dropouts when recording live events.  Streaming media becomes more consistent.

The full-blown media tools are powerful, but they consume your machine.      Linux offers an alternative.  I have used it to produce 4 GB of mp3 music without a problem.  That's 5 days of playback consisting of recording, mixing, and compressing on a 2.8 GHz P4.  The music server is hosted on a 1 GHz Celeron machine.

You get more mileage out of old hardware with Linux.  The tools are free and the result is the same--music, video or whatever.

Oh, and you get the predictable behavior that Linux is known for.

---

### Post by TRinQtown on 2007-07-02
It's not FREE, but energyXT2 is the closest thing in Linux to a full DAW. $75

---

