---
title: "no sound with alsa_out and jack"
date: 2011-08-16
forum: Multimedia Software
---

### Post by DatBugler on 2011-08-16
Hi,

I'm experimenting with setting up jack with multiple soundcards using alsa_in and alsa_out. I am having trouble getting sound output from alsa_out. Here are my sound cards:
```

~$ cat /proc/asound/cards
 0 [M2496          ]: ICE1712 - M Audio Audiophile 24/96
                      M Audio Audiophile 24/96 at 0xec00, irq 20
 1 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfbff4000 irq 16
 2 [PCR            ]: USB-Audio - PCR
                      EDIROL PCR at usb-0000:00:12.1-3, full speed
 3 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfe97c000 irq 19
 4 [USX2Y          ]: USB US-X2Y - TASCAM US-X2Y
                      TASCAM US-X2Y (1604:8007 if 0 at 004/002)

```
When I have QJackCtl set to use hw:SB as the output device, the connections window displays 8 playback channels on system out, the first two of which produce stereo sound on my speakers. 

The setup I'm experimenting with has QJackCtl set to use hw:M2496 as both input and output device. I then have QJackCtl run the following script after jack starts up:
```

#! /bin/bash

alsa_in -j USX2Y_in -d hw:USX2Y &
alsa_out -j USX2Y_out -d hw:USX2Y &
alsa_in -j SB_in -d hw:SB &
alsa_out -j SB_out -d hw:SB -c 8 &

```
QJackCtl runs "killall alsa_in & killall alsa_out" before shutdown.

Problem one is that I have yet to see all four alsa_in/out instances show up in QJackCtl. I typically will see a random selection of three, and get these errors in Jack messages:
```
Unable to set hw params for playback: Invalid argument
Setting of hwparams failed: Invalid argument
```
Then on shutdown of jack, I get the following errors:
```
JackClientSocket::Read time out
selected sample format: 24bit - real
delay = 4934
delay = 1021
delay = 1019
delay = 1012
JackProcessSync::LockedTimedWait error usec = 92876 err = Connection timed out
JackEngine::ClientCloseAux wait error ref = 3
#-- snip (a bunch of ports get deleted) --
Cannot read socket fd = 3 err = Connection reset by peer
Cannot write socket fd = 3 err = Broken pipe
Cannot write socket fd = 3 err = Broken pipe
Could not read result type = 24
18:46:08.514 ALSA connection graph change.
selected sample format: 32bit
selected sample format: 32bit
delay = 4094
delay = 1009
Cannot write socket fd = 21 err = Broken pipe
18:46:08.642 JACK was stopped successfully.
18:46:08.642 Post-shutdown script...
18:46:08.642 killall jackd
18:46:08.643 JACK has crashed.
```
Every so often on jack startup I also get errors complaining that one of the alsa_in/out instances couldn't find a jack server to connect to.

Problem two, and the bigger one, is that while I have successfully gotten audio input from USX2Y_in, I get no sound when I connect audio output to any channel of SB_out. I don't know what the problem is, given that I successfully get sound on hw:SB when it is controlled directly by jack, and I have sound on hw:SB through PulseAudio/ALSA.

I'd appreciate suggestions on either or both of those problems. Sorry for the long post.

---

