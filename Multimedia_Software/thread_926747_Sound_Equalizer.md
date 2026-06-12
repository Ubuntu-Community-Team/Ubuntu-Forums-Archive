---
title: "Sound Equalizer?"
date: 2008-09-22
forum: Multimedia Software
---

### Post by Nettoyer on 2008-09-22
Recently, I got my SB X-FI XtremeGamer soundcard to work. I decided to watch a movie on my desktop and noticed that when they talked, it was quieter than usual. I set VLCs sound to 1024 (it caps out at 200%). When they are talking, I turn my sound up, and when something happens, (gunshot, car exploding, etc..) I have to turn my sound back down.  

If I go to the Sound applet, it doesn't show me as having a sound card. I'm using OSS if that helps?  I tried to use the VLC sound options to compensate this issue, but that's just a bandaid.

Thanks,

Nett

---

### Post by aeiah on 2008-09-22
an equaliser probably wont be best suited. if it isnt a surround sound issue then its a compression issue. you need something that'll compress the sound, reducing the loud bits and increasing the quiet bits.

is there any reason why you're using oss instead of pulse or alsa? have you tried messing with ossmix (its a command line mixer for oss) or ossxmix (a gui mixer for oss)

see [http://manuals.opensound.com/usersguide/](http://manuals.opensound.com/usersguide/)

---

### Post by Nettoyer on 2008-09-22
It's the first walkthrough that would let my speakers work.
I've just had to jump through a few hoops to get both my soundcard and my video card to work. I read that OSS is old/outdated and that ALSA is the better half. Me? I just wanted them to work :)


I had played with ossxmix before and I'll give it a shot now that the card is working.

---

### Post by mailtwogopal on 2008-09-22
Hi,

  Alsamixer readily works. I had similiar problem and after using alsa it was fine. Try it.

---

### Post by markbuntu on 2008-09-22
VLC has an equalizer, have you tried that?

Also, if VLC thinks it is using surround sound it may route the front and center audio to the wrong place making the voices, which usually are in front and center speakers, sound muted while effects like gunshots are louder because they are usually routed through all the speakers. You may have the speakers confused, or OSS has confused them for you.

---

### Post by Nettoyer on 2008-09-22
When I get home I am going to fiddle with the ossxmix to see where it is.  The first thing that was peculiar was when it did the sound test in the Terminal, it had my left/right switched.  I thought it was odd, but ok & I switched them around.

I changed the EQ in VLC (it's usually at disabled) and changed it to different things, which worked, however, it wasn't the solid fix I want.

---

### Post by lwnexgen2 on 2008-09-22
> **markbuntu said:**
> VLC has an equalizer, have you tried that?

Also, if VLC thinks it is using surround sound it may route the front and center audio to the wrong place making the voices, which usually are in front and center speakers, sound muted while effects like gunshots are louder because they are usually routed through all the speakers. You may have the speakers confused, or OSS has confused them for you.

This is probably the issue. Look through the FFMPEG/VLC audio configuration and set it to downmux the audio to 2/0 channels.

---

### Post by Nettoyer on 2008-09-23
I modded the kernel and switched over to Alsa, thanks for all the help guys!

---

