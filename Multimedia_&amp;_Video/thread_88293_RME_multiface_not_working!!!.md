---
title: "RME multiface not working!!!"
date: 2005-11-09
forum: Multimedia &amp; Video
---

### Post by mathieujohnson on 2005-11-09
Hi,
I just bought an RME multiface to do studio stuff on linux and i pluged it in, got the pci in and all, everything is plugged ok but nothing works.
I tried doing a fresh install, but got nothing.
Its actually the rebranded version of the multiface made by steinberg, though it says RME on the back, so its obviously the same thing.
anyone has any help to give?
the host error led is on at all times
I'm on kubuntu breezy

---

### Post by 23meg on 2005-11-09
I heard RME publish Linux drivers for most of their cards, they must be on their site, not sure about yours though. If you didn't install the drivers, try doing so.

---

### Post by mathieujohnson on 2005-11-09
maby I missed it but all they say on RME's website about linux is to go download the alsa drivers and the oss drivers wich AFAIK are already in the breezy kernel.
I am positive that the soundcard I have is the same as the multiface wich is definitly supported by alsa, but I seem to have nothing working.
I will check again, it would be nice if some one had the same card ie a multiface or digiface and could let me know how their install went
thanx

---

### Post by mathieujohnson on 2005-11-10
well after 3 hours reading every info about rme and alsa and linux, I just don't get anything.
Seems like alsa is included in (k)ubuntu my card is detected as I get the name in jack hdsp hammerfall hw-0 but nothing works.
I tried compiling everything from the alsa website, main problem seems that there is no /dev/dsp and well I don't know how to make a device.
There is very little info about this card and linux.
seems like everyone that uses it has no problems at all.
or if they do, its about configuration for better result rather than any result at all.
If any one has any info at all.
Please help, This is a real pain.
thanx

---

### Post by mathieujohnson on 2005-11-10
All right, 
got alsa playback working, but can't get jack to work.
I had to compile all of alsa drivers libraries utils and all to make the card work.
really happy its working but can't really get any audio app to work.
Is there a way to get alsa devices to work with art, xine, gstreamer or oss?

---

### Post by 23meg on 2005-11-10
To get JACK working you may need to have a patched kernel that allows realtime operation. How exactly does it fail? Forgive my ignorance but the Multiface is a firewire card, isn't it? As far as I know firewire interfaces don't work very well with linux audio apps as of today..

---

### Post by mathieujohnson on 2005-11-10
no actually its a pci card with a breakout box
I got jack to work at 44.1khz wich is as of yet what I need, trying to go 96khz was the main problem but of what I read on a couple of websites this is easy to fix.
I pretty much have a working card.
except a couple of bugs, will try to do the kernel patching to fix things
thanx a bunch

---

### Post by 23meg on 2005-11-10
Happy that you got it working with little effort, that encourages me to keep trying: I have yet to get my M-Audio Quattro working with JACK at all, even with a patched kernel..

---

### Post by corrosive23 on 2005-11-13
[quote=23meg]Happy that you got it working with little effort, that encourages me to keep trying: I have yet to get my M-Audio Quattro working with JACK at all, even with a patched kernel..[/quote]


[http://www.opensound.com](http://www.opensound.com)


They provide drivers for M-Audio devices.

---

### Post by tmckellar on 2005-11-16
[http://wiki.linuxquestions.org/index.php?title=M-Audio_Quattro&redirect=no](http://wiki.linuxquestions.org/index.php?title=M-Audio_Quattro&redirect=no)

That's where I looked at to get my Quattro working. Even got it working at 48 kHz. You'll probably have to play around with the jackd script to get it to work especially if you have two sound devices. Qjackctl is pretty much useless as far as the Quattro goes you'll jackd will pretty much be the only way it'll work.

---

### Post by 23meg on 2005-11-16
[QUOTE=tmckellar][http://wiki.linuxquestions.org/index.php?title=M-Audio_Quattro&redirect=no](http://wiki.linuxquestions.org/index.php?title=M-Audio_Quattro&redirect=no)

That's where I looked at to get my Quattro working. Even got it working at 48 kHz. You'll probably have to play around with the jackd script to get it to work especially if you have two sound devices. Qjackctl is pretty much useless as far as the Quattro goes you'll jackd will pretty much be the only way it'll work.[/QUOTE]
Did you get it working with a standard Ubuntu kernel or a patched one? Does it work in realtime mode? What latency do you typically get?

---

