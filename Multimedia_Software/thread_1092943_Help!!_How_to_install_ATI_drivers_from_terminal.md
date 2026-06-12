---
title: "Help!! How to install ATI drivers from terminal?"
date: 2009-03-10
forum: Multimedia Software
---

### Post by humphreybc on 2009-03-10
Hi, I was trying to get HDMI output running and read somewhere that to do this you needed to use the ATI proprietory drivers. I thought I was running the open source ATI drivers so I removed a whole bunch of ATI related packages and then rebooted... oops!

Now the GUI won't load and i'm stuck in a terminal. How can I install the proprietory drivers from terminal... or at least get the GUI loading again?

Thankyou very much

---

### Post by linuxuser21 on 2009-03-10
Perhaps [this]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") will help.

---

### Post by humphreybc on 2009-03-11
Thanks, I just fixed it myself though. I realised that of course wireless internet wouldn't be working, hence why I was getting errors when I ran

```
sudo apt-get install xserver-xorg-video-ati
```

So I plugged in an ethernet cable and ran that command and it worked.

Cheers

---

### Post by benplanet on 2010-08-20
```
sudo apt-get install xserver-xorg-video-ati 
```

absolutely sensational! that solved my problem as i was stuck in black/white login screen for what seemed like an eternity.

i have learned my lesson though: stay as far away as possible from ATI gpus.


thanks again for the xorg re-installation command with ati settings.

---

