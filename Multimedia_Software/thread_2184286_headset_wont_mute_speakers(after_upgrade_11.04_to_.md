---
title: "headset wont mute speakers(after upgrade 11.04 to 12.04LTS)"
date: 2013-10-28
forum: Multimedia Software
---

### Post by OS Instructor on 2013-10-28
in 11.04, when the headset was plugged in the speakers "auto-muted" when unplugged the sound would switch back to the laptop speakers. worked fine!

i upgraded to 12.04LTS now both headset jack and speakers play at the same time...  ..no "auto-mute" :( 

i have tried reloading alsa uninstall and reinstall ... 

i have read through every thread i can find concerning the subject..

---

### Post by ajgreeny on 2013-10-28
I thought this was a often hardware switch which worked when you plugged in headphones.

Have you tried wiggling the plug in and out a bit to see if the switch has become a bit sticky?

---

### Post by Yellow Pasque on 2013-10-28
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by OS Instructor on 2013-10-28
here my config info..

 ALSA information is located at [http://www.alsa-project.org/db/?f=4e3b4722ec4d13d0b98b4520b273d340b0881676](http://www.alsa-project.org/db/?f=4e3b4722ec4d13d0b98b4520b273d340b0881676)

thx

---

### Post by OS Instructor on 2013-10-28
aj..  i did use a "pipe cleaner" to try and "clean out" the audio port... no avail..  thx for responding...


 NOTE:  

if i boot up with the headset "in"  then remove the headset... the laptop speakers dont turn on... it will only play through headset jack.
like wise, if the headset is left out during boot up the speakers will always be on, but the headset still works, but speakers remain on.

so i think the audio jack "switch" works.. (not sure if it's "switch" or a "votage detect", idk)

---

### Post by Yellow Pasque on 2013-10-29
Let's try latest driver and see if it fixes it: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

---

### Post by OS Instructor on 2013-10-29
OK, Done!

tested....  no difference.. :( :(

(but i got the latest driver installed :) )

---

### Post by olli-sylvanne on 2013-10-30
Had the same problem. Installed the driver as advised. After this:
When I open the music section with File manager, speakers are on and if I connect the headset, both go quiet. 
But when I open Rhytmbox and start music,  it works allright: speakers go quiet when haedset plugged.
THANK YOU FOR ADVISE.

---

