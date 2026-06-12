---
title: "Surround with ALC850"
date: 2005-12-25
forum: Multimedia &amp; Video
---

### Post by yohan on 2005-12-25
Im using breezy on Asus A8V with intigrated soundcard Realtek ALC850. In windows Ive tested all the channels and they work fine. In ubuntu when i type:
speaker-test -Dplug:surround51 -c6 
All speakers work fine except the center speaker and LFE. Why is this? Please help me! Has anyone had a similar problem?

in alsamixer everything is unmuted and cranked fully. Also I am using libesd-alsa0.

Do I need to download new drivers from somewhere? How do i reinstall the ones I have?

Here is from aplay -l:
**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Thanks...!

Johan

---

### Post by yohan on 2005-12-26
Nobody has this sound card? Nobody nows? :( 

Would it help to reinstall ubuntu or alsa or something? Maybe OSS?

---

### Post by yohan on 2005-12-27
cant someone just say no hope or something :/

thanks anyways guys

---

### Post by viaciofano on 2005-12-27
if the speaker is ok... eg hardware and is only not working wiht the software change. it has to be a configuration or software issue...im not clued up on the software to advise though.
regards Vincenzo

---

### Post by yohan on 2005-12-28
Now ive checked all the outputs and it seems three of them are outputs for the rear speakers. The one that is suppose to be the center/LFE is not working, im assuming maybe ubuntu thinks its a mic or something. Does anyone know how I manually change these assignments? Is it even possible?

Thanks...

---

### Post by yohan on 2005-12-28
After many hours I have solved this problem by following these instructions:
[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=VIA&card=VIA+southbridge+AC97+audio.&chip=VIA82C686%2C+VIA8233%2C+VIA8233A%2C+VIA8235%2C+VIA8237&module=via82xx](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=VIA&card=VIA+southbridge+AC97+audio.&chip=VIA82C686%2C+VIA8233%2C+VIA8233A%2C+VIA8235%2C+VIA8237&module=via82xx)

After doing this I unmuted everything and the center/lfe still didnt work. I checked Gnome-volume-control out.....everything seemed normal and under options it said that it was in 6ch mode. I changed it to 4ch mode and ran a speaker-test -c6 -Dplug:surround41 which only sounded output out my front left and right speaker. I later flicked it back into 6ch mode and then made the same stupid test ive done so many times now:
speaker-test -c6 -Dplug:surround51

And it worked!

Im not sure what I did but I think one of the extra steps in the url which was not noted in the standard readme did the trick.

---

### Post by yohan on 2005-12-29
I played around with the settings and I think I know what fixed it. I switched from Surround Jack Mode shared to independant. If its not in independant it doesnt work on my system. I have no idea what the difference is but now it works so im happy..

---

### Post by sdyson on 2006-01-02
[QUOTE=yohan]I played around with the settings and I think I know what fixed it. I switched from Surround Jack Mode shared to independant. If its not in independant it doesnt work on my system. I have no idea what the difference is but now it works so im happy..[/QUOTE]
This did the trick for me! Thanks very much for posting it yohan.

---

