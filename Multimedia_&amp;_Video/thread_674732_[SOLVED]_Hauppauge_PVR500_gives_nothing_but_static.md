---
title: "[SOLVED] Hauppauge PVR500 gives nothing but static"
date: 2008-01-22
forum: Multimedia &amp; Video
---

### Post by bethebunny on 2008-01-22
In Vista I can sometimes get it to play whatever channel I'm on, but it has horrifying vertical lines and a buzzing that covers up the sound. Debian never recognized it as a video device (didn't add anything to the /dev folder).

Using Ubuntu Gutsy AMD64:

I never explicitly installed drivers or firmware, as the IVTV Howto for Ubuntu told me they were built into the Linux kernel a while ago.

Ubuntu sees all of the devices. After an hour or so of configuring Mplayer (MythTV for some reason won't start MySQL, which is a can of worms I'd much rather save for another day, when I'm actually sure that the tuner's working.

After a while screwing with Mplayer to make it work on my install (Unfortunately the Radeon HD3750 doesn't have Linux driver support yet...) I finally got it to output mpeg2 encoded files from /dev/video0 and /dev/video1. Dandy. Except they're all just static. Doing cat /dev/video0 > file.mpg and watching it with Totem or VLC yields the same result.

Attempting to view raw video with mplayer (necessary if I want to hook my Wii up and play on my comp) results in mplayer hanging.


Additional info:
Athlon 64 x2 6400+ Processor
VisionTek HD3870 Radeon graphics card
Hauppauge PVR500 TV tuner
MSI K9A2 Platinum Motherboard
DirecTV connection

I tried using both the coaxial and RCA connector types (at different times) from the STB to my Tuner. Also tried STB -> Coaxial -> VCR -> RCA -> Tuner, which didn't work. All I ever see is static.

What am I doing wrong? Is my card busted? I don't think it is, since my comp sees all the devices, and on Vista I can get a slight signal even if it sucks terribly. There's probably some simple thing that I completely missed. Any ideas?

---

### Post by wolfen69 on 2008-01-22
I have a Hauppauge pvr card running on my gutsy box, and I get live tv by: 

sudo apt-get install ivtv-utils 

open VLC player

File -> Open Capture Device -> PVR -> OK

then you can do (in terminal)

ivtv-tune -c25 (25 is channel number)

which changes the channel.

ivtv-tune -h

to see the options which control the card. 


for a cool desktop tv remote,(so you dont have to use terminal to change channels) go to: [http://tvremote.sourceforge.net/](http://tvremote.sourceforge.net/)

remember to have java installed first. then you can right click: open with java.

i am connected via coax from a signal splitter.

---

### Post by bethebunny on 2008-01-22
After installing ivtv-utils, VLC also works to view Tuner input. However, the problem still remains that all I ever see is static (watching from another STB output on a TV works just fine).

---

### Post by bethebunny on 2008-01-22
Hrm... coaxial works with VLC as long as I'm on channel 3 (makes sense). Now the issue is, how do I make it take RCA input? (I'll need one for hooking up my Wii.) Is there a specific channel in IVTV-tune for the A/V inputs?

---

### Post by wolfen69 on 2008-01-22
```
ivtv-tune -h
```

---

### Post by shad0w_walker on 2008-01-25
Sorry to burst your bubble but you won't get to play the Wii through your tuner. There is a few seconds lag between the data coming in and the picture you end up viewing. By the time you saw what was happening it would have already happened.

---

### Post by bethebunny on 2008-01-25
> **shad0w_walker said:**
> Sorry to burst your bubble but you won't get to play the Wii through your tuner. There is a few seconds lag between the data coming in and the picture you end up viewing. By the time you saw what was happening it would have already happened.

Check out [this page]("http://ubuntuforums.org/showthread.php?p=3299935"). Incidentally, not only does this make video games playable, I also used some of the code to make my TV work ;) This topic is now solved.

---

