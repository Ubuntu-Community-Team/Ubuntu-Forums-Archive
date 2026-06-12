---
title: "TV-out not working with my nVidia card"
date: 2008-09-27
forum: Multimedia Software
---

### Post by kung fu buntu on 2008-09-27
I have tried lots of different things, but I'm just not able to get this working :-(
After googling, ubuntuforuing and what else... this is what I ended up with:


The relevant sections of my xorg.conf:
```
        Option          "TwinView"              "True"
        Option          "TwinViewOrientation"   "Clone"
        Option          "TVOutFormat"           "COMPOSITE"
        Option          "TVStandard"            "HD1080p"
        Option          "ConnectedMonitor"      "CRT,TV"
        Option          "MetaModes"             "1280x1024,800x600; 1280x1024,NULL"
        Option          "TVOverScan"            "1.0"

```
What's wrong? What am I missing?
And I'm not exactly sure if I should choose COMPOSITE or SCART, neither if HD1080p or PAL-B.

I have also tried using nvidia-settings, by setting the resolution to Auto for the TV-0 display (in the X Server Display Configuration menu) and then clicking apply.

I have also tried using nvidia-settings, doing the same thing and clicking "save to x configuration file" instead, but it still doesn't work.

And I also tried using the autodetect feature of nvidia-settings, but it doesn't detect my TV.


I don't know if this is important or not.. but here is my hardware setup:
GPU with S-Video <-> S-Video to Composite Video adapter <-> wireless AV transmitter <-> wireless AV receiver with Composite Video output <-> Composite to SCART adapter (it takes as input the audio RCA + Composite Video) <-> plasma TV with HD and all that jazz

Things are plugged nicely because I can hear music in my TV. But as for video, the TV uses the "no signal screensaver".


Any help?!?!? :'(
I'm really going nuts with this... and I have no idea on what is wrong.


Thank you!

---

### Post by kung fu buntu on 2008-09-28
Anybody? :-(

---

### Post by kung fu buntu on 2008-09-28
I've been trying lots of things, but another thing I have noticed is that I get this warning in /var/log/Xorg.0.log:
> 
TwinView requested, but only 1 display devices found.
....
Option "UseDisplayDevice" requested "TV", but no unused TVs are available.



If my xorg.conf didn't have any sort of twinview or tv options (like the ones on my first post), should nvidia-settings detect my TV out when I click on "Detect Displays"???
Because nothing shows up :(

---

### Post by kung fu buntu on 2008-09-29
Any suggestion?

---

### Post by Azazel on 2008-10-17
I hope someone has an answer for you because i am having a very similar problem. it doesnt seem like nvidia-settings does much of anything successfully...

---

### Post by fenian on 2008-10-18
Here is what you need to do to set up twinview clone.
Open up nvidia settings as root with the command...

> sudo nvidia-settings

Click X server display configuration (on the left)
Choose the TV
Click configure button and choose twinview
From the positions pulldown menu choose clones
Click the save to X configuraion file and save.
Reboot the computer (you could just reboot the x server by pressing Ctrl+Alt+Backspace)

---

### Post by Dazzla2008 on 2008-10-23
I am having a similar problem with nvidia. After updating to a newer PC i cant get a good picture on my TV, i know it works because i used to connect to my TV via s-video all the time on my old PC however it was ATI not nvidia! My PC recognises my TV but when i connect the picture is awful, just a red and blue mess but i can make out my desktop... just! Any ideas?? :(

---

### Post by ftugrul on 2009-12-06
Hello,

I had same problem while trying to activate SVDEO out as a separate X screen. I've found the solution, and I'm attaching my working xorg.conf here.

---

