---
title: "sound setting not saving"
date: 2006-12-10
forum: Multimedia &amp; Video
---

### Post by broekskw on 2006-12-10
hello everyone.finally got my sound card going some what on ubuntu 6.10.i have to use this guide [http://doc.gwos.org/index.php/Compre...olutions_Guide](http://doc.gwos.org/index.php/Compre...olutions_Guide)
and go to this section and follow the direction

update I now recommend using the stable version 1.0.12

The alsa-project route is very similar to the alsa-source route without the module-assistant. First you would have to get the alsa-driver tar from alsa-project then pretty much do configure, make and make install again. However, I do recommend that you make a specific directory when you compile something from source. Remember the name of your soundcard driver and use it place of the blue text below.

mkdir src
cd src
mkdir alsa
cd alsa
sudo apt-get install build-essential linux-headers-$(uname -r)
wget [ftp://ftp.alsa-project.org/pub/drive...1.0.12.tar.bz2](ftp://ftp.alsa-project.org/pub/drive...1.0.12.tar.bz2)
tar -xvjf alsa-driver-1.0.12.tar.bz2
cd alsa-driver-1.0.12
sudo ./configure --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=<enter driver name here e.g. via82xx> --with-oss=yes
sudo make
sudo make install

after this i can type this command into terminal and see my sound card aplay -l then i go into alsamixer and unmute everything and exit then i type this in terminal to save my setting from alsamixer sudo alsactl store 0 then i go into my sudo nano /etc/modules and under the last line type in snd-sbawe and then save file but everytime i reboot i loose everything no more sound card,have to do all again just to get it going again. how do i get everything to save

thanks :mrgreen:

---

### Post by broekskw on 2006-12-10
ok under sudo nano /etc/modules command the modules window opens up and then i use the down arrow key to got under the last line(lp) and type in snd-sbawe and the ctrl + x ,then another screen comes up  Save modified buffer (ANSWERING "No" WILL DESTROY CHANGES) ?                    
 Y Yes
 N No           ^C Cancel

i type yes and then another screen ask me to "
File Name to Write: /etc/modules    
what do i do here just input /etc/modules sbawe??? did that then another screen ask me Save file under DIFFERENT NAME ?  hit yes and the back to terminal mode, but if i go back into  /etc/modules and see if that line is added it is gone, like it was never inputted. what am i doing wrong](*,)

---

### Post by broekskw on 2006-12-10
everyone must be watching nfl :mrgreen:

---

### Post by broekskw on 2006-12-10
just did a reboot after adj winecfg and selecting asla sound but still lost everything, have to reload sbawe again.hope some one reads this and can help find a solution to this problem

---

