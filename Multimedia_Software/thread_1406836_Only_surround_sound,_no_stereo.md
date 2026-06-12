---
title: "Only surround sound, no stereo"
date: 2010-02-14
forum: Multimedia Software
---

### Post by Eril on 2010-02-14
Hello,

I am using Ubuntu 9.10 and I'm new to Linux. I've got a few questions. I have 5.1 surround speakers and when I go to the hardware tab in sound preferences and select Analog Stereo Duplex (which I assume is stereo sound) sound comes from all of the speakers, instead of only the 2 front speakers.

Now I've got a workaround for this, by going to terminal and going to alsamixer and then sliding down the "surround" bar. But whenever I increase or decrease the volume by clicking on the speaker icon on the top bar, alsamixer resets itself. I've tried saving it by using the "alsactl store" command in terminal, but I'm not sure if I've done that right (I exit alsamixer by pressing esc and then use the alsactl store command).
So, I'd like to know how to save alsamixer settings (correctly?) and how to get stereo sound when I select a stereo profile in the sound preferences window. Any help is appreciated.

Thanks in advance,
Eril

---

### Post by b9k9kiwi on 2010-02-14
Surround Sound 5.1 - also known as 3-2 Stereo.

Why would you prefer stereo from only two speakers instead of from 5.1?

---

### Post by Eril on 2010-02-14
> **b9k9kiwi said:**
> Surround Sound 5.1 - also known as 3-2 Stereo.

Why would you prefer stereo from only two speakers instead of from 5.1?

Well, I have not set up my rear speakers all the time and set them up only when I need them (it's inconvenient for me to have them set up all the time as I'm sitting in an open room but they stay connected, I just put them under my desk). As it is now, sound comes from all of the speakers in Ubuntu and the only way as far as I know to mute the rear and center speakers  is to mute "surround" in alsamixer. But alsamixer won't save settings. Well, at least until I touch the volume button.

Thanks for your reply.

---

### Post by b9k9kiwi on 2010-02-15
I don't know what you mean by "Well, at least until I touch the volume button", but anyway;

alsactl store

is the terminal command to save alsamixer current settings.

---

### Post by Eril on 2010-02-15
> **b9k9kiwi said:**
> I don't know what you mean by "Well, at least until I touch the volume button", but anyway;

alsactl store

is the terminal command to save alsamixer current settings.

If I change any settings in Alsamixer, and then exit by pressing esc and then use the volume button (the speaker icon) on the top bar in Ubuntu to turn up the volume or something all settings in Alsamixer are reset. I've tried the "alsactl store" command many times now. But it resets right away when I turn the volume up or down.

---

