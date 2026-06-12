---
title: "Radeon HD 6620G graphics card"
date: 2012-04-27
forum: Multimedia Software
---

### Post by david_d_barnett on 2012-04-27
I have just purchased a Toshiba Satellite L755D-S5130 with an
AMD Radeon HD 6620G graphics card. I installed Ubuntu 10.04
and most things appear to be working smoothly. However, the Ubuntu
does not recognize my graphics card. When I look at System/Preferences/Monitor,
it lists monitor "UNKNOWN". And the only resolution available is 1024 X 768.

I am relatively new to Linux. Could anyone tell me how to install a driver that will allow me 
to get more resolution. I don't care if I am not able to use all of the features of the card.

---

### Post by MonkeyPaw on 2012-04-28
Welcome to the forum. The main issue is that you are using relatively new hardware (AMD Fusion) with a pretty old version of Ubuntu. More than likely if you install the AMD drivers from the "Additional Drivers" application, you will fix your resolution issue, but have problems with lag. 

Moving to 12.04 is probably your best shot, but you might run into a few issues installing until you get the AMD drivers installed.

---

### Post by david_d_barnett on 2012-04-28
> **MonkeyPaw said:**
> Welcome to the forum. The main issue is that you are using relatively new hardware (AMD Fusion) with a pretty old version of Ubuntu. More than likely if you install the AMD drivers from the "Additional Drivers" application, you will fix your resolution issue, but have problems with lag. 

Moving to 12.04 is probably your best shot, but you might run into a few issues installing until you get the AMD drivers installed.

After searching for a solution, I decided that would uograde to 12.04. I think I don'tknow whether 64 bit or 32 bit. What "issues" are you referring to if the AMD drivers are not installed first?

Also what "Additional Drivers" application are you referring to? 

Thanks for the time.

---

### Post by MonkeyPaw on 2012-04-28
The problem you might have is a blank screen during the install. This is pretty common on Llano (your CPU+GPU). The easiest work-around is to plug the laptop into an HDMI display and boot the installer. Install 12.04, reboot, go to System Settings/Additional Drivers (or just type "Additional Drivers" in the launcher lens), and install the AMD Proprietary drivers. The next reboot should enable your laptop display. 

I'm not sure if you'll have the blank screen issue, as the bug was fixed recently and might be merged into the final release of 12.04.

---

### Post by david_d_barnett on 2012-04-29
> **MonkeyPaw said:**
> The problem you might have is a blank screen during the install. This is pretty common on Llano (your CPU+GPU). The easiest work-around is to plug the laptop into an HDMI display and boot the installer. Install 12.04, reboot, go to System Settings/Additional Drivers (or just type "Additional Drivers" in the launcher lens), and install the AMD Proprietary drivers. The next reboot should enable your laptop display. 

I'm not sure if you'll have the blank screen issue, as the bug was fixed recently and might be merged into the final release of 12.04.

They fixed the problem. I installed 12.04 64 bit with no issues and the resolution problem is solved. Right now everything is running good. Thanks for everything.):P

---

### Post by MonkeyPaw on 2012-04-29
Glad to help. Enjoy! :D

Also, you might change your thread to "Solved."

---

