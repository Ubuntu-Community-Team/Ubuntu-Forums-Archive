---
title: "Help using getting my headset microphone needed"
date: 2012-09-13
forum: Multimedia Software
---

### Post by agrayray on 2012-09-13
I have a thinkpad t410 with a combo headset/mic jack (just one for both) but can not seem to get ubuntu to use my headset microphone.

The internal microphone works fine..in fact, when I plug in my headset the audio comes through the headset but the microphone is actually the internal mic not the ones from the headset.

I have checked my sound preferences and only have one option of device to choose for input:

"internal Audio Analog Stereo"

my hardware tab only lists various output names except one entry which is actually what is selected:

"Analog Stereo Duplex"

Does anyone know how I can add other hardware for sound to include a microphone or get my external microphone to work...

BTW, I actually have four different headset microphones..all different models of logitech..and oh most important probably...I am still on Ubuntu 10.10 (gnome)....and do not want to change/upgrade and would prefer not to install anything new on this machine because with it not being supporting and all...I do not want to screw up machine which is utopia for me at 10.10 the way it is (minus this microphone issue)

Thanks in advance!!!

---

### Post by opensshd on 2012-09-13
Can you tell me a couple things about the specifics of your mic. Are you using a 2pt 3.5mm mic plug in a 3pt 3.5mm jack? Or is this mic with the stereo earphones in a 3pt plug?

3.5mm comes in 2 or 3 pt jacks and plugs. You can tell the difference in plugs by how many bands are on the part to plug into the jack.

Also, that model came out with a hardware switch for the mic, that is not it eh? It says "mic/headseat combo jack" I just wonder if that is a switching 2pt or a 3pt... I would think 3pt...

It's possible that hardware switch might not be recognized by the Ubuntu OS, but should be for the builtin mic, not the input jack?

perhaps Ubuntu needs something for those mic/headphone combo jacks.. lemme check.

---

### Post by agrayray on 2012-09-13
I actually have two different sets of headset/microphones (2 of each)..but they all are the standard 2pt 3.5mm plugs...one set actually has two different plugs one for mic and one headphones...I have tried inserting both..only the headphone one works..with the mic plug in..there is no sound but unfortunately also no headset mic.  The other model just is one plug with a switch button on to turn microphone on or off...but again none works.

Thanks for the reply.

---

### Post by opensshd on 2012-09-13
You could try this without hurting anything:

this will add a repository for the developers of alsa:

sudo add-apt-repository ppa:ubuntu-audio-dev/ppa

then, you would get the latest alsa drivers by typing:

sudo apt-get update && sudo apt-get upgrade

Then modifying:

sudo gedit /etc/modprobe.d/alsa-base.conf

adding this line:

options snd-hda-intel

Maybe try that? You'll have to reboot.

---

### Post by opensshd on 2012-09-13
Ah sorry, you don't want to upgrade... not sure if adding that line to the asla conf file will work with current versions of what you have.

Worth a try :)

---

### Post by agrayray on 2012-09-13
No luck however...i think opensshd was onto something as this might not be a ubuntu issue at all as it appears from reading lenovo forum and threads like:

[http://forums.lenovo.com/t5/T400-T500-and-newer-T-series/Use-T410-audio-jack-for-line-input/td-p/344473](http://forums.lenovo.com/t5/T400-T500-and-newer-T-series/Use-T410-audio-jack-for-line-input/td-p/344473)
(they are set to use 2pt type headphones by default)

I need a 3pt jack for the microphone to work with the computer so apparently I dont have the right headsets to use with this computer

and am giving up...unless any of you know better

thanks to all for the help!

---

