---
title: "Issues with headphones and front panel jack detection - total newb"
date: 2011-04-02
forum: Multimedia Software
---

### Post by Jojia on 2011-04-02
Hey all

I'm totally new to ubuntu and i'm using 10.10.

The issues i have have to do with the front panel audio jacks and headphones.

Basically when i plug in my headphone and mic there i get sound out to the headphones but my speakers still play, also when trying to use skype my mic doesn't seem to be working. 

I've been looking around for help but there are loads and loads of different posts and being new i got kinda confused. I've tried to find some settings in the sound preferences but nothing there makes any difference and the terminal command alsamixer doesn't seem to help either, 

What i want is for ubuntu to detect that i have headphones in the jack and disable the speakers untill i remove the headphones again and for the mic connected to my headphones to work.

noticed that usually you want a alsa-info something something posted so here is the link for that
[http://www.alsa-project.org/db/?f=ec46d62ecf1569834f509a4dff1ea4c58115a562](http://www.alsa-project.org/db/?f=ec46d62ecf1569834f509a4dff1ea4c58115a562)

What shall i do oh Ubuntu Gurus?

---

### Post by Jojia on 2011-04-02
Saw some other stuff you might wanna know so posting it here to. 

uname -a
Linux ubuntu 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:39:03 UTC 2011 x86_64 GNU/Linux

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.

head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC889A

==> /proc/asound/card1/codec#0 <==
Codec: ATI R6xx HDMI

Dunno what else to provide, really want to be able to use ubuntu so i would appreciate some help. Also when i plug in my headphone in the volume control box that came with my 5.1 surround system the speakers shut up. But i want to be able to use my front panel jacks and i still can't get my mic to work.

---

### Post by Jojia on 2011-04-02
Well i've got the mic working atleast but i have to turn of my speakers if i dont want to get sound from them. so if anyone know how to fix that problem i'm all ears.

---

### Post by Jojia on 2011-04-03
I'm really hoping for some help here!

My mic was working fine with skype yesterday but when i got back home today that is no longer the case. It works when i try the recording program in ubuntu so i know the mic is working but it's not working in skype. 

I'm happy to provide any information that is needed to solve this thing so could someone please give me some pointers?

---

### Post by Jojia on 2011-04-03
okay this is driving me nuts. I've tried everything i can think of, I've played around in Alsamixer and downloaded and installed pulseaudio volume controller, I've tried to mute one channel and that does nothing except making it so i can only hear in one headphone speaker when i blow into the mike. I've called that stupid echo service a billion times without results and i've yet to get a single reply from this forum.... Someone has to know something about all this!

---

### Post by Jojia on 2011-04-03
Oookay this is getting weird now. If i play music or record something and then play it the other person i'm calling on skype can hear it. I don't even have to have my mic in the jack and yet skype is sending what i hear to him. Something must have gotten mixed up somewhere but i have no idea where that could be.

aight i've uninstalled ubuntu, i'll give it a fresh start and see if things work better with a dedicated partition instead of using the windows installer.... later

---

### Post by ankarajasekar on 2011-05-07
> **Jojia said:**
> okay this is driving me nuts. I've tried everything i can think of, I've played around in Alsamixer and downloaded and installed pulseaudio volume controller, I've tried to mute one channel and that does nothing except making it so i can only hear in one headphone speaker when i blow into the mike. I've called that stupid echo service a billion times without results and i've yet to get a single reply from this forum.... Someone has to know something about all this!

my headphones  mike is not working 
the same problem i am getting  in  11.04  so can u helpome to fix  the same

---

