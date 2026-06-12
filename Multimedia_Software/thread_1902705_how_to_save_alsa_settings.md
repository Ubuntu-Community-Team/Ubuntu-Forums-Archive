---
title: "how to save alsa settings ?"
date: 2011-12-31
forum: Multimedia Software
---

### Post by doron387 on 2011-12-31
Hi,
_BACKGROUND_ :
I am using gigabyte w566u laptop, intel core2duo, ubuntu 10.10 64-bit.
everything is working great except for a sound problem :

(1) When I boot into the machine, I have the speaker icon in the notification area and it works fine, 
e.g. I can play music, watch videos etc, change the volume ....
 2 things don't work :
(2) When I start skype, I can hear it ringing and i can hear the person from the other side but the microphone is not responding. after googling it for a while I realised that the problem is in alsa's settings.
I opened alsamixer and I changed the 'mic' option from 'mic' to 'internal mic' because I am using the built-in mic of the laptop. 
and then I can use skype fine.

I then can also use the built-in sound recorder in applications>sound&viseo>sound recorder.

_THE PROBLEM_ :
the problem is that after rebooting, alsa's settings is going back to it's defaults.
after googling it for 2 hours and trying some offers from old posts, among them i have been trying :
(1) to open a terminal and type : 
    **gksudo gedit /etc/pulse/default.pa**
    and comment the line : **load-module module-device-restore**  
(2) to open a terminal and type : **sudo alsactl store**  
    and **sudo alsactl store 0**

nothing happens, when rebooting, again, alsa's settings are the default which means that the 'mic' option is set to 'mic' and not to 'internal mic'.
 
I have been trying to google about alsa and pulseaudio but it is a huge complicated field and from my memory, playing the trial and error game in the audio environment usually makes things wrong unless you really know what you are doing.

so, if somebody understands perfectly what is going on I will appreciate an advice.
 
i have no problem to type commands in terminal and post the output so you'll have all the info needed to solve the problem, but please DO NOT play the trial and error game with my machine, as except for this flaw it works beautifull and i don't wish to ruin it. i rather change the alsa's settings manually when needed skype and not ruin my over whole configuration.

it actually should be very basic solution, it just that I am not swimming in the audio field.


thnks a lot guys.
doron387

---

### Post by doron387 on 2012-01-05
Bump

---

