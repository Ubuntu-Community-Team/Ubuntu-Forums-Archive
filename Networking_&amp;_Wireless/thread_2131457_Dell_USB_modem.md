---
title: "Dell USB modem"
date: 2013-04-01
forum: Networking &amp; Wireless
---

### Post by Terryl2 on 2013-04-01
OK guys, this is getting beyond me, I cant get Ubuntu to use the DIAL up USB modem, I have gone through every post on this site regarding this type of modem, and have got nowhere fast.

 am not a programmer so can anyone provide the commands to set the USB ports up so that Gnome PPP can see them?

All it sees is the com ports, my modem is listed as "dev/ttyACM0" and that is not showng up on the Gnome program

I'm lost.


Oh the type of modem is a "Conexant RD-02-D400" from Dell, it plugs into one of the USB ports and the phone line plugs into it'

---

### Post by Terryl2 on 2013-04-03
Ok, I went and tested this modem in my laptop, it's running XP pro, it found it and it runs fine, I can even dial out, it shows up as a USB device in system hardware, so I know that this modem is working.


OK, how do you get Gnome PPP to see a USB modem?

Is is listed as "dev/ttyACM0" how to change this to "dev/USB0" or should it be "dev/ttyUSB0" ???  so Gnome PPP will find it.

---

### Post by Irihapeti on 2013-04-05
It's been a long time since I used dialup, but I seem to recall doing this:

Open a terminal and enter the command:
```
sudo ln -s /dev/ttyACM0 /dev/modem
```

Then Gnome-PPP may be able to see it.

If it doesn't work, try this:

```
sudo pppconfig
```

When you get to the configure modem part, answer "no" (to having the modem identified automatically) and enter the modem string yourself. That will be either /dev/ttyACM0 or /dev/modem (if you've used the command above).

Once you've finished, you can try to connect with the modem using "pon" to connect, and "poff" to disconnect.

---

### Post by Terryl2 on 2013-04-08
OK got this thing working, I don't know how!!

I did several downloads of network drivers and programs, also an up date of the system software, and **BOINK** something found the modem, and allowed me to setup on /dev/ttyACM0 on Gnome PPP, I can now dial out and connect to the internet with FF or IE.

Thanks for what help was offered, but not knowing what fixed it I cant be of any help back to anyone with the same type of problems.

---

