---
title: "i want to hear myself on headphones through internal microphone"
date: 2011-03-11
forum: Multimedia Software
---

### Post by hallansing on 2011-03-11
Hi all, 
setup:
64 bit laptop 
pulseaudio + alsa 
ghome alsa mixer installed 

All sound works fine: speakers, headphones, microphone, recording ( microphone or sound card output ), etc.

Question: 
The default setup is that I can't hear myself on headphones through the internal microphone, 
but the microphone is working fine when capturing from it or on skype...

I want to somehow enable the microphone patch through so that I could hear myself talk 
through it on headphones. 
I tried Pulse Audio volume control app, Gnome Alsa mixer, Alsamixer ( shell version ) 
there are seem to be no settings to patch the mike through to either speakers or headphones...

Anybody got any solutions on how to do it... It worked like that  by default in windows...

Any scripts, pointers, settings ???

Thanks.

---

### Post by hallansing on 2011-03-14
found the solution here:

[http://superuser.com/questions/127276/how-to-play-from-mic-to-speakers-in-ubuntu-karmic](http://superuser.com/questions/127276/how-to-play-from-mic-to-speakers-in-ubuntu-karmic)

basically to enable microphone -> speakers/headphones pass through
 ( so that you can hear yourself in your headphones on internal microphone ):
1. from terminal run this command:
pacat -r | pacat -p 
2. keep terminal window open 
3. open Pulseaudio volume control application 
4. input devices -> click speaker button to unmute microphone 

microphone will be patched to headphones/speakers 

5.to disable simply close the terminal 

Regards.
ps. on further testing, noticed about 1-2 second echo delay between when you speak and when you hear yourself !!! pulseaudio sucks

---

