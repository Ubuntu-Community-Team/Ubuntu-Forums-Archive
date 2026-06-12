---
title: "Minicom 'minirc.dfl' file does not exist"
date: 2012-08-11
forum: Networking &amp; Wireless
---

### Post by murderd2death on 2012-08-11
K, so I just got this old Catalyst 2900 xl switch from a friend of mine, and hooked it up to an extra comp of mine running ubuntu. I installed minicom and setserial, I got into minicom to configure the serial port. when i exit out and try to save, it says I can't save to 'minirc.dfl' . I went to [this site]("http://www.linuxquestions.org/questions/linux-general-1/my-minicom-configuration-settings-are-not-updated-839032/") that were someone solved the same issue by editing the file directly. I went to the directory through the file manager, only to find that there aren't any files in /etc/minicom/ at all. I even ctrl+h to see if there were any files hidden, and found nothing. 

Now before I go out of my way to just up and invent the file myself, is this odd? is there an update I need to be making or other files that need to exist that I need to gather together or download before I go any further?

---

### Post by bakegoodz on 2012-08-12
You need root permissions to save the serial port settings as default.
```
sudo minicom
```
After you done with the settings, make sure you select > Save setup as dfl
Then run minicom without sudo

---

### Post by murderd2death on 2012-08-14
> **bakegoodz said:**
> You need root permissions to save the serial port settings as default.
```
sudo minicom
```
After you done with the settings, make sure you select 
Then run minicom without sudo

k, i got it to save the .dfl, but when i run it without sudo, i get 
```
minicom: cannot open \dev\tty0: Permission denied
```

when i run it with sudo I get 
```
Welcome to minicom 2.5

OPTIONS: I18n
Compiled on May 2 2011, 10:05:24
Port /dev/tty0

Press CTRL-A Z for help on special keys

CTRL-A Z for help | 9600 8N1 | NOR | Minicom 2.5  | VT102|   Offline
```

the switch is on and plugged in, from the impressions i get from [this site]("http://www.cyberciti.biz/tips/connect-soekris-single-board-computer-using-minicom.html"), i should get a screen looking like [this]("http://files.cyberciti.biz/uploads/tips/2008/02/minicom-in-action.png"). 

Any quick advice or hints before I go through digging up all the manuals? I'm apologize for being a drag, but i'm used to using hyperterminal, and i'm trying to get familiar with minicom for linux. 

regards

edit: 
at this point i'm starting to think that one end of the console cable i have is bad. but i can't be to sure yet.

---

### Post by bakegoodz on 2012-08-15
You probably want to use a serial port and not the virtual terminal. A serial port is /dev/ttyS0 or a USB-serial adapter is /dev/ttyUSB0

The instructions I gave were from memory, but it been at least a year since I used minicom. It is strange that I found Ubuntu only allows root access to my serial adapter now. It has been documented not to need sudo before [http://processors.wiki.ti.com/index.php/Setting_up_Minicom_in_Ubuntu](http://processors.wiki.ti.com/index.php/Setting_up_Minicom_in_Ubuntu)
It worked after I changed permissions of /dev/ttyUSB0, but will change back after reboot. Probably not worth writing a udev rule to modify the device permissions, so I guess just run as sudo or root every time.

---

