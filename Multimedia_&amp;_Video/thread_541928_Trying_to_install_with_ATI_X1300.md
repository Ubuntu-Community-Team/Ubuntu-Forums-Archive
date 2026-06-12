---
title: "Trying to install with ATI X1300"
date: 2007-09-03
forum: Multimedia &amp; Video
---

### Post by Rei216 on 2007-09-03
I see the sticky on how to install the driver for my video card (ATI Radeon X1300). But I'm under the impression that you need Ubuntu installed already... Or am I wrong? I can't even get Ubuntu to install on my PC, I keep getting an error message. Can anyone help me to install Ubuntu?

---

### Post by phreadom on 2007-09-03
Can you tell us the error message you're getting?

---

### Post by Rei216 on 2007-09-03
The error message is saying "Failed to start X server"... Then after I hit OK it says the X server is disabled then takes me to a login and I put my login info, then it just sits at a prompt...

---

### Post by phreadom on 2007-09-04
Check the end of the file /var/log/Xorg.0.log and see what the error message was that caused the X server to fail to start.

Should have an (EE) to the left of it signifying the error.

That should give us an idea what is causing the failure.

---

### Post by Rei216 on 2007-09-04
How do I check that file? Sorry, I'm new to this...

---

### Post by phreadom on 2007-09-04
type the following:

```
nano /var/log/Xorg.0.log
```

Scroll down to the end of the file and look for the (EE) error(s) and copy them down. When you're done, hit CTRL-X to exit nano.

---

### Post by Rei216 on 2007-09-05
It says, "screens found, but none have usable configuration"...

---

### Post by nzadLithium on 2007-09-08
when it brings up the failed xserver message hit enter until you get a login terminal.

login using the username and password you set in the installer.

now type sudo passwd

set a password there. 

That is you super password the one that gives you access to things you wont normally need to access.

type 
sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r) 
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial /etc/X11/xorg.conf
sudo aticonfig --overlay-type=Xv

with any luck it should go now

use 

sudo shutdown -r now

that will restart hopefully you get a proper gui login after that.

tell me if you have trouble with anything.

This should get it going. its how i did it. but im only getting 20 fps in games so maybe this isnt everything you have to do. I would do it this way to get xserver up though then try some games and see if you get good frame rates. If you don't then you can investigate it further coz you can actually get into a browser now :P

---

