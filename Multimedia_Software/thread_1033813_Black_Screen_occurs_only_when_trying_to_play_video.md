---
title: "Black Screen occurs only when trying to play video file..."
date: 2009-01-07
forum: Multimedia Software
---

### Post by Pyreus on 2009-01-07
Hello, I'm new to Ubuntu and the forums here. I have been searching the message boards about my black screen problem, seems most people have the problem at start up, I do not.

My screen only goes black when I try to play a video file, and it doesn't always do it, only sometimes.

None of the commands work, Ctrl + Alt + F1 or any of that, have tried numerous combinations, and the screen is just black and unresponsive. So, I have to hold the power button down to turn it off and then back on and it is fine again until I try to play another video file.

I am using a Toshiba intel laptop, and running Ubuntu 8.04.

Any help would be greatly appreciated, such as something I can type into the Terminal that will fix it.

---

### Post by Pyreus on 2009-01-07
Should I have posted this in a different forum? This seemed like the appropriate place.

---

### Post by Pyreus on 2009-01-08
Could really use some help.

---

### Post by NickLondon28 on 2009-01-20
I have exactly the same problem on my eeeBox B202 running eeebuntu...

---

### Post by polmir on 2009-01-20
Type in the terminal command:```
dpkg -l | grep mplayer
```and his score on the Send forum.

---

### Post by NickLondon28 on 2009-01-20
I seem to have fixed it by adding this line to the devices section in xorg.conf

Option "FramebufferCompression" "off"

Which I found here: [http://ubuntuforums.org/showthread.php?t=880303&page=4](http://ubuntuforums.org/showthread.php?t=880303&page=4)

I've just watched a DVD using VLC for about 1 hour and no blackouts!

---

