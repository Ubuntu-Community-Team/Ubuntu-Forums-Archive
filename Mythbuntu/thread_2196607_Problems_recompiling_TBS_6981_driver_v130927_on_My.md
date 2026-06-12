---
title: "Problems recompiling TBS 6981 driver v130927 on Mythbuntu 12.04.3 LTS"
date: 2013-12-30
forum: Mythbuntu
---

### Post by ub40dd on 2013-12-30
Hello

This is a TBS 6981 dual tuner dvb-s2 card that has been working in this dedicated mythbuntu machine (on and off) for at least a couple of years. Whenever a new kernel is published I have to recompile the driver, which is a minor pain and sometimes breaks things.

This time the system was messy enough that I restarted it all from scratch, wiping the disk and doing a fresh install of Mythbuntu 12.04.3. However, on recompiling the driver, it doesn't come up in dmesg.

The instructions are in the README_TBS6981 of the zip file of the drivers, [http://www.tbsdtv.com/download/document/common/tbs-linux-drivers_v130927.zip](http://www.tbsdtv.com/download/document/common/tbs-linux-drivers_v130927.zip) , and also at various other places such as [http://www.robclarkey.com/technology/2012/06/05/installing-tbs6981-dvb-s2-dual-tuner-on-ubuntu-11-04/](http://www.robclarkey.com/technology/2012/06/05/installing-tbs6981-dvb-s2-dual-tuner-on-ubuntu-11-04/) .
In summary, after installing the necessary tools:

   69  tar xvfj linux-tbs-drivers.tar.bz2 
   70  cd linux-tbs-drivers
   71  ./v4l/tbs-x86_64.sh 
   72  make && make install
   73  shutdown -r now

After the reboot, the card should appear in 
      dmesg | fgrep frontend

but now it doesn't!

The supplied readme and the various help files / tutorials / blog posts I found on the net all seem to assume that, if the make and make install completed without errors, the card will appear in dmesg. None of them provided any debugging suggestions on what to do if it doesn't. 

Has anyone had a similar experience? Can anyone offer any clues?
Thanks

---

### Post by Gillingham on 2014-01-05
Hi

I recently installed this driver for another card TBS6220 (a DVB-T2 card), while researching the installation I found this [http://linuxtv.org/wiki/index.php/TBS6280]("http://linuxtv.org/wiki/index.php/TBS6280") page.  Which suggested that the permissions were incorrect in the bz2 file, so I wonder if the permissions are wrong whether the tbs-x86_64.sh doesn't give any error messages.

David

---

