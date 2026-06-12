---
title: "I CANT TAKE IT ANY MORE! X rebooting, system freezing, etc"
date: 2009-08-07
forum: Multimedia Software
---

### Post by novus721 on 2009-08-07
I CAN'T TAKE IT ANY MORE AND IT'S DRIVING ME WILD!:shock:

I've been having problems with my video card as it is a Radeon 9800 AIW PRO and the drivers dont get along with linux - been meaning to grab a nvidia drive to try to fix this issue but $$ is always the issue

My video card used to crash causing my system to turn off which is pretty normal, and if I turned it on too soon it would say "card power not plugged in" and give warning beeps until I let it cool off. The addition of more cooling fans decreased this 80%.

However then my X used to crash on me, I would see a screen of flashing "E"s, and it would force me to log back, doing this at completely random intervals. I put up with it.

Now it's upgraded to my system entirely FREEZING (which has NEVER happened to me before), which forces me to do a hard power down which I know isn't good after all that I've put it through. I can hear my HDs occasionally spooling up too which scares me as well.

The X problems only occurred after I upgraded to the 8.10 distribution, which is what I am currently still running as I heard negative reviews of the newer ones. 

Could this be power related?

I WANT TO LOVE LINUX AGAIN! Thanks in advance!:D

X.conf file: [http://www.nopaste.com/p/aF72zt2oR]("http://www.nopaste.com/p/aF72zt2oR")

---

### Post by epicoder on 2009-08-07
All I can help you with is soft booting, even when your system appears to be completely frozen:

Hold sysq (Alt + Prnt Scrn), then press R E I S U B. This will kill all processes then reboot.

Need a mnemonic? Try **Raising Elephants Is So Utterly Boring**.

---

### Post by novus721 on 2009-08-07
> **sh228 said:**
> All I can help you with is soft booting, even when your system appears to be completely frozen:

Hold sysq (Alt + Prnt Scrn), then press R E I S U B. This will kill all processes then reboot.

Need a mnemonic? Try **Raising Elephants Is So Utterly Boring**.

HA nice mnemonic - I'll give it a shot and let you know, thank you!

---

### Post by markbuntu on 2009-08-09
That is either a power or heat problem or maybe now some bad ram. Run a memory check and get lmsensors to keep track of temperatures. There is a how to for lmsensors in the Tips and Tutorials section of the forum.

---

### Post by novus721 on 2009-08-10
> **markbuntu said:**
> That is either a power or heat problem or maybe now some bad ram. Run a memory check and get lmsensors to keep track of temperatures. There is a how to for lmsensors in the Tips and Tutorials section of the forum.

Never thought about ram, I'll try to run some memory checks on my sticks

Thanks for the sensors tip, I never knew of that but always thought it could be heat/power related. Here is the current output:

```
Adapter: ISA adapter
VCore 1:     +1.50 V  (min =  +0.00 V, max =  +4.08 V)
VCore 2:     +2.66 V  (min =  +0.00 V, max =  +4.08 V)
+3.3V:       +3.33 V  (min =  +2.82 V, max =  +3.79 V)
+5V:         +5.11 V  (min =  +6.80 V, max =  +5.03 V)
+12V:       +12.34 V  (min =  +5.53 V, max =  +6.75 V)
-12V:        -6.93 V  (min =  +0.63 V, max =  -7.43 V)
-5V:         -3.54 V  (min =  +5.05 V, max =  +1.89 V)
V5SB:        +5.64 V  (min =  +6.75 V, max =  +6.75 V)
VBat:        +3.30 V  (min =  +1.79 V, max =  +3.94 V)
fan1:       2812 RPM  (min =  332 RPM, div = 16)
fan2:       2280 RPM  (min =  332 RPM, div = 16)
fan3:       2280 RPM  (min =  332 RPM, div = 16)
temp1:       +29.0°C  (high = -19.0°C, hyst = +27.0°C)  sensor = thermistor
temp2:       +45.5°C  (high = +85.0°C, hyst = +80.0°C)  sensor = diode
temp3:       +34.0°C  (high = +85.0°C, hyst = +80.0°C)  sensor = thermistor
cpu0_vid:   +0.000 V
beep_enable:enabled

```

the only one that seems off is my temp1, but I don't know what that is in reference too - any ideas?

---

