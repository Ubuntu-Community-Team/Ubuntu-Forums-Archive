---
title: "envy24 / Teratec6fire - no sound in 9.10"
date: 2009-10-30
forum: Multimedia Software
---

### Post by its_jon on 2009-10-30
I have a Teratec6fire soundcard .... envy24 chipset.

This is the 3rd release of Ubuntu where my sound has not worked.
To fix sound in the past I have followed the instructions below in the link

[http://idyllictux.wordpress.com/2008/10/29/alsa-instead-of-pulseaudio-for-ubuntu-810-intrepid-a-non-destructive-way/](http://idyllictux.wordpress.com/2008/10/29/alsa-instead-of-pulseaudio-for-ubuntu-810-intrepid-a-non-destructive-way/)

Should I try this again for 9.10 ?

Or is there a better way to get my sound working ?

Thanks
John
Scotland.

---

### Post by Paulo Wageck on 2009-10-30
perhaps we are on the same boat: [http://ubuntuforums.org/showthread.php?p=8194905#post8194905](http://ubuntuforums.org/showthread.php?p=8194905#post8194905)

---

### Post by its_jon on 2009-10-30
I followed the instructions here 
[http://idyllictux.wordpress.com/2008/10/29/alsa-instead-of-pulseaudio-for-ubuntu-810-intrepid-a-non-destructive-way/](http://idyllictux.wordpress.com/2008/10/29/alsa-instead-of-pulseaudio-for-ubuntu-810-intrepid-a-non-destructive-way/)
that always got my card working after other distro upgraded.

It was a last resort have tried everything else (that I could understand) that I have read about.

Im open to any suggestions.

I use Ardour/audacity a lot, and was just about to master a Xmas CD for a local primary school.... :(

Im feeling a but winded at the moment...

help :redface:[-o<[-o<

---

### Post by its_jon on 2009-11-02
Its been some days now.
I have kindly been pointed towards lots of help, 

This is where I am at:-

I think I have disabled Pulse Audio
Im not sure I have correctly enabled Alsa mixer
I have downloaded alsa driver source and enabled ice1712(envy24)
My soundcard appears to be correctly identified (I think it always was)
each time I read something which is supposed to help I try it (further links in the chain - could be making things worse?)

Is there any info I can post that could help someone help me ?

I have followed the common sound card help threads with no success.

---

### Post by its_jon on 2009-11-02
I realized that I could try my motherboards sound..... yay ! it worked....

However as I use the good sound card for accurate monitoring I have dropped a ton of quality by using it....

HOWEVER ](*,)

After a reboot I have lost sound again ... and whenever I go to pref/sound I get the message:-

"Waiting for sound system to respond"

And volume control's are hashed out.

This is turning into a nightmare

---

### Post by its_jon on 2009-11-02
Tracked down the "Waiting for sound system to respond" error

It was the /etc/pulse/default.pa file..... I had read somewhere that pasting some compatibility code for M-audio cards (same chipset) at the end of the file made a lot of envy24 soundcards work.
When I rebooted the change must have took effect unknowing to me.... but it was the wrong result !!

After I removed the code I instantly got sound back...

I would like to keep experimenting (in the dark) in the hope my 24/96khz soundcard starts to work, but I am even more afraid now after nearly loosing my backup mobo soundchip functionality !

---

### Post by evozero on 2010-01-15
Hi All,
I have just done a fresh install of UbuntuStudio 9.10, and have lost sound output from my envy24/ Maudio 2496 card?
I will work with ardour / jack but not with any system sounds or wav files, mp3, web, cd etc.
The outputs are not muted and the card is recognised, very odd.
Any ideas?
Thanks
Ian

---

