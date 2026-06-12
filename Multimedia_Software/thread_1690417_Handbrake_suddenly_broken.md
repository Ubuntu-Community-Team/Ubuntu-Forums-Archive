---
title: "Handbrake suddenly broken"
date: 2011-02-18
forum: Multimedia Software
---

### Post by Ghost_Mazal on 2011-02-18
Lo Guys , I have been using handbrake for a long time to encode dvd's to mp4. The dvd's always resides on HDD in VIDEO_TS structure.

Previously I always could select the folder as there was an option for that on the bottom left after you selected "source".

Suddenly now that option to read the whole folder is gone. I can only select a single file. I didn't fiddle with it or anything. That option is just suddenly gone.

Can anyone help with a fix please ?

Ubuntu 10.04.2 64 Bit

---

### Post by inobe on 2011-02-18
do you have the handbrake repo?

if yes, that's why, on every updated version, things will change.

but you can select, dev/sr0, things should work nicely if that's the path to your drive.

---

### Post by johntaylor1887 on 2011-02-18
Go to your home folder and do ctrl-H to show your hidden config files. Then go to the .config folder and open it. Then look for the **ghb** folder and delete it. It will regenerate when you open handbrake again. Re-spawning config files often fixes things.

---

### Post by Ghost_Mazal on 2011-02-19
Thank you guys. I found out that you now have to select the folder and not go into the folder itself. Handbrake then scans the folder automatically. Kinda better now than it was.

---

