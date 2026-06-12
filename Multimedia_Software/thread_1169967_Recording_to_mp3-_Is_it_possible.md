---
title: "Recording to mp3- Is it possible?"
date: 2009-05-25
forum: Multimedia Software
---

### Post by sp0nge on 2009-05-25
Hello again!

I have been trying to successfully record audio from my sound card. I have been playing with the sound recorder within applications but it is not recording very well- I have toyed with the preferences but i'm getting fuzzy sound. 

Any better options for recording what comes through the sound card?

---

### Post by logos34 on 2009-05-25
> **sp0nge said:**
> 
Is there a way to do this? I tried Audacity and I even attempted to install my windows app in WINE to no avail. I just think there has to be some option to record from the sound card- I'm just not seeing it?

here you go (terminal):
> 
arecord -f cd -t raw | lame -x - out.mp3 (default - 44100Hz, joint stereo, 128kbps cbr)
arecord -f cd -t raw | lame -x -b bitrate out.mp3 (custom bitrate)
arecord -f cd -t raw | oggenc - -r -o out.ogg (default -q3 I think)
arecord -f cd -d numberofseconds -t raw | lame -x - out.mp3

to cancel recording just do CTRL+C

make sure you have lame

sudo apt-get install ubuntu-restricted-extras

you could also use gnome sound-recorder, set source to 'mix' and select output format

---

### Post by sp0nge on 2009-05-25
Thank you. I will try using the sound recorder and will also install lame and see how that works. 

Very helpful!

---

### Post by zobcat on 2009-05-25
Why didn't Audacity meet your needs? Did you set it to capture the Mix in the volume control? If you want a simpler program, you can try Jokosher. 

Jokosher is in the repositories, but if it doesn't work for some reason, then here is the [deb]("http://launchpad.net/jokosher/0.11/0.11.1/+download/jokosher_0.11.1-0ubuntu1_all.deb").

Good luck!

---

### Post by sp0nge on 2009-05-25
The sound recorder is working, but I'm not able to figure out how to adjust the sound settings appropriately. The bass is too much and the treble is too light..

---

### Post by sp0nge on 2009-05-26
Sorry.. I didn't see the post about audacity. I will try that again. I attempted it at first, but didn't change any options.. that will be my next step today.

---

### Post by sp0nge on 2009-05-27
Wow.. I had a really nice reply about my tale of failure but apparently someone didn't like it as my browser just cleared the post on it's own. I'm not up to typing it again now so this must suffice...

no go! I got the mic to record, audio playing still sounds fuzzy and it's as if audacity is not capturing the sound to the speakers. I used [these Google results ]("http://lmgtfy.com/?q=audacity+how+to+record+from+sound+card+ubuntu") and tried every valid solution as well as toying with the settings on my own to no avail!

There is NO mix options of any sort available in my sound settings, I have explored all options there. Please help me understand what I'm missing!

---

### Post by Bungo Pony on 2009-05-27
Either try a different microphone, or make sure that your mic is plugged into the mic jack and NOT the Line-In.

---

### Post by xzero1 on 2009-05-28
Instead of arecord you could use sox. It can record and has powerful sound processing options which can be chained together. It is a command line program and a bit more difficult to use but you may want to check into it. Install it by sudo apt-get install sox, then do man sox to see the manual.

---

### Post by sp0nge on 2009-05-30
Well perhaps I'll revisit this again at some point. For now, mission accomplished although not quite the route I'd hoped for. I have installed a windows machine within VirtualBox and will use the good ol' [Free Hi-Q Sound Recorder]("http://www.roemersoftware.com/free-sound-recorder/more-info/freehiqrec.exe"). 

Thanks for the help and input.

---

