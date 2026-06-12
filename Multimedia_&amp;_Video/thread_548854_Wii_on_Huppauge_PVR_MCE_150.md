---
title: "Wii on Huppauge PVR MCE 150?"
date: 2007-09-11
forum: Multimedia &amp; Video
---

### Post by st00ner on 2007-09-11
Hi, ive been digging around a bit and just recieved my new Huppauge PVR MCE 150 from newegg.
I checked dmesg and it appreared to set up the video devices fine.

[   17.068000] ivtv:  ==================== START INIT IVTV ====================
[   17.068000] ivtv:  version 0.10.1 (tagged release) loading
[   17.068000] ivtv:  Linux version: 2.6.20-16-generic SMP mod_unload 586 
[   17.068000] ivtv:  In case of problems please include the debug info between
[   17.068000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[   17.068000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[   17.068000] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   17.072000] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   17.748000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[   17.964000] ivtv0: Encoder revision: 0x02050032
[   17.964000] ivtv0: Recommended firmware version is 0x02060039.
[   18.028000] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   18.056000] tuner 2-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   18.060000] tuner 2-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   18.104000] cx25840 2-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[   23.004000] wm8775 2-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   23.068000] ivtv0: Registered device video0 for encoder MPEG (4 MB)
[   23.068000] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   23.068000] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   23.068000] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   23.068000] ivtv0: Registered device radio0 for encoder radio
[   23.456000] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
[   23.456000] ivtv:  ====================  END INIT IVTV  ====================
[ 2497.592000] ivtv0: All encoder VBI stream buffers are full. Dropping data.
[ 2497.592000] ivtv0: Cause: the application is not reading fast enough.


I plugged my Wii into the video inputs (the red white yellow cables etc)
When i do
mplayer /dev/video0 
all i get is a bunch of static.
On these, i get nothing
mplayer /dev/video24
mplayer /dev/video3


Does anyone know how to do what i want to do :{

---

### Post by rsambuca on 2007-09-11
The card is set by default to the coax input.  You have to change it to the composite inputs.  Try this in a terminal:```
v4l2-ctl -d /dev/video0 --set-input=2
```Just so you know, with this card there will probably be a small delay due to the mpeg decoder, so gaming may be difficult.

EDIT:  You may have to add ivtv-utils prior to executing the above command.  You can use Synaptic Package Manager for this or "sudo apt-get install ivtv-utils"

---

### Post by st00ner on 2007-09-11
> **rsambuca said:**
> The card is set by default to the coax input.  You have to change it to the composite inputs.  Try this in a terminal:```
v4l2-ctl -d /dev/video0 --set-input=2
```Just so you know, with this card there will probably be a small delay due to the mpeg decoder, so gaming may be difficult.

EDIT:  You may have to add ivtv-utils prior to executing the above command.  You can use Synaptic Package Manager for this or "sudo apt-get install ivtv-utils"

Yeah i just tried it and its basicly unplayable :\ (around a 10 second delay) is there cards without delay, or do i need to get converters and put it on my monitor somehow lol. yarrgg this is frustrating. O well at least i can watch cable on my computer now >.>

Does anyone happen to know the name of the converters that would let my wii go from the video in to DVI or to headphone jacks?

EDIT: i might have to get a TV... or a monitor TV... gawd :[

---

### Post by rsambuca on 2007-09-11
A ten second delay seems odd.  There will always be a slight delay due to the hardware encoder, but it shouldn't be anywhere near that high.  What software are you using for a viewer?

---

### Post by st00ner on 2007-09-11
> **rsambuca said:**
> A ten second delay seems odd.  There will always be a slight delay due to the hardware encoder, but it shouldn't be anywhere near that high.  What software are you using for a viewer?

mplayer. i dont mind less than a second of delay honestly, but right now its just absurd lol.
I play casual games like Mario party and action games, but none of them take super fast reflexes like guitar hero.
If i can make this work it would be great as i am a poor college student T_T

---

### Post by rsambuca on 2007-09-11
Try vlc.  My delay is less than a second using this.

---

### Post by st00ner on 2007-09-12
> **rsambuca said:**
> Try vlc.  My delay is less than a second using this.

the video conferencing tool?

I tried doing the command line

vic /dev/video0

but it just quits after. I read the manual but im still quite confused

A command line example would be great

---

### Post by rsambuca on 2007-09-12
You can try this command```
vlc pvr:// :pvr-device="/dev/video0"
```

---

### Post by rsambuca on 2007-09-12
LOL, Oh, I see the problem now.  I was talking about vee-el-cee!  VideoLan player!

---

### Post by st00ner on 2007-09-12
> **rsambuca said:**
> LOL, Oh, I see the problem now.  I was talking about vee-el-cee!  VideoLan player!

Just tried it, still tho im getting 2-3 seconds lag. I wonder if i have it confugured wrong

The quality is about the same i get on my junky tv, which is fine with me.
I just wish i could kill the lag abit :[

---

### Post by rsambuca on 2007-09-12
Check out the instructions in post #4 of this thread.  Looks like a perfect solution!

[http://ubuntuforums.org/showthread.php?p=3299935](http://ubuntuforums.org/showthread.php?p=3299935)

---

### Post by st00ner on 2007-09-12
> **rsambuca said:**
> Check out the instructions in post #4 of this thread.  Looks like a perfect solution!

[http://ubuntuforums.org/showthread.php?p=3299935](http://ubuntuforums.org/showthread.php?p=3299935)

Wow it works perfectly now! almost no noticable delay :D
i dont mind the poor picture quality as long as i can play the game :P

Thank you soooo much for the help!

---

### Post by rsambuca on 2007-09-12
So it works well then?  How much is the lag, now?

---

