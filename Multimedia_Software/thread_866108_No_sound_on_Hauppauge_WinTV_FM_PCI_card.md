---
title: "No sound on Hauppauge WinTV FM PCI card"
date: 2008-07-21
forum: Multimedia Software
---

### Post by bsh on 2008-07-21
hello,

the main reason i still use windows is that i have no television, and i watch tv on my pc, and i just can't get my tuner card to work in ubuntu.
i have been googling for this for several days, only to find similar topics with no solution.
i have already tried a lot of things, to no avail.

so this forum is my last hope!

so i have this hauppauge wintv pic fm card, with cz881 chip. it's line out is connected to the line in of a sound blaster audigy card. the line out from this goes further to a turtle beach santa cruz, which is my main sound card. it then goes further to my hi-fi. i also have a motherboard audio chip, but i have turned it off to make things easier. i also have a usb sound card for monitoring purposes.
so you can imagine my audio/mixer setup in ubuntu looks somewhat crowded :)
i have gone through all the possible mixer settings and all channels volumes are turned to full, no muting, etc.
i also tried using pulse audio, alsa and even oss.
when i play audio on the turtle beach, it's fine.
when i play sound on the creative, it's also fine.
the usb sound card also works.

yet, there is no sound in tvtime. (neither in xawtv)

the tuner card is properly recognized by the kernel, the modules are installed and working.

however, there's no audio in tvtime. it's not muted. when i try to change the volume with the left/right keys, it always display "volume 0", and doesn't change it.

so i have no idea.
it's either the cx audio module not working, or it's set to use a non-existant mixer, or even tvtime tries to use a mixer for the card, that is not existing. (it is set to /dev/mixer:line in the config file)
all /dev's exist.

i have no idea.

please help to get sound from my card!

i am on ubuntu 8.04-amd64, using gnome.

---

### Post by sky pilot on 2008-11-15
I know this is an old thread but I am having a similar problem with my ATI AIW card and would love a solution,

Well dummy me, all I had to do was go to the sound volume interface and unmute line in.  Wow, completely hooked up my ATI AIW.

---

### Post by bshamel on 2011-12-03
This worked for me.  Install the GNOME ALSA Mixer Application.  I used the ubuntu software center.  After the application is installed I opened it and extended the window until I could see the LINE heading.  I unchecked the mute box and moved the slide to obtain the proper volume.  Not very techie, but as I said, it worked for me.

---

