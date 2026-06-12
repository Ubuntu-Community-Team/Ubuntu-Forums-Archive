---
title: "Pulseaudio randomly stops working"
date: 2010-11-10
forum: Multimedia Software
---

### Post by jbirdjavi on 2010-11-10
Routinely, while I'm working on my laptop, the sound will randomly stop working and I can only get it back by rebooting.  I can't seem to find any sort of pattern to what gets it to stop working, but I do have the following programs almost always running:  Evolution, Chrome, Transmission, and Pidgin.  I usually notice it first when Pidgin stops beeping when I receive IMs.

In the messages log I see lots of messages like this when the audio stops working:

```
Nov  9 10:35:04 jbirdjavi-l-u pulseaudio[2031]: sink-input.c: Failed to create sink input: sink is suspended.
Nov  9 10:35:42 jbirdjavi-l-u pulseaudio[2031]: last message repeated 7 times
Nov  9 10:38:18 jbirdjavi-l-u pulseaudio[2031]: sink-input.c: Failed to create sink input: sink is suspended.
Nov  9 10:39:29 jbirdjavi-l-u pulseaudio[2031]: last message repeated 8 times
Nov  9 10:40:42 jbirdjavi-l-u pulseaudio[2031]: last message repeated 3 times
Nov  9 11:01:16 jbirdjavi-l-u pulseaudio[2031]: sink-input.c: Failed to create sink input: sink is suspended.
Nov  9 11:02:43 jbirdjavi-l-u pulseaudio[2031]: last message repeated 3 times
Nov  9 11:08:08 jbirdjavi-l-u kernel: [91809.368563] lo: Disabled Privacy Extensions
Nov  9 11:09:25 jbirdjavi-l-u pulseaudio[2031]: sink-input.c: Failed to create sink input: sink is suspended.
Nov  9 11:10:44 jbirdjavi-l-u pulseaudio[2031]: last message repeated 7 times
Nov  9 11:12:42 jbirdjavi-l-u pulseaudio[2031]: sink-input.c: Failed to create sink input: sink is suspended.
Nov  9 11:13:19 jbirdjavi-l-u pulseaudio[2031]: last message repeated 7 times
Nov  9 11:13:19 jbirdjavi-l-u kernel: [92120.417961] lo: Disabled Privacy Extensions
Nov  9 11:13:53 jbirdjavi-l-u pulseaudio[2031]: sink-input.c: Failed to create sink input: sink is suspended.
Nov  9 11:15:14 jbirdjavi-l-u pulseaudio[2031]: last message repeated 3 times
Nov  9 11:19:38 jbirdjavi-l-u pulseaudio[2031]: sink-input.c: Failed to create sink input: sink is suspended.
Nov  9 11:20:44 jbirdjavi-l-u pulseaudio[2031]: last message repeated 3 times
Nov  9 11:21:44 jbirdjavi-l-u pulseaudio[2031]: last message repeated 40 times
Nov  9 11:22:44 jbirdjavi-l-u pulseaudio[2031]: last message repeated 8 times
Nov  9 11:23:24 jbirdjavi-l-u pulseaudio[2031]: last message repeated 4 times
Nov  9 11:23:24 jbirdjavi-l-u pulseaudio[2031]: sink-input.c: Failed to create sink input: too many inputs per sink.
Nov  9 11:24:44 jbirdjavi-l-u pulseaudio[2031]: last message repeated 2 times
```


I'm running Ubuntu 10.10 on a Dell Latitude E6500.  Any thoughts?  Thanks!

---

### Post by lidex on 2010-11-11
Try removing your pulse config files.Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Logout/in.**

No joy? Post this output please:
```
pkill pulseaudio; sleep 2; pulseaudio -vv
```

---

### Post by jbirdjavi on 2010-11-12
Thanks!  Only the ~/.pulse folder existed out of those, but I removed it.  Since it's random I'll have to wait and see if that did the trick or not...

---

### Post by Dr. Feltersnatch on 2010-11-21
I've had this behavior occur since 9.10. What I've found to get audio working again without rebooting is to change the hardware profile to another profile arbitrarily in sound preferences under the Hardware tab. I've also fully removed pulseaudio and added back, but the behavior still exists. I have notice it occurs quite a bit with adobe flash running in any browser or when when there is a high amount of CPU activity. I'll try out this solution to see what the results are. Thanks!

---

### Post by jbirdjavi on 2010-11-22
I haven't had any issues since I deleted my .pulse folder over a week ago.  Plus, I'm now hearing some sounds that I never heard before as well.  :)  Seems that the .pulse folder was the culprit.

---

### Post by lidex on 2010-11-25
> **jbirdjavi said:**
> I haven't had any issues since I deleted my .pulse folder over a week ago.  Plus, I'm now hearing some sounds that I never heard before as well.  :)  Seems that the .pulse folder was the culprit.

Good deal. I wonder how the Doctor came out...

---

