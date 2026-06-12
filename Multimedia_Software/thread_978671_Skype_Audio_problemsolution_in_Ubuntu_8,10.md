---
title: "Skype Audio problem/solution in Ubuntu 8,10"
date: 2008-11-11
forum: Multimedia Software
---

### Post by Julianz on 2008-11-11
Hello, 

In Hardy skype gave sometimes the "no audio playback' message.
This could be fixed by chosing another driver in Skype - Options - Sound devices - Sound out. In my case I solved it changing from 'default device' to the second in the list (motherboard sound driver).

After an upgrade to Ubuntu 8.10 only the left earphone of the headset was working with skype. This happened on three different computers with Ubuntu in my company. I found a bugreport [http://ubuntuforums.org/showthread.php?t=944742](http://ubuntuforums.org/showthread.php?t=944742) but it is closed so therefore this new one.

The fix was to put the Sound Out setting in Skype to 'pulse'

---

### Post by volkswagner on 2009-09-06
I also had to set all devices to Pulse.  I also had to uncheck the box for "allow skype to adjust audio settings".  If the box is checked, when making a call the app kept setting mic volume to zero.

---

