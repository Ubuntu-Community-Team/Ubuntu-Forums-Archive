---
title: "Mythbuntu remote control problems"
date: 2008-04-23
forum: Mythbuntu
---

### Post by Tom Mann on 2008-04-23
Hi all,

I have been investing my time into installing a Mythbuntu/File server recently and come across a few problems. I've managed to figure out a lot of my issues but seem to have come to a complete halt when it comes to the remote control.

I have a Hauppauge USB-Nova-T-Stick, which come with a A415-HPG-WE-A remote control. It is partially supported by Mythbuntu under the HVR-1100 remote, but certain buttons do not work (in particular the OK button!)

After a lot of searching and finding configurations for the remote (none of which worked) I found [http://lircconfig.commandir.com]("http://lircconfig.commandir.com") which can make configurations for you. I built a myth profile (lircrc) and lirc configuration (lirc.conf) and these didn't work either.

I think I've been putting these files in the right places; I have put lircrc into ~/.mythtv/lircrc and ~/.lirc/mythtv, and restarted /etc/init.d/lirc but I still get no OK button in Myth.

I then tried starting the client up manually with lircd -n and attaching to it with irw, irw starting killed lircd with the following error:

> could not get file information for /dev/lirc

Performing a web search on this points to changing hardware.conf to point to lirc0 or lirc1, however these files do not exist in my /dev/ folder (including lirc).

I know the IR sensor is working (as the remote control) as if I type 
```
sudo cat /dev/input/event7 
```
and press buttons on the remote (including the OK button) I get text (garbage text but a response at least) on the screen.

Is there anything in Mythbuntu that could be 'taking over' from lirc and stopping my remote from working correctly, and if so how do I make lirc take over the IR reception?

Finally, any help on getting this to work would be gratefully received. :)

Thanks,
Tom

---

### Post by Tom Mann on 2008-04-23
Never mind - I have success!

[http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_USB2]("http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_USB2")

I needed to change hardware.conf and modify the following lines:

REMOTE_DRIVER="dev/input"
REMOTE_DEVICE="/dev/input/event7"

Now everything works fab! :)

Tom

---

