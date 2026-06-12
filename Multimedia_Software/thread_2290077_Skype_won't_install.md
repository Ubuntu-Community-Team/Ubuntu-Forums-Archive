---
title: "Skype won't install"
date: 2015-08-09
forum: Multimedia Software
---

### Post by Nina_W on 2015-08-09
I've tried installing Skype using several methods but not getting anywhere.
I tried from the Skype site which then brings up the normal Ubuntu installed. I click on install, it asks for password and then looks like its installing. But then when its finished the Install button is the instead of the uninstall one. I got the Skype logo on my applications, but nothing happens when I click is (I have tried waiting a while). There seems to be no way to get rid of the logo.

The latest I have tried is this link [https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)  is gets as far as looking like everything is installing then ends with
Fetched 3,376 kB in 4s (682 kB/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package pulseaudio

Can anybody give me any clues? I'm not sure if a previous install is stopping a subsequent one working but I did do an uninstall on the terminal at some point and it still left the logo there. I suspect older instructions aren't working due to Ubuntu and Skype both having updates.

---

### Post by ajgreeny on 2015-08-09
Enable the partner repos in software-sources and you can then install skype from the normal repositories with no difficulties.

---

### Post by Nina_W on 2015-08-11
Thanks for that. Changed the permissions as you suggested.
First install didn't work, looked like it installed but didn't work.
Used the remove button, then reinstalled. Worked that time.

I looks like the logo and possibly other bits of code weren't getting removed until I had a Remove button available, and that was stopping it working. Weird, but working now.

---

### Post by ajgreeny on 2015-08-11
Great!

Please mark as SOLVED from the Thread Tools menu up-top.

---

