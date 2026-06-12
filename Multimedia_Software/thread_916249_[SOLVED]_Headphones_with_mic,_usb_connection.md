---
title: "[SOLVED] Headphones with mic, usb connection"
date: 2008-09-10
forum: Multimedia Software
---

### Post by Mariane on 2008-09-10
Hi, 

I have a set of headphones with a microphone which plug into a 
usb socket. They are supposed to be "driverless" so I bought 
them supposing they would work under ubuntu. They are driverless 
in the sense that they do not come with an install CD. 

They work under Windows Vista and XP, so "physically" they work. 

Ubuntu ignores them and goes on sending the sound from the laptop 
speakers. 

They are: MMX 1 "usb multimedia headset" by Beyerdynamic. 

What should I do, please? 

Mariane

---

### Post by fballem on 2008-09-10
> **Mariane said:**
> Hi, 

I have a set of headphones with a microphone which plug into a 
usb socket. They are supposed to be "driverless" so I bought 
them supposing they would work under ubuntu. They are driverless 
in the sense that they do not come with an install CD. 

They work under Windows Vista and XP, so "physically" they work. 

Ubuntu ignores them and goes on sending the sound from the laptop 
speakers. 

They are: MMX 1 "usb multimedia headset" by Beyerdynamic. 

What should I do, please? 

Mariane

The attached might be helpful: [http://ubuntuforums.org/showthread.php?t=910994](http://ubuntuforums.org/showthread.php?t=910994)

---

### Post by FlamingTeddiz on 2008-09-10
This happens with me too but only on a restart. I just unplug and replug in the external audio device.

---

### Post by Mariane on 2008-09-11
Thank you for the link fballem. 

I launched asoundconf-gtk by typing asoundconf-gtk in 
a terminal. The default is blanked out, no sound card 
is displayed. So I select one and close again ("quit"). 
If I re-launch it it appears blanked out again. 

It does not seem to be taken into account - or then 
maybe something was taken into account because I test 
it with "say hello" and the output sounds better than 
it did. But the sound still comes out of the laptop 
speakers. 

The solution "Well, use the small ones then" is not good, 
because only one of the small things actually functions 
and they have no mic. 

Unpluging and replugin does not work, either.

> aplay -l
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: U0xd8c0x0c [USB Device 0xd8c:0x0c], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

> asoundconf list
Names of available sound cards:
Intel
U0xd8c0x0c

When I plug a set of small headphones (the little things which go 
into your ears, I don't know what they are called in english) into 
the jack the sound comes out of the small headphones. It is only 
the usb connected-headphones which don't function. The small ones 
have no mic. 


Mariane

---

### Post by fballem on 2008-09-11
[COLOR="Navy"]Mariane: I have put some notes inside your quote [FB][/COLOR]

> **Mariane said:**
> Thank you for the link fballem. 

I launched asoundconf-gtk by typing asoundconf-gtk in 
a terminal. The default is blanked out, no sound card 
is displayed. So I select one and close again ("quit"). 
If I re-launch it it appears blanked out again. 

[COLOR="Navy"][FB] - that is how mine works as well. On mine, I have two choices - SB, which will go through the Speakers and Headset which will go through the USB Headphones. By the way, could you please tell me if there is a Default Sound Card option under System | Preferences. If there is, then that's how you can launch asoundconf-gtk.
[/COLOR]

It does not seem to be taken into account - or then 
maybe something was taken into account because I test 
it with "say hello" and the output sounds better than 
it did. But the sound still comes out of the laptop 
speakers.

[COLOR="Navy"]I use Exaile (for sound files) and VLC for Video. In each program, I need to make sure under Preferences that the ALSA is being used. Once this is done, then close the application, change the Default Sound Card (Sytem | Preferences | Default Sound Card) and change from speakers to Headphone. Then restart your application. The sound should come from the device that you selected.[/COLOR]

[COLOR="Navy"]Another question: Please right-click the speaker in the upper panel on the right side, the select Open Volumne Control from the menu. When the volume control is open, please select File | Change Device. This should give a list of the display devices (I have attached a screen shot of mine with this note. Is one of the ALSA Mixer devices selected? On mine, they are the first two devices in the list.[/COLOR]

The solution "Well, use the small ones then" is not good, 
because only one of the small things actually functions 
and they have no mic. 

Unpluging and replugin does not work, either.

> aplay -l
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: U0xd8c0x0c [USB Device 0xd8c:0x0c], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

> asoundconf list
Names of available sound cards:
Intel
U0xd8c0x0c

When I plug a set of small headphones (the little things which go 
into your ears, I don't know what they are called in english) into 
the jack the sound comes out of the small headphones. It is only 
the usb connected-headphones which don't function. The small ones 
have no mic. 


Mariane

[COLOR="Navy"]Hope this helps,[/COLOR]

---

### Post by Mariane on 2008-09-12
Thank you. I'll switch to the gnome interface and try to 
find this. 

Mariane

---

### Post by Mariane on 2008-09-12
Later: found it, but it doesn't work any better than any 
of the others... (If someone else is looking for it, right 
click on the little speaker icon top right). 

The others I tried were:
alsamixergui
alsamixer
gnome alsa mixer
cam
and moc which didn't work

Yesterday evening I watched a DVD using these headphones 
(windows vista) so I know they are not out of order... 

Just one thing strange on the Volume control: one of the 
speakers had a cursor which kept falling back down. (The 
left cursor). I could raise it but the moment the mouse 
let it go it fell straight down again. I tried several 
times (even once while holding down the control key on 
the off-chance this would help). 

Mariane

---

### Post by Mariane on 2008-09-12
I've just tried another one. 
I installed the xfce4 desktop (sudo apt-get install xfce4) 
and then switched to it (log out, use the little icon bottom 
left to change session, log back in). 

This one had alsamixergui, and it enabled me to raise the 
volume of the left speaker. Didn't make the left speaker 
produce any sound, though. Anyway I don't care if I have 
only one speaker working on this set of headphones, I would 
settle for only one, I'm starting to despair... :( 

Mariane

---

### Post by Mariane on 2008-09-15
GOT IT!!! 

I had to edit /etc/modprobe.d/alsa-base

The relevant driver used to be numbered -2 and I had already 
re-numbered it to 1. This was wrong. I renumbered it to 0 
(zero) and rebooted: 

It is towards the bottom of the file, a line: 
options snd-usb-audio index=0
instead of:
options snd-usb-audio index=-2

Thanks everyone for your help. 

After all the fiddling I've done, the sound is now much better 
under Ubuntu than under windoze, loud and clear! Hurray! 

Mariane

---

### Post by Joeb454 on 2008-09-15
Great :) You can mark your thread as solved from thread tools at the top of this page (as long as you started the thread :))

---

