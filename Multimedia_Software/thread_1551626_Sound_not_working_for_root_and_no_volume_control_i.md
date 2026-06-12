---
title: "Sound not working for root and no volume control icon"
date: 2010-08-12
forum: Multimedia Software
---

### Post by rdnrvn on 2010-08-12
Hi,

I'm not able to hear any sounds from my system. The panel does not have the volume control button anymore.
I'm not able to run System -> Preferences -> Sound. I get an error saying "Waiting for sound system to respond"
And if I run 'pavucontrol' in the terminal, I get "Connection failed: Connection refused"

Also recently I've noticed that when I run some commands in the terminal I often get this message "Home directory /root not ours." Can this be related to the sound problem? I am on the system as root.

Please help
Thanks!

---

### Post by ajgreeny on 2010-08-12
Why on earth are you on the system as root, and what exactly do you mean by that statement?  You should only use a gui as user, and at least partly for that reason, the root user account is disabled in ubuntu unless you have gone out of your way to enable it.  If you have done so, I assume you must know a great deal about linux in general and should be able to sort out why you have no sound.

However, the volume control is now in "Indicator applet" which should be on your  panel by default.  I wonder if you have removed it at some time, or perhaps the reason it is not there is because you are running as root.

Run ```
alsamixer
``` in terminal and check that the levels of outputs are not set too low.

Move from slider to slider, and raise and lower levels with the cursor keys;
Mute and unmute with the "M" key.
Tab will move you from "playback" to "capture".
Esc will save and exit.

---

### Post by rdnrvn on 2010-08-12
Solved!

The problem was related to "Home directory /root not ours" I had to change the ownership of the root directory back to root. I dont know how it got changed in the first place. 

In the future installations I will not use/create gui for root.

Thanks.

---

