---
title: "Onboard Sound Drv Install Problem"
date: 2006-10-17
forum: Multimedia &amp; Video
---

### Post by Sierra_Dave on 2006-10-17
Hi,

I received this while trying to follow ALSA driver install directions:

bob@bob-desktop:/usr/src/alsa/alsa-driver-1.0.12$ sudo ./configure --with-cards=es1869 --with-sequencer=yes;make;make install
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
bash: make: command not found
bash: make: command not found

I was following these instructions:

"Now unzip and install the alsa-driver package

        bunzip2 alsa-driver-xxx
        tar -xf alsa-driver-xxx
        cd alsa-driver-xxx
        ./configure --with-cards=es18xx --with-sequencer=yes;make;make install "

I got all the files unzipped and installed but the config line gave me this error remark.
Thanks in advance for any help! 
Dave

---

### Post by John.Michael.Kane on 2006-10-17
What hardware is this driver for? most onboard sound devices are supported with the normal install.

---

### Post by PugTheBlack on 2006-10-17
Well to me it looks like you are missing some libraries and stuff..

**sudo apt-get install build-essential ncurses-dev**

**sudo apt-get install linux-headers-2.6.15-27-386**

This should get you on the way to compiling the latest ALSA drivers. Try to run these commands first and then try the **sudo ./configure --with-cards=es1869 --with-sequencer=yes;make;make install** command again 

Oh - actually, the command will work alot better if it looks like this:

**sudo ./configure --with-cards=es1869 --with-sequencer=yes;sudo make;sudo make install**

Because ./configure, make and make install are 3 different commands run after each other you need to add sudo in front of each of them to actually get it to work. ( To be honest I think you may only need "sudo" in front of the "make install" part, but better safe than sorry I guess ) 

After you have installed the new drivers + libs and utils ( and maybe the oss-libs too ), reboot the machine and run "alsamixer" to unmute your soundcard. 

Hope this is some help

-Pug

---

