---
title: "Volume range not correct"
date: 2010-07-29
forum: Multimedia Software
---

### Post by lamb123 on 2010-07-29
I spent hours and hours digging through this thread, and other random ones, where everything succeeds.  I have an **onboard** **Intel ICH6**.  Its details are located at: [http://alsa-project.org/main/index.p...x:Vendor-Intel]("http://alsa-project.org/main/index.php/Matrix:Vendor-Intel")   (btw, the part of about going and finding your chipset from a dropdown  and the green text is a broken link.  I think it should point here,  instead: [http://alsa-project.org/main/index.php/Matrix:Main](http://alsa-project.org/main/index.php/Matrix:Main)).
[I] 
My resolution ended up being, in the sound preferences, to change the  Connector under Output from "Analog Output/Amplifier" to "Analog Mono  Output/Amplifier" (No Amplifier works too).

I didn't find this advice anywhere.  I was going to give up, and was  poking around, and saw the mono options.  Since onboard speakers are  mono, I gave these choices a try.  So, hopefully, this helps someone  else.  I appreciate this sticky; maybe there should be some information  about how to find the appropriate sound settings in the guide ...  somewhere in the beginning, around where you should check that your  volume is up and your mute is off :smile:


-----------------

This is a quote from sound solutions thread. i had this problem too with ICH6 but now that i have sound i have a new issue. While a normal sound range is 0-100% my sound range is about 0-10% meaning that about if i put my volume on 3% it it as loud as about 30% should be normally.

Any ideas?
[/I]

---

### Post by lamb123 on 2010-07-31
bump

---

### Post by lidex on 2010-08-01
Scroll to this section - Volume range anomalies - of this page:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats)

---

### Post by lamb123 on 2010-08-04
> **lidex said:**
> Scroll to this section - Volume range anomalies - of this page:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats)

Fantastic, all works now. Thanks alot.

---

### Post by lidex on 2010-08-04
You're welcome.

---

