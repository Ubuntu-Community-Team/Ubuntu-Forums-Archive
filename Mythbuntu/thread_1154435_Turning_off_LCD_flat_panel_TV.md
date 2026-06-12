---
title: "Turning off LCD flat panel TV"
date: 2009-05-09
forum: Mythbuntu
---

### Post by azmyth on 2009-05-09
I just purchased a FP and hooked mythbuntu up to it and all works well. I just can't find a way to shut off the fp tv. When I hooked up MB to a computer LCD, I could issue xset dpms off and this would shut the monitor down. The xset works on the FP but the backlight stays on. I can set the FP to auto shutdown after no use but then I have no way of turning it back on. I have a blaster to control the STB which works. For kicks, I irrecorded the LCD TV remote and moved the ir blaster up to the tv and it didn't shutoff the TV. I suspect the ir bl doesn't have enough power or I'd just build a dual head IR bl. I also tried vbetool which had the same effect as xset.

How does everyone else shut the FP off? I want to avoid the two remotes for the WAF.

---

### Post by nickrout on 2009-05-09
> **azmyth said:**
> I just purchased a FP and hooked mythbuntu up to it and all works well. I just can't find a way to shut off the fp tv. When I hooked up MB to a computer LCD, I could issue xset dpms off and this would shut the monitor down. The xset works on the FP but the backlight stays on. I can set the FP to auto shutdown after no use but then I have no way of turning it back on. I have a blaster to control the STB which works. For kicks, I irrecorded the LCD TV remote and moved the ir blaster up to the tv and it didn't shutoff the TV. I suspect the ir bl doesn't have enough power or I'd just build a dual head IR bl. I also tried vbetool which had the same effect as xset.

How does everyone else shut the FP off? I want to avoid the two remotes for the WAF.


My remote is programmable for the on/off switch. I taught it how to turn off the tv. Similarly the volume buttons operate the amplifier audio.

---

### Post by crez79 on 2009-05-09
My lg tv has a serial interface so I can turn it on and off and control many other things with serial commands. I haven't mapped the commands to any remote keys but it wouldn't be that hard. Currently I use a gyration universal remote and just had it learn the tv commands.

---

### Post by azmyth on 2009-05-09
> **crez79 said:**
> My lg tv has a serial interface so I can turn it on and off and control many other things with serial commands. I haven't mapped the commands to any remote keys but it wouldn't be that hard. Currently I use a gyration universal remote and just had it learn the tv commands.
Thanks, this would work well. I checked my owners manual and they have RS232 commands to control the TV. What type of cable do you use and do you have a script to send the proper hex code to the TV that you could share or a link on how to do it?

---

### Post by GuiGuy on 2009-05-09
Sorry to butt in, but on this topic, given all the smarts HDMI is supposed to deliver should it be possible to switch the (LCD) TV on and off using it?

---

### Post by azmyth on 2009-05-09
From looking at the owners manual, the RS232 was purely added to control the fp through a PC so I'd venture to say it's not possible to control through an HDMI.

---

### Post by GuiGuy on 2009-05-09
> **azmyth said:**
> From looking at the owners manual, the RS232 was purely added to control the fp through a PC so I'd venture to say it's not possible to control through an HDMI.

Pity. My previous LCD, a Sharp Aquos,was able to switch on and off based on video signal. Rather brilliant, I think. When we shopped for our current 42", none, not even the high end ones I looked at, had such a feature. And the one I did buy hasn't got RS232 :(

Cheers

---

### Post by azmyth on 2009-05-09
> **GuiGuy said:**
> Pity. My previous LCD, a Sharp Aquos,was able to switch on and off based on video signal. Rather brilliant, I think. When we shopped for our current 42", none, not even the high end ones I looked at, had such a feature. And the one I did buy hasn't got RS232 :(

Cheers
This is the TV I have 40". It'll switch off on no video signal but I didn't see an option to have it turn on when it sees a signal.

---

### Post by crez79 on 2009-05-10
I based what I use off [this.]("http://www.mythtv.org/wiki/LG_42LC7D") It doesn't interpret any replies from the tv, but that isn't all that important to me. 

I just use a standard serial cable. I made one based on a pinout I found on the internet.

I basically use it to switch inputs and raise the volume to play games, and then put the volume back to 0 and switch the input back to hdmi. If I had more usable buttons on my remote I would do more things, but a more complex remote isn't exactly what the wife desires... so it's a trade off.

---

