---
title: "Problems with d-link wireless adapter"
date: 2009-09-10
forum: Networking &amp; Wireless
---

### Post by mac. on 2009-09-10
[U][B]Problem has been solved, thank you for your time.
[/B][/U]

I extremely new to linux and ubuntu(infact I have just installed it this evening). I have dual booted it with the windows vista basic that came on my computer. I previously used a d-link WUA 2340 wireless network adaptor(external), but when I tried to use it while my newly installed ubuntu, it would not recognize it and therefore not allow me to connect to the internet. I read a previous topic([http://ubuntuforums.org/showthread.php?t=331625)which](http://ubuntuforums.org/showthread.php?t=331625)which) is a very similar model, so I tried what it described. The problem started I believe when I had checked "enable multiverse repositories" and tried to use the reload to enable what I had checked. At first a window poped up saying it was installing 1 of 6 somethings... then it closes and a new window pops up saying there was an error(6 it all) for each of these somethings. I was first of all wondering if to complete the steps indicated in the previous topic required an internet connection, and secondly(if not and mine is a messed up case) how would I go about getting the required drivers to enable my ubuntu to run my wireless adaptor.

Please forgive me if I have just made a foolish error/newbie mistake as I really do not have a clue what I am doing.

---

### Post by Villiam on 2009-09-10
I recommend you to install d-link wireless adapter there is a how-to guide. You may like to check the site out over here: [http://jakeyoon.com/2009/09/09/how-to-install-d-link-wua-2340-usb-wireless-adapter-driver-on-ubuntu/](http://jakeyoon.com/2009/09/09/how-to-install-d-link-wua-2340-usb-wireless-adapter-driver-on-ubuntu/)****

---

### Post by mac. on 2009-09-11
So, being completely linux illiterate, I require some assistance with some of the steps in the tutorial...:confused: If someone wouldn't mind helping me out, that would be awesome.

> Step 1. Login as root or use sudo on each step

        su -

This step is completely over my head as far as ubuntu goes, I am really not sure what he is telling me to do.

> Step 2. Install ndiswrapper on Ubuntu

aptitude install ndiswrapper-utils-1.9

Is this already on ubuntu when it is installed? If so where how would I find it(not sure if it relates to the first step or not)



Thats all I need to know to get my started for now... im going to read some ubuntu guides to hopefully get myself ubuntu savvy asap.

---

### Post by t0mppa on 2009-09-11
The tutorial needs Internet access for some of the commands, so you should plug in your wired for it to work. If that's not an option, you'll have to do the downloads on another computer and it will get a little more complex.

About step 1, some of the commands require admin access and your user account does not have that one (security issue). Using sudo infront of any command gives you access temporarily to the root account to perform the required operation. Steps 2, 7 & 8 are the ones requiring root access, but you can use sudo in front of all commands like tutorial says, it just isn't necessary and in general you shouldn't use sudo unless you need to and know what you're doing, since that way you can't do anything stupid and/or irreversible with the root account.

About step 2, it's not installed by default and that's why you have to install it yourself.

Some more clarifications for the tutorial:

Step 3: Run **mkdir ~/d-link && cd ~/d-link** before the wget to create and go to a directory called d-link inside home directory, just so you know where to find the driver in the future, if you need it.
Step 8: Use **gksudo gedit /etc/modules** instead, emacs is not installed to Ubuntu by default.
Step 9: Remember to add the word ndiswrapper on its own line.

---

### Post by mac. on 2009-09-11
Well, more complex is definitly not a good idea for me...

I will connect to the internet via cable and attempt to follow the instructions, post back with results.

---

### Post by mac. on 2009-09-11
okay, so I have gotten up to step 5, finished installing ndiswrapper and the 1.9 thingy it said I needed. It says the code for terminal I need is 

```
ndiswrapper -i 20071112-WUA-2340-S0026/Drivers/WinXP_2K/netA5AGU.inf
```I know this one will not work die to this not being where my wua driver is located, is named the same (neta5agu) it is located: 

desktop/drivers/winxp_2k/neta5agu 

O.O confused more now than I ever knew possible... used to windows

---

### Post by mac. on 2009-09-12
Alright, so my ndiswrapper was not working correctly according to my friend, he recommended ndisgtk and I used that instead, my drivers are now installed properly I think; I am now just trying to set up my wireless network; anyone know a program I can use to do this(where it detects networks instead of me needed to enter all the things like SSID, MAC address and such)

---

### Post by t0mppa on 2009-09-13
Ndisgtk is simply the graphical front end for ndiswrapper. :)

To choose which network to use, click the wireless symbol in the notification at right end of the upper panel (see screenshot) and then pick which network to connect to. Network manager will then try connecting to said network and if it's not open, it will ask for the password.

---

