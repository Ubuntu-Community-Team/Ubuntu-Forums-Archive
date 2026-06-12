---
title: "Can anybody help NuB with ATI graphics card problem?"
date: 2007-06-01
forum: Multimedia &amp; Video
---

### Post by drakebarimore on 2007-06-01
Can anybody please help me get Ubuntu to work using my PCI Radeon ATI 256MB graphics card? I can load up the ubuntu LIVE CD and get to the desktop, but I can't do much beyond that. Like if I pull up a game like chess or something, the system crashes (well at least it kills the monitor display everything else seems to keep going like the fans leds etc).  And I can't install.

Is there any step by step guide to make these cards work so that absolue beginners can follow along?

This is a new PC build (obviously my first) and I really want to get everything working. I don't have the money to keep putting out for new hardware, so it would really be great if I could get this card working. I have a borrowed card that I must return which is a SLI nVidia card (PCI-E) and it works great without any problems, but I can't keep that card, and I'm out of money for components.

So, can anybody help me get this running right?

---

### Post by eye208 on 2007-06-01
> **drakebarimore said:**
> Like if I pull up a game like chess or something, the system crashes (well at least it kills the monitor display everything else seems to keep going like the fans leds etc).
Does the same thing happen when you run the Live CD in safe graphics mode? Are you using the latest version (7.04) of Ubuntu?

---

### Post by drakebarimore on 2007-06-01
Yes, same thing is safe graphics mode.  Yes 7.04

---

### Post by btechcs on 2007-06-01
What's your config?? 
Have you downloaded the right cd? (32bit or 64bit)
What's the graphic card model and make?

also can you access the terminal?
if so, try running the same program with command line, and post your command line output.

---

### Post by eye208 on 2007-06-01
> **drakebarimore said:**
> Yes, same thing is safe graphics mode.
Then the problem might be unrelated to Linux. Safe graphics mode will use the VESA driver with 100% software rendering. It should work with *every* graphics card. :-k

---

### Post by daschmidty on 2007-06-01
You may have better luck using the alternate install cd. I know on edgy my X850 was not detected properly by the livecd and would always crash. With the alternate cd you will be able to install, and on first boot, X may not start but you will get a working console. You can then do 
```
sudo vim /etc/X11/xorg.conf
```
to determine what driver the system guessed was right for your card. In my case it tried the open source "ati" driver which did not work, but changing it to the open source "radeon" allowed me to boot. Worse case scenario change the driver to "vesa" which will basically disable hardware acceleration but at least not crash. (oh and ps. type "i" in vim to insert text)
once your system is up google for the "envy" script and download it. Install it with 
```
sudo dpkg -i (filename)
```
if it complains about failed dependencies type
```
sudo apt-get install -f
```
once envy installs run it. It will download and compile the latest "fglrx" which is the proprietary  driver direct from ati. 
On a sidenote, I am using Kubuntu, but I believe GNOME ubuntu has the "restricted driver manager" that may be able to install fglrx without envy, but i haven't used it.
Hope this helps.

---

