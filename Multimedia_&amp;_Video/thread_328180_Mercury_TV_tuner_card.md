---
title: "Mercury TV tuner card"
date: 2006-12-30
forum: Multimedia &amp; Video
---

### Post by azure_look on 2006-12-30
Hi,
With Ubuntu, its been a love at first sight...I just love it.. Its so much more better than Mandrake or Redhat linux..and damn fast too

Only two things are really coming between me and a lifelong love affair with Ubuntu, for which I keep visiting my other mistress WinXP.
My tv card does not work in Ubuntu for some reason. The tuner card details and Ubuntu version details are

Ubuntu 6.06 LTS - Dapper Drake 
Company: Mercury TV tuner card.
Vendor: (from Device manager) Philips Semiconductors
Device: SAA7130 Video Broadcast Decoder

Have attached the screenshot of the same.

I have tried  TVtime, mplayer..Gxine to get it to run... and all I get is a black screen....
Have attached screen shots of what happens when I do thatPlease tell me what do I do....I keep booting into winxp to watch some TV..which is pretty irritating...
HEELLP..

TheLook..

---

### Post by 1337 on 2006-12-30
Hey, other tuner than you but I found some info about yours, try this:

> sudo rmmod saa7130
sudo modprobe saa7130 card=2 tuner=3

And see that thread: [http://ubuntuforums.org/showthread.php?t=170870](http://ubuntuforums.org/showthread.php?t=170870)
I hope it gonna be helpful.

Regards

---

### Post by azure_look on 2006-12-31
thanks,
that helped!! ...have sound too...!! but only one problem.. I am using TVtime and even after I run tvtime-scanner, I  do not get all the channels as in Windows...Frequencies are detected but when I go to that channel, all I get is static.
What I also did was modify the stationlist.xml of tvtime with frequency list from windowsXP, so that I can compare one-one.  Same frequency which works in windows does not work in TVtime. Did you face similar problem? any other software for tv which works better.??

---

### Post by 1337 on 2007-01-01
> **azure_look said:**
> thanks,
that helped!! ...have sound too...!! but only one problem.. I am using TVtime and even after I run tvtime-scanner, I  do not get all the channels as in Windows...Frequencies are detected but when I go to that channel, all I get is static.
What I also did was modify the stationlist.xml of tvtime with frequency list from windowsXP, so that I can compare one-one.  Same frequency which works in windows does not work in TVtime. Did you face similar problem? any other software for tv which works better.??

Hello, try to choose frequency from frequency table inside TVtime menu, do not use frequency with name of your country or continent. Try tu use the last one (user defined or something like that) then run tvtime-sanner again it should find all your stations. I hope it works, it worked in my case :)

Regards

---

