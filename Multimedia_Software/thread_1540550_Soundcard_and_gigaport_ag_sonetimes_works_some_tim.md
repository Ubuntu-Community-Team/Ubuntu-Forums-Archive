---
title: "Soundcard and gigaport ag sonetimes works some times it goes to onboard card."
date: 2010-07-28
forum: Multimedia Software
---

### Post by phillytomcat on 2010-07-28
Hello, I am on a Hp pavillion dv6000 with an AMD64,3gig ram and Nvidia graphic card.
Currently I have an external usb soundcard with 8 outputs connected.
I am running xbuntu 904.
I have the gigaport configured in my mixer to alsa gigaport ag. The mixer recognizes it.
My problem is, sometimes xbuntu uses the gigaport card and it goes in nice stereo to my speakers.  Other times it uses the onboard Conextant sound card.
I can ususally use the giga usb card when I reboot. 
So, it is as if the computer can't make up it's mind. Any ideas. Currently the usb card works. I don't know how to keep it consistent though. It is hard to replicate what goes wrong with this , so it is hard to troubleshoot. Thanks for your help.:)

---

### Post by P4man on 2010-07-28
try installing pavucontrol and run it from apps > sound and video > pulseaudio volume control.

its lets you define default sound cards for different (running!) apps, exclude cards, set fallback etc.

Another less elegant solution could be to just disable the onboard audio in your bios if you dont use it.

---

