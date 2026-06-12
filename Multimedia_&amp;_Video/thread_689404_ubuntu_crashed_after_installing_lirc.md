---
title: "ubuntu crashed after installing lirc"
date: 2008-02-06
forum: Multimedia &amp; Video
---

### Post by BXCracer on 2008-02-06
So decided to install lirc to use remote with my playtv pro
i will post all the commands i used to install it:

sudo apt-get install linux-source-2.6.22 linux-headers-`uname -r
sudo tar xvjf /usr/src/linux-source-*.tar.bz2 -C /usr/src/
sudo ln -s /usr/src/linux-source-#kver# /usr/src/linux
sudo ln -s /usr/src/linux /lib/modules/`uname -r`/build

these commands i commed from one how to but then desided not to use it, after that i 
downloaded lirc from they'r website
then did "sudo apt-get install dialog" 
then 
sudo tar xvfz lirc-*.tar.gz ---or--- sudo tar xvfj lirc-*.tar.bz2
cd lirc-*
sudo ./setup.sh (here i chose my card)
sudo make

then got an eror that there is not bttv drivers so i downloaded it and copied to /usr/src/linux-2.6.22-14/drivers/media/video/bt8xx/

after that make still gave me an eror but not the one about bttv drivers
then i started module-assistan and installed lirc-kernel-modules
then i saw that lirc is unsuported by 2.6.22 kernel so i find an russian how-to about how to get it working with 2.6.22

then i added 
alias char-major-81     videodev
alias char-major-81-0   bttv
options bttv            card=37 radio=1 pll=1 tuner=5

to /etc/modprobe.d/bttv
then tryed to modprobe bttv and got fatal error, then restarted the system and got window with low resolution and the mouse wasnt working.

So how can recover ubuntu? is there a way to correctly install lirc?

---

