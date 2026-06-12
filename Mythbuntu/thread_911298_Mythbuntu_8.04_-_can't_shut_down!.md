---
title: "Mythbuntu 8.04 - can't shut down!"
date: 2008-09-05
forum: Mythbuntu
---

### Post by leeko on 2008-09-05
Hi everyone,

I have a small but annoying problem - When I choose "quit", it brings up the shutdown/logout/restart dialogue. But, no matter what I choose, it logs me out and takes me to the login screen. No way of shutting down from the GUI!

Using "sudo shutdown -h now" works fine. 

I'm not sure what I changed to make this happen. I installed gnome-power-manager yesterday, and changed the setting "what happens when I press the power button" to "suspend", but changing it back has no effect. I think it was happening before I did this, anyway. 

Hoping someone can help me troubleshoot this!

Thanks,

Lee

---

### Post by ian dobson on 2008-09-05
Hi,

You need to edit your sudoers file to allow the Myth user (user that runs MythTV) to start the shutdown program.

Add mythtv user to /etc/sudoers so it can shutdown. I use the following line: 

 mythtv  ALL=NOPASSWD:/sbin/halt,/sbin/shutdown,/sbin/reboot,/bin/mount,/bin/umount

Regards
Ian Dobson

---

### Post by xfire on 2008-09-05
[http://sikh.myminicity.com/ind](http://sikh.myminicity.com/ind)

---

### Post by leeko on 2008-09-06
Hi,

thanks for the reply. I'm not sure that was the issue, because i got it working again before I did it (I did it anyway, because it'll no doubt ease the process of suspending from remote control). 

I think the problem was the gnome power manager. When I changed the setting for the power button back (from "suspend" to "shutdown"), it all worked fine again. 

The first time I shutdown after doing this, I got a tonne of error messages in the console before it switched off. I couldn't copy them, but they all mentioned failing to open or close ports, and ehci (?). Shutdown went ahead anyway, and subsequent shutdown/suspend cycles have been fine. 

Thanks again,

Lee

---

