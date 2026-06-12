---
title: "Internet Dj Console. audio port buffers in use!"
date: 2009-09-11
forum: Multimedia Software
---

### Post by wesleybishop on 2009-09-11
I try running the program and this is what I get

UPDATE!
ok this is what I get when I try to start idjc

[COLOR=DarkRed]The JACK sound server needs to be running in order to run IDJC.
In order to manually start it try something like:

    $ jackd -d alsa -r 44100 -p 2048

If you would like JACK to start automatically with your user specified parameters try something like this, which will create a file called .jackdrc in your home directory:

    $ echo "/usr/bin/jackd -d alsa -r 44100" > ~/.jackdrc

If you have already done this it is possible another application or non-JACK sound server is using the sound card.

Possible remedies would be to close the other audio app or configure the sound server to go into suspend mode after a brief amount of idle time.

If you are trying to connect to a named jack server, either set the environment variable JACK_DEFAULT_SERVER to that name or launch IDJC with the -j jackservername option. For example:

     $ jackd -n xyzzy -d alsa -r 44100 -p 2048 &
     $ idjc -p profilename -j xyzzy[/COLOR]

Can anyone help me please :D

---

### Post by StephenF on 2009-09-19
> **wesleybishop said:**
> 
Can anyone help me please :D
Maybe shut down whatever programs are using the sound card and any sound servers like portaudio.

---

### Post by wesleybishop on 2010-06-11
Still never got this to work :( I will post more info on the issue in a few days in the mean time does any one have a program comparable to virtual dj?

---

### Post by StephenF on 2010-06-12
Start the sound server jackd in a console with:

jackd -d alsa 

It will probably error out and give instructions on how to configure your operating system for real-time scheduling. Once you have it start you will be able to run IDJC.

---

### Post by vmosorio on 2010-06-24
> **StephenF said:**
> Start the sound server jackd in a console with:

jackd -d alsa 

It will probably error out and give instructions on how to configure your operating system for real-time scheduling. Once you have it start you will be able to run IDJC.

Hello,

For now I just need to use IDJC for playing my audio files and use the nice feature it has of normalizing  the audio and skipping silence. My problem is that if I start Firefox while IDJC is playing the audio starts to drop until it disappears and then the IDJC buttons do not respond. I have to restart the system if I want to be able to hear the music again. 
I tried a different audio player after the freze and it played ok it is just IDJC.
I have installed jack control as IDJC requires and I'm using Ubuntu 10.04

I appreciate any ideas.

Victor

---

### Post by StephenF on 2010-06-28
IDJC is not the best for general listening because it blocks other audio applications that don't route their audio through JACK. The audio shouldn't sputter/fade out though. It sounds more like a problem with the sound server. I suspect a dodgy patch for audio sharing may have been applied.

Jack control (aka QjackCtl) is not as necessary as you think. After saving the settings a JACK sound server will load and run automatically with the first JACK application.

---

### Post by slammurai on 2010-09-29
I am having the same issue wit IDJC but I am trying to set it up for a shoutcast server.

---

