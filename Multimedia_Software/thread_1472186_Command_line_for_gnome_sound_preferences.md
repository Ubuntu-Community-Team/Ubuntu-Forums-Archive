---
title: "Command line for gnome sound preferences?"
date: 2010-05-04
forum: Multimedia Software
---

### Post by harfa on 2010-05-04
Is there a way to control the gnome sound preferences widget via the command line? I use optical digital out (IEC958). It works fine. but everytime I reboot there is no sound, I have to go to sound preferences, hardware tab, select my internal audio device, change it from digital stereo duplex to analog surround 5.1, then back to digital stereo duplex, and then the sound works again. I would like to be able to do this via command line so I can write a little startup script and not have to do that every time i reboot. thankyou

---

### Post by r0t on 2010-05-18
*bump*
I've been looking for this too. I can use e.g. amixer from the command line to change volume etc of my devices, but how to I tell gnome which device to use?

---

### Post by Dkkline on 2010-05-18
Not sure if this can help but give it shot

[http://www.zolved.com/synapse/view_content/27985]("http://www.zolved.com/synapse/view_content/27985")

---

### Post by r0t on 2010-05-29
That seems to be exactly what I'm looking for, except that it won't work with Ubuntu 10.04....

---

### Post by okuryazar on 2010-10-17
gnome-volume-control

---

### Post by phd.bigben on 2011-10-03
i had to do exactly the same thing every time i logged on to get my mic working (change to mic 1 and change back to mic 2). after some research, here's the code:

pacmd set-source-port 1 input-microphone-1
sleep 0.1
pacmd set-source-port 1 input-microphone-2
echo "mic fixed"

you can probably adopt this solution to your needs
i put it among the startup applications, skype works like a charm

---

