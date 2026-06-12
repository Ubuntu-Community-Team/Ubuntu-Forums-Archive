---
title: "Network-manager applet... crazy?"
date: 2009-11-09
forum: Networking &amp; Wireless
---

### Post by PauGNU on 2009-11-09
Hi,

Since I installed Ubuntu Karmic, the network-manager applet is having a weird behavior: sometimes (not always), when the desktop starts, it doesn't work at all. At the place where the networ-manager icon should be, there is only something strange (see the picture):
[IMG]http://dl.dropbox.com/u/120126/network-manager-bug.png[/IMG]

If I log out and log in again, it works. 

Any ideas?

Thanks!

---

### Post by bshosey on 2009-11-09
Sometimes I have a black box instead of the icon and I cannot click or right click on the box no menu shows up. And this is only with my 64 bit box and it has an ATI 1250 video.

---

### Post by riknos on 2009-11-09
I upgraded from 9.04 to Karmic a couple of days ago and my wired network - with static IP - didn't work at all to begin with, network shares not mounted and couldn't even ping the router. Network Manager hasn't worked at all for me yet - I am having to ifup eth1 all the time. It doesn't display its icon on the Panel. I have reinstalled NM a couple of times but to no avail. Can anyone help? Please!

---

### Post by YourFuzzyGod on 2009-11-09
I am going to jump on this bandwagon.  Does anyone have any ideas about this?  Sometimes when I log in I get a black box where the NM icon should be.  Clicking the black box gives the applet options (Help, About, Remove from panel, Lock to panel). Ubuntu 9.10 x64 (ATI x1100).

---

### Post by martijntje on 2009-11-11
I have this too and it seems to be getting worse. This morning it only worked on the fourth login.

---

### Post by pdc on 2009-11-11
it's new software guys .......... it's new software ......... you're testing it out ........... you're testing it out ..........

---

### Post by YourFuzzyGod on 2009-11-11
Here's a workaround for the problem:

1. Open a terminal and run:

gedit .run-nm-applet.sh

2. Copy and paste these 2 lines into it and save:

#!/bin/sh
sleep 5 && nm-applet --sm-disable

3. Then set the file as executable. In a terminal run:

chmod +x .run-nm-applet.sh

4. Open System -> Preferences -> Startup Applications
5. Uncheck "Network Manager"
6. Click "Add" and input the following (remember to add your username):

Name: Network Manager (Workaround)
Command: /home/<<USER NAME>>/.run-nm-applet.sh
Comment: <<Leave Blank>>

7. Click "Save"  
8. Log out and back in

I have logged off and back on 5 times and the network manager has come up every time.  I tried adding "sleep 5 &&" to the beginning of the command under the Network Manager entry but it seems to ignore everything after the &&.  That is why I made the file (in case you were wondering).

---

### Post by bshosey on 2009-11-16
I got something for you to try. Go to Synaptic Package Manager and search for network-manager Mark two packages for reinstallation.

network-manager-gnome
network-manager

after the reinstallation it will need to be restarted. System should prompt you for this.

---

### Post by bshosey on 2009-11-20
OK. I have been fighting this issue for about a month now. This has been resolved for me. How I did it was marked all ubuntu one stuff that is install to Reinstall in synaptic and reinstalled the software. All icons work now with no issues. Worked on my amd64 install and i386 install.

---

### Post by cnja on 2009-11-24
Ok guys, got a noob here, installed Ubuntu 9.10 and I have had nothing but head aches with the wireless.  Tried both of the suggestions, reinstalling the network management and network management gnome files. and the .run-applet workaround.  the ONLY way I can get the wireless to work is to pull out the wireless card, wait for a minute or two and then plug it back in, after a few seconds my network connection works.

Tried the wicd file, and the ndiswrapper, no different.

did notice one thing, the connection light on the card comes on, and stays on until I type in my password, the one for accessing the network.

specs.
Dell CPX-j laptop
Oronico Silver card

It appears that Ubuntu recognizes the wireless card, otherwise unplugging and then plugging back in wouldn't work.  (would it??)

any thoughts??????

@bshosey--- "OK. I have been fighting this issue for about a month now. This has been resolved for me. How I did it was marked all ubuntu one stuff that is install to Reinstall in synaptic and reinstalled the software."  not sure what you ment by "How I did it was marked all ubuntu one stuff that is install to Reinstall..." did i miss something?

---

### Post by martijntje on 2009-11-24
cnja: the issues you are having are unrelated to the issue discussed in this topic. It's a better idea to start a separate topic for your problem.

---

### Post by cnja on 2009-11-24
sorry about that, thought it might have been related, will start a new thread.

---

### Post by YourFuzzyGod on 2009-12-01
I completely uninstalled Ubuntu One from my machine and it is still having the black square problem.  Oh well, I will live with my fix for the next few months and reinstall when 10.4 comes out.  Thanks guys.

---

