---
title: "Edirol UA-4FX with Jack and Ardour"
date: 2009-08-26
forum: Multimedia Software
---

### Post by power.dragon on 2009-08-26
I bought the sound card UA-4FX and in Internet I didn't find nothing of useful to record in Ardour with this device. So after some afternoon, I found a solution. 

First I read this [article]("http://alsa.opensrc.org/index.php/Edirol_UA-4FX") that is very interesting and useful to understand how it function under linux ( the most important thing is the hot and cold reboot) :)

After we can start.  

1) Download the most recent kernel rt and install it (now is the 2.6.28-3) and restart the pc with this kernel. After load the module snd_usb_audio

[INDENT]sudo modprobe snd_usb_audio[/INDENT]

(for load the module at the start give this command

[INDENT]sudo gedit /etc/modules[/INDENT]

and add this line at the end and after do a return

[INDENT]snd_usb_audio[/INDENT]

save and close so at the next start it's already load :)

)

2) Kill the process pulseaudio that don't permit to work at Jack :)

[INDENT]killall pulseaudio[/INDENT]


3) Discover the number of our device with:

[INDENT]$ cat /proc/asound/cards[/INDENT]


This is my output
[INDENT]
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf8400000 irq 22
 1 [UA4FX          ]: USB-Audio - UA-4FX
                      EDIROL UA-4FX at usb-0000:00:1d.0-2, full speed
[/INDENT]
So the number of the device is 1.

4) We start jack in the konsole

[INDENT]jackd --realtime -d alsa -C hw:1 -P hw:1 &[/INDENT]

-C insert the device hw:1 to the ua-4fx card or the hw:0 to HDA-Intel device. this device capture the data 

The same is for -P that it's for the playback


There is the possibility to record with Edirol and playback with the Intel

We can control all with qjackctl.

5) Now start ardour and :guitar:

I hope that this guide is useful for someone and I posted in the right place. :)

---

