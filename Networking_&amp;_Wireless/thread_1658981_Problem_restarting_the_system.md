---
title: "Problem restarting the system"
date: 2011-01-03
forum: Networking &amp; Wireless
---

### Post by Chuyg9 on 2011-01-03
Hi everyone, this is my first post here. I posted these topic on Ubuntu's Spanish Web, but no one helped me :S

I have a problem with my **BROADCOM BCM4311 802.11b/g WLAN**... I made a clean installation of **Maverick Meerkat** and everything runs perfect except the card drivers... then I investigated almost a week on the net and finally the problem was solved (I made the installation of some drivers on Synaptics tool, then I wrote some codes on the Terminal to activate the light to turn it blue and the Wi-Fi IS ON AND WORKS!). 

I thought everything was ok, but when _I restarted the laptop, the wifi conections aren't able to be detected so I must re-install the card driver to get it active again_ :S. I really don't know why the card drivers works only when I install them, because restarting the system make them simply don't work.

I read something about changing my user's state (it was 'personalized') to 'administrator', but nothing happened.
Can anyone help me with this? I searched on Ubuntu's web but nothing works.

P.S. It's a Compaq Presario V3000.

(Sorry for my bad writting in English, I am working on that :P)

---

### Post by Chuyg9 on 2011-01-03
Solution by BKRATZ and JACOBSCA: 

Code:
echo wl | sudo tee -a /etc/modules

well, /etc/modules just has lp in it. nothing else.

Well that file contains the modules that are loaded at boot time.
echo wl line above would append wl (which is the name for STA driver) there also so it would load at boot.

Another way would be to 

gksudo gedit /etc/modules

and add a line with just wl below the other one. Gksudo would require your password which would not be seen on the screen at all, not even ****. Just put the password in and press return(enter). It would look like this

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
wl


Just save and reboot when done

---

### Post by bkratz on 2011-01-03
Glad you found what you were looking for!!

---

