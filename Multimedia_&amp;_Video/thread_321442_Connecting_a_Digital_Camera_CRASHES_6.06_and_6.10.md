---
title: "Connecting a Digital Camera CRASHES 6.06 and 6.10"
date: 2006-12-18
forum: Multimedia &amp; Video
---

### Post by mswoon on 2006-12-18
I have a Nikon CoolPix 4300 and I have been downloading the pictures to a laptop that is running Ubuntu 6.06 (Drapper). I also have two desktops that are running 6.10 (Edgy). Recently, the laptop developed heating problems so I have to send it back for repair. The last time, I sent my laptop for repair, I was able to use my desktop to download the pictures. However, today, when I used my desktop, the system freezes! Ping, Ctrl-Alt-Del, Ctrl-Alt-Backspace, all did not work. The system is dead. Only a hard reboot works. 

I tried a few times on the desktop, and once even running tail -f /var/log/messages and a number of other log files. Log messages appear saying that the device is recognized, and then, EVERYTHING died. No further log messages and only a hard reboot works. 

The laptop was running 6.10 for a while, but I didn't like the libnss bug, so I downgraded the laptop back to 6.06, but left the two desktop at 6.10. Thinking that it is a 6.10 bug, I decided to downgrade one of the desktop to 6.06. After one night's work, apt-get update && apt-get upgrade etc etc (and libnss-ldap definitely worked on 6.06, unlike 6.10), it comes time to connect my digital camera and turn the camera on. Wow, it crash again! Exactly like 6.10!

Surprisingly, no one else seems to have the problem. I do have a pretty old system - purchase in 2000, and running AMD Athlon 1.1GHz, but ... this is odd. 

I am thinking that maybe if I do a plain install of 6.06, it might work again, or perhaps even just boot the install CD and see what is the effect of turning on the digital camera. 

Wierd.

P.S. Guess what? Booting from 6.06 install disk, the digital camera worked flawlessly! Seems like there is some problem with the USB software somewhere.

---

