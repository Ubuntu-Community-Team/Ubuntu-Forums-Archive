---
title: "Darkice - 0 bytes transfered to the encoders"
date: 2009-06-09
forum: Multimedia Software
---

### Post by Duckter on 2009-06-09
To summarise a long problem I cannot get Darkice to do what I want it to.

I have successfully hooked up my decks and can record from the input via Audacity so looks good there.

I have a SHOUTCAST server that is configured and working perfectly

I have installed Darkice (compiled it from source for lame support) and installed jackd

This is the problem... I have no idea what is not working and cannot find any info specific to this problem via google or these forums.

```
09-Jun-2009 15:18:19 Using OSS DSP input device: /dev/dsp
09-Jun-2009 15:18:19 encoding
09-Jun-2009 15:18:19 scheduler high priority 99
09-Jun-2009 15:18:19 Using POSIX real-time scheduling, priority 98
**09-Jun-2009 15:18:19 0 bytes transfered to the encoders**
09-Jun-2009 15:18:19 reverted to original scheduling
09-Jun-2009 15:18:19 encoding ends

```I have tried using jack and jack_atuo for the device, but just get the same error. I think its something to do with the darkice but my config seems fine as far as i can tell.

```
[general]
duration        = 7200
bufferSecs      = 5

[input]
device          = /dev/dsp
sampleRate      = 44100
bitsPerSample   = 16
channel         = 2

[shoutcast-0]
bitrateMode     = cbr
bitrate         = 96
quality         = 0.8
server          = xxx.xxx.xxx.xxx
port            = 80xx
password        = lalalalala
name            = Spiffy radio
url             = na
genre           = live
public          = no
irc             = na
aim             = na
icq             = na
```Hopefully it's just a really simple oversight. Help as always is appreciated. :)

---

### Post by Duckter on 2009-06-09
SORTED!

One of the problems with darkice seems that you have to enter the port number +1

e.g. for 8000 enter the port number as 8001

Woulda saved me hours if I knew that. Hope this helps others.

---

### Post by RandomJoe on 2009-07-28
Can you think of anything else you may have done to fix this?  I'm having exactly the same problem, and changing the port number by one doesn't fix it.

Every example I find online suggests my config is fine, and I even tried a simple save-to-file config and still the same thing.  Feel like I'm beating my head against a wall! :confused:

In case it might matter, I'm on 8.10 with this machine, used the lame that's in the repo and compiled my own darkice - v0.19.

---

### Post by Duckter on 2009-08-03
Here is the config that I use for live streaming via line in.  If it's not a config issue you might need to install jack [sudo apt-get install jack] assuming you havent already and check the mixer settings to make sure you havent got your line in capture muted.

```
[general]
duration        = 0
bufferSecs      = 5

[input]
device          = jack_auto
sampleRate      = 44100
bitsPerSample   = 16
channel         = 2

[shoutcast-0]
bitrateMode     = cbr
bitrate         = 96
quality         = 1
server          = 123.45.67.89
port            = **8013**
password        = imapassword
name            = ONLINE RADIO
url             = na
genre           = music
public          = no
irc             = na
aim             = na
icq             = na

```

You can always try running darkice using sudo... if it works then its maybe just a permissions issue and you can set that up via System -> Administration -> Authorisations

Are you getting any specific messages that can help the trouble shooting or is it the same one about 0 bytes transfered? The server i use is on port 8012 and as soon as i set it to 8013 it was happy. Sorry about the late reply but i'll try my best to help you. This thing was a total nuisance for me too but I got there in the end!

---

### Post by Duckter on 2009-08-07
I also use this for my jack server

```
jackd  -d alsa  -r 44100 -C
```

---

