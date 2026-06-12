---
title: "Hauppauge WinTV-HVR-1600 Woes"
date: 2010-01-28
forum: Multimedia Software
---

### Post by hlygrail on 2010-01-28
Downloaded and installed Mythbuntu 9.10.

Installation was a breeze, but I can't seem to get the tuner card to work.  

I've followed the steps here:  [http://www.mythtv.org/wiki/Hauppauge_HVR-1600](http://www.mythtv.org/wiki/Hauppauge_HVR-1600)

Everything seems to be OK, but when I run the final command to verify that everything was installed correctly (dmesg | grep cx18), nothing happens.  It simply returns to the prompt awaiting the next command.

Any suggestions?

There's no nvidia card installed, so that's out of the equation.


Thanks,
Chris

---

### Post by sports.car.guy on 2010-01-29
> **hlygrail said:**
> Downloaded and installed Mythbuntu 9.10.

Installation was a breeze, but I can't seem to get the tuner card to work.  

I've followed the steps here:  [http://www.mythtv.org/wiki/Hauppauge_HVR-1600](http://www.mythtv.org/wiki/Hauppauge_HVR-1600)

Everything seems to be OK, but when I run the final command to verify that everything was installed correctly (dmesg | grep cx18), nothing happens.  It simply returns to the prompt awaiting the next command.

Any suggestions?

There's no nvidia card installed, so that's out of the equation.


Thanks,
Chris

Running 9.10 all you needed to do is install the firmware package for DVB devices and then run MythTV setup. It should initialize the card and allow for you to get it up and running with MythTV. That was how the WinTV-HVR 950Q was for me setup wise on Kubuntu running as a MythTV server.

---

### Post by hlygrail on 2010-01-29
If I understand the response correctly, the problem is that I walked through the suggestions in the MythTV wiki?  That I "over corrected"?

Is the easiest solution now to reinstall Mythbuntu and try again?

---

### Post by sports.car.guy on 2010-01-29
> **hlygrail said:**
> If I understand the response correctly, the problem is that I walked through the suggestions in the MythTV wiki?  That I "over corrected"?

Is the easiest solution now to reinstall Mythbuntu and try again?


Yeah you walked through the MythTV wiki and it was out of date. They have updated it to reflect that 9.10 has the firmware on some of the other cards, seems not the 1600.

Reinstall might be a little overkill. I mean if you went through, did all of the things most cards have listed prior to 9.10, such as a kernel compile and update of v4l I would consider it though. If you are just getting into the setup of the machine and haven't moved everything over, etc, it could be a lot quicker then trouble shooting.

---

### Post by SupraGuy on 2010-02-01
> **sports.car.guy said:**
> Running 9.10 all you needed to do is install the firmware package for DVB devices and then run MythTV setup.
Okay, I've been using Unix/Linux for a long time, but Myth (And tuner cards in general) are new to me. Where does one get the DVB package, and how does one install it?
 
I want to get rid of the plethora of devices that I have hanging around the TV, and get it set up to just have a Mythbox doing everything from TV to DVD to music, and when a Linux blu-ray player becomes available, add that, too. With luck I can use the inputs on the card to get the Wii connected.
 
I was trying with 9.04, but it looks like 9.10 will be a better bet, so it's fresh installation time...  again...

---

