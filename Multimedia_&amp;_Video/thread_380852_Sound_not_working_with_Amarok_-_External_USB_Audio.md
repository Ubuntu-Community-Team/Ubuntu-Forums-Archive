---
title: "Sound not working with Amarok - External USB Audio card"
date: 2007-03-10
forum: Multimedia &amp; Video
---

### Post by didobuntu on 2007-03-10
Hello,

I have no Sound under Amarok. The music seems to play but all is muted.

I don't understand where is the problem because there is sound when I use the Rythmbox music player.


I have an Asus W2Jc laptop with the following characteristics :

==================================================
cat /proc/asound/cards

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfebfc000 irq 66
 1 [SAA7134        ]: SAA7134 - SAA7134
                      saa7133[0] at 0xfeaff800 irq 169
 2 [Audio          ]: USB-Audio - USB Audio
                      USB Audio at usb-0000:00:1d.0-2, full speed
==================================================

Thank you for your help

P.S. I use an external usb audio sound card because because the hda-intel/Realtek alc882 integrated sound card don't work (a W2Jc laptop's specific problem).

---

### Post by ssavelan on 2007-03-10
Instead of having the HDA as the default, you should try to make the USB device the default, perhaps.

If you are lucky, that could be as easy as Preferences>>Sound

and use the drop down to select the USB device.

Keep me posted.  I have been setting up few friends with Ubuntu who have USB devices with good success.

sos

---

### Post by ssavelan on 2007-03-10
Well, I see you have a lot of beans there and the previous advice is probably worthless.

the following is the first set of instructions I started running a few months ago when working with two sound cards.  My guess is that you want your USB device to be 0 instead of 2.  Do you get sound out of the usb-audio upon boot up?

[https://help.ubuntu.com/community/EchoMia]("https://help.ubuntu.com/community/EchoMia")

---

### Post by didobuntu on 2007-03-10
Hello,

Thank you for the replay.

The external sound card is configured and is selected via the "preferences --> sound .."

I have sound using Rythmbox and Totem

The problem is with Amarok .. I cannot hear sound.

Any Idea?

Many thanks

---

### Post by ajm2005 on 2007-03-11
is the usb sound card recognised by the ALSA sound system and classified as one of ALSA's devices?

if so, then it shouldn't be too hard to get it to work in Amarok.

To see what sound devices alsa is recognizing, type this in a terminal window:

aplay -l

If you see the usb card listed, it will just be a matter of using the alsa output plugin within Amarok, and specifying the right alsa sound card.

---

### Post by didobuntu on 2007-03-12
Hello,

Thank you for your reply. Here what I get with the command aplay -l:

==================================================================
aplay -l

**** Liste des PLAYBACK périphériques ****
carte  0: Intel [HDA Intel], périphérique 0 : ALC882 Analog [ALC882 Analog]
  Sous-périphériques: 0/1
  Sous-périphérique: #0: subdevice #0
carte  0: Intel [HDA Intel], périphérique 1 : ALC882 Digital [ALC882 Digital]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
carte  1: Audio [USB Audio], périphérique 0 : USB Audio [USB Audio]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
==================================================================

So the usb Audio sound card is recognized. 

In the "Setting" --> "Configure Amarok" --> "Engine", I tried many configurations. From the Autodetect option to alsa selection I tried many speaker arrangements. The music is playing but I can hear no sound. 

The reason why I want to make Amarok is evident. There, the is beautiful sound together with the "lyric" option where I can follow the songs .. etc .. 

That seems very strange .. maybe I reinstall of Amarok can Help?

Many thanks for your help and suggestions.

---

### Post by didobuntu on 2007-03-12
Hello again,

I just solved the problem.

I had to comment the line related to the snd-usb-audio option in the /etc/modprobe.d/alsa-base file to get :

...
#options snd-usb-audio index=-2
...

Now the sound works under Amarok.

Many thanks for your Help.

---

### Post by kroustou on 2008-04-19
that was really  good thanx

---

