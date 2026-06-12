---
title: "Logitech ClearChat Headset acts like Keyboard"
date: 2010-07-14
forum: Multimedia Software
---

### Post by CaptainDoomsday on 2010-07-14
Hi, I would appreciate some help.

Basicly i am trying to get my Headset to play audio within Ubuntu 8.04. I do not want to upgrade distro as the laptop acts very buggy with lucid.

I have trough testing found out that:

cat /bin/bash > /dev/dsp :-will play that annoying static through the headphones.

the usb volume control effects the on board volume, probably because the input is not distinguished from my keyboard volume controls.

I have set the headset to be the default device and no luck.

Everytime i try and test the sound i get:
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open audio device for playback.

Which seems to point to the card being in use however nothing is using it for sound, so the only thing i can think of is that the usb keyboard effect is locking the usb device.

Thus id like to remove the usb keyboard effect from the headset. 

T:  Bus=02 Lev=01 Prnt=01 Port=01 Cnt=02 Dev#=  5 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=046d ProdID=0a02 Rev=10.13
S:  Manufacturer=Logitech
S:  Product=Logitech USB Headset
C:* #Ifs= 4 Cfg#= 1 Atr=80 MxPwr=100mA
I:* If#= 0 Alt= 0 #EPs= 0 Cls=01(audio) Sub=01 Prot=00 Driver=snd-usb-audio
I:  If#= 1 Alt= 0 #EPs= 0 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
I:* If#= 1 Alt= 1 #EPs= 1 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
E:  Ad=01(O) Atr=09(Isoc) MxPS= 192 Ivl=1ms
I:  If#= 1 Alt= 2 #EPs= 1 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
E:  Ad=01(O) Atr=09(Isoc) MxPS=  96 Ivl=1ms
I:  If#= 2 Alt= 0 #EPs= 0 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
I:* If#= 2 Alt= 1 #EPs= 1 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
E:  Ad=84(I) Atr=09(Isoc) MxPS=  96 Ivl=1ms
I:* If#= 3 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid
E:  Ad=83(I) Atr=03(Int.) MxPS=   2 Ivl=8ms

So i would like to know if there is a way to remove/disable/kill the last input line from a usb device namely (i really couldn't give a monkeys about the lack of volume control):

I:* If#= 3 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid
 Without losing the audio input of course. 

Thank you.

---

