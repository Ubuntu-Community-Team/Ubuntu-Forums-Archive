---
title: "High-pitched whine on 5.1 but not stereo duplex"
date: 2010-11-10
forum: Multimedia Software
---

### Post by pyromidget on 2010-11-10
What it says on the tin really.  Whenever i set my sound preferences to 5.1 analog surround i get a sort of high-pitched whine/buzz coming through the speakers along with the regular sound, however if i switch to stereo duplex, it vanishes.

I'm stumped.  Any ideas?

---

### Post by pyromidget on 2010-11-13
Apologies for the bump, but this really is driving me crazy, and i'm no closer to a solution.  I'm not new to linux, but i've never had to deal with sound issues before, so i don't even know where to begin...

---

### Post by pyromidget on 2010-11-13
**update**
A friend was messing around with fade/balance controls and from what we noticed the problem gets worse the more these are messed around with.  possibly a driver issue with 5.1?

---

### Post by pyromidget on 2010-11-30
Bump as the issue is as bad as ever.  If more info is needed, feel free to ask - i'm just not sure what people might need to diagnose.

Cheers all :)

---

### Post by lidex on 2010-12-02
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by M3WDD on 2012-02-27
I know this is a "dead" thread - but I have the same problem.  All correct and functional in Analog Stereo Output but nasty when 5.1 is selected

The whine gets worse if I move sliders balance, fade or sub-woofer to the extreme left or right  output tab on sound preferences, with "Analog Sound 5.1 Output" selected under hardware.  

Here is my data:

[http://www.alsa-project.org/db/?f=c69249295b7ed859e8b8136ff7020a2b9159462e](http://www.alsa-project.org/db/?f=c69249295b7ed859e8b8136ff7020a2b9159462e)

Shame really - I don't remember having this problem some months ago -

---

