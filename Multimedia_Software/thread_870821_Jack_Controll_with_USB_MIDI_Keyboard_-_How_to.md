---
title: "Jack Controll with USB MIDI Keyboard - How to"
date: 2008-07-26
forum: Multimedia Software
---

### Post by Ben Carlin on 2008-07-26
Hi,

I recently bought a USB MIDI connector for my computer & am a bit bewildered on how to set it up with Jack Control. I tried using a guide from this link:

[http://64studio.com/quickstart_jack](http://64studio.com/quickstart_jack)

but after following all the steps, still no luck. I get this message from the messages button:

"13:17:57.074 Patchbay deactivated.
13:17:57.374 Statistics reset.
13:17:57.780 ALSA connection graph change.
13:17:57.786 ALSA connection change.
13:17:58.659 JACK is starting...
13:17:58.660 /usr/bin/jackd -R -p128 -dalsa -r44100 -p128 -n2 -D -Chw:0 -Phw:0
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread -1693575456, from thread -1693575456] (1: Operation not permitted)
cannot create engine
13:17:58.678 JACK was started with PID=6344.
13:17:58.679 JACK was stopped successfully.
13:17:58.679 Post-shutdown script...
13:17:58.680 killall jackd
jackd: no process killed
13:17:59.088 Post-shutdown script terminated with exit status=256.
13:18:00.811 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info."

I also get this message from a seperate box:

"Could not connect to JACK server as client.
- Overall operation failed.
- Unable to connect to server.
Please check the messages window for more info."

In the setup area these are the options of Input device (Drop down menu):

HW:0        CA0106
Hw:0,0      CA0106
Hw:0,1      CA0106
Hw:0,2      CA0106
Hw:0,3      CA0106
HW:1        USB to Midi Adaptor
(Default)

I'm not sure what I should select for the input & output?

In the connections section of Jack Control I have 3 tabs:

Audio MIDI ALSA

Jack Control hasn't detected anything in Audio or MIDI but it has detected it all in ALSA I'm not sure if this is right? In the ALSA tab it displays all of these:

_Readable Clients/Output Ports_   _Writable Clients/Input Ports_       


14:MIDI Through                                     
16:CA0106                                           
20:USB to MIDI Adaptor                              

How am I meant to link these up?
Sorry complete noob at this sound stuff!:(

Hope I've explain that all ok? Very grateful for any help!!

---

### Post by vivichrist on 2008-08-06
> How am I meant to link these up?
Sorry complete noob at this sound stuff!

select the ones you want to connect and press the connect button ya big noob.:)

---

