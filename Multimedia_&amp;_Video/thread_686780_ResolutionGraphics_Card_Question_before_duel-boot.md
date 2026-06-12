---
title: "Resolution/Graphics Card Question before duel-boot"
date: 2008-02-03
forum: Multimedia &amp; Video
---

### Post by Aiello on 2008-02-03
Well, I am thinking setting up a duel-boot but I have a quick question before hand. While in the LiveCD, I can not get the best resolution on my monitor, 1440x900. When I go to change the screen resolution, it won't even give me an option for 1440x900. My graphics card is  a Nvidia GeForce 6150 SE Graphics with TurboCache and my monitor is a HP w1907. Any help would be greatly appreciated!
-Thanks!

---

### Post by Aquaman420 on 2008-02-03
In the screen and resolution page do you have the widescreen box checked?

---

### Post by Aiello on 2008-02-03
I have checked the widescreen box and selected the Monitor type as a generic LCD 1440x900 because the w1907 model is not under HP. When I click okay, it says that the system must be restarted, or the users logged off, or something like that in order for the changes to take effect. Since I am using the LiveCD, this is pointless as no changes are actually saved. Is there anyway to see if I can get the proper resolution without having to duel-boot first?

---

### Post by hyperair on 2008-02-03
Um try using System->Administration->Screen and Graphics. Or try using nvidia-settings after installing nvidia drivers and restarting X (Ctrl+Alt+Backspace)

---

### Post by Aiello on 2008-02-03
Erm... I did what I said I did in post #3 again (selected 1440x900 and widescreen). I then restarted X like hyper told me and the desktop became about 5 times to big for the screen. I had to scroll down to reach the lower task bar. Hyper, you also suggested to install some nvidia drivers? How would I do that? I am a Linux noob, so things might be a bit slow going.

---

### Post by Aiello on 2008-02-03
Well, I tried enabling the Nvidea restricted driver and then reboot X. All that got me was a black background with a white text command line. I had no idea what to do, so I just shut down the computer. Anyways, please keep the suggestions coming!

---

### Post by Aquaman420 on 2008-02-03
I have an ATI myself so I don't know much about Nvidia but it sounds like your xorg.conf got messed up or that wasn't the correct driver.  To get the default xorg back enter this command in a terminal:

sudo dpkg-reconfigure xserver-xorg    

- and just hit enter to pick the defaults.  You should be back where you started at.  As for the original problem with the resolution I have included an attachment of what the screens and graphics look like for me--- keeping in mind yours would be 1440x900 and not 1680x1050. I think the main thing is to pick "generic" monitor and "plug n play" for the model. With the widescreen ticked and then choose the resolution on the first page that opened  Hope this helps you.

---

### Post by Aiello on 2008-02-09
Well, I went ahead and set up a duel-boot anyways. I then downloaded the restricted driver that was available and my resolution automatically changed to 1440x900. Thanks to everyone for their input! :KS

---

