---
title: "Sound broken, became EXTREMELY QUIET"
date: 2008-05-27
forum: Multimedia Software
---

### Post by ichudov on 2008-05-27
I have Ubuntu Hardy 64 bit version.

Suddenly sound stopped working. To be more exact, sound is extremely
quiet. As in, if I turn up my stereo (which is used as a speaker) all
the way up, I can barely hear the music along with a lot of noise. It
is as if the sound level was turned down by 40 decibel or some such.

I verified this condition by using headphones.

Since I have two sound outputs, the build in sound on the Dell mobo,
and an old Creative Labs card, I also tried outputs of both  cards.

I am fairly sure that I have sound device connected to the active
card (mobo built in).

I then ran pulse audio volume control. The volume is set to 100%. If I
mute, the sound mutes. If I un-mute, the sound resumes but it is the
same old super quiet sound that is no good.

The sound level applet on the gnome-panel is set to 100% also.

I rebooted and it did not help.

The most annoying aspect of all this is that everything was working
great.

Somewhere in the guts of the most advanced sound architecture in the
world something is not working, and I have no idea why.

Another discovery. If I switch to OSS in System/Preferences/Sound, and         
run mplayer with "-ao oss" option, the sound works normally.

I would be cool with this, if only I could know how to swotch the                
Flash player to OSS in Firefox.

---

### Post by jethro10 on 2008-05-27
Double click the sound applet icon and you get a more expanded list of options.

Is PCM slid up far enough? it happens to me and my max volume seems so quiet until I do this.

J

---

### Post by chrisN_uk on 2008-07-31
Cheers, I just had the same problem, that fixed it fine!

---

