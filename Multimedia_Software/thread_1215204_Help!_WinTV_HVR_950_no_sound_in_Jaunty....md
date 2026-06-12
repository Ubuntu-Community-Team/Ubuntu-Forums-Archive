---
title: "Help! WinTV HVR 950 no sound in Jaunty..."
date: 2009-07-16
forum: Multimedia Software
---

### Post by gm_w on 2009-07-16
I followed these steps to setup my HVR 950 usb tv tuner on Ubuntu 9.04 Jaunty:


wget [http://www.steventoth.net/linux/xc5000/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip](http://www.steventoth.net/linux/xc5000/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip)
unzip -j HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip Driver85/hcw85bda.sys

sudo apt-get install linux-headers-generic

cp /usr/src/linux-headers-`uname -r`/Documentation/video4linux/extract_xc3028.pl ~/HVR950
chmod +x extract_xc3028.pl
./extract_xc3028.pl

sudo cp xc3028-v27.fw /lib/firmware

Tvtime is able to recognize the device and is producing great video. But the problem is no audio at all. I used to have the same device working in Ubuntu 7.10 Gutsy and the command I used to get audio working then was:

/usr/bin/sox -r 48000 -w -c 2 -t ossdsp /dev/dsp1 -t ossdsp /dev/dsp  &

I believe SOX's version has upgraded and some of the options no longer work as before. After reading through SOX documentation, I modified the command above to:

/usr/bin/sox -r 48000 -b 16 -c 2 -t ossdsp /dev/dsp1 -t ossdsp /dev/dsp  &

Now the problem is sox can't find ossdsp: no handler for given file type `ossdsp'

I am no expert in this matter and I don't really know how to use SOX and why ossdsp was used in the previously working command. Can anyone help me out here?

I have Dell Vostro 1500 laptop. I did not do any manual installation of the audio driver -- regular audio seems to be working properly.

Thanks

---

### Post by gm_w on 2009-07-17
ok I believe solved this. Now I can view and listen using TVtime with WinTV HVR 950 In Jaunty. Just for the record, besides what I did above, I did:

install sox (using synaptic package manager)
libsox-fmt-oss
libsox-fmt-alsa
libsox-fmt-base
libsox1

Then I start TV time, and using following sox line to get audio:

/usr/bin/sox -r 48000 -b 16 -c 2 -t ossdsp /dev/dsp1 -t ossdsp /dev/dsp  &


The last point I need to solve is, I have to run above sox command as root.. if I run as an user, I'll get permission denied when access /dev/dsp1

Anyone can help me out on this last bit? I'll figure it out soon or later

---

### Post by igorzwx on 2009-07-17
sox can work with alsa too

---

### Post by gm_w on 2009-07-18
yes sox can work with alsa, but alsa does not work with HVR 950


and I just need to add user id to audio user group to run sox command as non-root

---

### Post by igorzwx on 2009-07-18
have you tried it with OSS4?

---

### Post by Nullexe on 2009-08-29
Thanks for this, I got my HVR950 working in Jaunty.  The OSS command is great but the audio is a second off, how do you get it in sync?

---

### Post by arkros on 2009-10-24
The sound command produces only clockwork static ticks for me on ubuntu 8.10.

I've tried messing with the sox options, but nothing seems to work. The only thing I haven't tried is something other than ossdsp.

Edit:

It seems /dev/dsp2 is the right device for me. It's still distorted, but I'm getting closer. I will post my setting when it's working.

Edit 2:
Ok, > /usr/bin/sox -r 48000 -w -c 2 -t ossdsp /dev/dsp2 -t ossdsp /dev/dsp & works for me. I also had to change permissions on /dev/dsp2 or run as root.

Edit 3:

I've tried piping tvtime and sox together to get rid of the sound sync issues, but the sound cuts out after 1/2 second when I do this. Ex:
> tvtime | /usr/bin/sox -r 48000 -w -c 2 -t ossdsp /dev/dsp2 -t ossdsp /dev/dsp &
The sound stops after 1/2 second. Any ideas?

Edit 4:

Ok, sound is in sync if I launch tvtime first, and then 1/2 second later (not immediately) run sox. I don't have this automated yet. Does anyone know how to give a delay between command execution? Piping is too fast so that's why it fails.

---

