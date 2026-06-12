---
title: "Use PulseAudio to pipe audio output into a mic input"
date: 2016-10-05
forum: Multimedia Software
---

### Post by lightspectra on 2016-10-05
I am currently using Ubuntu 16.04. My friends and I play video games while talking over VoIP[SUP]1[/SUP]. I want to play sound clips through Rhythmbox so they hear the music as if it's coming from my microphone, and I hear it as normal; that is to say, **I want to [B]duplicate** the audio output of Rhythmbox, and pipe/route it into my mic input. 
[/B]
I followed the instructions on [this AskUbuntu question]("https://askubuntu.com/questions/257992/how-can-i-use-pulseaudio-virtual-audio-streams-to-play-music-over-skype") but it didn't work for me; I'm stuck on the step "Loopback to Null Output (1): Your headset/microphone" because the GUI for PulseAudio configuration (pavucontrol) did not let me change "Loopback to Null Output" to my mic input, only another output source. The question is now over three years old so I didn't want to add to it. Assuming I'm on the right track, the last piece of the puzzle I need is: is there a terminal command I can use for pacmd or pactl in order to pipe/route a source-output into a sink-input?

Or, does anybody know of some PulseAudio configuration tool or shell script or whatnot that would automatically do what I am asking for?

[SIZE=1][SUP]1 [/SUP]I asked a similar question on StackExchange and somebody demanded to know what program I was using for the VoIP call. I don't think it should matter because I don't see how it's relevant to the question, but it's Google Hangouts. I've achieved a result similar to what I want by entering the Hangout using both Firefox and Chrome, and then configuring Rhythmbox to go through RTP multicast and then changing the Firefox mic input into the RTP multicast, but that requires essentially being in two Hangouts at the same time, using double the bandwidth. StackExchange also suggested I use jackd, but I was hoping somebody here would know the answer for how to do it in PulseAudio before I go through the trouble of learning how to use jackd.[/SIZE]

---

