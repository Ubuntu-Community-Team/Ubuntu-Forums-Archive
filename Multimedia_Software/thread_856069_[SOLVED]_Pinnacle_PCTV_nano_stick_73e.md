---
title: "[SOLVED] Pinnacle PCTV nano stick 73e"
date: 2008-07-11
forum: Multimedia Software
---

### Post by tchu on 2008-07-11
I have managed to install this TV stick without problems in Ubuntu 8.04 and I thought I should put this on the record to help anyone who may be stuck. I am not a technical person so I cannot comment on the finer points of the commands used here.

For those of you living in the UK, firstly find out the name of your nearest digital TV transmitter using your postcode at [www.digitaluk.co.uk](www.digitaluk.co.uk)

Kaffeine is the only media player I have found out (so far) that can watch digital TV using Pinnacle nano stick. Install the Kaffeine: menu bar > Applications > Add / Remove... > Sound & Video. Look for and install Kaffeine.

Go to command line interface: menu bar > Applications > Accessories > Terminal

Run these line by line:
wget [http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.gz](http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.gz)
tar -xvzf tip.tar.gz
ls -al
## look for a directory starting with "v4l-dvb" and go there ##
cd v4l-dvb-XXXXXXXXX
make
sudo make unload
sudo make install

It is important re-start the computer after all these to ensure everything will work correctly. The 'make' command itself took the longest to run (5 - 10 minutes).

Then plug the TV stick into the USB port, start Kaffeine: menu bar > Applications > Sound & Video > Kaffeine. You should see a 6th button called "6. Digital TV" on the title page.

Go to Kaffeine menu bar > DVB > Channels... > Start Scan to scan for TV signals, click "Select All" at bottom right and then "<< Add Selected" at bottom centre.

---

### Post by tchu on 2008-07-11
Sources and further references:
1. [http://linuxtv.org/wiki/index.php/Pinnacle_PCTV_73e](http://linuxtv.org/wiki/index.php/Pinnacle_PCTV_73e)
2. [http://doc.ubuntu-fr.org/pinnacle_pctv_dvb-t_stick_72e](http://doc.ubuntu-fr.org/pinnacle_pctv_dvb-t_stick_72e)
3. [http://linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers](http://linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers)
Under heading "Case 2..." and point number 2
4. [http://linuxtv.org/repo/](http://linuxtv.org/repo/)
Sections "Access V4L-DVB via web browser" and "How to build the v4l-dvb kernel modules"
5. Instead of running the "wget" line above, you can go to [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb) and download the latest driver by clicking the word "gz" at the end of the 2nd line: "summary | shortlog..."

---

### Post by tchu on 2008-07-16
A Linux kernel upgrade today that came with Ubuntu security updates has the undesirable effect of wiping the driver for the TV stick from the hard disk, and the stick will not function after plugged into the USB port.

So it seems that the driver has to be re-installed every time after kernel upgrades, starting from the 'wget' line.

If anyone knowns how to avoid the trouble of re-installation after each kernel upgrade, please post below.

---

### Post by tchu on 2008-11-01
The new Ubuntu (Intrepid Ibex 8.10) is even cleverer. It doesn't need to download a driver from [www.linuxtv.org](www.linuxtv.org) to work.

Just download Kaffeine player and then plug the TV stick into the USB socket, and you can start watching TV straight away.

** In fact, if you install the driver from linuxtv.org, the TV stick will stop working. **

---

### Post by abcdefghijklmn on 2008-11-02
> **tchu said:**
> The new Ubuntu (Intrepid Ibex 8.10) is even more clever. It doesn't need to download a driver from [www.linuxtv.org](www.linuxtv.org) to work.

Just download Kaffeine player and then plug the TV stick into the USB socket, and you can start watching TV straight away.

** In fact, if you install the driver from linuxtv.org, the TV stick will stop functioning. **

Ok, I installed the v4l driver when I should not have and now the tv is not working anymore in 8.10 and Kaffeine (the blue light on the stick is not lit at startup).  

What should I do to completely reverse my changes?

Thanks!

---

### Post by tchu on 2008-11-02
Sorry, I really don't know. I made that mistake initially, and I had to re-install Intrepid Ibex from scratch all over again.

---

### Post by mgp on 2008-11-06
I'm no expert but before reinstalling I'd try:

"""
wget [http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.gz](http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.gz)
tar -xvzf tip.tar.gz
ls -al
## look for a directory starting with "v4l-dvb" and go there ##
cd v4l-dvb-XXXXXXXXX
make
sudo make unload
sudo make **uninstall**
"""

Do this ONLY if you are about to reinstall as I can't guarantee it will not break something. No idea if this will work but giving it a shot before you decide to reinstall can't hurt. Please feel free to shoot if I'm wrong (quite possible).

PS: If you have just installed or still have the directory and everything in it unchanged you can just "cd v4l-dvb-XXXXXXXXX" and then "sudo make unistall".

---

### Post by haiko2201 on 2009-02-08
> **tchu said:**
> The new Ubuntu (Intrepid Ibex 8.10) is even cleverer. It doesn't need to download a driver from [www.linuxtv.org](www.linuxtv.org) to work.

Just download Kaffeine player and then plug the TV stick into the USB socket, and you can start watching TV straight away.

** In fact, if you install the driver from linuxtv.org, the TV stick will stop working. **

It's working well on my Dell Inspiron 1525n. Webcam runs at the same time :D

---

### Post by tchu on 2009-11-01
The new Kaffeine in Ubuntu 9.10 does not automatically download the necessary codec to play digital TV from this TV stick (ie. gives a rather cryptic error message instead).

To solve this, go to the Synaptic Package Manager and install the "libxine1-ffmpeg" package.

---

