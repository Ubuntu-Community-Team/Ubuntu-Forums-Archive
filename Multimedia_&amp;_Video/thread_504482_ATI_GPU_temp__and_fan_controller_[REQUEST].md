---
title: "ATI GPU temp  and fan controller [REQUEST]"
date: 2007-07-19
forum: Multimedia &amp; Video
---

### Post by scarnia on 2007-07-19
Hi to all, I've an ATI X850XT PE ,this works with a high clock and mem rate and if the fan isn't set to spine fast the card get hot.

I've benn searching for an ATI fan controller for linux, with no sucess. I've tried to detect the sensor with lm-sensor, no sucess. I don't know what to do.

I've mailed Ray Adams , author of ATI Tool, a very usefull utility for windows. His app control fan speed and gpu temp without using Radeon drivers, only using the hardware layer with a low level driver to handle the built in i2c controller. This is a copy for the info he mail me:

[PHP]FAN control as well as temperature reading is a very complicated thing. I have no idea how to work with hardware on low level under Linux. Under Windows I have low level driver to access video board registers using I2C (embedded into GPU) controller.

This is not standard I2C controller and you have to work with it using video board PLL registers. Also ATI has 3 kind of I2C controller with different protocols and access modes.
You can find some information in xc/programs/Xserver/hw/xfree86/drivers/ati/r128_video.c file as well in radi2c.c[/PHP]


Well, here my questions: :)
*Is there actually some tool to handle the ATI fan?
*is't possible to modify the fan power changing some values in the ATI open source driver?
*Could someone help me to build a program to handle the fan starting from the info given by Ray Adams?

Thanks to all.

---

### Post by Gan Quan on 2007-08-10
hi scarnia, I have the same problem except my video card is from nvidia, my laptop locks under linux when running programs that need 3d acceleration, always. however, this never happen under windows.
I can't help you but I hope someone else can give us some input, I'm looking for a program that can handle my video card and its fan power under linux too.

---

### Post by toasty_ghosty on 2007-09-05
I too have the same issue, an x850xt, I was wondering if there was a way to mount the fan power wire to a fan controller.

---

### Post by Dropknee on 2007-10-16
I have this same problem, have a ATI X800 XT PE, and the card run freaking hot. Im looking for a solution without success. Someone help us pls.

Thanks

---

### Post by toasty_ghosty on 2007-10-22
When I am gaming I don't want to even know how hot my card gets. If there were something much like rivatuner.

---

### Post by XaTriX on 2007-12-10
I'm interested for a fan control onATI card (i've a X800GTO²) to down the fan-rate on the gpu.

XaT

---

### Post by acoustibop on 2007-12-10
A possible solution, if you have a non-stock GPU cooler with a 12v fan, might be to stick a temperature sensor on the card and use a hardware temperature controller to regulate the fan.

I've never like the coolers that come with graphics cards: even though the coolers are sometimes well thought out, the fans are always rubbish: flimsy, don't move air well enough and noisy - even more so when they get a bit of use.

There are some good, inexpensive coolers on the market that will take an 80mm fan, and with these you can choose your fan: I usually prefer a Panaflo or NMB - quiet, efficient and last forever.  I've seen some good quality ones that will take a 92mm fan, but you must really have heat/noise problems to need those.

Recently I took the stock cooler off an ATI 9800, cut a 60mm to 80mm fan adapter down so the smaller end fit on the fan aperture on the cooler (AIR about 70mm diameter), and superglued it on - removing the rubbish fan and blocking the aperture it mounts on, of course.  Then I put an NMB lowspeed 80mm fan on it.  Pretty much inaudible, and cooled the card far more effectively than the rubbish one did.  In fact, doing this obviates the need for a speed controller; the fan is so quiet, it's no problem to have it running full speed all the time.

The only problems with this cooler are putting it back on the card ensuring that all the heatsinks and the GPU are making good contact, and the fact that, since the fan is right at the front of the card and the cut down adapter does raise it up a bit, it effectively blocks two slots.  But, as I say, it works excellently.

---

### Post by ithasacarb on 2008-01-17
Same problem here.  I got a ATI X1950 Pro.  I need to be able to control this fan.  And with software, not by wiring up a fan to the card.  Thanks in advance if anyone could help us.

---

### Post by XaTriX on 2008-04-04
Any news ?

XaT

---

