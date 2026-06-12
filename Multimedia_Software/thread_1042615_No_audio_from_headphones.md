---
title: "No audio from headphones"
date: 2009-01-17
forum: Multimedia Software
---

### Post by MISIIM on 2009-01-17
I am having trouble getting headphones to work on my gateway laptop. (I had the same issue on Kubuntu.) I tried a lot of different solutions and in the end wrecked my Xubuntu installation (actually just the audio drivers, I tried using OSS instead of alsa). I reinstalled today and was hoping that someone knows the solution. I also tried recompiling alsa, but it had some compilation errors. Before you ask, yes I did check alsamixer and nothing is muted or at low volume. I know there was a list somewhere about posing the output of some commands, but I'm not sure what they are. ("aplay -l" ?)

Thanks.

---

### Post by John Jason Jordan on 2009-01-17
> **MISIIM said:**
> I am having trouble getting headphones to work on my gateway laptop. (I had the same issue on Kubuntu.) I tried a lot of different solutions and in the end wrecked my Xubuntu installation (actually just the audio drivers, I tried using OSS instead of alsa). I reinstalled today and was hoping that someone knows the solution. I also tried recompiling alsa, but it had some compilation errors. Before you ask, yes I did check alsamixer and nothing is muted or at low volume. I know there was a list somewhere about posing the output of some commands, but I'm not sure what they are. ("aplay -l" ?)

First, some more information would be helpful:

1) What make/model headphones? Are they wired, bluetooth, or what?

2) Do you get sound from the speakers?

3) What application(s) are you using to generate sound (Rhythmbox, etc.)?

There are probably other things, but that is all I can think of at the moment. Post back and we'll go from there.

---

### Post by MISIIM on 2009-01-18
> **John Jason Jordan said:**
> First, some more information would be helpful:

1) What make/model headphones? Are they wired, bluetooth, or what?

2) Do you get sound from the speakers?

3) What application(s) are you using to generate sound (Rhythmbox, etc.)?

There are probably other things, but that is all I can think of at the moment. Post back and we'll go from there.

1. They are wired using the standard headphone plug. Brand = Radioshack (They work in Vista (same computer) properly.) I also plugged speakers into the same spot and they didn't work.

2. Yes, I do get sound from the speakers.

3. I've tried VLC and XBMC.

---

### Post by John Jason Jordan on 2009-01-18
> **MISIIM said:**
> 1. They are wired using the standard headphone plug. Brand = Radioshack (They work in Vista (same computer) properly.) I also plugged speakers into the same spot and they didn't work.

2. Yes, I do get sound from the speakers.

3. I've tried VLC and XBMC.

What happens if you use an Ubuntu live CD? My point here is that if they work with the live CD then there is something messed up in your installation of Ubuntu. If they don't work with the live CD either, then there is some serious incompatibility problem. 

I'd also suggest reinstalling alsa. And once you have alsa running check the settings. You can get a GUI by right-clicking on the volume control icon in the Gnome panel, or you can get it in the terminal with "alsamixer." You might have to do "alsamixer -D hw:0" in order to see all the sliders and controls. 

One of the controls in the alsa settings is a checkbox for headphones. You problem could be something as silly as not having that box checked. 

I am far from an audio guru. It has always "just worked" for me. So if none of that works I hope someone smarter than me jumps in.

---

### Post by MISIIM on 2009-01-18
Thank you!

I tried the live CD but it didn't work. I tried alsa mixer with the aditional options, but nothing was muted. It worked after I reinstalled alsa (using sudo apt-get remove alsa redirected it to alsa-base) and rebooted and it worked.

:P

Edit: Isn't there is some way to mark this as solved? I can't find it.

---

### Post by HavocXphere on 2009-01-18
> **MISIIM said:**
> 
Edit: Isn't there is some way to mark this as solved? I can't find it.
afaik that functionality is still offline. something went wrong with the ubuntuforums server & they disabled all the "gimmicky" feature until everything is sorted out.

---

### Post by John Jason Jordan on 2009-01-18
> **MISIIM said:**
> Isn't there is some way to mark this as solved? I can't find it.

Yes, at the top of the page under Thread Tools you should see an option to mark the thread solved.

Just now I looked and the option is not there. I'm assuming that's because I'm not the one who started the thread. If it doesn't appear for you either, then the feature is broken.

---

### Post by MISIIM on 2009-01-18
:(

I forgot that when I reboot with headphones in it works. When I rebooted that was why it worked. Apparently it still doesn't work.

---

