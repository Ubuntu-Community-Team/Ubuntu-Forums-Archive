---
title: "HDA Intel Capture Volume setting not sticking"
date: 2009-10-08
forum: Multimedia Software
---

### Post by njhwang on 2009-10-08
Hi all,

My first post, so I apologize if this information is elsewhere...hopefully you can point me in the right direction!

So I have an Acer D150 running Jaunty Netbook Remix 9.04. I ran into the same microphone issues that everyone else ran into, and fixed most of them by installing the latest ALSA drivers. I also made sure to install Skype 2.0.0.72, since Skype 3.0 wouldn't allow me to select the HDA Intel microphone as my input. Skype works marginally well (that's another issue), but my issue is this...

If I go to Volume Control->Recording, the Capture setting (that little microphone button) just refuses to stay enabled. I can enable capture, close Volume Control, and then open it up again and it'll be disabled. I initially tried setting up a volume configuration startup script with a bunch of amixer commands, including ```
amixer cset iface=MIXER,name='Capture Volume' on
```, which can successfully enable capture from the command line. I also made sure that this script runs after the pulseaudio startup script in case pulseaudio was the culprit, but capture starts out disabled on boot and also refuses to stick if I manually configure it. I'm not really sure what's going on, since I can enable capture and happily Skype away, but if I open Volume Control again, capture will be disabled...

I'd like to be able to 1) boot with capture enabled and 2) have the enable capture setting not disappear automagically. Anyone have any ideas?

Thanks!

---

