---
title: "Nvidia 256.53 and Ubuntu 10.04 LTS"
date: 2010-09-20
forum: Multimedia Software
---

### Post by fredo2121 on 2010-09-20
Hello all i am new to Ubuntu/Linux and have spent about a week figuring stuff out... My first mission was to load the Nvidia driver to attain the max performance from my Nvidia 6200 AGP 8X card. I have to say i was a bit nervous but am getting comfortable with this more and more by the day and have to say that i am one step closer to being Windows free lol .....I tried a new install of windows7 but found it a bit sluggish on my P4 2.8GHz with 1 gig of DDR memory. I also tried to get a copy of XP PRO but it is no longer available(aside from bootlegs which i did not want) so this is what worked for me... I have to give credit to a few people on this forum and from other sites which my method is a combo of a few tutorials with some trial and error.... I am running Ubuntu 10.04 LTS so here it is:

1) Download Newest Nvidia drivers from their website
(Mine was 256.53 stable)

2) Open module blacklist as admin: (i use gedit for text file editing)

Code:
sudo gedit /etc/modprobe.d/blacklist.conf

3) Add these lines and save:

Code:
blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv

4) Uninstall any previously installed Nvidia drivers:

Code:
sudo apt-get --purge remove nvidia-*

5)Press Ctrl+Alt+F1 to enter in real terminal mode

6) Enter location where file is located, mine was on desktop
Code:
cd Desktop

7)Stop GDM (Gnome Display Manager)
Code: 
sudo stop gdm

8)Install file(if you press tab after "N" it will automatically complete file name
Code:
sudo sh ./Nxxxxxxxx.run 

9) Choose x.org automatic configuration in the last step

10) Reboot!

Good Luck!

---

