---
title: "Alesis iO2 + Jack + Ardour"
date: 2014-02-22
forum: Multimedia Software
---

### Post by jorishartog on 2014-02-22
Hi there!

I use Ubuntu 12.04 LTS(64-bit) and I want to connect the audio signal from my Alesis iO2 to Ardour with Jack. Jack only recognizes the midi channel of the iO2, but the audio channel doesn't show up in the connection list. I once solved this by changing the input device to hw:1(the iO2) and it worked, but after a reboot I was back at square one.

Everytime I change the settings in Jack, I get a warning in the bottom-right corner from which I can only see the title("Warning - JACK Audio Connection Kit"). Clicking it removes the message and changing my screen resolution does not help. Jack's Message Log doesn't mention any errors or warnings.

~/.jackdrc:
/usr/bin/jackd -P38 -dalsa -dhw:0 -r44100 -p1024 -n2 -D -Chw:1

I tried changing the Periods/Buffer from 2 to 3, my sample rate is correct (44100 Hz); I'm at a point that I don't know where to look for the answer :)

Have a nice day!

Joris Hartog

---

