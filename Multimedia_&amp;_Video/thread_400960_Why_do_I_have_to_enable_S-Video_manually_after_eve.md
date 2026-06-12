---
title: "Why do I have to enable S-Video manually after every reboot?"
date: 2007-04-04
forum: Multimedia &amp; Video
---

### Post by diablo75 on 2007-04-04
I have an Nvidia GeForce 5500.  I use the Nvidia driver settings app located Applications>System Tools.

I'll go into the app, select enable on the TV-out, then change it to "Clone" so both screens look the same, and then hit apply.  I'll then confirm the change, and then click on the "Save Settings" button.  And it asks me if I'm sure I want to make an alteration to the xorg.conf file, and I'll say yes.  And that's it....

Thing is...doesn't appear these saved changed....changed anything at all.  I have to turn the TV-Out back on every time I restart the computer.

What's going on?

---

### Post by Titus A Duxass on 2007-04-04
You may want to try and edit your xorg.conf file.
That should cure your problem.

---

### Post by fenian on 2007-04-04
Open nvidia-settings from a terminal with the command....
> 
gksudo nvidia-settings

adjust the settings and click the save to x configuration button.This will write the changes to your xorg.conf file.

---

