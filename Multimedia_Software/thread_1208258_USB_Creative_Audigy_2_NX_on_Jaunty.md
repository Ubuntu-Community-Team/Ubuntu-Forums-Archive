---
title: "USB Creative Audigy 2 NX on Jaunty"
date: 2009-07-09
forum: Multimedia Software
---

### Post by jerez76 on 2009-07-09
Although the card is promptly added and it is on the Volume Control list, you still need to add this card since supports 48kHz while linux supports 44100Hz

$  gedit ~/.asoundrc
add 
pcm.usb {
	type hw;
	device 0;
	card 0;
}

pcm_slave.sl {
	pcm usb
	rate 48000
}

pcm.!default {
	type plug
	slave sl
}

if your you other sound card is available then change it to card 1

easy way to check is to do

$ alsamixer -c 1

ref.
[http://www.eng.uwaterloo.ca/~dtay/linuxLaptop.shtml#sound2](http://www.eng.uwaterloo.ca/~dtay/linuxLaptop.shtml#sound2)

---

