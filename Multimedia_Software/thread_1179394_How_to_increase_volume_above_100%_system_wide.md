---
title: "How to increase volume above 100% system wide"
date: 2009-06-05
forum: Multimedia Software
---

### Post by ManDay on 2009-06-05
Hello, the speakers of my Laptop are not loud enough for anything. Is there any way to tweak the volume up to an arbitrary level?

And please, just to cut that short: No other suggestions, solutions to whatever problem you might assume. I know it's just a will to help but in this case there is really no need for asking for the why and suggesting another way of solving it.

I'm really looking for a software-wise solution to increase the volume to just ANY level.

---

### Post by MadnessRed on 2009-06-05
> **ManDay said:**
> Hello, the speakers of my Laptop are not loud enough for anything. Is there any way to tweak the volume up to an arbitrary level?

And please, just to cut that short: No other suggestions, solutions to whatever problem you might assume. I know it's just a will to help but in this case there is really no need for asking for the why and suggesting another way of solving it.

I'm really looking for a software-wise solution to increase the volume to just ANY level.

sometimes there are volume meters which are not shown by default. For example with surround sound individual channels may all be low. Enable everything in the volume control applet and see if any of them are not full.

---

### Post by ManDay on 2009-06-05
Everything that is available is turned to 100%. Yet, it's not loud enough. Charge it on the actual audio-file or whatever, it doesnt matter. I just need to normalize to a level which is above the level I hear when everything is at 100%.

---

### Post by ajgreeny on 2009-06-05
> Everything that is available is turned to 100%But is everything that is available actually showing in the volume control?  You may need to set the tracks that show in the control using the Preferences option, or even use **alsamixer** in terminal or gnome-alsamixer for its gui if you prefer.  I would suggest you make sure the PCM is set high enough as that is what can be reduced without knowing it.

---

### Post by airchie on 2009-06-05
I had the same issue but by going through the preferences for every sound device and checking every item then putting every slider to max, that solved it. :)

---

### Post by ddrichardson on 2009-06-05
I've a Dell 1545 which will only adjust the level between nil and whatever it was last set at in Windows (i.e. if it was a 50% in Windows, then that is 100% in Ubuntu), I have no idea why this would be other than a pin out that is in the Windows' driver but not under ALSA.

---

### Post by lovinglinux on 2009-06-05
For videos you could use smplayer, which has an option to amplify the volume. Open smplayer preferences, select "General", then "Audio" tab, then tick "Use software volume control" then set "Max. Amplification" to 200 or 300.

Not a system wide solution, but at least you watch videos properly.

---

### Post by ManDay on 2009-06-06
#4, #5, Yes - everything is set to maximum.

#6, That's weird indeed, did you come across any solution?

#7, Thank you. I'd definitely prefer a more general solution (system wide), though. It goes beyond my own Video and Audio files.

---

### Post by ddrichardson on 2009-06-06
> **ManDay said:**
> #6, That's weird indeed, did you come across any solution?
No, I might email someone in th ALSA project though, now you mention it - it hadn't bothered me 'till now

---

### Post by ManDay on 2009-06-06
Isn't the current ALSA volume stored somewhere? What if I just make a 1.5 out of a 1.0? (I know sounds stupid but I need to keep trying)

---

### Post by ddrichardson on 2009-06-06
> **ManDay said:**
> Isn't the current ALSA volume stored somewhere? What if I just make a 1.5 out of a 1.0? (I know sounds stupid but I need to keep trying)
You can send commands using amixer but having just tried:```
amixer set Master 150% unmute
```It set it to 100%.

---

### Post by cammerv8 on 2009-06-06
> **ddrichardson said:**
> I've a Dell 1545 which will only adjust the level between nil and whatever it was last set at in Windows (i.e. if it was a 50% in Windows, then that is 100% in Ubuntu), I have no idea why this would be other than a pin out that is in the Windows' driver but not under ALSA.

yeah thats what happened to me!! i was like WTF id unaudible or really high ( on my logitech 2.1)  so at least i found a workaround just need to shutdown windows  with max volumen.

thanks ddrichardson

---

### Post by braete on 2009-06-06
with pulse audio you can do that (increase volume above 100%)

install pulse audio device chooser and run it.
click the icon and under manager, device tab, you have a list of devices.
under sinks, double click your card and set the slider to the level you want (up to 480%), but the quality will, ... well, ... it will not be "quite" good

but,  i dont know if the changes are kept after a restart (didnt tried it ...)

---

