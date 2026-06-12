---
title: "Questions on pulseaudio and A2DP"
date: 2015-02-10
forum: Multimedia Software
---

### Post by Stormlord on 2015-02-10
There are two questions I'd like to ask guys and I'd appreciate it if you could help on either or both of them.


1.  There are these options in pulseaudio's daemon.conf file
; default-sample-format = s16le
; default-sample-rate = 44100
; alternate-sample-rate = 48000
Do those settings tell pulseaudio that it should always resample all incoming audio to match those values no matter what, before it sends the sound to the sound card OR do they instruct pulseaudio to use these values as maximum settings and only downsample incoming audio if it exceeds them and keep the sound attributes as they are if they are <= to the shown values?


2.  I want to use my Xubuntu computer as an A2DP receiver and I am using he following settings in my bluetooth "audio.conf" file:
[General]
Enable=Source,Sink,Headset,Gateway,Control,Media,Socket
AutoConnect=true
[Headset]
HFP=false
MaxConnected=1
FastConnectable=false
[A2DP]
SBCSources=1
MPEG12Sources=0


I have also installed pulseaudio-module-bluetooth.


The computer connects successfully to my Android 4.4 phone using Blueman and music is streamed normally from the phone to the computer but there's absolutely no way for me to find the phone in pulseaudio sources or inputs so that I can route the incoming audio to the computer's speakers.  There's something missing and I can't find what it is.  All the instructions I've found so far assume that the bluetooth source is listed in pulseaudio sources which is exactly the issue.  It's not there.


Thanks in advance...  ;)

---

### Post by Yellow Pasque on 2015-02-11
> Do those settings tell pulseaudio that it should always resample all incoming audio to match those values no matter what
Yeah, that. [http://arunraghavan.net/2011/10/alternate-sample-rates/](http://arunraghavan.net/2011/10/alternate-sample-rates/)

---

