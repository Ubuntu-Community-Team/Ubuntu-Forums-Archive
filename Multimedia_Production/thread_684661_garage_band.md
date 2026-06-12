---
title: "garage band"
date: 2008-02-01
forum: Multimedia Production
---

### Post by patchido on 2008-02-01
>  Re: Garage Band on Linux?
No, GarageBand will not run without Mac OS X.

GarageBand is a pretty big program, being a DAW, MIDI sequencer, front-end for software synthesizers and DSP plugins, and who knows what else. There's nothing that does all that in Linux ... Yet. When Ardour gets MIDI capabilities, it'll be in the running, but until then, you'd need to use several programs under Linux, all connected with Jack. For example, you could use Rosegarden for MIDI sequencing, QSynth or ZynAddSubFX to control software synths, and Ardour to record live sound and mix it all together.


what does he mean y connecting them with jack?

---

### Post by nalmeth on 2008-02-01
All of those programs run on the JACK Audio Engine.
The audio/midi signal of any JACK app can be routed into any other JACK app.

qjackctl is a program that controls JACK. Using the JACK Connections window you can control where audio/midi is being routed.

So you would have Ardour running, and route ZynAddSubFX into a track in Ardour, and Hydrogen into another track in Ardour.

---

### Post by czman11 on 2008-05-09
A little help from one musician to another and I hope this will help you.  You will need strong and fast CPU and I would say at least 2G of RAM. 
Have you seen the PC version of Garageband yet?  It's called Mixcraft and it is a complete equivalent to Garageband for Windows.  I installed it on my Ubuntu 7.10 and run it with Wine.  It runs but I need to do some tweaking before I got it running 100%.  So far it runs little choppy.  You will need to get Wine (windows emulator) first.

open your terminal
Applications/Accessories/Terminal

after your terminal opens type:

sudo apt-get install wine

you will be asked to put in your password, type it in.
wine will be then installed onto your system. After the installation you can check if Wine is in your Applications.

Then go to [www.acustica.com](www.acustica.com) and download it free for 7 days.  After 7 days the only thing you will not be able to do with it is convert your work into mp3.

MAKE SURE THAT DURING INSTALLATION you change the path of the installation.  Ubuntu does not have a C drive.  The path you want to select is:

Z/home/your name/

Installation takes place from there and you are good to go.

Good luck

---

