---
title: "Sound Problems on Asus X50N AMD64"
date: 2007-11-07
forum: Multimedia &amp; Video
---

### Post by xgene on 2007-11-07
I have a really big problem...my sound won´t start....everything is installed, unmuted, set ...etc but sound isn´t  starting? I allready tryed everithing what´s on the Forum but somehow it doesn´t work. I have NVIDIA MCP67 hd card...

any smart Ideas?

---

### Post by richardhundt on 2007-12-09
*bump*

lspci says:

00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)

aplay -l says:

card 0: NVidia [HDA NVidia], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

So it looks like an snd-hda-intel (confirmed by NVidia's web site). I've tried the following module options:

options snd-hda-intel model=auto
options snd-hda-intel model=3stack
options snd-hda-intel model=asus
options snd-hda-intel model=asus-laptop

Tried newest alsa from source (v1.0.15)

I've had similar problems with a Realtek card with the same driver in an Acer laptop and had to get the drivers from their website, so I dunno if the manufacturers have the freedom to tweak the hardware to the point where it doesn't function with the snd-hda-intel driver, or if I'm doing something wrong.

If somebody at least has any tips for how to debug this animal, then perhaps I can figure something out with the Alsa crowd.

Cheers!

---

### Post by richardhundt on 2007-12-09
Okay, I've managed this with the following option in /etc/modprobe.d/alsa-base

options snd-hda-intel model=lenovo

I know it's not a Lenovo - but for some reason forcing this model works. Haven't tried plugging in headphones yet to see if that's automagic, but at least I've got sound!

If you're wondering how on Earth I figured that options line out (in the interests of teaching a man how to fish and all that), if you take a look at a file called ALSA-Configuration.txt, I've got 2 lying around on my machine:

/usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz
/usr/src/modules/alsa-driver/alsa-kernel/Documentation/ALSA-Configuration.txt

(use zless to view the gzipped one or just unzip it) - scroll down to snd-hda-intel section, there's a subsection with:

   ALC861VD/660VD (that's our card)

I basically went through each of the models listed there (3stack, 3stack-dig, ...) until I hit the lenovo and voila!

Try it and lemme know if it doesn't work for you.

P.S you'll need to reboot in between, but y'already know that :)

---

### Post by nikito on 2007-12-25
I have a Asus Z53S and lenovo worked for me too. Finally I have sound on my notebook. Thx!

---

### Post by BasKloet on 2008-03-10
Thanks, I never would have found that one out for myself! :D

---

### Post by ex17 on 2008-03-10
Yeah my Z53S sound is now working with that code line! Plus the earphones work 100% no problems!
Thanks a lot!

---

### Post by ex17 on 2008-05-04
eh I don't know if you have upgraded to Hardy Heron yet, but, using the Lenovo hack, I can barely hear anything :-k. It's like the maximum sound I can get is 1/3 of the sound I could hear before the upgrade.
Anybody got the same problem?

---

### Post by Tintazul on 2008-05-08
> **richardhundt said:**
> Okay, I've managed this with the following option in /etc/modprobe.d/alsa-base

options snd-hda-intel model=lenovo

I know it's not a Lenovo - but for some reason forcing this model works. Haven't tried plugging in headphones yet to see if that's automagic, but at least I've got sound!

If you're wondering how on Earth I figured that options line out (in the interests of teaching a man how to fish and all that), if you take a look at a file called ALSA-Configuration.txt, I've got 2 lying around on my machine:

/usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz
/usr/src/modules/alsa-driver/alsa-kernel/Documentation/ALSA-Configuration.txt

(use zless to view the gzipped one or just unzip it) - scroll down to snd-hda-intel section, there's a subsection with:

   ALC861VD/660VD (that's our card)

I basically went through each of the models listed there (3stack, 3stack-dig, ...) until I hit the lenovo and voila!

Try it and lemme know if it doesn't work for you.

P.S you'll need to reboot in between, but y'already know that :)
zomg richardhundt u rokkkkccckck so much !!!!1!!!1!!!

Now seriously: I'm another satisfied Z53S customer! Have had the laptop since December, and I had tried editing the file, even applying what are sensible options like asus-laptop :) nothing worked. Since I need to actually *work* on it I kind of gave up having sound... until about an hour ago when I found your post. Who would have thought? lenovo. 

The sound board is an HDA Intel, but hey -- whatever floats the ALSA boat! It it works with lenovo, then it's a lenovo! :D

---

