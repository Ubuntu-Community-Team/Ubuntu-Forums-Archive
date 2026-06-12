---
title: "Philips WiFi Media Connect on Ubuntu"
date: 2010-11-09
forum: Multimedia Software
---

### Post by BudWhite on 2010-11-09
Hello,
I recently installed Ubuntu 10.04 and I would use my tv as desktop, in wireless connection with my notebook. The problem is that on the page [http://www.wifimediaconnect.philips.com/](http://www.wifimediaconnect.philips.com/) I haven't  found the software for Linux. Someone can give me a hand?
Thanks

---

### Post by usyshkin on 2010-11-29
I have the same problem. I have tried ushare, mediatomb and even xbmc, but nothing seems to work.

---

### Post by GlisGlis on 2011-01-09
Seems impossible to connect my Wifi Mediaconnect PTA01 with my laptop under Ubuntu.

I ran Vmware player's Windows XP emulator. There my laptop sees my TV, but the TV doesn't see my laptop.
Trying to send gives the error : Coding error, Load MediaConnect again.

Any idees? :confused:

---

### Post by GlisGlis on 2011-01-17
Found that audiosettings in WindowsXP should be: WFMCVAD.
Still not working in UBUNTU.

---

### Post by Gallako on 2011-11-21
First of all, sorry for my bad english, not a native speaker.

i've managed to make my tv show my vids with ushare.

all you need to do is configure the config file --> /etc/ushare.conf with any text editor.
you need to set up the line 22 "USHARE_DIR=" and type the dirs you want to "share" with your TV.
then, restart the service with: sudo ushare restart and voila, it should be working.

i'm trying to set up my PC in order to not only share files, but use it as monitor as you guys are trying, if anyone made it work, please reply it here so that I stop the google search.. jeje

greetings from argentina! :D

---

### Post by ceciliasp on 2012-12-16
Hi... how can I know what dir should I share with the TV? Is it an ip address or a directory?

Txs
Cecilia

---

