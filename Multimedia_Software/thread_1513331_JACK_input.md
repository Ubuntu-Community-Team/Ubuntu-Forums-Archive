---
title: "JACK input"
date: 2010-06-19
forum: Multimedia Software
---

### Post by The_PhAnT0m on 2010-06-19
I am not sure if this is the proper forum to post in. If not feel free to redirect. So I am running the normal, vanilla, unexciting 32-bit version of Ubuntu. I am trying to hack it into something closer to Ubuntu Studio. I have JACK installed and running fine. Can direct audio output, MIDI works, and can get every application with a JACK plug in to work fine. The problem is, I can not get any audio input. I have an X-Fi which has otherwise worked fine. In Windows, works perfectly. I just cannot figure out how to get any sort of audio input at all. It gives me two (by default) capture lines. Directing them straight to playback has no effect whatsoever. Any help or tips would be appreciated.

---

### Post by The_PhAnT0m on 2010-06-22
Still been working on my problem. Under Windows XP, I can get the audio input (is actually a guitar hooked up to a pre-amp/amp that sends the headphone-out to the mic jack on the X-fi. Best solution I have with limited equipment) to work fine. When I boot into Ubuntu 10.04, no changes to hardware whatsoever, it won't work. No matter what configuration I have it under (5.0, 7.1, Stereo Duplex, etc.), all I get is a faint version of the audio ouput. Its like the input is some strange internal software feed of the audio output to the input. That is all under Pulseaudio. When I start JACK, I get no input at all. The output will work fine though. Anybody have any suggestions?

---

### Post by cchhrriiss121212 on 2010-06-23
First stop would be to open a terminal and type alsamixer. Then press f4 to see your capture levels, they are likely too low, so raise them up a bit.

---

### Post by The_PhAnT0m on 2010-06-23
Thanks for the help. When I run alsamixer, and unmute the line-in on playback, my guitar will be heard through the speakers, so I know it is plugged into line-in. I want to route the audio through various filters using JACK. Unfortunately, even when I set the volume for every capture channel to max, I get nothing. (To test, JACK's 2 default capture channels are sent directly to playback, each capture channel is sent to every playback just to make sure) As an extra precaution, I switch the capture device in alsamixer between Line in and mic. Nothing on either. Thanks again for the advice. Im closer lol.

---

### Post by cchhrriiss121212 on 2010-06-23
> When I run alsamixer, and unmute the line-in on playback, my guitar will be heard through the speakers, so I know it is plugged into line-in.
So your inputs are working without jack, but not working when it is running? Or does the above quote refer to something else?
Could you post your jack settings? Either a screenshot or just put "cat proc ~/.jackdrc" into a terminal.

---

