---
title: "Only two speakers out of 4 work on Ubuntu 14.04 Acer Laptop"
date: 2016-01-10
forum: Multimedia Software
---

### Post by Hyrr_Climaxx on 2016-01-10
Hello everyone.

I recently bought an Acer Aspire V 17 Nitro and have some hard time configuring it to work.
I managed to get the wireless driver to work using backports and also the nVidia video card and the touchpad - these didn't work out of the box, but I can't figure how to make the audio to be surround.

I've searched on multiple forums, but couldn't find any updated information.

My info is : [http://www.alsa-project.org/db/?f=48c6a861c798c665597bb45d4b8c0b7e1c34001a](http://www.alsa-project.org/db/?f=48c6a861c798c665597bb45d4b8c0b7e1c34001a)

Can anyone help with an idea ?

Thanks anyway and have a great new week! 
Stefan

---

### Post by Bucky Ball on 2016-01-10
It would help if you told us what speaker system you are attempting to use and how you have it plugged in to the computer.

What have you done already, where are you at now with it, links to anything you've tried. Please provide all relevant info you can think of.

Unsure fiddling with ALSA is the cure. Have you looked in 'Configuration' tab in Pulseaudio Volume Control and made sure you are using the right device there and in 'Playback' and 'Output'?

---

### Post by Hyrr_Climaxx on 2016-01-12
Hi, thanks for the response.

I'm actually only trying to get all of the built-in speakers to work. 

I haven't had problems with the audio in a while and I am a little outdated as to what has happened in the last few years since the last laptop had some alsa problems.
I would say I want a standard thing - pulse audio, I guess - no other output device (changing from speakers to headphones or some other music device works)

From what I saw, Ubuntu doesn't detect more than 2 speakers (only a stereo output in the pulse audio settings).
I have tried using pavucontrol and there there are multiple outputs, but it seems that all of them are unplugged - and they don't seem to be what I have anyway - they are 5.1 HDMI and I seem to have 4.0 (only 4 speakers, no sub-woofer).

I've looked at a surroundsound guide on Ubuntu ( [https://help.ubuntu.com/community/SurroundSound](https://help.ubuntu.com/community/SurroundSound) ) and also tried bits and pieces of a long sound troubleshooting guide on the same site.

Then I tried using aplay and speaker-test to see if it detects the hardware controls - and only two were targeted and responding. 

I saw that there is an optional modprobe string that could be added to alsa-base.conf - this was actually my previous laptop's fix that couldn't switch from speakers to headphones - but what snd-hda-intel model strings I've tried don't do anything.

I didn't actually make note of all of the things I've tried, this is a short and probably imprecise recall - I've tried most of the things I could find that seemed similar to what I encountered - a rough estimate would be that I had about 4-5hours of trying and followed about 10 articles, but some where outdated, others didn't work - probably because of different manufacturer - and others where in the 'no sound' category.

I don't know how to actually debug the card more than I did and see if it's the kernel's module or something else. It's more like a blindfolded process: I've tried what I knew and searched for other similar problems, but nothing worked.

Don't know if this helps with what you asked, but I am willing to dig deeper if pointed in the right direction.

Thanks!

 :)

---

### Post by Hyrr_Climaxx on 2016-01-23
Does anybody have any ideas here?

Thanks

---

